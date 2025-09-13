
### Tree
A **tree** is a **non-linear hierarchical data structure** made up of **nodes** connected by **edges**, with **one node designated as the root**. It is a type of **graph** that is **connected and acyclic**

**Why non-linear hierarchical ?**
- A node can be connected to **multiple children**. There's no strict sequential order.
- A **tree** represents a **parent-child** relationship. One node (root) is the starting point, and all others branch out from it.
### Why?

-> Hierarchical Data Representation (DOM, File Systems)
-> Faster Search and Insertion (BST)
-> Efficient Routing (routing Algo )
-> Structural Relationships (siblings, Parent-Child)
-> Foundation of Many Algorithms( Heap, Segment Tree, AVL, B-trees)

### Terminologies
##### 1. **Root**

- The **topmost node** of a tree.
    
- It has **no parent**.
    
- Every tree has **exactly one root**.
##### 2. **Node**

- A **basic unit** of a tree that contains a value/data.
    
- Nodes can have **children** and **a parent**, except the root (no parent).
##### 3. **Edge**

- A **connection between two nodes** (like a branch).
    
- For a tree with `n` nodes, there are always `n - 1` edges.
##### 4. **Leaf (or External Node)**

- A node with **no children**.
    
- These are the **end points** of the tree.
##### 5. **Height**

- The **longest path** from the node to a leaf.
    
- Height of a **tree** = height of the **root**.
    
- Height of a **leaf node** = 0.
##### 6. **Depth**

- The **number of edges** from the **root to that node**.
    
- Depth of the **root** is 0.
    
- Depth increases as you go down the tree.
##### 7. **Level**

- Similar to depth, but usually **starts from 1**.
    
- Nodes at the same depth are said to be at the same **level**.
##### 8. **Subtree**

- Any **child node** and all its descendants form a **subtree**.
    
- Every node is a **root of its own subtree**.
##### 9. **Degree**

- Number of **children** a node has.
    
- **Leaf nodes have degree 0.**
    
- Maximum degree in the tree = maximum number of children any node has




### Properties
##### 1. **A Tree with n Nodes Has n - 1 Edges**

- Each node (except the root) has exactly one incoming edge (from its parent).
    
- So, `n - 1` edges are needed to connect `n` nodes.
    
- This is a **defining property** of trees.
##### 2 . **Uniqueness of Paths**

- There is **only one path** between any two nodes in a tree.
    
- This prevents cycles and ensures a **unique structure**.
##### 3. **Acyclic and Connected Structure**

- A tree is a type of graph that is:
    
    - **Acyclic**: no cycles or loops.
        
    - **Connected**: there is a path from the root to every other node.
        
- These two properties define a **tree** in graph theory.

### Representation

![[Pasted image 20250703010147.png|250]]

### Types of Trees

##### General Tree vs Binary Tree

| General tree                                                                 | Binary tree                                                                                                                               |
| ---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| General tree is a tree in which each node can have many children or nodes.   | Whereas in binary tree, each node can have at most two nodes.                                                                             |
| The subtree of a general tree do not hold the ordered property.              | While the subtree of binary tree hold the ordered property.                                                                               |
| In data structure, a general tree can not be empty.                          | While it can be empty.                                                                                                                    |
| In general tree, a node can have at most **n(number of child nodes)** nodes. | While in binary tree, a node can have at most **2(number of child nodes)** nodes.                                                         |
| In general tree, there is no limitation on the degree of a node.             | While in binary tree, there is limitation on the degree of a node because the nodes in a binary tree can’t have more than two child node. |
| In general tree, there is either zero subtree or many subtree.               | While in binary tree, there are mainly two subtree: **Left-subtree** and **Right-subtree**.                                               |

### Binary Tree Types

A **binary tree** is a tree data structure where **each node has at most two children**:
- Typically called the **left** and **right** child.

#### Types
##### On Basis of Children
###### 1 . **Full Binary Tree**

A **full binary tree** is a binary tree in which:
- **Every node has either 0 or 2 children**.
- No node has **only one** child.
![[Pasted image 20250703091920.png]]

###### 2 . Degenerate Tree (Pathological Tree)

A **degenerate tree** is a tree where:
- Each node has **only one child**.
- It behaves like a **linked list** in structure.
![[Pasted image 20250703092406.jpg|300]]

