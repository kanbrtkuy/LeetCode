<h1>Solve by bucket sort</h1>
<p>Create a HashMap to put the number and it's frequency in it</p>
<p>Create a bucket, position number of the bucket refers to the frequency of the KeyValue in HashMap</p>
<p>Put each key in it's corresponding position in the bucket</p>
<p>Get the top K element from the bucket from back to start</p>


```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {

        Map<Integer, Integer> map = new HashMap<>();
        for(int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        List<Integer>[] bucket = new List[nums.length + 1];

        for(int key : map.keySet()) {
            int frequency = map.get(key);
            if(bucket[frequency] == null) {
                bucket[frequency] = new ArrayList<>();
            }
            bucket[frequency].add(key);
        }

        List<Integer> res = new ArrayList<>();

        

        for(int i = bucket.length - 1; i >= 0 && res.size() < k; i--) {
            if(bucket[i] != null) {
                res.addAll(bucket[i]);
            }
        }

        int[] ans = res.stream().mapToInt(Integer::intValue).toArray();

        return ans;

        
    }
}
```
