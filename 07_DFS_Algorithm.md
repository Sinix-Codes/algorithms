#### 📅 Discovered Date: 1959
#### 📃 Detailed Description
Depth First Search (DFS) is an algorithm for traversing or searching tree or graph data structures. The algorithm starts at the root (selecting some arbitrary node as the root in the case of a graph) and explores as far as possible along each branch before backtracking.

* 🔹 Algorithm Steps:
Start at the root node.
Explore each branch as far as possible before backtracking.
Repeat the process until all nodes are visited.
* 🔹 Complexity:
Time Complexity: O(V + E) where V is the number of vertices and E is the number of edges.
Space Complexity: O(V).

#### 💻 Java Code Snippet
```
import java.util.*;

public class DFS {
    private LinkedList<Integer> adjLists[];
    private boolean visited[];

    DFS(int vertices) {
        adjLists = new LinkedList[vertices];
        visited = new boolean[vertices];
        for (int i = 0; i < vertices; i++)
            adjLists[i] = new LinkedList<Integer>();
    }

    void addEdge(int src, int dest) {
        adjLists[src].add(dest);
    }

    void dfs(int vertex) {
        visited[vertex] = true;
        System.out.print(vertex + " ");
        Iterator<Integer> ite = adjLists[vertex].listIterator();
        while (ite.hasNext()) {
            int adj = ite.next();
            if (!visited[adj])
                dfs(adj);
        }
    }

    public static void main(String args[]) {
        DFS graph = new DFS(4);
        graph.addEdge(0, 1);
        graph.addEdge(0, 2);
        graph.addEdge(1, 2);
        graph.addEdge(2, 3);
        graph.addEdge(3, 3);

        System.out.println("Following is Depth First Traversal");
        graph.dfs(2);
    }
}
