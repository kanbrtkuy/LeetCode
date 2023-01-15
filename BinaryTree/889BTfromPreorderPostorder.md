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
    Map<Integer, Integer> map;

    public TreeNode build(int[] preorder, int preleft, int preright, int postleft, int postright) {
        if(preleft > preright) {
            return null;
        }

        if(preleft == preright) {
            return new TreeNode(preorder[preleft]);
        }

        int rootVal = preorder[preleft];
        TreeNode root = new TreeNode(rootVal);
        int leftChild = preorder[preleft+1];
        int postIndex = map.get(leftChild);
        int Size = postIndex - postleft + 1;

        root.left = build(preorder, preleft + 1, preleft + Size, postleft, postright);
        root.right = build(preorder, preleft + Size + 1, preright, postIndex + 1, postright - 1);

        return root;
    }

    public TreeNode constructFromPrePost(int[] preorder, int[] postorder) {

        map = new HashMap<>();

        for(int i = 0; i < postorder.length; i++) {
            map.put(postorder[i], i);
        }

        return build(preorder, 0, preorder.length-1, 0, postorder.length-1);
    }
}
```
