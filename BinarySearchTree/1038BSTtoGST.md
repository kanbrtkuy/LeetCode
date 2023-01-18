<h1>Solve by inorder traversal</h1>
<p>Traverse from right to left</p>
<p>Add the count and current node value up, and give the sum value to current node</p>

```java
class Solution {
    int count = 0;
    public void GST(TreeNode root) {
        if(root == null) {
            return;
        }

        GST(root.right);
        count += root.val;
        root.val = count;
        GST(root.left);
    }
    
    public TreeNode bstToGst(TreeNode root) {
        GST(root);
        return root;
    }
}
```
