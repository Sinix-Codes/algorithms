#### 📅 Discovered Date: 1945
#### 📃 Detailed Description
Breadth First Search (BFS) is an algorithm for traversing or searching tree or graph data structures. It starts at the root node and explores all the neighbor nodes at the present depth level before moving on to nodes at the next depth level.

* 🔹 Algorithm Steps:
Start at the root node.
Explore all neighbor nodes at the present depth level.
Move on to the nodes at the next depth level.
Repeat the process until all nodes are visited.
* 🔹 Complexity:
Time Complexity: O(V + E) where V is the number of vertices and E is the number of edges.
Space Complexity: O(V).
#### 💻 Java Code Snippet
```
import java.util.LinkedList;
import java.util.Queue;

public class BFS {
    private LinkedList<Integer> adjLists[];
    private boolean visited[];

    BFS(int vertices) {
        adjLists = new LinkedList[vertices];
        visited = new boolean[vertices];
        for (int i = 0; i < vertices; i++)
            adjLists[i] = new LinkedList<Integer>();
    }

    void addEdge(int src, int dest) {
        adjLists[src].add(dest);
    }

    void bfs(int startVertex) {
        Queue<Integer> queue = new LinkedList<>();
        visited[startVertex] = true;
        queue.add(startVertex);

        while (!queue.isEmpty()) {
            int vertex = queue.poll();
            System.out.print(vertex + " ");

            for (int adj : adjLists[vertex]) {
                if (!visited[adj]) {
                    visited[adj] = true;
                    queue.add(adj);
                }
            }
        }
    }

    public static void main(String args[]) {
        BFS graph = new BFS(4);
        graph.addEdge(0, 1);
        graph.addEdge(0, 2);
        graph.addEdge(1, 2);
        graph.addEdge(2, 0);
        graph.addEdge(2, 3);
        graph.addEdge(3, 3);

        System.out.println("Following is Breadth First Traversal");
        graph.bfs(2);
    }
}
