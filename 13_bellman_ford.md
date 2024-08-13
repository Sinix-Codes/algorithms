#### 📅 Discovered Date: 1958
#### 📃 Detailed Description
The Bellman-Ford Algorithm is used to find the shortest path from a source vertex to all other vertices in a weighted graph. Unlike Dijkstra's algorithm, it can handle graphs with negative edge weights. However, it does not work with graphs containing negative weight cycles.

* 🔹 Algorithm Steps:
- Initialize the distance to the source vertex as 0 and all other vertices as infinite.
- Relax all edges |V| - 1 times, where |V| is the number of vertices. Update the distance to each vertex by checking if a shorter path exists.
- Check for negative weight cycles. If any edge can still be relaxed, a negative weight cycle exists.
* 🔹 Complexity:
- Time Complexity: O(V * E).
- Space Complexity: O(V).
#### 💻 Java Code Snippet
```
import java.util.*;

public class BellmanFord {
    class Edge {
        int src, dest, weight;
        Edge(int src, int dest, int weight) {
            this.src = src;
            this.dest = dest;
            this.weight = weight;
        }
    }

    int V, E;
    Edge edge[];

    BellmanFord(int v, int e) {
        V = v;
        E = e;
        edge = new Edge[E];
        for (int i = 0; i < e; ++i)
            edge[i] = new Edge(0, 0, 0);
    }

    void addEdge(int i, int src, int dest, int weight) {
        edge[i].src = src;
        edge[i].dest = dest;
        edge[i].weight = weight;
    }

    void bellmanFord(int src) {
        int dist[] = new int[V];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[src] = 0;

        for (int i = 1; i < V; ++i) {
            for (int j = 0; j < E; ++j) {
                int u = edge[j].src;
                int v = edge[j].dest;
                int weight = edge[j].weight;
                if (dist[u] != Integer.MAX_VALUE && dist[u] + weight < dist[v])
                    dist[v] = dist[u] + weight;
            }
        }

        for (int j = 0; j < E; ++j) {
            int u = edge[j].src;
            int v = edge[j].dest;
            int weight = edge[j].weight;
            if (dist[u] != Integer.MAX_VALUE && dist[u] + weight < dist[v])
                System.out.println("Graph contains negative weight cycle");
        }

        printArr(dist);
    }

    void printArr(int dist[]) {
        System.out.println("Vertex Distance from Source");
        for (int i = 0; i < V; ++i)
            System.out.println(i + "\t\t" + dist[i]);
    }

    public static void main(String[] args) {
        int V = 5;
        int E = 8;

        BellmanFord graph = new BellmanFord(V, E);

        graph.addEdge(0, 0, 1, -1);
        graph.addEdge(1, 0, 2, 4);
        graph.addEdge(2, 1, 2, 3);
        graph.addEdge(3, 1, 3, 2);
        graph.addEdge(4, 1, 4, 2);
        graph.addEdge(5, 3, 2, 5);
        graph.addEdge(6, 3, 1, 1);
        graph.addEdge(7, 4, 3, -3);

        graph.bellmanFord(0);
    }
}
