```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        memo = new int[m][n];
        return dp(obstacleGrid, m - 1, n - 1);
    }

    // 备忘录
    int[][] memo;

    // 定义：从 grid[0][0] 出发到达 grid[i][j] 的路径条数为 dp(grid, i, j)
    public int dp(int[][] grid, int i, int j) {
        int m = grid.length, n = grid[0].length;
        // base case
        if (i < 0 || i >= m || j < 0 || j >= n || grid[i][j] == 1) return 0;
        
        if (i == 0 && j == 0) return 1;
        
        if (memo[i][j] > 0) {
            // 避免冗余计算
            return memo[i][j];
        }
        // 状态转移方程：
        // 到达 grid[i][j] 的路径条数等于
        // 到达 grid[i-1][j] 的路径条数加上到达 grid[i][j-1] 的路径条数
        int res = dp(grid, i, j - 1) + dp(grid, i - 1, j);
        // 存储备忘录
        memo[i][j] = res;
        return res;
    }
}
```

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;

        int[][] memo = new int[m + 1][n + 1];

        memo[1][1] = obstacleGrid[0][0] == 1 ? 0 : 1;

        for(int i = 1; i <= m; i++) {
            for(int j = 1; j <= n; j++) {
                if(i == 1 && j == 1) continue;

                if(obstacleGrid[i - 1][j - 1] == 1) continue;

                memo[i][j] = memo[i - 1][j] + memo[i][j - 1];
            }
        }

        return memo[m][n];
    }
}
```
