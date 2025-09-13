
**Process**

- A **process** is an independent program in execution.
- Each process has:
    - Its own **memory space** (heap, stack, code, data).
    - Its own **resources** (file handles, sockets, etc.).
- Processes are **isolated** from each other → one crashing doesn’t usually affect others.

**Thread**

- A **thread** is the smallest unit of execution **within a process**.
- Multiple threads in the same process:
    - Share the **same memory space (heap)**.
    - Have **separate stacks** for execution.
- Threads are **lighter** than processes.

**Example:**
- MS Word = process.
- Spell checking, autosave, UI rendering = threads.


### Life Cycle of Thread

- **New**
    - Thread object created (`Thread t = new Thread()`), but not started.
        
- **Runnable**
    - After calling `t.start()`, thread is ready to run.
    - It’s in the **thread scheduler’s queue**.
        
- **Running**
    - The thread scheduler picks it → executes `run()` method.
    - Only one thread per core can be **running** at a time.
        
- **Waiting / Blocked / Timed Waiting**
    - **Waiting**: `wait()` → waits until notified.
    - **Timed Waiting**: `sleep(1000)`, `join(2000)` → waits for a fixed time.
    - **Blocked**: waiting for a resource/lock.
        
- **Terminated (Dead)**
    - Thread finishes execution.


### Thread Creation

#### 1. Extending `Thread` class

- You create a class that **extends `Thread`** and override its `run()` method.
- Start the thread using `start()` (not `run()` directly).

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running: " + Thread.currentThread().getName());
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start(); // creates a new thread
    }
}
```

#### 2. **Implementing `Runnable` interface**

- More flexible because you can extend another class while implementing `Runnable`.
- The `run()` method is defined in the interface.

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable thread: " + Thread.currentThread().getName());
    }
}

public class Main {
    public static void main(String[] args) {
        Thread t1 = new Thread(new MyRunnable());
        t1.start();
    }
}
```

### Thread Methods

**1. start()**
- Starts a new thread and calls its `run()` method internally.
- **Never call `run()` directly** (that would execute on the same thread).

```java
Thread t = new Thread(() -> System.out.println("Hello"));
t.start(); // creates new thread
```

**2. run()**

- Defines the logic a thread will execute.
- It is called automatically by `start()`.

**3. sleep(milliseconds)

- Pauses the current thread for the given time.
- Does **not release lock** if inside a synchronized block.

```java
Thread t = new Thread(() -> {
    try {
        System.out.println("Sleeping...");
        Thread.sleep(1000);
        System.out.println("Awake!");
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
});
t.start();
```

**4. join()**

- `join()` makes the **calling thread wait** until the thread on which `join()` was called has finished execution.

```java
Thread t1 = new Thread(() -> {
    for (int i = 1; i <= 3; i++) {
        System.out.println("t1 running " + i);
    }
});

t1.start();
t1.join(); // main waits until t1 completes
System.out.println("Main thread resumes after t1");
```

**5 . interrupt**

- Signals a thread that it should stop its current task.
- Doesn’t kill the thread directly, but sets an **interrupt flag**.

```java
Thread t = new Thread(() -> {
    try {
        while (!Thread.currentThread().isInterrupted()) {
            System.out.println("Working...");
            Thread.sleep(500);
        }
    } catch (InterruptedException e) {
        System.out.println("Interrupted!");
    }
});

t.start();
Thread.sleep(1500);
t.interrupt(); // requests t to stop
```


**6 . Yield()

- Suggests the thread scheduler to **pause the current thread** and let others run.
- It’s just a **hint**, not guaranteed.

```java
Thread t = new Thread(() -> {
    for (int i = 1; i <= 5; i++) {
        System.out.println(Thread.currentThread().getName() + " - " + i);
        Thread.yield();
    }
});
t.start();
```

- `currentThread()` → current executing thread
    
- `getName()` / `setName()` → thread name
    
- `getId()` → thread ID
    
- `getPriority()` / `setPriority()` → thread priority
    
- `isAlive()` → checks if still running
    
- `isDaemon()` / `setDaemon()` → daemon thread
    
- `getState()` → current state of thread
    
- `activeCount()` → active threads in group

| Method        | Definition                                                                                                                            |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `wait()`      | Causes the current thread to **release the lock and wait** until another thread calls `notify()` or `notifyAll()` on the same object. |
| `notify()`    | Wakes **one** of the threads waiting on this object’s monitor.                                                                        |
| `notifyAll()` | Wakes **all** threads waiting on this object’s monitor.                                                                               |


### Daemon Thread

- Background threads that **run until all user threads finish**.
- JVM exits when **only daemon threads remain**.
- Used for **garbage collection, background logging, etc.**

**Analogy**

- **User threads** → Guests at the party (main program tasks).
- **Daemon threads** → Background staff (cleaning, serving snacks, music).

```java
Thread daemonThread = new Thread(() -> {
    while (true) System.out.println("Daemon running...");
});
daemonThread.setDaemon(true); // must be before start()
daemonThread.start();

System.out.println("Main thread ends, daemon will exit automatically");
```

### Thread Priorities

- Priority is a hint to the thread scheduler about **which thread should run first**.
- Range: `Thread.MIN_PRIORITY = 1` to `Thread.MAX_PRIORITY = 10`.
- Default: `Thread.NORM_PRIORITY = 5`

```java
Thread t1 = new Thread(() -> System.out.println("High priority thread"));
Thread t2 = new Thread(() -> System.out.println("Low priority thread"));

t1.setPriority(Thread.MAX_PRIORITY);
t2.setPriority(Thread.MIN_PRIORITY);

t1.start();
t2.start();
```

### Synchronization

**Race Condition**

A **race condition** occurs when **two or more threads access shared data at the same time** and the result depends on the timing of thread execution.

```java
class Counter {
    int count = 0;

    public void increment() {
        count++;  // not atomic! (read → update → write)
    }
}

public class RaceExample {
    public static void main(String[] args) throws InterruptedException {
        Counter c = new Counter();

        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) c.increment();
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) c.increment();
        });

        t1.start(); t2.start();
        t1.join(); t2.join();

        System.out.println("Final count = " + c.count);
    }
}
```


**synchronized Keyword (Methods & Blocks)**

- **Solution** to race conditions → **synchronize access** to shared data.
    
- When a method/block is `synchronized`, only **one thread at a time** can enter it using that object’s intrinsic lock.

**Synchronized Method**

```java
class Counter {
    int count = 0;

    public synchronized void increment() {
        count++;
    }
}
```

**Synchronized Block**

```java
class Counter {
    int count = 0;

    public void increment() {
        synchronized (this) {  // lock on the current object
            count++;
        }
    }
}
```


**Intrinsic Locks**

- Every Java object has an **intrinsic lock (monitor)**.
- When a thread enters a `synchronized` method/block, it **acquires the lock** of that object.
- While holding the lock, **no other thread** can enter another synchronized method/block of the same object.
- When the thread exits, the lock is **released**.

### Thread Safety Measures

- **Synchronization** (`synchronized`, `ReentrantLock`).
- **Atomic variables** (`AtomicInteger`, etc.).
- **Immutable objects** (cannot be changed once created).
- **Thread-safe collections** (`ConcurrentHashMap`, `CopyOnWriteArrayList`).