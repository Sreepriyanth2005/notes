### Easy
##### 1. Two Sum(Two Pointers + Class)
##### 643 . Maximum Average Subarray I
####  Maximize Number of 1's (gfg)

### Medium
##### 287 . Find the Duplicate Number(Array)
##### 31 . Next Permutation(Array)
##### 2. Three Sum(Two Pointers, BackTracking)

##### 2461 . Maximum sum of distinct subarray with k (also gfg)

##### 209 . Minimum size subarray sum

##### 904 . Fruits in the Basket

##### 48 . Rotate Image

##### 2125. Number of Laser Beam in the Bank

##### 554 . Brick Wall

##### 234 . Palindrome List
##### 143. ReorderList
##### 19 .Remove Nth node from List

#### [Unfold List](https://crafterhack.com/problems/unfold-of-linked-list-1)

##### 2487 . Remove Nodes from Linked List

##### 328 . Odd Even LinkedList

##### Next Greater Element ( GFG)

##### Stock Span Problem (GFG)

##### 84 . Largest Rectangle in Histogram
##### 735 . Asteroid Collision
##### 150. Evaluate Reverse polish Notation 
##### 155. Min Stack
#### 145. Postorder Traversal Binary Tree
#### 94. Inorder Traversal Binary Tree
#### 144. Preorder Traversal Binary Tree
#### 111. Min Depth
#### 104. Max Depth
#### 230. Kth Smallest Element
#### 671.Second Minimum node in a BT
#### 1161.Maximum Level Sum of a BT
#### 2583 . Kth largest element in a BT
#### Maximum width of the tree ( GFG) 
#### 662. Maximum width of the tree(Include Null)
#### 863.All nodes Distance k in binary tree
#### 226 . Invert a Tree
#### Burning Tree(GFG)
#### 236 . LCA
#### 235 . LCA of BST
#### Permutation I,II
#### Combination Sum I,II,III
#### Rat in Maze (gfg)
#### No of enclaves
#### Frog Jump(GFG)
#### Path Sum I , II ,III
#### Unique Paths I,II,III
#### Climbing Stars
#### Triangle path Sum
#### Minimum Falling Path Sum I,II
#### Minimum Subset Sum(gfg)
#### Knapsack Problem (gfg)
### General 

##### 1.Two Array Sum

```java
class Solution {
    ArrayList<Integer> findSum(int arr1[], int arr2[]) {
        ArrayList<Integer> res = new ArrayList<>();
        int i = arr1.length-1;
        int j = arr2.length -1;
        
        int carry = 0;
        
        while( i >= 0  j >= 0  carry != 0){
            int digit1 = (i>=0) ? arr1[i] : 0;
            int digit2 = (j>=0) ? arr2[j] : 0;
            
            int sum = digit1 + digit2 + carry;
            
            res.add(sum%10);
            carry = sum / 10;
            i--;
            j--;
        }
        Collections.reverse(res);
        return res;
    }
}
```



