#Find the exact value
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while(left <= right) {
            int mid = left + (right - left) / 2;

            if(nums[mid] == target) {
                return mid;
            }else if(nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
    }
}
```


#Upper Bound

<p>Initialize the boundaries of the search space as left = 0 and right = nums.size (Note that the maximum insert position can be nums.size)</p>
<p>If there are elements in the range [left, right], we find the middle index mid = (left + right) / 2 and compare the middle value nums[mid] with target:</p>
<p>If nums[mid] <= target, let left = mid + 1 and repeat step 2.</p>
<p>If nums[mid] > target, let right = mid and repeat step 2.</p>
<p>We finish the loop and left stands for the insert position:</p>
<p>If left > 0 and nums[left - 1] = target, return left - 1.</p>
<p>Otherwise, return -1.</p>

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length;

        while(left < right) {
            int mid = left + (right - left)/2;
            if(nums[mid] <= target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        
        if(left > 0 && nums[left - 1] == target) {
            return left-1;
        }

        return -1;
    }
}
```

#Lower bound
<p>Initialize the boundaries of the search space as left = 0 and right = nums.size (Note that the maximum insert position can be nums.size)</p>
<p>If there are elements in the range [left, right], we find the middle index mid = (left + right) / 2 
and compare the middle value nums[mid] with target:</p>
<p>If nums[mid] >= target, let right = mid - 1 and repeat step 2.</p>
<p>If nums[mid] < target, let left = mid and repeat step 2.</p>
<p>We finish the loop and left stands for the insert position:</p>
<p>If left < nums.size and nums[left] = target, return left.</p>
<p>Otherwise, return -1.</p>

```java
class Solution {
    public int search(int[] nums, int target) {
        // Set the left and right boundaries
        int left = 0, right = nums.length;
        
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] >= target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        
        if (left < nums.length && nums[left] == target) {
            return left;
        } else {
            return -1;
        } 
    }
}
```
