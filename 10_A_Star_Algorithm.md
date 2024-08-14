#### 📅 Discovered Date: 1968
#### 📃 Detailed Description
The A* algorithm is a popular pathfinding and graph traversal algorithm. It is widely used due to its performance and accuracy. A* uses a heuristic to determine the best path from a start node to a goal node by considering both the distance from the start and the estimated distance to the goal.

* 🔹 Algorithm Steps:
- Initialize an open list and a closed list.
- Add the starting node to the open list.
- Repeat until the goal is found:
- Remove the node with the lowest cost from the open list.
- Add it to the closed list.
- Generate its neighbors.
- If a neighbor is the goal, stop the search.
- Else, calculate the total cost for the neighbor and add it to the open list.
- Return the path found.
* 🔹 Complexity:
Time Complexity: O(E) where E is the number of edges.
Space Complexity: O(V).

#### 💻 Java Code Snippet
```
import java.util.*;

class Node implements Comparable<Node> {
    public final String value;
    public double g = Double.POSITIVE_INFINITY;
    public final double h;
    public double f = Double.POSITIVE_INFINITY;
    public Node parent = null;
    public final Map<Node, Double> neighbors = new HashMap<>();

    public Node(String value, double h) {
        this.value = value;
        this.h = h;
    }

    @Override
    public int compareTo(Node other) {
        return Double.compare(this.f, other.f);
    }

    public void addBranch(Node node, double cost) {
        neighbors.put(node, cost);
    }
}

public class AStar {
    public static void aStar(Node start, Node goal) {
        PriorityQueue<Node> openList = new PriorityQueue<>();
        HashSet<Node> closedList = new HashSet<>();

        start.g = 0;
        start.f = start.h;
        openList.add(start);

        while (!openList.isEmpty()) {
            Node current = openList.poll();
            if (current == goal) {
                printPath(current);
                return;
            }

            closedList.add(current);

            for (Map.Entry<Node, Double> neighborEntry : current.neighbors.entrySet()) {
                Node neighbor = neighborEntry.getKey();
                double tentative_g = current.g + neighborEntry.getValue();

                if (tentative_g < neighbor.g && !closedList.contains(neighbor)) {
                    neighbor.parent = current;
                    neighbor.g = tentative_g;
                    neighbor.f = neighbor.g + neighbor.h;

                    if (!openList.contains(neighbor)) {
                        openList.add(neighbor);
                    }
                }
            }
        }
    }

    private static void printPath(Node node) {
        if (node.parent != null) {
            printPath(node.parent);
        }
        System.out.print(node.value + " ");
    }

    public static void main(String[] args) {
        Node start = new Node("Start", 10);
        Node goal = new Node("Goal", 0);

        Node nodeA = new Node("A", 7);
        Node nodeB = new Node("B", 8);
        Node nodeC = new Node("C", 6);
        Node nodeD = new Node("D", 5);

        start.addBranch(nodeA, 1);
        start.addBranch(nodeB, 4);
        nodeA.addBranch(nodeC, 2);
        nodeB.addBranch(nodeD, 5);
        nodeC.addBranch(goal, 6);
        nodeD.addBranch(goal, 1);

        aStar(start, goal);
    }
}
