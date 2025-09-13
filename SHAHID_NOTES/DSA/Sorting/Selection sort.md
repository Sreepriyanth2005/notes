#### Procedure

- The array is divided into two parts:
    - **Sorted part** (left side).
    - **Unsorted part** (right side).
- On each iteration, the algorithm selects the **minimum element** from the unsorted part and swaps it with the first unsorted element.

```java
import java.util.*;
class Main {
    
    public static void selectionSort(int[] arr){
        int n = arr.length;
        for(int i = 0; i < n-1; i++){
            int minIdx=findMin(arr,i);
            if(i!=minIdx)
                swap(arr,i,minIdx);
        }
    }
    
    public static int findMin(int[] arr,int left){
        int n = arr.length;
        int min=arr[left];
        int minIdx=left;
        for(int i = left+1; i < n; i++){
            if(arr[i] < min){
                min = arr[i];
                minIdx = i;
            }
        }
        return minIdx;
    }
    
    public static void swap(int[] arr, int first, int second){
        int temp=arr[first];
        arr[first]=arr[second];
        arr[second]=temp;
    }
    
    public static void main(String[] args) {
        int[] arr={7,6,5,4,3,2,1};
        selectionSort(arr);
        int n = arr.length;
        for(int i = 0; i < n; i++){
            System.out.print(arr[i]+ " ");
        }
    }
}
```