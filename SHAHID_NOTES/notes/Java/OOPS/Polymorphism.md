_Polymorphism_ means **“many forms”** — a single entity (method or object) behaving differently based on context.

### Why?

1. Without polymorphism, you write the same code many times for different types.
2. You use lots of if-else checks to handle different cases, making code messy.
3. Adding new types means changing existing code, which can cause bugs.
4. Code gets tightly tied to specific classes, so it’s hard to reuse or change.
5. Fixing or updating one type’s behaviour spreads changes all over the code.

## **Compile-time Polymorphism (Method Overloading)**

- Same method name, **different parameters** (type, number, or order) in the **same class**.
- Decided at **compile time** based on argument list

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

## **Runtime Polymorphism (Method Overriding)**

- Subclass **provides its own version** of a method declared in superclass.
- Decided at **runtime** based on actual object type (not reference type).
- Allows dynamic behavior.

```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();  // upcasting
        a.sound();             // calls Dog’s version at runtime (Dog barks)
    }
}
```

### Upcasting and Downcasting

**Upcasting:** Assigning a subclass object to a superclass reference. Safe and implicit.

```java
Animal a = new Dog();  // upcasting
```

**Downcasting:** Converting a superclass reference back to a subclass type. Needs explicit cast and can fail at runtime if object is not really that subclass.

```java
Dog d = (Dog) a;  // downcasting (safe only if a really refers to a Dog)
```

### Dynamic Method Dispatch

- When you call an overridden method through a **superclass reference**, Java decides **at runtime** which method to execute based on the actual object type.
- This enables **runtime polymorphism**.

```java
Animal a = new Dog();
a.sound();  // Java dynamically dispatches to Dog's sound()
```

