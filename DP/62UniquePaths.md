```java
class Solution {
    int[][] memo;

    public int dp(int x, int y) {
        int[][] temp = memo;

        //起点处标记为1
        if(x == 0 && y == 0) return 1;

        //边界之外的点标记为0
        if(x < 0 || y < 0) return 0;

        //记录节省查询时间
        if(memo[x][y] > 0) return memo[x][y];

        //每个点的值是左边和上边点标记数字的和
        memo[x][y] = dp(x-1, y) + dp(x, y-1);
        return memo[x][y];

    }

    public int uniquePaths(int m, int n) {
        memo = new int[m][n];
        return dp(m - 1, n - 1);
        
    }
}
```
