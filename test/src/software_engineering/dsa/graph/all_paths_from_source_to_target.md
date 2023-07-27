# 🧩 Que
- [Link](https://leetcode.com/problems/all-paths-from-source-to-target/)
Given a graph find all the possible paths from 0 to n-1
```ad-question
title: Test Case
![[Pasted image 20230707143722.png]]
**Input:** graph = [ [4,3,1],[3,2,4],[3],[4],[] ]
**Output:** [ [0,4],[0,3,4],[0,1,3,4],[0,1,2,3,4],[0,1,4] ]
```

---
# Abstract
```ad-abstract
The idea is to first keep track of all the parents of each of the node and then use it to create the path
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- To create a parent array. Use a visited and visit each node only once. Once you look at child of node to call bfs add that node as parent of that child

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def allPathsSourceTarget(self, graph: List[List[int]]) -> List[List[int]]:
        n = len(graph)
        parent = [[] for _ in range(n)]
        visited = [False]*n
        def dfs(node):
            visited[node] = True
            for nbr in graph[node]:
                parent[nbr].append(node)
                if not visited[nbr]:
                    dfs(nbr)
        def create_path(node):
            if node == 0:
                return [[0]]
            paths = []
            for par in parent[node]:
                path_till_0 = create_path(par)
                for pth in path_till_0:
                    pth.append(node)
                    paths.append(pth)
            return paths
        dfs(0)
        return create_path(n-1)
```
---
