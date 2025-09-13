
### What?

- SQL is a **domain-specific language** designed for managing data stored in a **Relational Database Management System (RDBMS)**.
- It allows you to **create, read, update, and delete (CRUD)** data in databases.

### Why?

- Data Management
- Data Querying
- Data Manipulation
- Data Definition
- Data Security

### SQL vs NoSQL

| Feature             | SQL (Relational Databases)                                       | NoSQL (Non-Relational Databases)**                                                        |
| ------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **Full Form**       | Structured Query Language                                        | Not Only SQL                                                                              |
| **Data Model**      | Structured → Tables (rows & columns)                             | Flexible → Document, Key-Value, Column, Graph                                             |
| **Schema**          | Fixed schema (predefined structure required)                     | Dynamic schema (can store data without predefined structure)                              |
| **Scalability**     | Vertical scaling (scale-up: add more CPU/RAM to a single server) | Horizontal scaling (scale-out: add more servers)                                          |
| **Best For**        | Complex queries, structured data, relationships                  | Unstructured/semistructured data, high-speed and large-scale applications                 |
| **Examples**        | MySQL, PostgreSQL, Oracle, MS SQL Server                         | MongoDB, Cassandra, CouchDB, Redis, Neo4j                                                 |
| **Query Language**  | SQL (standardized)                                               | No standard query language (each DB has its own API/commands)                             |
| **ACID Compliance** | Strong support (Atomicity, Consistency, Isolation, Durability)   | Many NoSQL databases sacrifice ACID for speed/availability (though some provide ACID now) |
| **Joins**           | Supports complex joins                                           | Usually does not support joins (data often denormalized)                                  |
| **Data Storage**    | Tables with fixed rows & columns                                 | JSON-like documents, key-value pairs, graphs, wide-columns                                |
| **Use Cases**       | Banking, ERP, CRM, traditional business apps                     | Big data, IoT, real-time analytics, social networks, content management                   |

- **SQL** → Best when your data is structured, consistent, and requires complex relationships.
- **NoSQL** → Best when your data is large, unstructured, and needs fast access with flexibility.