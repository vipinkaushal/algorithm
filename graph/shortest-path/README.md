# Shortest Path

In this chapter, we will learn two “single source shortest path” algorithms:

1. Dijkstra’s algorithm
2. Bellman-Ford algorithm

“Dijkstra's algorithm” can only be used to solve the “single source shortest path” problem in a graph with non-negative weights.

“Bellman-Ford algorithm”, on the other hand, can solve the “single-source shortest path” in a weighted directed graph with any weights, including, of course, negative weights.

| Algorithm      | Time Complexity | Usecase              |
| -------------- | --------------- | -------------------- |
| Bellman-Ford   | O(VE)           | Single Source to All |
| Dijkstra       | O(VlogV)        | Single Source to All |
| Floyd-Warshall | O(V^3)          | All to All           |
