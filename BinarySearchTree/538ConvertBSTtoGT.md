<h1>Solve by inorder traversal</h1>

<p>Traverse from right to left, and  add the Node value which are larger than it self</p>

```java
 */
class Solution {
    int count = 0;
    public void count(TreeNode root) {
        if(root == null) {
            return;
        }

        count(root.right);
        int temp = root.val;
        root.val = root.val + count;
        count += temp;
        count(root.left);

    }

    public TreeNode convertBST(TreeNode root) {
        count(root);
        return root;
    }
}
```
