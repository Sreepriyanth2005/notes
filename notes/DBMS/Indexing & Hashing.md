
## Indexing

- Searching in a large database table (millions of rows) is slow if DBMS has to scan row by row (**linear search**).

- **Indexing** is like an index in a book: instead of scanning every page, you look up the keyword in the index, which tells you exactly where to go.

- Improves **search speed** (O(log n) instead of O(n)).


### Types of Indexing

#### **Single-Level Index**

One index file maps **search key → data block**.

**Example**

| RollNo | Name   | Dept |
| ------ | ------ | ---- |
| 1      | Aditi  | CS   |
| 2      | Bharat | IT   |
| 3      | Charan | ECE  |
| 4      | Divya  | CS   |
| 5      | Farah  | IT   |
**Index (on RollNo):**

| RollNo (Key) | Pointer to Record |
| ------------ | ----------------- |
| 1            | → Student(1)      |
| 2            | → Student(2)      |
| 3            | → Student(3)      |
| 4            | → Student(4)      |
| 5            | → Student(5)      |

#### Multi-Level Index

- When the index itself becomes too large → create an **index on the index**.
- Like a hierarchy: **Outer index → Inner index → Data**.

**Example**

**Level 1 (Outer Index):** Index on disk **blocks**.

```scss
Roll_No Range   →   Block Address
1–1000          →   Block A
1001–2000       →   Block B
2001–3000       →   Block C
```

**Level 2 (Inner Index):** Inside Block A, we have another **index**:

```scss
Roll_No   →   Record Address
1         →   Addr 101
2         →   Addr 102
...
1000      →   Addr 200
```

#### Dense vs Sparse

##### Dense

- In **dense indexing**, **every search key value** in the data file has a corresponding entry in the index file.
- So the index is “dense” → it covers _all records_.

```scss
Roll | Pointer to Block
------------------------
1    | → Block 1
2    | → Block 1
3    | → Block 1
4    | → Block 2
5    | → Block 2
6    | → Block 2
7    | → Block 3
8    | → Block 3
9    | → Block 3
```

- Every record has a direct entry in the index.  
- Faster search.

##### Sparse

- In **sparse indexing**, only some search key values have entries (typically the first value of each block).
- Saves space but needs extra block access.

```scss
Roll | Pointer to Block
------------------------
1    | → Block 1
4    | → Block 2
7    | → Block 3
```

If you want to search Roll = 5:
- Index tells → Block 2 (because 4 ≤ 5 < 7).
- Then search inside Block 2.

## Hashing

- Indexing is efficient for **range queries** (e.g., RollNo between 100 and 200).
- But for **exact match queries** (e.g., RollNo = 12345), **hashing is faster**.
- Uses a **hash function h(key) → bucket address**.
- Average O(1) access time
#### **Static Hashing**

- Hash table has **fixed number of buckets**.
- Collisions handled by chaining/linear probing.

**Example**

Hash function: `h(RollNo) = RollNo mod 10`

|RollNo|h(RollNo)|Bucket|
|---|---|---|
|101|1|B1|
|202|2|B2|
|112|2|B2 (collision)|
|305|5|B5|

#### Dynamic Hashing

- Hash table **grows/shrinks** as data changes.
- Buckets split when overflow occurs.

**Example**

Extendible Hashing


