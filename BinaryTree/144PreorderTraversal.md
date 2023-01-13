<h1>Solve with iterative recursion</h1>

```java
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {

        List<Integer> res = new LinkedList<>();

        if(root == null) {
            return res;
        }

        res.add(root.val);
        res.addAll(preorderTraversal(root.left));
        res.addAll(preorderTraversal(root.right));

        return res;
        
    }
}
```

