```java
class Solution {


    public int[] productExceptSelf(int[] nums) {

        int n = nums.length;
        int[] time = new int[n];
        int temp = 1;
        int count = 0;

        for(int i = 0; i < n; i++) {
            if(nums[i] == 0){
                count += 1;
            } else {
                temp *= nums[i];
            }
        }

        if(count > 1) {
            return new int[nums.length];
        } else if(count == 1) {
            for(int i = 0; i < nums.length; i++) {
                if(nums[i] == 0) time[i] = temp;
            }
        } else {
            for(int i = 0; i < n; i++) {
                time[i] = temp / nums[i];
            }
        }

        return time;
        
    }
}
```
