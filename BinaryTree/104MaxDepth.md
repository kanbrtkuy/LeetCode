#Solve with iterative recursion

<p>depth += 1 during preorder traversal</p>
<p>Give the max value of res and depth to res</p>
<p>depth -= 1 during postorder traversal</p>

```java
class Solution {
    int depth = 0;
    int res = 0;

    public void traverse(TreeNode root) {
        if(root == null) {
            res = Math.max(res, depth);
            return;
        }

        depth += 1;
        traverse(root.left);
        traverse(root.right);
        depth -= 1;
    }

    public int maxDepth(TreeNode root) {
        traverse(root);
        return (res);
        
    }
}
```

#Solve with factorization

<p>Find left depth</p>
<p>Find right depth</p>
<p>Compare left and right depth, give the max depth to res and +1</p>
<p>recursion until the end</p>

```java
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) {
            return 0;
        }

        int leftMax = maxDepth(root.left);
        int rightMax = maxDepth(root.right);

        int res = Math.max(leftMax, rightMax) + 1;

        return res;
    }
}
```
