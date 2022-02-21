# Bellman Ford

* Computes shortest paths from **a single source vertex** to all of the other vertices in a weighted directed graph.
* Slower than Dijkstra's algorithm. Its time complexity is `O(VE)`.
* Can handle graph with negative weight edges.
* Works better (than Dijkstra's) for distributed system. Unlike Dijkstra's where we need to find minimum value of all vertices, Bellman-Force considers edges one by one.

### **Limitation of the algorithm**

“Bellman-Ford algorithm” is only applicable to “graphs” with no “negative weight cycles”.

#### **How does the Bellman-Ford algorithm detect “negative weight cycles”?**

Although the “Bellman-Ford algorithm” cannot find the shortest path in a graph with “negative weight cycles”, it can detect whether there exists a “negative weight cycle” in the “graph”.

**Detection method**: After relaxing each edge `N-1` times, perform the `N`th relaxation. According to the “Bellman-Ford algorithm”, all distances must be the shortest after relaxing each edge `N-1` times. However, after the `N`th relaxation, if there exists `distances[u] + weight(u, v) < distances(v)` for any `edge(u, v)`, it means there is a shorter path . At this point, we can conclude that there exists a “negative weight cycle”.

## Implementation

Let `dist[u]` be the length of the shortest path from `src` to `u`.

Initially `dist[src] = 0` and `dist[u] = INF` for all other vertices.

Repeat `V - 1` times (since the path in the graph is at most of length `V - 1`):

* For each edge `E = (u, v, weight)`, try to use `E` to update the `dist[v]`: If `dist[u] + weight < dist[v]`, then `dist[v] = dist[u] + weight`.

```cpp
// Time: O(VE)
// Space: O(V)
vector<int> bellmanFord(vector<vector<int>>& edges, int V, int src) {
    vector<int> dist(N, INT_MAX);
    dist[src] = 0;
    for (int i = 1; i < V; ++i) { // try to use all the edges to relax for V-1 times.
        for (auto &e : edges) {
            int u = e[0], v = e[1], w = e[2];
            if (dist[u] == INT_MAX) continue;
            dist[v] = min(dist[v], dist[u] + w); // Try to use this edge to relax the cost of `v`.
        }
    }
    return dist;
}
```

## Problems

* [743. Network Delay Time](https://leetcode.com/problems/network-delay-time/)
* [787. Cheapest Flights Within K Stops (Medium)](https://leetcode.com/problems/cheapest-flights-within-k-stops)

## Reference

* [Bellman–Ford algorithm](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford\_algorithm)