###### 3  . Skewed Tree (Left or Right)

A **skewed tree** is a binary tree where:
- **Each node has only one child**, either:
    - All **left children** → **left-skewed**
    - All **right children** → **right-skewed**
![[Pasted image 20250703092126.png]]



##### On basis of Level
###### 4 . Complete Binary Tree

A **complete binary tree** is a binary tree where:
- All levels are **completely filled**, except possibly the **last level**
- The **last level** has all nodes as **left as possible**.
![[Pasted image 20250703092029.jpg]]

###### 5 . Perfect Binary Tree

A **perfect binary tree** is a binary tree where:
- **All internal nodes** have **2 children**, and
- **All leaf nodes** are at the **same level**.
![[Pasted image 20250703092100.png]]
###### 6 . Balanced Tree (Height-Balanced)

A **balanced binary tree** is a tree where:
- The **height difference** between left and right subtrees of any node is **at most 1**.
> Balance ensures operations are in **O(log n)** time.

**Types**![[balance-vs-unbalance-binnary-tree.webp|350]]
- **AVL Tree**: strictly height-balanced
- **Red-Black Tree**: balanced using color and rotation rules

##### On Basis of Number of Values

###### 7 . Binary Search Tree

A **Binary Search Tree** is a binary tree where:
- **Left child < Parent node**
- **Right child > Parent node**
- This property is **recursively true** for every subtree.
- **Search, Insert, Delete**: `O(h)` where `h = height of tree`
###### 8 . AVL Tree (Adelson - Velsky and Landis Tree)

A **self-balancing binary search tree** where:
- The **balance factor** (height difference) of each node is **-1, 0, or 1**.
> If unbalanced after insertion/deletion, **rotations** (single or double) are used to re-balance

`BF = height(left subtree) - height(right subtree)`
- **Search, Insert, Delete**: `O(log n)`

###### 9 . Red Black Tree

A **self-balancing BST** with **less strict balancing than AVL**. Each node has a color : **red or black**.
**Rules**:
1. Each node is either red or black.
2. The root is black.
3. Red nodes can’t have red children (no two reds in a row).
4. Every path from root to null leaf has the same number of black nodes (black-height).

Search, Insert, Delete: `O(log n)`
Slightly faster insertion than AVL due to fewer rotations.![[Pasted image 20250703102553.jpg]]
###### 10 . N-ary Tree

An **N-ary tree** is a general tree where:
- Each node can have **at most N children** (not just 2)
- Binary tree is a **2-ary tree**.
- Below Example of **3-ary Tree**
![[Pasted image 20250703092208.png]]

###### 11 . B Tree

A **self-balancing N-ary search tree** used in **disk-based systems** where:
- A node can have **more than two children** (usually many).
- All leaves are at the **same level**.
**Key Properties**:
- Each node can store **multiple keys**.
- Minimizes **disk read/write** by using **large nodes** (with many children).
- Balanced and optimized for **slow storage (e.g., HDDs)**.
**Time Complexity**:
- Search, Insert, Delete: `O(log n)`

![[Pasted image 20250703102731.png|500]]

###### 12 . B+ Tree

A variation of the B Tree where:
- All **values are stored only at leaf nodes**.
- Internal nodes store **only keys** for navigation.
- Leaf nodes are **linked** together for **range queries**.
**Advantages over B Tree**:
- **Faster range queries** (thanks to linked leaf nodes).
- Internal nodes are smaller — so more fit in memory → fewer disk accesses.
**Time Complexity**:
- Same as B Tree: `O(log n)`
![[Pasted image 20250703112202.jpg]]

###### 13. Segment Tree

A **Segment Tree** is a **binary tree** used for answering **range queries** and performing **range updates** efficiently on arrays or sequences.

- **Range Sum**
- **Range Minimum / Maximum**
- **Range GCD / LCM / XOR**
- **Range Count of an element**
- **Range updates (with Lazy Propagation)**

**Segment Tree Structure**
- It’s a **binary tree** (not necessarily balanced).
- Each **node stores information about a segment (range)** of the array.
- The **leaf nodes** represent **individual elements** of the array.
- The **internal nodes** store **aggregated values** (e.g., sum, min, max) of their respective child segments.

**Segment tree for Sum**
![[Pasted image 20250703115920.png]]