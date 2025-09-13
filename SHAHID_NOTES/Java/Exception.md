
## **Checked Exceptions**

- **Definition**: Exceptions that are **checked at compile time** by the compiler.
- If your code **might throw** a checked exception, you must either:
    1. **Handle it** using `try-catch`, OR
    2. **Declare it** using `throws` in the method signature.
- These exceptions represent **recoverable conditions** — situations the program can anticipate and handle.

- **Examples**:
    - `IOException`
    - `SQLException`
    - `ClassNotFoundException`

**Checked** → “You must deal with me now!” (compile-time enforcer)


## **Unchecked Exceptions**

- **Definition**: Exceptions that are **not checked at compile time**.
- They are subclasses of **`RuntimeException`**.
- They usually indicate **programming mistakes** such as:
    - Logical errors
    - Violating array bounds
    - Null pointer access
- You are **not required** to handle them with `try-catch` or `throws`.
- **Examples**:
    - `NullPointerException`
    - `ArrayIndexOutOfBoundsException`
    - `ArithmeticException`

- **Unchecked** → “I’ll surprise you later!” (runtime only)

## try/catch vs throws
### **try/catch**

- **Purpose:** To handle exceptions **inside** the method where they occur.
- **Behaviour:**
    - Code inside the `try` block is monitored for exceptions.
    - If an exception occurs, it is caught by the matching `catch` block.
    - You can recover or take alternative actions right there.
- **Usage:** When you **know how to handle** the exception in the same method.

```java
public void readFile() {
    try {
        FileReader fr = new FileReader("data.txt");
    } catch (FileNotFoundException e) {
        System.out.println("File not found! Please check the path.");
    }
}
```


### **throws**

- **Purpose:** To **declare** that a method **might** throw an exception, but **not handle** it there.
- **Behaviour:**
    - Simply passes the responsibility of handling the exception to the caller of the method.
    - The caller method must handle it with `try/catch` or declare `throws` again.
- **Usage:** When you **don’t want to handle** the exception in the current method, but let the caller handle it.

```java
public void readFile() throws FileNotFoundException {
    FileReader fr = new FileReader("data.txt");
}

public static void main(String[] args) {
    try {
        new MyClass().readFile();
    } catch (FileNotFoundException e) {
        System.out.println("Handled in main method");
    }
}
```

## throw vs throws
### **throw**

- **Purpose:** Used **inside a method or constructor body** to actually _throw_ an exception.
- **Usage:** Followed by a single exception object.
- **Effect:** Stops execution at that point and transfers control to the nearest matching `catch` block (or up the call stack).
- **Can only throw one exception at a time**.

```java
void divide(int a, int b) {
    if (b == 0) {
        throw new ArithmeticException("Cannot divide by zero"); 
    }
    System.out.println(a / b);
}
```


### throws

- **Purpose:** Declares **what exceptions a method (or constructor) _might_ throw** so that the caller knows and handles them.
- **Usage:** Appears in the method signature after parameters.
- **Can declare multiple exceptions**, separated by commas.
- **Compile-time requirement:** If you throw a checked exception inside the method, you must either handle it with `try-catch` or declare it with `throws`.

"Hey, I _might_ throw this exception — be ready for it."

```java
void readFile() throws IOException {
    FileReader fr = new FileReader("file.txt"); 
}
```

