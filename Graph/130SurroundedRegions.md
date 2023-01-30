<h1>Solved by DFS</h1>

<p>Use DFS check if there are some O on the four boarded</p>
<p>If tehre is, mark as P<p>
<p>change unmarked O to X, and change P to O</p>


```java
class Solution {
    public void dfs(char[][] board, int r, int c, int rLen, int cLen) {
        if(r<0 || c<0 || r>=rLen || c>=cLen || board[r][c] != 'O') {
            return;
        }

        board[r][c] = 'P';


        dfs(board, r+1, c, rLen, cLen);
        dfs(board, r, c+1, rLen, cLen);
        dfs(board, r-1, c, rLen, cLen);
        dfs(board, r, c-1, rLen, cLen);


    }

    public void solve(char[][] board) {

        int r = board.length;
        int c = board[0].length;

        for(int i = 0; i < r; i++) {
            dfs(board, i, 0, r, c);
            dfs(board, i, c-1, r, c);
        }

        for(int i = 0; i < c; i++) {
            dfs(board, 0, i, r, c);
            dfs(board, r-1, i, r, c);
        }

        for(int i = 0; i < r; i++) {
            for(int j = 0; j < c; j++) {
                if(board[i][j] == 'P') {
                    board[i][j] = 'O';
                } else {
                    board[i][j] = 'X';
                }
            }
        }
        
    }
}
```
