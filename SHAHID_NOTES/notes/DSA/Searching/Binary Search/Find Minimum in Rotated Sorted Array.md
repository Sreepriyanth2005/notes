
```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        int[] arr={4,5,6,7,8,2,3};
        int left = 0;
        int right = arr.length-1;
        while(left<right){
            int mid=(left+right)/2;
            
            if(arr[mid]>arr[right]){
                left=mid+1;
            }
            else{
                right=mid;
            }
        }
        System.out.print(arr[left]);
    }
}
```

