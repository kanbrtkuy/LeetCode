<h1>Solve by Preorder Traversal</h1>

<p>Put each inorder's value as key and index as value in a hashmap</p>
<p>Traverse each Inorder's element</p>
<p>Make each element as root</p>
<p>Find that element's index in inorder, to get it's left side and right side's child</p>
<p>Use recursion to build the tree</p>

```java
class Solution {
    int preorderIndex;
    Map<Integer, Integer> inorderIndexMap;
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        preorderIndex = 0;
        // build a hashmap to store value -> its index relations
        inorderIndexMap = new HashMap<>();
        for (int i = 0; i < inorder.length; i++) {
            inorderIndexMap.put(inorder[i], i);
        }

        return arrayToTree(preorder, 0, preorder.length - 1);
    }

    private TreeNode arrayToTree(int[] preorder, int left, int right) {
        // if there are no elements to construct the tree
        if (left > right) return null;

        // select the preorder_index element as the root and increment it
        int rootValue = preorder[preorderIndex++];
        TreeNode root = new TreeNode(rootValue);

        int index = inorderIndexMap.get(rootValue);
        // build left and right subtree
        // excluding inorderIndexMap[rootValue] element because it's the root
        root.left = arrayToTree(preorder, left, index - 1);
        root.right = arrayToTree(preorder, index + 1, right);
        return root;
    }
}
```
