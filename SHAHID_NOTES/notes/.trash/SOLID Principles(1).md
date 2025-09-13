

## S - Single Responsibility Principle (SRP)

**" A class should have one, and only one, reason to change. "**

A class should have one, and only one, reason to change. If you find yourself saying “this class also does X,” it’s probably breaking SRP.

**Why?**
- Easier to understand
- Promotes **separation of concerns**

```java
//DON'T
class Report {
    void generateReport() { /* logic */ }
    void printReport() { /* logic */ }
    void saveToDatabase() { /* logic */ }
}
```

```java
//DO
class Report {
    void generateReport() { /* logic */ }
}

class ReportPrinter {
    void printReport(Report report) { /* logic */ }
}

class ReportRepository {
    void saveReport(Report report) { /* logic */ }
}
```


## O – Open/Closed Principle (OCP)

**" Software entities should be open for extension, but closed for modification. "**

You should be able to **add new behaviour** without **modifying existing code**. This prevents introducing bugs into stable code.

**How?**
- Use **interfaces, abstract classes, and polymorphism** to add new features.

```java
//DON'T
class Shape {
    String type;
}

class AreaCalculator {
    double calculateArea(Shape shape) {
        if (shape.type.equals("circle")) {
            return /* circle area logic */;
        } else if (shape.type.equals("square")) {
            return /* square area logic */;
        }
        return 0;
    }
}
```

```java
//DO
interface Shape {
    double calculateArea();
}

class Circle implements Shape {
    double radius;
    public double calculateArea() { return Math.PI * radius * radius; }
}

class Square implements Shape {
    double side;
    public double calculateArea() { return side * side; }
}

class AreaCalculator {
    double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}


Circle circle=new Circle()

AreaCalculator areaCalc=new AreaCalculator(circle);

```


## L – Liskov Substitution Principle (LSP)

**" a program uses a base class, it should be able to use any of its derived classes interchangeably without causing errors or unexpected behaviour. "**

```java
//DON'T
class Bird {
    void fly() { System.out.println("Flying"); }
}

class Ostrich extends Bird {
    void fly() { throw new UnsupportedOperationException("Ostriches can't fly"); }
}
```

```java
//DO
interface Bird {}

interface FlyingBird extends Bird {
    void fly();
}

class Sparrow implements FlyingBird {
    public void fly() { System.out.println("Flying"); }
}

class Ostrich implements Bird {
    // no fly method here
}
```

## I – Interface Segregation Principle (ISP)

**" No client should be forced to depend on methods it does not use. Don’t force me to implement things I don’t need. "**

Instead of one large “fat” interface, create smaller, more specific interfaces. Clients should only know about methods they actually need.

```java
//DON'T
interface Worker {
    void work();
    void eat();
}

class HumanWorker implements Worker {
    public void work() {}
    public void eat() {}
}

class RobotWorker implements Worker {
    public void work() {}
    public void eat() { throw new UnsupportedOperationException(); }
}
```

```java
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class HumanWorker implements Workable, Eatable {
    public void work() {}
    public void eat() {}
}

class RobotWorker implements Workable {
    public void work() {}
}
```

## D – Dependency Inversion Principle (DIP)

**" Depend upon abstractions, not concrete implementations. "**

High-level modules shouldn’t depend on low-level modules. Both should depend on abstractions (interfaces). This makes code **flexible and testable**.

```java
//DON'T
class MySQLDatabase {
    void connect() {}
}

class UserService {
    MySQLDatabase db = new MySQLDatabase();
}
```

```java
//DO
interface Database {
    void connect();
}

class MySQLDatabase implements Database {
    public void connect() {}
}

class MongoDatabase implements Database {
    public void connect() {}
}

class UserService {
    Database db;
    UserService(Database db) { this.db = db; }
}
```




