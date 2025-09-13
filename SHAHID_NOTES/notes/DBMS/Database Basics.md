
### Database Model

##### 1. **Hierarchical Model**

- Data stored in a **tree structure** (parent-child).
- Example: Company → Departments → Employees.

##### 2. **Network Model**

- Data stored as **records connected by links (graph)**.
- Example: Student ↔ Courses (many-to-many).

##### 3. **Relational Model (Most Used)**

- Data stored in **tables (rows & columns)**.
- Uses **keys** and **SQL** for queries.
- Example: MySQL, PostgreSQL, Oracle.

#####  4. **Object-Oriented Model**

- Combines **objects + database**.
- Example: Storing multimedia, CAD designs, scientific data.
- Supported in PostgreSQL (object-relational).

### Architecture of DBMS

##### **1-tier**

- DBMS + user on the same machine.
- Example: MS Access (desktop).
##### **2-tier**

- Client → Application Server → DB.
- Example: Java app directly connecting to MySQL.
##### **3-tier (most common)**

- Client → Application Server (business logic) → DB Server.
- Example: Web apps (React frontend → Node.js backend → MySQL DB).


### Components of DBMS

##### 1. Query Processor
##### 2. Storage Manager
##### 3. Database Engine
##### 4. Database Schema & Catalog


