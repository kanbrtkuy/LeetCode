<h1>Solved by BFS</h1>

<p>Create an array to count how many pre courses does each course need</p>
<p>Create a queue to put all of the basic course in it</p>
<p>Start BFS, if cur is some course's pre course, - 1 from the array</p>
<p>After -1, if preNum[i] == 0, queue.offer</p>

```java
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {

        if(numCourses <= 0) {
            return false;
        }

        Queue<Integer> queue = new LinkedList<>();

        int[] preNum = new int[numCourses];

        for(int i = 0; i < prerequisites.length; i++) {
            preNum[prerequisites[i][0]] += 1;
        }

        for(int i = 0; i < preNum.length; i++) {
            if(preNum[i] == 0) {
                queue.offer(i);
            }
        }

        while(!queue.isEmpty()) {
            int cur = queue.poll();
            for(int i = 0; i < prerequisites.length; i++) {
                if(cur == prerequisites[i][1]) {
                    if(--preNum[prerequisites[i][0]] == 0) {
                        queue.offer(prerequisites[i][0]);
                    }
                }
            }
        }

        for(int i = 0; i < preNum.length; i++) {
            if(preNum[i] != 0) {
                return false;
            }
        }

        return true;
        
    }
}
```

<h1>Solve by DFS</h1>

<p>Creat a graph</p>
<p>Traverse each node and cheack if there is a cycle</p>

```java
class Solution {

    // 记录一次递归堆栈中的节点
    boolean[] onPath;
    // 记录遍历过的节点，防止走回头路
    boolean[] visited;
    // 记录图中是否有环
    boolean hasCycle = false;

    public List<Integer>[] buildGraph(int numCourses, int[][] prerequisites) {
        List<Integer>[] graph = new LinkedList[numCourses];
        for(int i = 0; i < numCourses; i++) {
            graph[i] = new LinkedList<>();
        }
        for(int[] edge : prerequisites) {
            int from = edge[1], to = edge[0];
            graph[from].add(to);
        }
        return graph;
    }

    public void traverse(List<Integer>[] graph, int s) {
        if (onPath[s]) {
            // 出现环
            hasCycle = true;
        }

        if (visited[s] || hasCycle) {
            // 如果已经找到了环，也不用再遍历了
            return;
        }
        // 前序代码位置
        visited[s] = true;
        onPath[s] = true;
        for (int t : graph[s]) {
            traverse(graph, t);
        }
        // 后序代码位置
        onPath[s] = false;
    }

    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<Integer>[] graph = buildGraph(numCourses, prerequisites);

        visited = new boolean[numCourses];
        onPath = new boolean[numCourses];

        for (int i = 0; i < numCourses; i++) {
            traverse(graph, i);
        }
        return !hasCycle;
        
    }
}
```
