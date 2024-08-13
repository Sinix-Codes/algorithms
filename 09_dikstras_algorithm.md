#### 📅 Discovered Date: 1956
#### 📃 Detailed Description
Dijkstra's Algorithm is a famous algorithm used to solve the shortest path problem for a graph with non-negative edge weights. This algorithm finds the shortest path from a source vertex to all other vertices in the graph.

* 🔹 Algorithm Steps:
Initialize distances from the source to all vertices as infinite except the source itself, which is zero.
Create a priority queue to store vertices.
Dequeue the vertex with the smallest distance and explore its neighbors.
Update the distances of the neighboring vertices.
Repeat until all vertices are processed.
* 🔹 Complexity:
Time Complexity: O(V^2) or O((V + E) log V) with a priority queue.
Space Complexity: O(V).
#### 💻 Java Code Snippet
```
import java.util.*;

class Dijkstra {
    static final int V = 9;

    int minDistance(int dist[], boolean sptSet[]) {
        int min = Integer.MAX_VALUE, min_index = -1;
        for (int v = 0; v < V; v++)
            if (!sptSet[v] && dist[v] <= min) {
                min = dist[v];
                min_index = v;
            }
        return min_index;
    }

    void dijkstra(int graph[][], int src) {
        int dist[] = new int[V];
        boolean sptSet[] = new boolean[V];

        for (int i = 0; i < V; i++) {
            dist[i] = Integer.MAX_VALUE;
            sptSet[i] = false;
        }

        dist[src] = 0;

        for (int count = 0; count < V - 1; count++) {
            int u = minDistance(dist, sptSet);
            sptSet[u] = true;

            for (int v = 0; v < V; v++)
                if (!sptSet[v] && graph[u][v] != 0 && dist[u] != Integer.MAX_VALUE && dist[u] + graph[u][v] < dist[v])
                    dist[v] = dist[u] + graph[u][v];
        }

        printSolution(dist);
    }

    void printSolution(int dist[]) {
        System.out.println("Vertex Distance from Source");
        for (int i = 0; i < V; i++)
            System.out.println(i + " \t\t " + dist[i]);
    }

    public static void main(String[] args) {
        int graph[][] = new int[][]{{0, 4, 0, 0, 0, 0, 0, 8, 0}, {4, 0, 8, 0, 0, 0, 0, 11, 0}, {0, 8, 0, 7, 0, 4, 0, 0, 2},
                {0, 0, 7, 0, 9, 14, 0, 0, 0}, {0, 0, 0, 9, 0, 10, 0, 0, 0}, {0, 0, 4, 14, 10, 0, 2, 0, 0}, {0, 0, 0, 0, 0, 2, 0, 1, 6},
                {8, 11, 0, 0, 0, 0, 1, 0, 7}, {0, 0, 2, 0, 0, 0, 6, 7, 0}};
        Dijkstra t = new Dijkstra();
        t.dijkstra(graph, 0);
    }
}
