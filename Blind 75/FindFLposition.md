#Solve with binary search

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {

        int left = findPosition(nums, target, 0);
        
        if (left == -1) {
            return new int[]{-1, -1};
        }

        int right = findPosition(nums, target, 1);

        return new int[]{left, right};

    }

    public int findPosition(int[] nums, int target, int i) {
        int left = 0;
        int right = nums.length - 1;

        while(left <= right) {
            int mid = left + (right - left)/2;

            if(target == nums[mid]) {
                if(i == 0) {
                    if(mid == left || target != nums[mid - 1]) {
                        return mid;
                    } else {
                        right -= 1;
                    }

                } else {
                    if(mid == right || target != nums[mid + 1]) {
                        return mid;
                    } else {
                        left = mid + 1;
                    }

                }
            } else if(target > nums[mid]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;

    }
}
```