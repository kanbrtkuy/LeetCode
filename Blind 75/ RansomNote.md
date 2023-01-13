#Solved the question by HashMap

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {

        Map<Character, Integer> rn = new HashMap<>();
        Map<Character, Integer> ma = new HashMap<>();

        char[] arr_r = ransomNote.toCharArray();
        char[] arr_m = magazine.toCharArray();

        for(Character r : arr_r) {
            if(rn.containsKey(r)) {
                rn.put(r, rn.get(r) + 1);
            } else {
                rn.put(r, 1);
            }
        }

        for(Character m : arr_m) {
            if(ma.containsKey(m)) {
                ma.put(m, ma.get(m) + 1);
            } else {
                ma.put(m, 1);
            }
        }

        int flag = 0;

        for(Map.Entry<Character, Integer> MapElement : rn.entrySet()) {
            if(ma.containsKey(MapElement.getKey()) && ma.get(MapElement.getKey()) < MapElement.getValue()) {
                flag += 1;
            } else if (!ma.containsKey(MapElement.getKey())) {
                flag += 1;
            }
        }

        if(flag > 0) {
            return false;
        }

        return true;
        
    }
}
```