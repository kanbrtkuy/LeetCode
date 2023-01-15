<h1>Solved by Preorder Traversal</h1>

<p>Create a inrder HashMap and import the value and index of inorder elements</p>
<p>From end to start, convert the element as root</p>
<p>Get the index of the root in inorder HashMap, and find the left side and right side of the tree</p>
<p>We start from the right side, use recursion to build the tree</p>


```java
class Solution {
    int PostorderIndex;
    Map<Integer, Integer> InorderMap;

    public TreeNode build(int[] postorder, int left, int right) {
        if(left > right) {
            return null;
        }
        
        int rootValue = postorder[PostorderIndex--];
        TreeNode root = new TreeNode(rootValue);
        int index = InorderMap.get(rootValue);
        root.right = build(postorder, index + 1, right);
        root.left = build(postorder, left, index - 1);


        return root;
    }

    public TreeNode buildTree(int[] inorder, int[] postorder) {
        PostorderIndex = postorder.length - 1;
        InorderMap = new HashMap<>();
        for(int i = 0; i < inorder.length; i++) {
            InorderMap.put(inorder[i], i);
        }

        return build(postorder, 0, postorder.length - 1);
    }
}
```
