```java
class Solution {
    public int climbStairs(int n) {   
        return fibonacciHelper(n);
    }
    
    public int fibonacciHelper(int n) {
        if(n == 1) {
            return 1;
        } 

        if(n == 2) {
            return 2;
        }

        int cur = 0;
        int two = 1;
        int one = 2;

        for(int i = 2; i < n; i++) {
            cur = one + two;
            two = one;
            one = cur;
        }
        return cur;
    }
}
```
