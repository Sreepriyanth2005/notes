
In Java, a **Collection** is a framework that provides **an architecture to store and manipulate groups of objects**. It’s part of the **Java Collections Framework (JCF)**, which is a set of classes and interfaces that implement commonly reusable collection data structures like **lists, sets, queues, and maps**.

### Why?
- Dynamic Data Handling
- In-Build Data Structures
- Ease of Use
- Standardized API
- Iteration Support 
- Performance 

### Key Interfaces in Collections Framework

- **List:** Ordered collection, allows duplicates. (ArrayList, LinkedList)
- **Set:** No duplicates, unordered (HashSet, LinkedHashSet, TreeSet)
- **Queue:** FIFO structure (LinkedList, PriorityQueue)
- **Map:** Key-value pairs, unique keys (HashMap, TreeMap, LinkedHashMap)

### Collection Interface

- The **`Collection` interface** is the **root interface** in the **Java Collections Framework** (excluding `Map`, which is a separate hierarchy).
- It defines the **basic operations** that can be performed on any group of objects.

📦 Package: `java.util`


#### List Interface 

`List` is a **sub-interface** of the `Collection` interface.  
It represents an **ordered collection (sequence)** of elements where:
- **Insertion order is preserved**.
- **Duplicate elements are allowed**.
- Elements can be accessed by their **index** (position).

**Classes Implementing List**

- **ArrayList** → Dynamic array, fast for search, slow for insert/delete in middle.
- **LinkedList** → Doubly linked list, better for frequent insert/delete.
- **Vector** → Legacy, synchronized version of ArrayList.
- **Stack** → Legacy, LIFO structure (extends Vector).
- **CopyOnWriteArrayList** → Thread-safe, used in concurrency.

#### Set Interface

- A **subinterface** of `Collection`.
- Represents a collection that **does not allow duplicate elements**.
- At most **one null element** (depending on implementation).
- Does **not guarantee order** (except special implementations).

**Classes Implementing Set**

- **HashSet** ->  when order doesn’t matter.
- **LinkedHashSet** -> when you want **insertion order preserved**.
-  **TreeSet** -> when you want **sorted order**.

#### Queue Interface

- A **subinterface** of `Collection`.
- Designed for **holding elements prior to processing**, usually in **FIFO (First In, First Out)** order.
- Some implementations follow **priority ordering** instead of FIFO.

**Classes Implementing Queue**

- `LinkedList` → simple FIFO.
- `PriorityQueue` → elements ordered by priority.
- `ArrayDeque` → efficient double-ended queue.(FIFO + LIFO)


### Map Interface

- A **Map** is a collection that stores **key-value pairs**.
- Each key is **unique**, but values can be **duplicate**.
- A `Map` **does not extend the Collection interface** (it’s a separate hierarchy).
- It is widely used when we want to **associate one object (key) with another object (value)**.

**Classes implementing Map**

- **HashMap** ->No order, fast lookup
- **LinkedHashMap** -> Maintains insertion order
- **TreeMap** -> Sorted by keys

### Iterators

#### Iterator (Universal Traversal Tool)

- Works with **all Collection types** (List, Set, Queue, etc.).
- Provides a **forward-only** way to traverse elements.
- **Important Methods**:
    - `hasNext()` → Checks if there’s another element.
    - `next()` → Returns the next element.
    - `remove()` → Removes the last element returned by `next()`.
#### ListIterator (Only for List types like ArrayList, LinkedList, Vector)

- Extends `Iterator` → allows **bidirectional traversal**
- Can **add** and **set** elements while iterating.
- **Important Methods**:
    - `hasNext(), next()` → forward traversal.
    - `hasPrevious(), previous()` → backward traversal.
    - `add(E e)` → adds an element at current position.
    - `set(E e)` → replaces last returned element.

### Generics

- Generics in Java let you write **type-safe** and **reusable code**.  
- Instead of using `Object` (which can cause runtime errors), you can specify a **type parameter** that works with any data type.

**Generic class Example**

```java
class Account<T> {
    private T accountId;  // can be String, Integer, UUID, etc.
    public Account(T accountId) {
        this.accountId = accountId;
    }
    public T getAccountId() {
        return accountId;
    }
}



 Account<String> acc1 = new Account<>("ACC123");
 Account<Integer> acc2 = new Account<>(456);
```

