
```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        int[] arr={3,4,5,6,7,0,1,2};
        int left=0;
        int right=arr.length-1;
        while(left<right){
            int mid=(left+right)/2;
            
            if(arr[right]<arr[mid]) left=mid+1;
            else right=mid;
        }
        int maxIdx=(left-1+arr.length)%arr.length;
        System.out.println(arr[maxIdx]);
    }
}
```

