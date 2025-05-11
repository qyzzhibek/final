# 📘 Topic: Graphs - Definitions and Traversals

## Overview

Graphs are mathematical structures used to model pairwise relationships between objects. They consist of **vertices** (or nodes) and **edges** (connections between the nodes). Graphs are used in various fields, including computer networks, social media, transportation systems, and many algorithmic problems.

There are different types of graphs:

- **Directed Graph (Digraph)**: Edges have a direction.
- **Undirected Graph**: Edges do not have a direction.
- **Weighted Graph**: Each edge has a weight or cost.
- **Unweighted Graph**: Edges have no associated weight.
- **Cyclic and Acyclic Graphs**: A graph with or without cycles.
- **Connected Graph**: There is a path between every pair of vertices.

## 🔸 Graph Representations

- **Adjacency Matrix**: A 2D array where `matrix[i][j] = 1` (or weight) if there is an edge from vertex `i` to `j`.
- **Adjacency List**: A list where each vertex points to a list of adjacent vertices.

Example (Undirected Graph):

0 --- 1
|   /
|  /
2make

Adjacency List:

0: [1, 2]
1: [0, 2]
2: [0, 1]


##  Graph Traversal Algorithms

**1. Breadth-First Search (BFS)**

- Explores neighbors first.
- Uses a queue.
- Good for shortest path in unweighted graphs.

**Time Complexity:** O(V + E)

```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])

    while queue:
        node = queue.popleft()
        if node not in visited:
            print(node)
            visited.add(node)
            queue.extend(graph[node])
```
**2. Depth-First Search (DFS)**

- Explores as far as possible along each branch before backtracking.
- Uses a stack (explicit or recursion).
- Useful for topological sorting, cycle detection.

**Time Complexity:** O(V + E)

```python
def dfs(graph, node, visited):
    if node not in visited:
        print(node)
        visited.add(node)
        for neighbor in graph[node]:
            dfs(graph, neighbor, visited)
```

## Applications of Traversals

- Finding connected components
- Detecting cycles
- Finding shortest paths
- Web crawling (BFS)
- Solving puzzles/mazes (DFS)

## Comparing DFS and BFS

| Feature        | DFS               | BFS                        |
| -------------- | ----------------- | -------------------------- |
| Data Structure | Stack / Recursion | Queue                      |
| Use Case       | Deep exploration  | Shortest path (unweighted) |
| Space Usage    | Can go deep       | Can be wide                |

## Key Takeaways

- Graphs model real-world relationships.
- BFS and DFS are fundamental traversal techniques.
- Choice of representation impacts efficiency.
- Traversal algorithms are the basis for solving many graph problems.
