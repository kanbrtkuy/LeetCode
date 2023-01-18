<h1>Solve by inorder traversal</h1>

<p>Since the nodes in the tree are ascending order, the time the recursion program return is the ranking the node in the tree</p>
<p>Use inorder traversal to find the rank to each node and return it's value</p>

```java
class Solution {
    int rank = 0;
    int res = 0;
    
    public void find(TreeNode root, int k) {
        if(root == null) {
            return;
        }

        find(root.left, k);
        rank += 1;
        if(k == rank) {
            res = root.val;
            return;
        }
        find(root.right, k);
    }

    public int kthSmallest(TreeNode root, int k) {
        find(root, k);
        return res;
    }
}
```
