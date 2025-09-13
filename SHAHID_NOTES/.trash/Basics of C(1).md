
Operators - 45
Keywords - 34
Seperators - 14
Constants - 3 (Integer, Real/Float, )
 
### **1. Primary (Basic) Data Types in C**

C provides the following **primary/basic data types**:

| Data Type | Description                      | Size (Typical 32-bit) | Format Specifier |
| --------- | -------------------------------- | --------------------- | ---------------- |
| `int`     | Integer (whole numbers)          | 4 bytes               | `%d` / `%i`      |
| `float`   | Single-precision decimal numbers | 4 bytes               | `%f`             |
| `double`  | Double-precision decimal numbers | 8 bytes               | `%lf`            |
| `char`    | Single character (ASCII)         | 1 byte                | `%c`             |
| `void`    | No value / empty type            | —                     | —                |

### 2. Extended Basic Data Types

##### Integer Modifiers

| Type                 | Size (32-bit) | Range (Signed)                  | Format Specifier |
| -------------------- | ------------- | ------------------------------- | ---------------- |
| `short int`          | 2 bytes       | -32,768 to 32,767               | `%hd`            |
| `unsigned short int` | 2 bytes       | 0 to 65,535                     | `%hu`            |
| `int`                | 4 bytes       | -2,147,483,648 to 2,147,483,647 | `%d`             |
| `unsigned int`       | 4 bytes       | 0 to 4,294,967,295              | `%u`             |
| `long int`           | 4 bytes       | -2,147,483,648 to 2,147,483,647 | `%ld`            |
| `unsigned long int`  | 4 bytes       | 0 to 4,294,967,295              | `%lu`            |
| `long long int`      | 8 bytes       | ±9.22×10¹⁸                      | `%lld`           |

##### Floating-Point Types

| Type          | Size        | Precision          | Format Specifier |
| ------------- | ----------- | ------------------ | ---------------- |
| `float`       | 4 bytes     | ~6 decimal digits  | `%f`             |
| `double`      | 8 bytes     | ~15 decimal digits | `%lf`            |
| `long double` | 12/16 bytes | ~18-19 digits      | `%Lf`            |
### **3. Character Type**

- Stores a single character or small integer.
- Internally stored as **ASCII value** (0–255 in unsigned).

`char ch = 'A'; 

### **4. Void Type**

- Indicates **no value or empty type**.
- Commonly used in:
    - Functions that **return nothing** → `void functionName()`
    - **Generic pointers** → `void *ptr`