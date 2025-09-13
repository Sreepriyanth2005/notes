
#### Procedure

1. Pick the **first element** of the subarray as the pivot.
2. Partition the array so that:
    - All elements **≤ pivot** go to the left side.
    - All elements **> pivot** go to the right side.
3. Recursively apply Quick Sort to left and right subarrays.


```java
import java.util.*;
class Main {
    public static void quickSort(int[] arr,int left,int right){
        if(left<right){
            int p=partition(arr,left,right);
            
            quickSort(arr,left,p-1);
            quickSort(arr,p+1,right);
        }
    }
    
    public static int partition(int[] arr,int left,int right){
        int pivot=arr[left];
        int i=left+1;
        int j=right;
        
        while(true){
            while(i<=right && arr[i]<=pivot){
                i++;
            }
            
            while(j>=left+1 && arr[j]>pivot){
                j--;
            }
            
            if(i>j) break;
            
            swap(arr,i,j);
        }
        swap(arr,left,j);
        return j;
    }
    
    public static void swap(int[] arr,int i,int j){
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
    }
    
    public static void main(String[] args) {
        int[] arr={7,6,23,4,3,9,12};
        quickSort(arr,0,arr.length-1);
        int n = arr.length;
        for(int i = 0; i < n; i++){
            System.out.print(arr[i]+ " ");
        }
    }
}
```


#### Quick Select

```java
import java.util.*;
class Main {
    public static int quickSort(int[] arr,int left,int right,int k){
        if(left==right) return arr[left];
        int p=partition(arr,left,right);
            
        if(p==k)
            return arr[k];
        else if(k<p)
            return quickSort(arr,left,p-1,k);
        else
            return quickSort(arr,p+1,right,k);
    }
    
    public static int partition(int[] arr,int left,int right){
        int pivot=arr[left];
        int i=left+1;
        int j=right;
        
        while(true){
            while(i<=right && arr[i]<=pivot){
                i++;
            }
            
            while(j>=left+1 && arr[j]>pivot){
                j--;
            }
            
            if(i>j) break;
            
            swap(arr,i,j);
        }
        swap(arr,left,j);
        return j;
    }
    
    public static void swap(int[] arr,int i,int j){
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
    }
    
    public static void main(String[] args) {
        int[] arr={7,6,23,4,3,9,12};
        int n = arr.length;
        int result=quickSort(arr,0,arr.length-1,arr.length-2);
        System.out.print(result);
    }
}
```