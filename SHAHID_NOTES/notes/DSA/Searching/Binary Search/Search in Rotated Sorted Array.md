

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        int[] arr={4,5,6,7,8,2,3};
        int left = 0;
        int right = arr.length-1;
        int target=3;
        while(left<=right){
            int mid=(left+right)/2;
            
            if(arr[mid]==target){
                System.out.print("Element found at index "+mid);
                return;
            }
            
            else if(arr[left]<=arr[mid]){
                if(arr[left]<=target && target<arr[mid]){
                    right=mid-1;
                }
                else{
                    left=mid+1;
                }
            }
            else{
                if(arr[mid]<target && target<=arr[right]){
                    left=mid+1;
                }
                else{
                    right=mid-1;
                }
            }
        }
        System.out.print("Element not found");
    }
}
```

