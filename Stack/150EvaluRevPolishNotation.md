```java
class Solution {
    public int evalRPN(String[] tokens) {

        Stack<Integer> stack = new Stack<>();

        for(String token : tokens) {
            
            if("+-*/".contains(token)) {
                int a = stack.pop(), b = stack.pop();
                switch(token) {
                    case "+":
                        stack.push(a + b);
                        break;
                    case "-":
                        stack.push(b - a);
                        break;
                    case "*":
                        stack.push(b * a);
                        break;
                    case "/":
                        stack.push(b / a);
                        break;
                }
            } else {
                stack.push(Integer.parseInt(token));
            }
        }

        return stack.pop();
        
    }
}
```
