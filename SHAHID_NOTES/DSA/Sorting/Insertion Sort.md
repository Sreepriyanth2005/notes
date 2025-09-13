
#### Procedure

- You start with one card (already "sorted").
- Take the next card and insert it in the right place among the cards in your hand.
- Repeat until all cards are sorted.

```scss
Unsorted: [5 | 3, 4, 1, 2]
Step 1:   [3, 5 | 4, 1, 2]
Step 2:   [3, 4, 5 | 1, 2]
Step 3:   [1, 3, 4, 5 | 2]
Step 4:   [1, 2, 3, 4, 5]
```


```java
import java.util.*;
class Main {
    
    public static void insertionSort(int[] arr){
        int n = arr.length;
        for(int i = 1; i < n; i++){
            int key = arr[i];
            int j = i - 1;
            
            while(j >= 0 && arr[j] > key){
                arr[j + 1] = arr[j];
                j--;
            }
            
            arr[j + 1] = key;
        }
    }
    public static void main(String[] args) {
        int[] arr={2,5,3,5,1};
        insertionSort(arr);
        int n = arr.length;
        for(int i = 0; i < n; i++){
            System.out.print(arr[i]+ " ");
        }
    }
}
```

