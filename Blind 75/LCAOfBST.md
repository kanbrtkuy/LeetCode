#Solve this question by recursive approach

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {

        	int parentValue = root.val;
	int pValue = p.val;
	int qValue = q.val;
	
	if(pValue > parentValue && qValue > parentValue) {
		return lowestCommonAncestor(root.right, p, q);
	} else if(pValue < parentValue && qValue < parentValue) {
		return lowestCommonAncestor(root.left, p, q);
	} else {
		return root;
	}

    }
}
```

#Solve the question by iterative approach

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {

        	
	int pValue = p.val;
	int qValue = q.val;

	TreeNode node = root;
	
	while(root!=null) {
		if(pValue > root.val && qValue > root.val) {
			root = root.right;
		} else if(pValue < root.val && qValue < root.val) {
			root = root.left;
		} else {
			return root;
		}
	}
	return null;

    }
}
```