<h1>Solve by preorder traversal</h1>

<p>左行min不变，右行max不变</p>
<p>For two side of the tree</p>
<p>For left side</p>
<p>If max is not null and the current root vlaue is larger than previous root value, return false</p>
<p>For right side</p>
<p>If min is not null and the current root vlaue is larger than previous root value, return false</p>
<p>For the nodes in the middle</p>
<p>If min is not null and the current root vlaue is larger than previous root value, return false</p>
<p>If max is not null and the current root vlaue is larger than previous root value, return false</p>

```java
class Solution {
    public boolean isValidBST(TreeNode root, TreeNode min, TreeNode max) {
        if(root == null) {
            return true;
        }

        if(min != null && root.val <= min.val) {
            return false;
        }
        if (max != null && root.val >= max.val) {
            return false;
        } 

        return isValidBST(root.left, min, root) && isValidBST(root.right, root, max);

    }
    
    public boolean isValidBST(TreeNode root) {
        return isValidBST(root, null, null);
    }
}
```

