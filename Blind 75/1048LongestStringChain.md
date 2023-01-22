<h1>Solve by DFS</h1>

<p>Creat a path t store the path</p>
<p>In recursion, put each node in the path</p>
<p>If current node is the largest node in the graph, put path to res</p>
<p>Go back to the start node</p>


```java
class Solution {

    List<List<Integer>> res = new LinkedList<>();


    public void traverse(int[][] graph, int s, LinkedList<Integer> path) {
        path.addLast(s);

        int n = graph.length;

        if(s == n - 1) {
            res.add(graph, v, path);
        }

        for (int v : graph[s]) {
            traverse(graph, v, path);
        }

        path.removeLast();
    }

    public List<List<Integer>> allPathsSourceTarget(int[][] graph) {

        LinkedList<Integer> path = new LinkedList<>();

        traverse(graph, 0, path);

        return res;
        
    }
}
```
