# Breadth-First Search (BFS) in C++

## Introduction
**Breadth-First Search (BFS)** is a graph traversal algorithm that explores all the vertices of a graph layer by layer. It uses a **queue (FIFO)** to traverse the graph, ensuring that all neighbors of a node are visited before moving to the next level.

## Properties of BFS
- Works for both **graph** and **tree** traversal.
- Finds the **shortest path** in an unweighted graph.
- Uses **queue (FIFO)** for traversal.
- **Time Complexity:** O(V + E) (where V = vertices, E = edges)
- **Space Complexity:** O(V) (for storing visited nodes and queue)

## BFS Algorithm
1. Start from a source node.
2. Mark the node as visited.
3. Add the node to a queue.
4. While the queue is not empty:
   - Remove the front node from the queue.
   - Process the node.
   - Add all unvisited adjacent nodes to the queue and mark them as visited.

## BFS Implementation in C++
### BFS on an Undirected Graph (Adjacency List Representation)
```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void bfs(int start, vector<int> adj[], int V) {
    vector<bool> visited(V, false);
    queue<int> q;
    
    visited[start] = true;
    q.push(start);
    
    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";
        
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

int main() {
    int V = 5;
    vector<int> adj[V];
    adj[0] = {1, 2};
    adj[1] = {0, 3, 4};
    adj[2] = {0, 4};
    adj[3] = {1};
    adj[4] = {1, 2};
    
    cout << "BFS starting from node 0: ";
    bfs(0, adj, V);
    return 0;
}
```

## BFS Applications
- **Shortest Path in an Unweighted Graph**
- **Connected Components in a Graph**
- **Cycle Detection in an Undirected Graph**
- **Web Crawlers** (exploring links in layers)
- **GPS Navigation Systems** (finding shortest routes)
- **Network Broadcasting**

## BFS vs DFS
| Feature | BFS | DFS |
|---------|----|----|
| Data Structure | Queue (FIFO) | Stack (Recursion/LIFO) |
| Traversal Order | Level-wise | Depth-wise |
| Space Complexity | O(V) | O(V) (recursive stack) |
| Finds Shortest Path? | Yes (for unweighted graphs) | No |
| Suitable for? | Shortest paths, connectivity | Topological sorting, cycles |

## Additional Resources
- [BFS Algorithm (GeeksforGeeks)](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)
- [BFS Explanation (YouTube)](https://www.youtube.com/watch?v=ZBHKZF5w4YU)

---
📌 *This file serves as a quick revision guide for BFS in C++. Feel free to contribute or suggest improvements!* 🚀
