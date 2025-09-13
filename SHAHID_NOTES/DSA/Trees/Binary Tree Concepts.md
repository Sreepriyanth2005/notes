#### Binary Tree Traversal Techniques

![[Tree-Traversal-Techniques.webp|400]]

#### DFS Traversal

##### 1 . Pre-Order
###### Root -> Left -> Right

##### 2 . In-order

###### Left -> Root -> Right
**Note:**
It gives the increasing order of elements, while performing In-order in BST

##### 3 . Post-Order

###### Left -> Right -> Root

##### Time and Space Complexity

| Tree Type          | Space (Recursive DFS) | Space (Iterative DFS using stack) |
| ------------------ | --------------------- | --------------------------------- |
| **BT **            | O(h)                  | O(log n)                          |
| **BST (balanced)** | O(log n)              | O(log n)                          |
| **Skewed Tree**    | O(n)                  | O(n)                              |

#### BFS Traversal

##### Level Order Traversal
It traverse the elements level by level from root to the leaves 

##### Time and Space Complexity

| Tree Type          | Space (BFS - Queue)                              |
| ------------------ | ------------------------------------------------ |
| **BT**             | O(n) in worst case (half of nodes at last level) |
| **BST (balanced)** | O(n) (same as above)                             |
| **Skewed Tree**    | O(1) (at most one node at any level)             |




