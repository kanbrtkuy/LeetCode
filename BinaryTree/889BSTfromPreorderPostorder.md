<h1>Solve by preorder traversal</h1>

<p>Create a hashmap to store the value and index of the postorder elements</p>
<p>In the recursion approach</p>
<p>If left index is larger than right index return null</p>
<p>If left index is equal to right index, create the last child of that side</p>
<p>Get cur preorder element value, and use the value create a new root</p>
<p>Find the left root value and fund it's index in postorder</p>
<p>Get left side's child size</p>
<p>doing recursion of left and right side</p>


```java
class Solution {
    HashMap<Integer, Integer> valToIndex = new HashMap<>();

    public TreeNode constructFromPrePost(int[] preorder, int[] postorder) {
        for (int i = 0; i < postorder.length; i++) {
            valToIndex.put(postorder[i], i);
        }
        return build(preorder, 0, preorder.length - 1,
                    postorder, 0, postorder.length - 1);
    }

    TreeNode build(int[] preorder, int preStart, int preEnd,
                   int[] postorder, int postStart, int postEnd) {
        if (preStart > preEnd) {
            return null;
        }
        if (preStart == preEnd) {
            return new TreeNode(preorder[preStart]);
        }

        int rootVal = preorder[preStart];
        TreeNode root = new TreeNode(rootVal);
        int leftRootVal = preorder[preStart + 1];
        int index = valToIndex.get(leftRootVal);
        int leftSize = index - postStart + 1;
        
        root.left = build(preorder, preStart + 1, preStart + leftSize,
                postorder, postStart, index);
        root.right = build(preorder, preStart + leftSize + 1, preEnd,
                postorder, index + 1, postEnd - 1);

        return root;
    }
}
```
