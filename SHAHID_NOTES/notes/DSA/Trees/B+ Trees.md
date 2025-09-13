
#### Definition

- A **B+ Tree** is a **balanced tree data structure** commonly used in **databases**.
- **All data records (actual values) are stored in the leaf nodes only.**
- **Internal nodes** store only keys (used for routing/searching).
- **Leaf nodes are linked** using **pointers**, forming a **linked list** for fast sequential access.
- Sorted Order in leaf nodes

#### Why B+ Trees?

| Problem in B-Trees                    | Solution in B+ Trees                                    |
| ------------------------------------- | ------------------------------------------------------- |
| Data spread across all nodes          | Data only in **leaf nodes**                             |
| No direct leaf-to-leaf navigation     | Leaf nodes are **linked**, enabling fast range queries  |
| Inefficient range queries             | **Sequential access** possible due to linked leaves     |
| Redundant data across internal levels | **Internal nodes only store keys**, making them smaller |

#### Use of B+ Trees?

- Used as **indexing structures** (especially for clustered and non-clustered indexes).
- Primary keys and foreign keys often use B+ Trees.
- Range queries like `BETWEEN`, `>`, `<` are efficient due to linked leaves.

#### Operations in B+ Trees?

- **Search**
    - Always ends at leaf level
- **Insertion**
    - Insert at leaf → Split leaf → Promote to parent
- **Deletion**
    - Delete from leaf → Borrow/Merge → Update internal nodes

#### Advantages

- Efficient Range Queries
- Faster Search Performance
- Sorted Data Access
- Dynamic Insertions and Deletions
- Optimized Disk Storage Utilization

#### Time Complexity

|Operation|Time Complexity|
|---|---|
|Search|O(log n)|
|Insert|O(log n)|
|Delete|O(log n)|
|Range Query|O(log n + k) where k = result count|