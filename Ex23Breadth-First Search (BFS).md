# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE: 20-02-2026
## AIM:
To design and implement a java program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.

## Algorithm

1. Start
2. Read number of vertices (n) and edges (e)
3. Create an adjacency list for the graph
4. For each edge:
5. Read vertices u and v
6. Add edge between u and v
7. Read source vertex (src)
8. Create a visited array and initialize all values to false
9. Create a queue and insert src into it
10. Mark src as visited
11. While queue is not empty:
12. Remove a vertex from the queue
13. Print the vertex
14. For each adjacent vertex:
15. If not visited, mark visited and add to queue
16. Stop  

## Program:
``` JAVA
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: DILLI PRATHAP
RegisterNumber:  212224110014  
*/

import java.util.*;

public class EmergencyRouteBFS {
public static void addEdge(List<List<Integer>> g, int u, int v) {
g.get(u).add(v);
g.get(v).add(u);
}

public static void bfs(List<List<Integer>> g, int src, boolean[] visited) {
Queue<Integer> q = new LinkedList<>();
q.offer(src);
visited[src] = true;
while (!q.isEmpty()) {
int curr = q.poll();
System.out.print(curr + " ");
for (int neighbor : g.get(curr)) {
if (!visited[neighbor]) {
visited[neighbor] = true;
q.offer(neighbor);
}
}
}
}

public static void main(String[] args) {
Scanner sc = new Scanner(System.in);
int n = sc.nextInt(), e = sc.nextInt();
List<List<Integer>> g = new ArrayList<>();
for (int i = 0; i < n; i++) g.add(new ArrayList<>());
for (int i = 0; i < e; i++) addEdge(g, sc.nextInt(), sc.nextInt());
int src = sc.nextInt();
bfs(g, src, new boolean[n]);
}
}
```

## Output:

<img width="332" height="209" alt="516890600-a38cd297-cc39-4eb9-b35e-0d8396223e21" src="https://github.com/user-attachments/assets/cda422e2-c22d-4cf7-8797-03e5f78e256a" />


## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
