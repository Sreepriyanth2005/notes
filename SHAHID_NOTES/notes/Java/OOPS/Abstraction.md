
## Abstraction in Java

****Abstraction in Java**** is the process of hiding the implementation details and only showing the essential details or features to the user. It allows to focus on what an object does rather than how it does it

### How to Achieve Abstraction in Java?
Java provides two ways to implement abstraction, which are listed below:

- Abstract Classes (Partial Abstraction)
- Interface (100% Abstraction)

### Abstract Classes and Abstract Methods

- An abstract class is a class that is declared with an abstract 
- An abstract class may have both abstract methods (methods without implementation) and concrete methods (methods with implementation).
- An abstract method must always be redefined in the subclass, making overiding compulsory or making the subclass itself abstract

# Abstract Class

- An abstract is a Java modifier applicable for classes and methods in Java but __not for Variables__.
- Java abstract class is a class that can not be instantiated by itself, it needs to be subclassed by another class to use its properties.
```java
abstract class Shape   
{  
    int color;  
    abstract void draw();  
}
	```

```Java
//Example
class Main{
    public static void main(String[] args){
        Engine streamEngine=new StreamEngine();
        streamEngine.connect();
        streamEngine.start("Stream Engine");
    }
}
abstract class Engine{
    public void connect(){
        System.out.println("Engine Connected");
    }
    abstract public void start(String engineName);
}

class StreamEngine extends Engine{
    public void start(String engineName){
        System.out.println(engineName+" Started. Add on Woods");
    }
}
```

# Interface

An Interface in Java programming language is defined as an abstract type used to specify the behaviour of a class. An interface in Java is a blueprint of a behaviour.

### Key Properties

- The interface in Java is a mechanism to achieve abstraction.
- variables in an interface are public, static, and final.
-  Achieve abstraction and multiple inheritance in Java.\
-  loose coupling

```java
interface Shape {
    void draw();  // abstract method
}

// Class that implements the interface
class Circle implements Shape {
    public void draw() {
        System.out.println("Drawing a circle");
    }
}
```

```java
//Example
class Main{
    public static void main(String[] args){
        Notifier email=new EmailNotification();
        Notifier sms=new SMSNotification();
        Notifier push=new PushNotification();
        
        Notification n1=new Notification(push);
        n1.sendNotification();
    }
}

class Notification{
    private Notifier notify;
    
    Notification(Notifier notify){
        this.notify=notify;
    }
    
    public void sendNotification(){
        notify.send();
    }
}

interface Notifier{
    void send();
}

class EmailNotification implements Notifier{
    public void send(){
        System.out.println("Notification Sent through Email");
    }
}

class SMSNotification implements Notifier{
    public void send(){
        System.out.println("Notification Sent through SMS");
    }
}

class PushNotification implements Notifier{
    public void send(){
        System.out.println("Notification Sent through Mobile message");
    }
}
```
## Relationship Between Class and Interface

![[Intefaces-in-Java-1.webp]]

## ** Default Methods in Interfaces**

- Added in Java 8 to allow **adding new methods to interfaces without breaking old code**.
    
- Useful for providing **optional or common functionality**.
    
- If multiple interfaces provide the same default method, the implementing class **must override it** (to resolve ambiguity).


## **Static Methods in Interfaces**

- Also added in Java 8.
    
- Can only be called using **InterfaceName.methodName()**
    
- Not inherited by implementing classes.

```java
interface MyInterface {
    // Constant
    int VALUE = 10; // public static final by default

    // Abstract method (no body)
    void abstractMethod();

    // Default method (has body, can be overridden by class)
    default void defaultMethod() {
        System.out.println("This is a default method in interface");
    }

    // Static method (belongs to interface, not instance)
    static void staticMethod() {
        System.out.println("Static method in interface");
    }
}
```

## **Multiple Inheritance via Interfaces**

Java **does not allow multiple inheritance** with classes (to avoid the diamond problem),  
but **does allow multiple interfaces** to be implemented by the same class.

```java
// First Interface
interface Engine {
    void start();
}

// Second Interface
interface Radio {
    void play();
}

// Class implementing multiple interfaces
class Car implements Engine, Radio {
    @Override
    public void start() {
        System.out.println("Car engine started");
    }

    @Override
    public void play() {
        System.out.println("Playing music");
    }
}

```

## Diamond Problem

- **Problem:** What if two interfaces have the same **default method**?
- **Java requires** the implementing class to **override** it.

```java
interface A {
    default void greet() {
        System.out.println("Hello from A");
    }
}

interface B {
    default void greet() {
        System.out.println("Hello from B");
    }
}

class MyClass implements A, B {
    @Override
    public void greet() {
        A.super.greet(); // or B.super.greet();
        System.out.println("Hello from MyClass");
    }
}
```