#### 📅 Discovered Date: 1930
#### 📃 Detailed Description
Prim's Algorithm is a greedy algorithm that finds a minimum spanning tree for a weighted undirected graph. The algorithm operates by starting from a single vertex and growing the spanning tree by adding the smallest edge from the current tree to a vertex not yet in the tree.

* 🔹 Algorithm Steps:
- Initialize a set of visited vertices.
- Select the starting vertex and add it to the visited set.
- While there are still vertices not in the visited set, select the edge with the smallest weight that connects a vertex in the visited set to one not in the set.
- Add the edge and the vertex to the visited set.
- Repeat until all vertices are visited.

* 🔹 Complexity:
- Time Complexity: O(E log V) with a priority queue.
- Space Complexity: O(V).

#### 💻 Java Code Snippet
```
import java.util.*;

public class PrimAlgorithm {
    class Edge implements Comparable<Edge> {
        int dest, weight;
        Edge(int dest, int weight) {
            this.dest = dest;
            this.weight = weight;
        }
        public int compareTo(Edge compareEdge) {
            return this.weight - compareEdge.weight;
        }
    }

    private int V;
    private LinkedList<Edge> adj[];

    PrimAlgorithm(int v) {
        V = v;
        adj = new LinkedList[V];
        for (int i = 0; i < V; ++i)
            adj[i] = new LinkedList();
    }

    void addEdge(int src, int dest, int weight) {
        adj[src].add(new Edge(dest, weight));
        adj[dest].add(new Edge(src, weight));
    }

    void primMST() {
        boolean visited[] = new boolean[V];
        PriorityQueue<Edge> pq = new PriorityQueue<>();
        pq.add(new Edge(0, 0));

        int totalWeight = 0;

        while (!pq.isEmpty()) {
            Edge edge = pq.poll();
            int u = edge.dest;

            if (visited[u])
                continue;

            totalWeight += edge.weight;
            visited[u] = true;

            for (Edge e : adj[u]) {
                if (!visited[e.dest]) {
                    pq.add(e);
                }
            }
        }

        System.out.println("Total weight of MST: " + totalWeight);
    }

    public static void main(String[] args) {
        PrimAlgorithm graph = new PrimAlgorithm(4);

        graph.addEdge(0, 1, 10);
        graph.addEdge(0, 2, 6);
        graph.addEdge(0, 3, 5);
        graph.addEdge(1, 3, 15);
        graph.addEdge(2, 3, 4);

        graph.primMST();
    }
}
