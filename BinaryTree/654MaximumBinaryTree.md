<h1>Solve by preorder traversal</h1>

```java pseudocode
TreeNode constructMaximumBinaryTree([3,2,1,6,0,5]) {
    // 找到数组中的最大值
    TreeNode root = new TreeNode(6);
    // 递归调用构造左右子树
    root.left = constructMaximumBinaryTree([3,2,1]);
    root.right = constructMaximumBinaryTree([0,5]);
    return root;
}
```

```java
class Solution {

    TreeNode build(int[] nums, int lo, int hi) {
        if(lo > hi) {
            return null;
        }
        
        int index = -1;
        int maxVal = Integer.MIN_VALUE;

        for(int i = lo; i <= hi; i++) {
            if(maxVal < nums[i]) {
                index = i;
                maxVal = nums[i];
            }
        }

        TreeNode root = new TreeNode(maxVal);
        root.left = build(nums, lo, index - 1);
        root.right = build(nums, index + 1, hi);

        return root;
    }

    public TreeNode constructMaximumBinaryTree(int[] nums) {
        return build(nums, 0, nums.length - 1);
    }
}
```

