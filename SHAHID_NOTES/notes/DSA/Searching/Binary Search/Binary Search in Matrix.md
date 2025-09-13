
```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        int[][] arr={
            {1,2,3},
            {4,5,6},
            {7,8,9}
        };
        int target=8;
        int row=arr.length;
        int col=arr[0].length;
        int left=0;
        int right=(row*col)-1;
        while(left<=right){
            int mid=(left+right)/2;
            int rowIdx=mid/col;
            int colIdx=mid%col;
            int middle=arr[rowIdx][colIdx];
            
            if(middle==target){
                System.out.print("Element found at index ("+rowIdx+","+colIdx+")");
                return;
            }
            else if(target<middle){
                right=mid-1;
            }
            else{
                left=mid+1;
            }
        }
        System.out.print("Element not found");
    }
}
```