**Advantages**

- **Type safety** → catches errors at compile time.
- **No casting** → reduces boilerplate code.
- **Reusability** → one generic class works for many data types.
- **Cleaner code** → improves readability.

#### Generics in collections

```java
ArrayList<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");

for (String n : names) {
    System.out.println(n.toUpperCase());
}
```

#### wildcards

- `?` → unknown type
- `? extends T` → upper bound (any subtype of T)
- `? super T` → lower bound (any supertype of T)

**`?` (Unbounded Wildcard → Unknown type)**

- Useful when you **don’t care about the actual type** — only that it’s an `Object`.
- You can **read safely**, but you **cannot add** elements (except `null`).

```java
import java.util.*;

public class UnboundedWildcard {
    public static void printList(List<?> list) {
        for (Object obj : list) {
            System.out.println(obj);
        }
        // list.add("Hi"); ❌ Not allowed, type is unknown
    }

    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob");
        List<Integer> numbers = Arrays.asList(1, 2, 3);

        printList(names);   // works
        printList(numbers); // works
    }
}
```


**`? extends T` (Upper Bounded Wildcard)**

- Used when you want to **read** items as type `T`.
- You **cannot add** new items (except `null`) because the actual subtype is unknown.

```java
import java.util.*;

class Animal {
    void sound() { System.out.println("Animal sound"); }
}

class Dog extends Animal {
    void sound() { System.out.println("Dog barks"); }
}

class Cat extends Animal {
    void sound() { System.out.println("Cat meows"); }
}

public class UpperBounded {
    public static void printSounds(List<? extends Animal> animals) {
        for (Animal a : animals) {
            a.sound(); // ✅ Safe to call
        }
        // animals.add(new Dog()); ❌ Not allowed
    }

    public static void main(String[] args) {
        List<Dog> dogs = Arrays.asList(new Dog(), new Dog());
        List<Cat> cats = Arrays.asList(new Cat(), new Cat());

        printSounds(dogs); // works with subtype
        printSounds(cats); // works with subtype
    }
}
```


**`? super T` (Lower Bounded Wildcard)**

- Useful when you want to **add objects** of type `T` safely.
- Reading only gives you `Object`, since you don’t know the exact supertype.

```java
import java.util.*;

public class LowerBounded {
    public static void addNumbers(List<? super Integer> list) {
        list.add(10);   // ✅ Safe to add Integer
        list.add(20);   // ✅ Safe
        // Integer num = list.get(0); ❌ Not safe, only Object type
    }

    public static void main(String[] args) {
        List<Integer> integers = new ArrayList<>();
        List<Number> numbers = new ArrayList<>();
        List<Object> objects = new ArrayList<>();

        addNumbers(integers);
        addNumbers(numbers);
        addNumbers(objects);
    }
}
```

### Comparable vs Comparator 

#### **Comparable (Natural Ordering)**

- Belongs to **`java.lang`** package.
- A class implements `Comparable<T>` to define its **natural sorting order**.
- Sorting logic is written **inside the class itself** (the object knows how to compare itself).
- Only **one sort sequence** can be defined this way.

```java
class Student implements Comparable<Student> {
    int rollNo;
    String name;

    Student(int rollNo, String name) {
        this.rollNo = rollNo;
        this.name = name;
    }

    // Natural ordering by rollNo
    @Override
    public int compareTo(Student s) {
        return this.rollNo - s.rollNo;
    }
}


List<Student> list = new ArrayList<>();
list.add(new Student(3, "A"));
list.add(new Student(1, "B"));
list.add(new Student(2, "C"));

Collections.sort(list);  // uses compareTo

```

#### Comparator (Custom Ordering)

- Belongs to **`java.util`** package.
- Define sorting **outside the class** (separate logic).
- Can create **multiple sorting strategies** without changing the class itself.
- Useful when you want to sort objects differently in different places.

```java
class SortByName implements Comparator<Student> {
    @Override
    public int compare(Student s1, Student s2) {
        return s1.name.compareTo(s2.name);
    }
}

Collections.sort(list, new SortByName()); // custom comparator
```

