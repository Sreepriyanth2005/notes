
**Modified Climbing Ways:**

You are climbing a staircase that has `n` steps.  
You can take either 1 step or 2 steps at a time.  
**However, you are NOT allowed to end your climb by taking a single step.**

Return the number of distinct ways you can reach the top of the staircase with this constraint.

### Memoization

```java
import java.util.*;
class Main {
    public static void main(String[] args) {
        int n=5;
        int[] dp=new int[n+1];
        Arrays.fill(dp,-1);
        int ans=rob(n,dp);
        System.out.print(ans);
    }
    public static int rob(int n,int[] dp){
        if(n==0) return 1;
        if(n==1) return 1;
        if(dp[n]!=-1)
            return dp[n];
        return dp[n]=rob(n-1,dp)+rob(n-2,dp);
    }
    
}
```

### Optimized

```java

class Main {
    public static void main(String[] args) {
        int n=5;
        int ans=rob(n);
        int[] dp=new dp[n+1];
        System.out.print(ans);
    }
    public static int rob(int n){
        if(n==0) return 1;
        if(n==1) return 1;
        int left=rob(n-1);
        int right=rob(n-2);
        return left+right;
    }
    
}
```



``
