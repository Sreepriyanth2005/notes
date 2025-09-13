
Normalization is the process of **organizing data** in a database into well-structured tables to:

- Reduce **data redundancy** (duplicate data)
- Avoid **insertion, deletion, and update anomalies**
- Maintain **data integrity**

#### Why?

- **Redundancy**: Same data repeated multiple times → wastes space.
- **Update anomaly**: Changing data in one place but forgetting another.
- **Insertion anomaly**: Cannot insert data because some unrelated field is missing.
- **Deletion anomaly**: Deleting one row causes loss of unrelated data.

#### Types of Normalization

##### 1 NF
- No **repeating groups** or arrays.
- Each column must have **atomic values**
- Example:

|CustomerID|Name|Orders|
|---|---|---|
|1|Alice|P1, P2|
|2|Bob|P3|
After  1 NF:

| CustomerID | Name  | OrderID |
| ---------- | ----- | ------- |
| 1          | Alice | P1      |
| 1          | Alice | P2      |
| 2          | Bob   | P3      |
##### 2 NF

- Must be in **1NF**.
- **No partial dependency**: Non-key attributes must depend on the **whole primary key** (applies only if composite primary key exists).

```scss
//Partial Dependency

A non-key attribute depends on part of the composite primary key 
instead of the whole key.
```

|OrderID|ProductID|ProductName|Quantity|
|---|---|---|---|
|O1|P1|Laptop|2|
|O1|P2|Mouse|5|
|O2|P1|Laptop|1|

Problem: `ProductName` depends only on `ProductID`, not `(OrderID, ProductID)`.

**How problem causes?**

- **Update anomaly** – If the product name changes (e.g., “Laptop” to “Gaming Laptop”), you must update it in all rows where `ProductID = P1`.
- **Insertion anomaly** – Can’t insert a new product name without creating a dummy order.
- **Deletion anomaly** – If all orders of a product are deleted, product info is lost.

**After 2NF:**

```scss
OrderDetails(OrderID, ProductID, Price)
Product(ProductID, ProductName)
```

##### 3 NF

- Must be in **2NF**.
- **No transitive dependency**: Non-key attributes should not depend on other non-key attributes.

```scss
//Transitive Dependency

A non-key attribute depends on another non-key attribute, which depends on the primary key
```

|StudentID|StudentName|DeptID|DeptName|
|---|---|---|---|
|S1|Alice|D1|CSE|
|S2|Bob|D2|ECE|
|S3|Charlie|D1|CSE|
- `StudentID → DeptID` ✅
- `DeptID → DeptName` ❌ **(Transitive dependency)**

**How Problem Causes ? **

- **Update anomaly** – If `DeptName` changes, you must update it for all students in that department.
- **Insertion anomaly** – Can’t add a department without adding a dummy student.
- **Deletion anomaly** – If last student of a department leaves, department info is lost.

**After 3NF**

```scss
Student(StudentID, StudentName, DeptID)
Department(DeptID, DeptName)
```

##### BCNF

**For every functional dependency (X → Y), X must be a superkey.**

It’s basically a stronger version of 3NF.

|CourseID|Instructor|Room|
|---|---|---|
|C101|Smith|R1|
|C102|Smith|R1|
|C103|John|R2|
**Why is this NOT in BCNF?**

- Dependency **Instructor → Room** violates BCNF because **Instructor** is not a superkey.
- This means **Room** depends on **Instructor**, not on the whole primary key.

**What causes the problem ?

**Redundancy:**
- The mapping _Smith → R1_ is repeated.
- If Smith’s room changes, we must update multiple rows → **update anomaly**.

**Insertion anomaly:**
- We cannot add the fact _Smith teaches in R1_ without assigning him to a course.

**Deletion anomaly:**
- If we delete all courses taught by Smith, we lose the information about his room.

**After BCNF **

```scss
InstructorRoom(Instructor, Room)  
Course(CourseID, Instructor)
```

##### 4 NF

It is in **BCNF** **and** it has **no non-trivial multivalued dependencies (MVDs)**, except those in which the left side is a superkey.

**What is a Multivalued Dependency (MVD)?**

- Denoted as **A ↠ B**
- Means: if two rows have the same **A**, then all combinations of **B** with other attributes are valid independently.
- This usually happens when an entity has **two or more independent multi-valued facts**.

| StudentID | Hobby | Language |
| --------- | ----- | -------- |
| S1        | Music | English  |
| S1        | Music | French   |
| S1        | Dance | English  |
| S1        | Dance | French   |
**What causes the problem?**

**Redundancy:**  
We are repeating combinations of Hobby and Language even though they are independent.  
If a student learns a **new hobby**, we must pair it with every language → explosion of rows.

**Update anomaly:**  
If S1 learns "Painting", we must insert for every language they know.

**Deletion anomaly:**  
If we delete the last row for "Dance", we might lose info about Dance entirely if it wasn't stored elsewhere.

```scss
StudentHobby(StudentID, Hobby)
StudentLanguage(StudentID, Language)
```

##### 5 NF

- Remove redundancy caused by _join dependencies_ — situations where data in one table actually comes from multiple independent relationships.
- Sometimes a single table is really _three or more separate relationships_ smashed together
- If you store them together, you store the same information many times
- 5NF says: _Split them apart so each table shows only one relationship._

|Project|Vendor|Part|
|---|---|---|
|P1|V1|A|
|P1|V1|B|
|P1|V2|A|
|P2|V1|A|
|P2|V2|A|
**why bad?**

- Which Vendors work on which Projects
- Which Parts are in which Projects
- Which Vendors supply which Parts

**After 5 NF

|Project|Vendor|
|---|---|
|P1|V1|
|P1|V2|
|P2|V1|
|P2|V2|

|Project|Part|
|---|---|
|P1|A|
|P1|B|
|P2|A|

| Vendor | Part |
| ------ | ---- |
| V1     | A    |
| V1     | B    |
| V2     | A    |


### Denormalization

- In highly normalized databases (3NF, BCNF…), data is spread across many tables.
- For every query, the DBMS has to perform multiple **JOIN operations** → which slows down performance, especially for large-scale databases.
- **Denormalization reduces joins by storing related data together**, making queries faster.