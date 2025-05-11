### Problem 1: Connected Components
**Problem Statement:** Given an undirected graph, find the number of connected components.

**Hints:**
- Use DFS to explore one component.
- Keep a visited set to track explored nodes.

**Brute Force Idea:** Try every node and count each new DFS call.  
**Optimized Idea:** Same as brute force; DFS or BFS is optimal here.

```python
def count_components(graph):
    visited = set()
    count = 0

    for node in graph:
        if node not in visited:
            dfs(graph, node, visited)
            count += 1
    return count
```
  
## Problem 2: Detect Cycle in Undirected Graph

**Problem Statement:** Check if an undirected graph has a cycle.

**Hints:**
- Use DFS with parent tracking.
- If a visited node is not the parent, there is a cycle.

**Brute Force Idea:** Check all paths for repetition.  
**Optimized Idea:** DFS with parent node tracking.

```python
def has_cycle(graph):
    visited = set()

    def dfs(node, parent):
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                if dfs(neighbor, node):
                    return True
            elif neighbor != parent:
                return True
        return False

    for node in graph:
        if node not in visited:
            if dfs(node, -1):
                return True
    return False
```

---

## Problem 3: BFS Shortest Path (Unweighted)

**Problem Statement:** Find the shortest path from source to target using BFS.

**Hints:**
- Use a queue.
- Track distances.

**Brute Force Idea:** DFS with backtracking all paths.  
**Optimized Idea:** BFS tracks shortest path efficiently in unweighted graphs.

```python
def bfs_shortest_path(graph, start, end):
    from collections import deque
    queue = deque([(start, [start])])
    visited = set()

    while queue:
        node, path = queue.popleft()
        if node == end:
            return path
        visited.add(node)
        for neighbor in graph[node]:
            if neighbor not in visited:
                queue.append((neighbor, path + [neighbor]))
    return []
```

---

## 🧭 Problem 4: DFS Shortest Path (Unweighted)

**Problem Statement:** Find one valid path from source to target using DFS.

**Hints:**
- Use recursion to explore paths.
- Return the path when the target is reached.

**Brute Force Idea:** Try all paths using DFS.  
**Optimized Idea:** Return early once the target is found.

```python
def dfs_path(graph, start, end, path=None, visited=None):
    if visited is None:
        visited = set()
    if path is None:
        path = []

    visited.add(start)
    path = path + [start]

    if start == end:
        return path

    for neighbor in graph[start]:
        if neighbor not in visited:
            result = dfs_path(graph, neighbor, end, path, visited)
            if result:
                return result
    return None
```
