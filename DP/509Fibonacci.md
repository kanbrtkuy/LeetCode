```java
class Solution {

    public int helper(int[] memo, int n) {
        if(n == 0 || n == 1) return n;

        if(memo[n] != 0) return memo[n];

        memo[n] = helper(memo, n - 1) + helper(memo, n - 2);
        return memo[n];

    }

    public int fib(int n) {
        int[] memo = new int[n + 1];
        return helper(memo, n);
    }
}
```

```java
class Solution {
    public int fib(int n) {
        if(n == 0) return 0;
        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp[1] = 1;

        for(int i = 2; i <=n; i++) {
            dp[i] = dp[i-1] + dp[i-2];
        }

        return dp[n];     
    }
}
```
```java
class Solution {
    public int fib(int n) {

        if(n == 0 || n == 1) return n;

        int fib1 = 1, fib2 = 0;

        for(int i = 2; i <= n; i++) {
            int fibi = fib1 + fib2;
            fib2 = fib1;
            fib1 = fibi; 
        } 

        return fib1;
        
    }
}
```
