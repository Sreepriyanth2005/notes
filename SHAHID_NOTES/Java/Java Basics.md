
### Stack vs Heap

| *Aspect*              | *Stack Memory*                                                            | *Heap Memory*                                   |
| --------------------- | ------------------------------------------------------------------------- | ----------------------------------------------- |
| **Usage**             | Stores **method call frames**, local variables, and **object references** | Stores **objects** and **instance variables**   |
| **Allocation Type**   | **Static memory allocation**                                              | **Dynamic memory allocation**                   |
| **Lifetime**          | Exists **until method execution ends**                                    | Exists **until Garbage Collector frees memory** |
| **Access Mechanism**  | **LIFO (Last In, First Out)**                                             | Random access via **object references**         |
| **Memory Management** | Managed automatically by JVM (method exit)                                | Managed by **Garbage Collector (GC)**           |
| **Thread Behavior**   | **Thread-specific** (each thread has its own stack)                       | **Shared across all threads**                   |
| **Size**              | Usually **smaller**                                                       | Usually **larger**                              |
| **Speed**             | **Faster** (simple allocation & deallocation)                             | **Slower** (dynamic allocation + GC overhead)   |
| **Stored Data**       | **Primitive variables** and **object references**                         | **Actual objects** and **instance variables**   |
| **Error on Overflow** | **StackOverflowError**                                                    | **OutOfMemoryError (Heap Space)**               |

## JVM Memory Structure

![[Pasted image 20250809211853.png]]

| Entity                      | Storage Location        |
| --------------------------- | ----------------------- |
| Primitive local variables   | Stack                   |
| Object references (local)   | Stack                   |
| Objects and arrays          | Heap                    |
| Static variables            | Method Area (Metaspace) |
| Class bytecode, method code | Method Area (Metaspace) |
| Method parameters           | Stack (local variables) |
| Return addresses            | Stack                   |

#### Execution flow 

.java --> java compiler (javac className) --> convert bytecode --> then below happens 

- **Class Loader:** Loads classes into **Method Area**.
- **JVM Bytecode Interpreter / JIT compiler:** When executing instructions:
    - `new` allocates object memory on **Heap**.
    - Method call pushes a **stack frame** onto the thread’s **Stack**.
    - Local primitives and object references go inside that stack frame.
- The JVM **runtime system** manages these allocations following JVM spec rules.

## Garbage Collection

### Why Garbage Collection?

- Java **automatically manages memory** to prevent memory leaks and dangling pointers.
- Objects on the heap that are **no longer reachable** (referenced) are marked for deletion.

### How GC Works (Simplified)

- The JVM periodically runs the **Garbage Collector**.
- It identifies which objects are **still reachable** by traversing from "GC roots".
- **GC Roots** include:
    - Local variables in all stack frames (references on stack)
    - Static variables in method area
    - JNI references
- Objects not reachable from GC roots are considered **garbage**.
- These objects are then reclaimed to free heap memory.


### Java Native Interface

**Java Native Interface** is a **bridge** between Java and other programming languages (mostly **C or C++**).

It allows Java code to:
- Call **native methods** written in C/C++.
- Be called **from** C/C++ code.
##### Working

1. Java declares a method as `native` (no body in Java).
2. You compile a matching **C/C++ function** that implements it.
3. Java loads the native code at runtime using `System.loadLibrary()`.
4. When Java calls the native method, the JVM hands control to your C/C++ function.

### All Keyword (67)

https://chatgpt.com/share/68aaf7ec-ed68-8004-84a7-3c19e07e7066

### Access Modifiers

https://chatgpt.com/share/68b34e7d-bd10-8004-9743-fdeaa5401383