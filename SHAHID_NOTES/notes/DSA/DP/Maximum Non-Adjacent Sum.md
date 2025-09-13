	

> Given an array of integers, find the maximum sum of elements such that **no two elements are adjacent**.


`Input: [2, 1, 4, 9]   Output: 11   Explanation: Pick 2 and 9 (2 + 9 = 11)`

## Memoization

```java
import java.util.*;
class Main {
    static int[] nums={2,1,4,9};
    public static void main(String[] args) {
        int n=3;
        int[] dp=new int[n+1];
        Arrays.fill(dp,-1);
        int ans=rob(n,dp);
        System.out.print(ans);
    }
    public static int rob(int n,int[] dp){
        if(n==0) return nums[0];
        if(n<0) return 0;
        if(dp[n]!=-1)
            return dp[n];
        int pick=nums[n]+rob(n-2,dp);
        int notPick=0+rob(n-1,dp);
        return dp[n]=Math.max(pick,notPick);
    }
    
}
```