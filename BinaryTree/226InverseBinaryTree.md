解题方法:\
前序遍历\
分解问题/后续遍历\


<h1>Solve with preorder traversal</h1>

<p>先进行左右交替</p>
<p>从左到右交替</p>


```java
class Solution {
    public void inverse(TreeNode root) {
        if(root == null) {
            return;
        }

        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;

        inverse(root.left);
        inverse(root.right);
    }

    public TreeNode invertTree(TreeNode root) {
        inverse(root);
        return root;
    }
}
```

<h1>Solve with pastorder traversal</h1>

```java
class Solution {
    public TreeNode invertTree(TreeNode root) {

        if(root == null) {
            return null;
        }

        TreeNode left = invertTree(root.left);
        TreeNode right = invertTree(root.right);

        root.left = right;
        root.right = left;

        return root;
        
    }
}
```
