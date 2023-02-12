```java
class Merge {

    private static int[] temp;

    private static void merge(int[] nums, int lo, int mid, int hi) {
        int[] temp2 = temp;
        for(int i = lo; i <= hi; i++) {
            temp[i] = nums[i];
        }

        int i = lo, j = mid + 1;

        for(int p = lo; p <= hi; p++) {
            if(i == mid + 1) {
                nums[p] = temp[j++];
            } else if(j == hi + 1) {
                nums[p] = temp[i++];
            } else if(temp[i] > temp[j]) {
                nums[p] = temp[j++];
            } else {
                nums[p] = temp[i++];
            }
        }
    }


    private static void sort(int[] nums, int lo, int hi) {

        if(lo == hi) return;

        int mid = lo + (hi - lo)/2;

        sort(nums, lo, mid);
        sort(nums, mid + 1, hi);

        merge(nums, lo, mid, hi);
    }

    public static void sort(int[] nums) {
        int n = nums.length;
        temp = new int[n];
        sort(nums, 0, n - 1);
    }
}

class Solution {
    public int[] sortArray(int[] nums) {
        Merge.sort(nums);
        return nums;
    }
}
```
