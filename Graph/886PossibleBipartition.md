<h1>Solve by DFS</h1>

<p>create graph</p>
<p>solve quetion by bipartition</p>


```java
class Solution {
    private boolean ok = true;
    private boolean[] color;
    private boolean[] visited;

    public boolean possibleBipartition(int n, int[][] dislikes) {
        color = new boolean[n + 1];
        visited = new boolean[n + 1];
        List<Integer>[] graph = buildGraph(n, dislikes);
        
        for (int v = 1; v <= n; v++) {
            if (!visited[v]) {
                traverse(graph, v);
            }
        }
        
        return ok;
    }

    private List<Integer>[] buildGraph(int n, int[][] dislikes) {
        List<Integer>[] graph = new LinkedList[n + 1];
        for (int i = 1; i <= n; i++) {
            graph[i] = new LinkedList<>();
        }
        for (int[] edge : dislikes) {
            int v = edge[1];
            int w = edge[0];

            graph[v].add(w);
            graph[w].add(v);
        }
        return graph;
    }

    private void traverse(List<Integer>[] graph, int v) {
        if (!ok) return;
        visited[v] = true;
        for (int w : graph[v]) {
            if (!visited[w]) {
                color[w] = !color[v];
                traverse(graph, w);
            } else {
                if (color[w] == color[v]) {
                    ok = false;
                    return;
                }
            }
        }
    }
}
```

<h1>Solved by BFS</h1>

```java
class Solution {
    boolean ok = true;
    boolean[] visit;
    boolean[] color;

    public List<Integer>[] CreateGraph(int n, int[][] dislikes) {
        List<Integer>[] graph = new LinkedList[n+1];
        for(int i = 1; i <= n; i++) {
            graph[i] = new LinkedList<>();
        }

        for(int[] edge : dislikes) {
            int v = edge[1];
            int w = edge[0];

            graph[v].add(w);
            graph[w].add(v);
        }
        return graph;

    }

    public void traverse(List<Integer>[] graph, int i) {
        Queue<Integer> queue = new LinkedList<>();

        visit[i] = true;

        queue.offer(i);

        while(!queue.isEmpty()) {
            int cur = queue.poll();

            for(int w : graph[cur]) {
                if(!visit[w]) {
                    color[w] = !color[cur];
                    visit[w] = true;
                    queue.offer(w);
                } else {
                    if(color[w] == color[cur]) {
                        ok = false;
                        return;
                    }
                }
            }
        }
    }



    public boolean possibleBipartition(int n, int[][] dislikes) {
        visit = new boolean[n + 1];
        color = new boolean[n + 1];

        List<Integer>[] graph = CreateGraph(n, dislikes);

        for(int i = 1; i <= n; i++) {
            if(!visit[i]) {
                traverse(graph, i);
            }
        }

        return ok;
    }
}
```
