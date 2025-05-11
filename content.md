# Graphs - Definitions and Traversals

## Overview

Graphs are powerful mathematical structures used to represent relationships between entities, where entities are modeled as **vertices (nodes)** and the relationships between them are represented as **edges (connections)**. Graphs are widely used in computer science, specifically in fields such as networking, artificial intelligence, social media, and web crawling, to solve problems that involve relationships and interactions.

A graph can be represented in different ways based on the nature of the relationship:

- **Directed Graph (Digraph)**: In a directed graph, each edge has a direction, represented by an arrow pointing from one vertex to another. Example: Twitter's follower graph.
- **Undirected Graph**: In an undirected graph, edges do not have a direction, meaning the relationship is bidirectional. Example: Facebook's friend network.
- **Weighted Graph**: A weighted graph assigns a weight or cost to each edge, representing the strength or cost of the relationship. Example: Road maps where the edges represent the distance between two locations.
- **Unweighted Graph**: In an unweighted graph, all edges are considered equal, and there is no weight associated with them. Example: A social network where friendships have equal importance.
- **Cyclic Graph**: A graph that contains at least one cycle (a path where the first and last vertices are the same). Example: A road map with one-way streets.
- **Acyclic Graph**: A graph with no cycles. Example: A hierarchical organization chart where there are no loops.
- **Connected Graph**: A graph is connected if there is a path between every pair of vertices, meaning you can reach any vertex from any other. Example: An undirected social network where everyone is connected directly or indirectly.

## Graph Representations

### 1. **Adjacency Matrix**:
An **Adjacency Matrix** is a 2D array (or matrix) where each cell `matrix[i][j]` represents whether an edge exists between vertex `i` and vertex `j`. If there is an edge, the cell contains a non-zero value (usually 1 for unweighted graphs or the edge's weight for weighted graphs). This representation is memory-intensive for sparse graphs but efficient for dense graphs.

Example (Undirected Graph):

```python
0 --- 1
|   /
| /
2
```

Adjacency Matrix (Undirected Graph):

```python
0 1 2
0 [0, 1, 1]
1 [1, 0, 1]
2 [1, 1, 0]
```

### 2. **Adjacency List**:
An **Adjacency List** is a more memory-efficient representation where each vertex stores a list of adjacent vertices (neighbors). This representation is especially useful for sparse graphs.

Example (Undirected Graph):

```python
0 --- 1
|   /
| /
2
```
Adjacency List (Undirected Graph):

```python
0: [1, 2]
1: [0, 2]
2: [0, 1]
```

## Graph Traversal Algorithms

### 1. **Breadth-First Search (BFS)**

**BFS** explores all the neighbors of a vertex before moving to the next level of neighbors. It is useful for finding the **shortest path** in an unweighted graph because it explores all vertices at the present depth level before moving on to vertices at the next depth level.

- **Data Structure Used**: Queue
- **Time Complexity**: O(V + E), where `V` is the number of vertices and `E` is the number of edges.
  
**Algorithm:**
- Initialize a queue and start from a source vertex.
- Visit all unvisited neighbors, enqueue them, and mark them as visited.
- Continue until all reachable vertices are visited.

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
### 2. Depth-First Search (DFS)

DFS explores as far as possible along a branch before backtracking. It uses recursion or a stack for its implementation. DFS is useful in problems such as topological sorting, cycle detection, and solving puzzles/mazes.

- **Data Structure Used:** Stack or Recursion  
- **Time Complexity:** O(V + E), where V is the number of vertices and E is the number of edges.

####  Algorithm Steps
1. Start from a source vertex and explore as deep as possible along each branch.
2. If you hit a dead-end, backtrack and continue exploring.

```python
def dfs(graph, node, visited):
    if node not in visited:
        print(node)
        visited.add(node)
        for neighbor in graph[node]:
            dfs(graph, neighbor, visited)

```
###  Applications of Traversals

- **Finding connected components**: Using BFS or DFS to identify isolated subgraphs.
- **Cycle detection**: Identifying cycles in directed and undirected graphs.
- **Shortest path**: BFS is particularly useful for finding the shortest path in unweighted graphs.
- **Web crawling**: BFS is used by search engines to traverse web pages, ensuring all links are explored.
- **Solving puzzles and mazes**: DFS can be used to explore possible solutions in puzzle-solving algorithms.


---

### Comparing DFS and BFS

| Feature          | DFS                  | BFS                          |
|------------------|----------------------|------------------------------|
| **Data Structure** | Stack / Recursion     | Queue                        |
| **Use Case**       | Deep exploration       | Shortest path (unweighted)   |
| **Space Usage**    | Can go deep            | Can be wide                  |
| **Traversal Order**| Goes deep first        | Explores level by level      |

---


### Key Takeaways

- Graphs represent relationships between entities and are fundamental structures in computer science.
- BFS is optimal for unweighted shortest path problems, exploring level by level.
- DFS is useful for deep exploration, topological sorting, and cycle detection.
- The choice of graph representation and traversal algorithm significantly impacts the performance of algorithms.

