
### Memoization

```java

class Main {
    public static void main(String[] args) {
       int n=4;
       int[] dp=new int[n+1];
       System.out.print(fibo(n,dp));
    }
    public static int fibo(int n,int[] dp)
    {
        if(n<=1)
            return n;
        if(dp[n]!=0)
            return dp[n];
        
        return dp[n]=fibo(n-1,dp)+fibo(n-2,dp);
    }
}
```

##### TC : O(n)  ; SC : O(n)+O(n)
### Tabulation

```java
class Main {
    public static void main(String[] args) {
       int n=6;
       int[] dp=new int[n+1];
       dp[0]=0;
       dp[1]=1;
       for(int i=2;i<=n;i++)
            dp[i]=dp[i-1]+dp[i-2];
       System.out.print(dp[n]);
    }
}
```
##### TC : O(n)  ; SC : O(n)

