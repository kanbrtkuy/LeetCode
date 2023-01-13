<h1>Solve with postorder traversal</h1>

<p>left + right</p>
<p>compare</p>
<p>go back to previous level</p>

```java
class Solution {
    int maxDiameter = 0;

    public int maxDepth(TreeNode root) {
        if(root == null) {
            return 0;
        }

        int leftMax = maxDepth(root.left);
        int rightMax = maxDepth(root.right);

        int myDiameter = leftMax + rightMax;
        int temp = maxDiameter;
        maxDiameter = Math.max(myDiameter, maxDiameter);

        return 1 + Math.max(leftMax, rightMax);


    }

    public int diameterOfBinaryTree(TreeNode root) {
        maxDepth(root);
        return maxDiameter;
    }
}
```
