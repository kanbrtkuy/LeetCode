<h1>Solve by postorder traversal</h1>
```java
class Solution {
  public int minDepth(TreeNode root) {
    if (root == null) {
      return 0;
    }

    if ((root.left == null) && (root.right == null)) {
      return 1;
    }

    int min_depth = Integer.MAX_VALUE;
    if (root.left != null) {
      min_depth = Math.min(minDepth(root.left), min_depth);
    }
    if (root.right != null) {
      min_depth = Math.min(minDepth(root.right), min_depth);
    }

    int res = min_depth + 1;

    return res;
  }
}
```
<h1>Solved by BFS</h1>

