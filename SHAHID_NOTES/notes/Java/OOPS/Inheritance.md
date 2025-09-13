Inheritance lets a class (child/subclass) acquire properties and behaviors (fields and methods) of another class (parent/superclass). This promotes code reuse and establishes an **“is-a”** relationship.

## Why?

1. Inheritance lets you reuse code from a parent class.
2. It models real-world “is-a” relationships between classes.
3. Changes in the parent class automatically affect child classes.
4. It enables polymorphism for flexible and dynamic behavior.
5. Inheritance helps organize code in a clear, logical hierarchy.


## Types

![[Pasted image 20250809174618.png|250]]
### Single inheritance

One class inherits from one parent class.

```java
class A {}
class B extends A {}
```

### Multilevel inheritance

Class C inherits from B, and B inherits from A.

```java
class A {}
class B extends A {}
class C extends B {}
```

### Hierarchical inheritance

Multiple classes inherit from one parent class.
```java
class A {}
class B extends A {}
class C extends A {}
```

### Multiple inheritance (via interfaces)

Java does **not** support multiple inheritance with classes (to avoid ambiguity).  
Multiple inheritance can be achieved with interfaces

```java
interface A {}
interface B {}
class C implements A, B {}
```

#### Because

1. To avoid Diamond Problem(until java 8's default method, safely handled)

### Hybrid inheritance 

**Hybrid Inheritance** is a combination of two or more types of inheritance (like single, multiple, multilevel, or hierarchical) in a program.

Since Java doesn’t support multiple inheritance with classes, **hybrid inheritance is achieved using classes + interfaces.**

```java
interface A {
    void methodA();
}

class B implements A {
    public void methodA() {
        System.out.println("B's implementation of A");
    }
}

interface C {
    void methodC();
}

class D extends B implements C {
    public void methodC() {
        System.out.println("D's implementation of C");
    }
}

```



## **extends keyword**

Used by a class to inherit from another class.

```java
class Parent { ... }
class Child extends Parent { ... }
```

## implements keyword

The keyword `implements` is used by a **class** to **implement one or more interfaces**.

```java
interface Flyable {}
class Duck implements Flyable{}
```

### NOTE
- A class can extend another class 
- A interface can extend another interface (even multiple interfaces).
- A class can implements interface
- A interface cannot implements class

## super keyword & super() constructor chaining

- **`super` keyword** refers to the immediate parent class instance.
- Use `super` to:
    - Call a parent class method overridden in the child (`super.methodName()`).
    - Access parent’s fields if hidden by child fields (`super.fieldName`).
- **`super()` constructor call** invokes the parent class constructor.
- In constructor chaining, child constructor calls parent constructor first (either explicitly with `super()` or implicitly if not written).

```java
class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    Dog() {
        super();  // Calls Animal's constructor
        System.out.println("Dog constructor");
    }
    @Override
    void sound() {
        super.sound();  // Call parent method
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.sound();
    }
}
```

## Object

- The **root of the Java class hierarchy**.
- If you write `class MyClass {}`, it’s equivalent to `class MyClass extends Object {}`

#### Common methods in Object class

##### 1. `toString()`

- Returns a **string representation** of the object.
- Default implementation returns a string like:  
    `ClassName@HashCodeInHex`
- Often **overridden** to provide meaningful info about the object’s state.

```java
class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person("Alice", 30);
        System.out.println(p);  // Calls p.toString() automatically
    }
}
```


#####  2. `equals(Object obj)`

- Checks if **this object is equal to another object**.
- Default implementation in `Object` compares **memory addresses** (same object).
    
- Usually **overridden** to compare **contents or logical equality** (like comparing two `Person` objects by name and age).

##### 3 . hashCode()

- Returns an **integer hash code** representing the object.
- Used in hash-based collections like `HashMap`, `HashSet`.
- If you override `equals()`, you must also override `hashCode()` so equal objects produce the same hash code.
- Default implementation returns a hash based on memory address.

```java
class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
	public int hashCode() {
        return Objects.hash(name, age);
    }
}

public class Main {
    public static void main(String[] args) {
	    Person p1 = new Person("John", 25);
	        Person p2 = new Person("John", 25);
        System.out.println(p1.hashCode() == p2.hashCode());  // true
    }
}
```

##### 4 . Clone()

- Creates and returns a **copy (clone)** of the object
- By default, it performs a **shallow copy** of the object’s fields.
- The class must implement the `Cloneable` interface to allow cloning; otherwise, `clone()` throws `CloneNotSupportedException`.

```java
class Person implements Cloneable {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();  // Shallow copy
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + "}";
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            Person p1 = new Person("Charlie", 40);
            Person p2 = (Person) p1.clone();
            System.out.println(p1);
            System.out.println(p2);
        } catch (CloneNotSupportedException e) {
            e.printStackTrace();
        }
    }
}
```

##### 5 . finalize()

- Called by the **Garbage Collector** before object memory is reclaimed.
- Used to perform cleanup (like closing files or releasing resources).
