<h1> Solve the question by hashmap</h>
<p>Time complexity O(n)</p>
<p>Space complexity O(1)</p>

```java
class Solution {
    public boolean isAnagram(String s, String t) {

        if(s.length() != t.length()) {
            return false;
        }

        Map<Character, Integer> map = new HashMap<>();
        int sum = 0;

        for(int i = 0; i < s.length(); i++) {
            if(!map.containsKey(s.charAt(i))) {
                map.put(s.charAt(i), 1);
                sum += 1;
            } else {
                map.put(s.charAt(i), map.get(s.charAt(i)) + 1);
                sum += 1;
            }
        }

        for(int i = 0; i < t.length(); i++) {
            if(!map.containsKey(t.charAt(i))) {
                return false;
            } else if(map.get(t.charAt(i)) == 0) {
                return false;

            } else {
                map.put(t.charAt(i), map.get(t.charAt(i)) - 1);
                sum -= 1;
            }
        }

        if(sum != 0) {
            return false;
        }

        return true;
        
    }
}
```
