
- **Divide and Conquer Algorithm**
- Breaks the array into halves → sorts each half recursively → merges them back together in sorted order.

#### Procedure

- **Divide** → Split array into 2 halves until you get single-element arrays.
- **Conquer** → Sort each half recursively.
- **Combine** → Merge the sorted halves into a single sorted array.

```java
import java.util.*;
class Main {
    
    public static void merge(int[] arr,int left,int mid,int right){
        int n1=mid-left+1;
        int n2=right-mid;
        
        int[] L=new int[n1];
        int[] R=new int[n2];
        
        for(int i=0;i<n1;i++)
            L[i]=arr[left+i];
        for(int i=0;i<n2;i++)
            R[i]=arr[mid+1+i];
            
        int i=0;
        int j=0;
        int k=left;
        
        while(i<n1 && j<n2){
            if(L[i]<=R[j]){
                arr[k]=L[i];
                i++;
            }
            else{
                arr[k]=R[j];
                j++;
            }
            k++;
        }
        
        while(i<n1){
            arr[k]=L[i];
            i++;
            k++;
        }
        
        while(j<n2){
            arr[k]=R[j];
            j++;
            k++;
        }
    }
    
    public static void mergeSort(int[] arr,int left,int right){
        if(left<right){
            int mid=(left+right)/2;
            
            mergeSort(arr,left,mid);
            mergeSort(arr,mid+1,right);
            merge(arr,left,mid,right);
        }
    }
    
    public static void main(String[] args) {
        int[] arr={7,6,23,4,3,9,12};
        mergeSort(arr,0,arr.length-1);
        int n = arr.length;
        for(int i = 0; i < n; i++){
            System.out.print(arr[i]+ " ");
        }
    }
}
```