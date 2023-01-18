<h1>Solve by recursion</h1>

<p>If target value is larger than current node value, go to right</p>
<p>If target value is less than current node value, go to left</p>
<p>If the current node is null, insert</p>

```java
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {

        if (root == null) return new TreeNode(val);
        if (root.val < val) 
            root.right = insertIntoBST(root.right, val);
        if (root.val > val) 
            root.left = insertIntoBST(root.left, val);
        return root;
        
    }
}
```
