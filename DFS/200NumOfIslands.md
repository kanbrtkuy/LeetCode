<h1>Solve by DFS</h1>

```java
class Solution {

    public void dfs(char[][] grid, int i, int j) {
        if(i < 0 || j < 0 || i >= grid.length || j>= grid[0].length) {
            return;
        }

        if(grid[i][j] == '0') {
            return;
        }

        grid[i][j] = '0';

        dfs(grid, i + 1, j);
        dfs(grid, i, j + 1);
        dfs(grid, i - 1, j);
        dfs(grid, i, j - 1);
    }

    public int numIslands(char[][] grid) {

        int c = grid.length;
        int r = grid[0].length;

        int count = 0;

        for(int i = 0; i < c; i++) {
            for(int j = 0; j < r; j++) {
                if(grid[i][j] == '1') {
                    count += 1;
                    dfs(grid, i, j);
                }
            }
        }

        return count;
        
    }
}
```
