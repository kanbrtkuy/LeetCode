#Solve the problem by recursive approach

```java
class Solution {
    	public boolean isBalanced(TreeNode root) {
		if(root == null) {
			return true;
		} 
		if(Height(root) == -1) {
			return -1;
		}
		return true;
	}
  
	public int Height(TreeNode root) {
		if(root == null) {
			return 0;
		}
		int leftHeight = Height(root.left);
		int rightHight = Height(root.right);
		if(leftHeight == -1 || rightHeight == -1) {
			return -1;
		}
		if(Math.abs(leftHeight - rightHight) > 1) {
			return -1;
		}
		
		return Math.max(leftHeight, rightHight) + 1;

	}
}
```