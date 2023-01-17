<h1>Solve by BFS</h1>
<p>If root is null, return res</p>
<p>Put root in to queue</p>
<p>Start BFS</p>
<p>While queue is not null</p>
<p>Traversal each level</p>
<p>In each level, add value to list, and pop the first value in queue and get it's children if it has</p>
<p>After each level, put the temp list to res</p>

```java
class Solution {
    public List<List<Integer>> levelOrder(Node root) {

        List<List<Integer>> res = new ArrayList<>();

        Queue<Node> queue = new LinkedList<>();

        if(root == null) {
            return res;
        }

        queue.offer(root);

        while(!queue.isEmpty()) {
            int size = queue.size();
            List<Integer> temp = new ArrayList<>();

            for(int i = 0; i < size; i++) {
                temp.add(queue.peek().val);
                queue.addAll(queue.poll().children);
            }

            res.add(temp);
        }

        return res;
        
    }
}
```

