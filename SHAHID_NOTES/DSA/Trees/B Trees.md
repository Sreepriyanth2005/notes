
#### Definition 

- Balanced-m Tree
- Generalization of BST in which a node can have more than one key and more than two children
- maintains the sorted order
- All leaf notes must be in same order
- B-Tree of order m has following properties:
	- Children
	 1. Every node has max m children
	 2. Min children
		 1. Leaf : 0
		 2. Root : 2 (only for root)
		 3. Internal Nodes : Ceil(m/2)
	- Keys
	 1. Every node has m-1 Keys
	 2. Min Keys
		 1. Root : 1
		 2. Internal Nodes : Ceil(m/2)-1



#### Insertion

- First note Max children, Min children, Max key, Min key.
- If Inserting violates above property then Middle element { Ceil(len/2) } transfer to its root node.
- Based on this construct the B Tree.

#### Deletion 

##### Deleting at leaf

1. If deleting the element does not affect the min key property then delete simply
2. If deleting the element violates the min key property then ask element from either left(Max Element) or right(Min Element) , move to its parent and bring parent down to deleted element node
3. If there is enough min keys in left node and right node, the ask from parent and merge either with left node or right node including the corresponding parent 
4. After that parent does not satisfied the B-Tree condition then it ask from its immediate siblings if there is enough min keys ask from root and merge

##### Deleting the Internal Nodes

1. If deleting the element it should be replaced with the Inorder predecessor and Inorder successor, only if it does not violates the B-Tree condition
2. Still it violates and can't get the Inorder predecessor and Inorder successor then delete the key and merge it 
3. If there no possible from asking to the parent then merge all current, parent and siblings 

#### Other Trees Drawbacks over B-Trees

| Limitation                 | Description                                                                                                                                                                                                                                |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **High tree height**       | BSTs and AVL trees tend to be tall (log₂N), which means more nodes are visited in searches or insertions. Each node access in external storage (like hard drives or SSDs) incurs an I/O operation, which is **very slow** compared to RAM. |
| **One key per node**       | In BSTs and AVL trees, each node stores only one key, which results in a large number of small nodes. This leads to **many disk accesses** for operations like search, insert, or delete.                                                  |
| **Inefficient disk usage** | Nodes are small and do not make full use of a disk page/block. Thus, **most of the disk block stays underutilized** in each read/write operation.                                                                                          |
| **Pointer overhead**       | Each node has two pointers in a BST or AVL. In disk-based systems, managing large numbers of pointers becomes inefficient and complex.                                                                                                     |

#### Why B-Trees

| Feature                          | Benefit                                                                                                                |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Multi-key nodes**              | A B-tree node can store **multiple keys and children**, allowing a single disk read to bring in **many keys at once**. |
| **Shallow height**               | Because of wide nodes, B-trees are **very shallow**. Fewer levels = **fewer I/O operations**.                          |
| **Disk-block alignment**         | Nodes are designed to match **disk block sizes** (e.g., 4KB), maximizing **data read per I/O**.                        |
| **Balanced tree structure**      | B-trees remain balanced at all times, ensuring **logarithmic search time**, with **minimal height**.                   |
| **Efficient insertion/deletion** | Unlike AVL trees, B-trees do not require complex rotations — they use **splits and merges** to balance.                |

#### Use Cases

##### 1. **Databases**

- **Indexing**: B-trees and B+ trees are used to **index tables** for fast search, insert, and delete.
    
- **Clustered indexes**: In systems like MySQL (InnoDB), **primary key indexes** are implemented using B+ trees.
    
- **Range queries**: B+ trees are ideal for **range-based searches** due to their sorted nature and sequential pointers.

#### Time Complexity

|Operation|Time Complexity|Explanation|
|---|---|---|
|**Search**|`O(log n)`|Traverse from root to leaf; at each level, binary search among ≤ `m` keys.|
|**Insert**|`O(log n)`|May need to split nodes, but done in top-down/bottom-up in log(n) depth.|
|**Delete**|`O(log n)`|May require merging or borrowing, but still logarithmic in height.|
|**Traversal**|`O(n)`|All keys are visited once in-order (DFS).|
|**Range Query**|`O(log n + k)`|Find range start (log n) + collect `k` items (linear scan in leaves).|




