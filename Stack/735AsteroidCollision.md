<h1>Solve by Stack</h1>

<p>If input larger than 0, push into stack</p>
<p>Else</p>
<p>While stack is not empty and stack.peek() larger than 0 and stack.peek() smaller than input, pop stack</p>
<p>If stack is empty or stack.peek() is smaller tha 0, push input</p>
<p>Else if stack.peek() is equal to input, pop stack</p>

```java
class Solution {
    public int[] asteroidCollision(int[] asteroids) {
        Stack<Integer> s = new Stack<>();
        for(int i: asteroids){
            if(i > 0){
                s.push(i);
            }else{// i is negative
                while(!s.isEmpty() && s.peek() > 0 && s.peek() < Math.abs(i)){
                    s.pop();
                }
                if(s.isEmpty() || s.peek() < 0){
                    s.push(i);
                }else if(i + s.peek() == 0){
                    s.pop(); //equal
                }
            }
        }
        int[] res = new int[s.size()];   
        for(int i = res.length - 1; i >= 0; i--){
            res[i] = s.pop();
        }
        return res;
    }
}

```
