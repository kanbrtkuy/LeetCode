<h1>Solve the question by deque</h1>
<p>Time complexity O(n)</p>
<p>Space complexity O(n)</p>
<p>Code</p>

```java
class Solution {
    public boolean isPalindrome(String s) {
        String str = s.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();

        if(str.length() == 0) {
            return true;
        }

         Deque<Character> deque = new ArrayDeque<>();
         char[] chars = str.toCharArray();
         for(int i = 0; i < chars.length; i++) {
             deque.add(chars[i]);
         }
        
        if(str.length() % 2 != 0) {
            while(deque.size() != 1) {
                if(deque.getFirst() == deque.getLast()) {
                    deque.pollFirst();
                    deque.pollLast();
                } else {
                    return false;
                }
            }
        } else {
             while(deque.size() != 0) {
                if(deque.getFirst() == deque.getLast()) {
                    deque.pollFirst();
                    deque.pollLast();
                } else {
                    return false;
                }
            }
        }

        return true;

    }
}
```
