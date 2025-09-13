
AVL - Adelson-Velsky and Landis

### Definition

An **AVL Tree** is a **self-balancing Binary Search Tree (BST)** in which **the difference between the heights of the left and right subtrees of any node is at most 1**.

- This difference is called the **Balance Factor (BF)**.
- Balance Factor = `Height of Left Subtree – Height of Right Subtree`
- Valid balance factors for any node: `-1, 0, +1`

### Why AVL ? 

A **normal BST** can become **unbalanced** when nodes are inserted in a sorted manner:  
Example: Insert `10, 20, 30, 40, 50` into a normal BST:

    10
      \
       20
         \
          30
            \
             40
               \
                50

**AVL Trees solve this by:**
1. Maintaining **height-balance** automatically after every insertion/deletion.
2. Ensuring **height ≈ log₂(n)**.
3. Making operations like **search, insertion, and deletion O(log n)**.

### Properties of AVL

- **1. Binary Search Tree Property**
    
    - AVL Tree is a BST:
        
        - Left subtree nodes < Root < Right subtree nodes
            
        - In-order traversal gives a **sorted sequence**.
            
- **2. Height-Balanced Property**
    
    - For **every node**, the **height difference** (Balance Factor) between left and right subtree is **at most 1**.
        
    - Ensures the tree **never becomes skewed** like a linked list.
        
- **3. Balance Factor Property**
    
    - **Balance Factor (BF) = Height(left) – Height(right)**
        
    - For AVL Tree: **BF ∈ { -1, 0, +1 }**
        
    - Any violation triggers **rotations** to restore balance.
        
- **4. Logarithmic Height (O(log n))**
    
    - AVL Tree maintains **height ≈ log₂(n)** for `n` nodes.
        
    - Guarantees **O(log n)** time for search, insertion, and deletion.
        
- **5. Self-Balancing with Rotations**
    
    - After each **insertion or deletion**, the tree **auto-balances** using rotations:
        
        - LL, RR, LR, RL rotations
            
    - Keeps operations efficient and the tree balanced.

### Operations of AVL

#### **Search 

1. Start at the **root**.
    
2. Move **left if key < node**, **right if key > node**.
    
3. Repeat until **key is found** or **NULL**.
    
4. **No rotations** needed.

#### **Insertion**

1. **Insert like BST** in the correct position.
    
2. **Update heights** of ancestor nodes.
    
3. **Check balance factor (BF)** for imbalance.
    
4. **Rotate** (LL, RR, LR, RL) if required.

#### **Deletion**

1. **Delete like BST** (leaf, 1 child, 2 children).
    
2. **Update heights** of ancestor nodes.
    
3. **Check balance factor** for imbalance.
    
4. **Rotate** to restore balance if needed.

### Advantages of AVL

- **Faster Searching**
    
    - Height-balanced structure ensures **quick lookup** compared to unbalanced BSTs.
        
- **Prevents Skewed Trees**
    
    - Automatically balances after insert/delete, avoiding **linked-list-like BSTs**.
        
- **Efficient Insert and Delete** 
    
    - Maintains logarithmic height, so **insertion and deletion remain fast**.
        
- **Ideal for Dynamic Datasets**
    
    - Best for applications with **frequent insertions and deletions** where balance is crucial.

### Disadvantages of AVL

- **Complex Implementation**
    
    - Requires maintaining **height/balance factor** and handling **rotations**.
        
- **Extra Memory Usage**
    
    - Each node stores **height or balance factor**, using more memory than BST.
        
- **Insertion/Deletion Overhead**
    
    - Rotations during **frequent updates** add **processing overhead**.

### Time Complexity

| **Operation**               | **Best Case** | **Average Case** | **Worst Case** | **Reason**                                  |
| --------------------------- | ------------- | ---------------- | -------------- | ------------------------------------------- |
| **Search**                  | O(log n)      | O(log n)         | O(log n)       | Tree always height-balanced                 |
| **Insertion**               | O(log n)      | O(log n)         | O(log n)       | Requires traversal to leaf and ≤2 rotations |
| **Deletion**                | O(log n)      | O(log n)         | O(log n)       | Delete + rebalance if needed                |
| **Find Min / Max**          | O(1)          | O(log n)         | O(log n)       | Min/Max could be root (best case)           |
| **Predecessor/Successor**   | O(1)          | O(log n)         | O(log n)       | Immediate child could be successor          |
| **Height Calculation**      | O(1)          | O(1)             | O(1)           | Height stored in each node                  |
| **Traversal (In/Pre/Post)** | O(n)          | O(n)             | O(n)           | All nodes must be visited                   |
