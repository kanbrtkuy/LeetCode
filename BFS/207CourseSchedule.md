<h1>Solved by BFS</h1>
<p>Creat an array to store how many pre course does each course need to tack</p>
<p>If there is any basic start course there, put them in a queue</p>
<p>Poll each basic course from queue, and match if any course have this basic course as pre course. If they have, delete one from the pre course array</p>
<p>Check if pre course array is emoty, if it is, return true, else return false</p>

```java
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        if(numCourses <= 0)
            return false;
        Queue<Integer> queue = new LinkedList<Integer>();
        int[] inDegree = new int[numCourses];
        for(int i = 0; i < prerequisites.length; i++) {
            inDegree[prerequisites[i][0]]++;
        } 
        for(int i = 0; i < numCourses; i++){
            if(inDegree[i] == 0){
                queue.offer(i); // find the start courses
            }
        }
        // begin traverse
        while(!queue.isEmpty()){
            int startCourse = queue.poll();
            for(int i = 0; i < prerequisites.length; i++){
                if(startCourse == prerequisites[i][1]){
                    if(--inDegree[prerequisites[i][0]] == 0){
                        queue.offer(prerequisites[i][0]);
                    }
                }
            }
        }
        for(int i =0; i < numCourses; i++){
            if(inDegree[i] !=0) return false;
        }
        return true;
    }
}
```
