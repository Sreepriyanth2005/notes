
### Binary Search Tree

**Binary Search Tree**  is a data structure used in computer science for organizing and storing data in a sorted manner. Binary search tree follows all properties of binary tree and for every nodes, its **left** subtree contains values less than the node and the **right** subtree contains values greater than the node. This hierarchical structure allows for efficient **Searching**, **Insertion**, and **Deletion** operations on the data stored in the tree.

#### Properties of Binary Search Tree
- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- The left and right subtree each must also be a binary search tree.  
- There must be no duplicate nodes(BST may have duplicate values with different handling approaches).

#### Important points about BST

- A **Binary Search Tree (BST)** maintains data in **sorted order**, supporting **search, insert, delete, ceiling, min, and max** in **O(h)** time.
    
- Using a **Self-Balancing BST** (like AVL or Red-Black Tree), the height is kept at **O(log n)**, ensuring all operations run in **O(log n)** time.
    
- If only **search, insert, and delete** are needed (and not sorted order or traversal), a **Hash Table** is preferred, as it offers **O(1)** average time for these operations.

#### Advantages
1. **Efficient Searching**
2. **Ordered Structure**
3. **Dynamic Insertion and Deletion**
4. **Balanced Structure**
5. **Doubly Ended Priority Queue Support in BSTs**

#### Deletion

- No child → Remove directly
- One child → Replace node with its child
- Two children → Replace with inorder successor or predecessor

#### Applications

##### 1. **Tree-based Maps (TreeMap, TreeSet)**

 **What they are:**
- **TreeMap** and **TreeSet** (in Java, C++, Python, etc.) are data structures that **automatically maintain elements in sorted order** using **Self-Balancing BSTs** like **Red-Black Trees** or **AVL Trees**.

 **How they work:**
- In a `TreeMap`, every insertion maintains the sorted order by balancing.
- Keys are ordered; values are mapped accordingly.
- Operations like `insert`, `delete`, `lookup`, and **range-based operations** run in **O(log n)**.
    
 **Real-time Example:**

> **Banking system** to store customer records by Account Number.

##### 2. **Indexing in Databases**

**What it is:**

- Indexing is used in databases to **quickly retrieve records** without scanning every row.
    
- Tree-based structures like **B-Trees** or **B+ Trees** are used in databases (e.g., MySQL, PostgreSQL) for indexing.
    
**How they work:**

- Indexes use multi-level trees (B-tree, B+ tree) to keep data sorted and searchable in **logarithmic time**.
    
- Nodes can store multiple keys to reduce height (unlike binary trees).
    
 **Real-time Example:**

> In a **hospital database**, patients are indexed by `PatientID`. 

##### 3. **Range-Based Queries**

**What it is:**

- **Find all values within a certain range** (e.g., age 25–35, prices ₹500–₹1000).
    
- Tree structures (like BST or Segment Trees) allow efficient querying in sorted data.
    
 **How they work:**

- Since tree nodes are ordered, you can **traverse only the needed subtree** that falls within range.

**Real-time Example:**

> **E-commerce filtering** (e.g., show products in price range ₹1000–₹2000)

##### 4. **Efficient Sorting and Searching**

**What it is:**
- BST-based structures keep elements in **sorted order**, which helps in:
    - Searching in O(log n)
    - Inorder traversal → sorted data
- Self-balancing trees like AVL or Red-Black Trees ensure this order is maintained after inserts/deletes.
    
 **How they work:**

- New values inserted in O(log n), ensuring tree stays balanced and sorted.
    
- In-order traversal returns sorted sequence.
    
 **Real-time Example:**

> **Auto-suggestions in search engines**:

- As you type "ab", it quickly narrows down all entries starting with "ab".


#### Questions

1. **Conditions that make a Binary Tree not a BST**
	- Left child is greater than or equal to the parent node.
	- Right child is less than or equal to the parent node.
	
2. **Rules for checking if a binary tree is a BST**
	- Traverse the tree in **inorder (Left → Root → Right)**.
	- If the result is **strictly increasing**, then it's a BST.

3. **LCA in Binary Tree**
	- The Lowest Common Ancestor (LCA) of two nodes `p` and `q` in a binary tree is the lowest (i.e., deepest) node in the tree that has both `p` and `q` as descendants
	- The **first common node** when moving up from both `p` and `q`.
 

#### Time Complexity

|**Operation**|**Average Case**|**Worst Case**|**Explanation**|
|---|---|---|---|
|**Search(x)**|`O(log n)`|`O(n)`|In a balanced BST, you discard half each step. In a skewed tree (like a linked list), you may traverse all nodes.|
|**Insert(x)**|`O(log n)`|`O(n)`|Depends on tree height — ideally `log n`, but could become `n`.|
|**Delete(x)**|`O(log n)`|`O(n)`|Must search and possibly rearrange subtrees.|
|**Inorder Traversal**|`O(n)`|`O(n)`|Visits every node once.|
|**Pre/Postorder**|`O(n)`|`O(n)`|Traverses all nodes.|
|**Find Min/Max**|`O(log n)`|`O(n)`|Always go left/right until leaf.|
|**Height**|`O(log n)`|`O(n)`|Height of a balanced BST is log n; skewed tree is n.|
#### Drawbacks

###1. **Unbalanced Tree → Poor Performance**

- **Drawback**: BST can become skewed (like a linked list) with sorted input.
    
- **Impact**: Search, insert, delete become **O(n)** instead of **O(log n)**.
    
- ** Solution**: Use **Self-Balancing Trees** like **AVL Tree** or **Red-Black Tree**.

2. **No Self-Balancing**

- **Drawback**: Standard BST does not automatically maintain balance.
    
- **Impact**: Tree height grows with insertions/deletions.
    
- ** Solution**: Implement **AVL Tree** or **Red-Black Tree** which maintain balance after each operation.
    
 3. **Handling Duplicate Values**

- **Drawback**: BSTs don’t naturally support duplicates.
    
- **Impact**: Requires extra logic (like count fields or special placement rules).
    
- **Solution**:
    - Allow duplicates on one side consistently (e.g., right).
    - Use **Multiset (TreeMap)** or store frequency counts.