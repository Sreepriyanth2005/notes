![[Pasted image 20250807222927.png]]

### Optimized

```java

class Main {
    public static void main(String[] args) {
       int[] height={10,20,30,10};
       int prev1=0;
       int prev2=0;
       for(int i=1;i<height.length;i++){
           int jump1=prev1+Math.abs(height[i]-height[i-1]);
           int jump2=Integer.MAX_VALUE;
           if(i>1){
               jump2=prev2+Math.abs(height[i]-height[i-2]);
           }
           int curr=Math.min(jump1,jump2);
           prev2=prev1;
           prev1=curr;
       }
       System.out.print(prev1);
    }
}
```

### Memoization

```java

import java.util.*;
class Main {
    public static void main(String[] args) {
       int[] height={10,20,30,10};
       int[] dp=new int[height.length+1];
       Arrays.fill(dp,-1);
       System.out.print(frog(height.length-1,height,dp));
    }
    public static int frog(int n,int[] height,int[] dp){
        if(n==0)
            return 0;
        
        if(dp[n]!=-1)
            return dp[n];
        int left=frog(n-1,height,dp)+Math.abs(height[n]-height[n-1]);
        int right=Integer.MAX_VALUE;
        if(n>1)
            right=frog(n-2,height,dp)+Math.abs(height[n]-height[n-2]);
        dp[n]=Math.min(left,right);
        return dp[n];
    }
    
}
```