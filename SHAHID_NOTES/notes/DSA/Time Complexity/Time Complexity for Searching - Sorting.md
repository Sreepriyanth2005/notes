
### *Best Searching and Sorting Algorithms*  

#### *Searching Algorithms*  
The choice of the best searching algorithm depends on the dataset size and whether the data is sorted or not.  

| *Algorithm* | *Best Case* | *Average Case* | *Worst Case* | *When to Use?* |
|--------------|-------------|---------------|--------------|------------------|
| *Linear Search* | O(1) | O(n) | O(n) | When data is *unsorted* and small |
| *Binary Search* | O(1) | O(log n) | O(log n) | When data is *sorted* |
| *Jump Search* | O(1) | O(√n) | O(√n) | When data is *sorted* and large |
| *Exponential Search* | O(1) | O(log n) | O(log n) | When the *search element is near the beginning* |
| *Interpolation Search* | O(1) | O(log log n) | O(n) | When *data is uniformly distributed* and sorted |

✅ *Best Searching Algorithm:*  
- *For Unsorted Data:* Linear Search (O(n))  
- *For Sorted Data:* Binary Search (O(log n))  
- *For Large Uniformly Distributed Data:* Interpolation Search (O(log log n))  

---

#### *Sorting Algorithms*  
Sorting algorithms can be compared based on their time complexity, stability, and space complexity.  

| *Algorithm*      | *Best Case* | *Average Case* | *Worst Case* | *Space Complexity* | *Stable?* | *When to Use?*                           |
| ---------------- | ----------- | -------------- | ------------ | ------------------ | --------- | ---------------------------------------- |
| *Bubble Sort*    | O(n)        | O(n²)          | O(n²)        | O(1)               | ✅ Yes     | Small datasets, simple to implement      |
| *Selection Sort* | O(n²)       | O(n²)          | O(n²)        | O(1)               | ❌ No      | Small datasets, requires minimum swaps   |
| *Insertion Sort* | O(n)        | O(n²)          | O(n²)        | O(1)               | ✅ Yes     | Small datasets, nearly sorted data       |
| *Merge Sort*     | O(n log n)  | O(n log n)     | O(n log n)   | O(n)               | ✅ Yes     | Large datasets, stable sorting needed    |
| *Quick Sort*     | O(n log n)  | O(n log n)     | O(n²)        | O(log n)           | ❌ No      | Large datasets, better for average cases |
| *Heap Sort*      | O(n log n)  | O(n log n)     | O(n log n)   | O(1)               | ❌ No      | Large datasets, no extra space needed    |
| *Counting Sort*  | O(n + k)    | O(n + k)       | O(n + k)     | O(k)               | ✅ Yes     | When range of numbers is small           |
| *Radix Sort*     | O(nk)       | O(nk)          | O(nk)        | O(n + k)           | ✅ Yes     | Large numbers, fixed-length numbers      |
| *Tim Sort*       | O(n)        | O(n log n)     | O(n log n)   | O(n)               | ✅ Yes     | Hybrid sort (used in Python’s sort())    |

✅ *Best Sorting Algorithm:*  
- *For Small Data: **Insertion Sort* (O(n²)) if nearly sorted  
- *For General Purpose: **Merge Sort* (O(n log n)) (stable sorting)  
- *For Large Data: **Quick Sort* (O(n log n), but unstable)  
- *For Special Cases: **Counting/Radix Sort* (O(n + k), when numbers have a small range)