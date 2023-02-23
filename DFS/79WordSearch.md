```java
class Solution {

    boolean found = false;

    public void dfs(char[][] board, int i, int j, String word, int p) {
        if(p == word.length()) {
            found = true; 
            return;
        } 

        if(found == true) return;

        if(i < 0 || j < 0 || i >= board.length || j >= board[0].length) return;

        if(board[i][j] != word.charAt(p)) return;

        board[i][j] = (char)(-board[i][j]);

        dfs(board, i + 1, j, word, p + 1);
        dfs(board, i, j + 1, word, p + 1);
        dfs(board, i - 1, j, word, p + 1);
        dfs(board, i, j - 1, word, p + 1);

        board[i][j] = (char)(-board[i][j]);

    }

    public boolean exist(char[][] board, String word) {
        for(int i = 0; i < board.length; i++) {
            for(int j = 0; j < board[0].length; j++) {
                dfs(board, i, j, word, 0);
                if(found) {
                    return true;
                }
            }
        }

        return false;
    }
}
```
