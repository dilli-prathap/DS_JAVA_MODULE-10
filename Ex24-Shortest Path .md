# Ex24 Shortest Path and Reachability in a Heritage Town using BFS
## DATE: 20-02-2026
## AIM:
To design and implement a java program that, given a map of attractions in a heritage town connected by walking paths, recommends:
The shortest number of paths (minimum hops) from a starting attraction to a target attraction.
The number of reachable attractions from the same starting point using Breadth-First Search (BFS)


## Algorithm

1. Start
2. Read number of vertices (n) and edges (e)
3. Create an adjacency list for the graph
4. For each edge:
5. Read vertices u and v
6. Add edge between u and v
7. Read start and target vertices
8. Perform BFS to find shortest path:
9. Initialize visited and distance arrays
10.Insert start into queue and mark visited
11.While queue is not empty:
12.Remove a vertex
13.If it is target, return its distance
14.For each neighbor, if not visited:
15.Mark visited, update distance, add to queue
16. Perform DFS from start to mark all reachable vertices
17. Count number of visited vertices
18. Display shortest path and total reachable vertices
19. Stop   

## Program:
``` JAVA
/*
Program to determine Shortest Path and Reachability in a Heritage Town using BFS
Developed by: DILLI PRATHAP
RegisterNumber:  212224110014  
*/
import java.util.*;

public class TouristNavigation {

public static int bfs(List<List<Integer>> graph, int start, int target, int n) {
boolean[] visited = new boolean[n];
int[] dist = new int[n];
Queue<Integer> q = new LinkedList<>();
q.offer(start);
visited[start] = true;
dist[start] = 0;

while (!q.isEmpty()) {
int curr = q.poll();
if (curr == target) return dist[curr];
for (int neigh : graph.get(curr)) {
if (!visited[neigh]) {
visited[neigh] = true;
dist[neigh] = dist[curr] + 1;
q.offer(neigh);
}
}
}
return -1;
}

public static void dfs(List<List<Integer>> graph, boolean[] visited, int node) {
visited[node] = true;
for (int neighbor : graph.get(node)) {
if (!visited[neighbor]) {
dfs(graph, visited, neighbor);
}
}
}

public static int countReachable(boolean[] visited) {
int count = 0;
for (boolean v : visited) if (v) count++;
return count;
}

public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
int n = sc.nextInt(), e = sc.nextInt();
List<List<Integer>> graph = new ArrayList<>();
for (int i = 0; i < n; i++) graph.add(new ArrayList<>());

for (int i = 0; i < e; i++) {
int u = sc.nextInt(), v = sc.nextInt();
graph.get(u).add(v);
graph.get(v).add(u);
}

int start = sc.nextInt();
int target = sc.nextInt();

int shortest = bfs(graph, start, target, n);
boolean[] visited = new boolean[n];
dfs(graph, visited, start);
int reachable = countReachable(visited);

System.out.println("Shortest path from start to target: " + shortest);
System.out.println("Total reachable attractions from start: " + reachable);
}
}
```

## Output:

<img width="927" height="235" alt="516891462-6d297bc4-1fe4-4b59-bc68-36ec9490cc8a" src="https://github.com/user-attachments/assets/a357971b-33e8-4986-9a85-9bd619081785" />


## Result:
The program has been successfully implemented and executed.
It correctly computes:
The shortest number of paths (minimum hops) between two attractions.
The total number of reachable attractions from a given starting point using BFS traversal.
