<h1>Solved by DFS</h1>

<p>Traverse each unvisited node</p>
<p>In recursion</p>
<p>If not ok, return</p>
<p>mark node as visited</p>
<p>recursion each node's connected node</p>
<p>if unvisited, make color different with previous one</p>
<p>recursion current noce</p>
<p>if visited</p>
<p>if color is same with previous one</p>
<p>ok is false, return</p>


```java
class Solution {
    boolean ok = true;
    boolean[] color;
    boolean[] visited;

    public void traverse(int[][] graph, int v) {
        if(!ok) return;

        visited[v] = true;

        for(int w : graph[v]) {
            if(!visited[w]) {
                color[w] = !color[v];
                traverse(graph, w);
            } else {
                if(color[w] == color[v]) {
                    ok = false;
                    return;
                }
            }
        }

    }

    public boolean isBipartite(int[][] graph) {
        int n = graph.length;
        color = new boolean[n];
        visited = new boolean[n];

        for(int v = 0; v < n; v++) {
            if(!visited[v]) {
                traverse(graph, v);
            }
        }

        return ok;
        
    }
}
```


```java
class Solution {
    boolean ok = true;
    boolean[] visit;
    boolean[] color;

    public void traverse(int[][] graph, int start) {
        if(ok == false) return;
        Queue<Integer> queue = new LinkedList<>();
        visit[start] = true;
        queue.offer(start);

        while(!queue.isEmpty()) {
            int v = queue.poll();
            for(int w : graph[v]) {
                if(!visit[w]) {
                    color[w] = !color[v];
                    visit[w] = true;
                    queue.offer(w);
                } else {
                    if(color[w] == color[v]) {
                        ok = false;
                        return;
                    }
                }
            }
        }
    }

    public boolean isBipartite(int[][] graph) {

        int n = graph.length;
        visit = new boolean[n];
        color = new boolean[n];

        for(int i = 0; i < n; i++) {
            if(!visit[i]) {
                traverse(graph, i);
            }
        }

        return ok;
        
    }
}
```
