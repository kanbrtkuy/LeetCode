<p>Time complexity: O(log(n))</p>
<p>Space complexity: O(log(n))</p>
```java
class Solution {

    private int getNext(int n) {
        int totalSum = 0;
        while(n > 0) {
            int d = n % 10;
            n = n / 10;
            totalSum += d*d;
        }
        return totalSum;
    }

    public boolean isHappy(int n) {
        Set<Integer> set = new HashSet<>();

        while(n != 1 && !set.contains(n)) {
            set.add(n);
            n = getNext(n);
        }
        
        return n == 1;
        
    }
}
```
