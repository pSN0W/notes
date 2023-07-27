# 🧩 Que
- [Link](https://www.interviewbit.com/problems/mother-vertex/)
Given a list of edges, find if the graph has a mother vertex. Mother vertex is one from where you can travel to all other vertices
```ad-question
title: Test Case
A = 3
B = [ [1, 3], [2, 3], [1, 3] ]
Output : 0
```

---
# Abstract
```ad-abstract
The idea is simple you can just start dfs from each of the non visited node. The node that you start your dfs at last has the probability of being the mother vertex so after you are done getting the last node to start dfs. Do a dfs traversal from that node to check if it is the mother vertex
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
import sys
sys.setrecursionlimit(1000000000)
from collections import defaultdict

def DFS(v,vis,d):
    vis[v] = True
    for i in d[v]:
        if not vis[i]:
            DFS(i,vis,d)
class Solution:
    # @param A : integer
    # @param B : list of list of integers
    # @return an integer
    def motherVertex(self, A, B):

        d = defaultdict(list)
        for i in B:
            d[i[0]-1].append(i[1]-1)
        v = 0
        vis = [False]*A
        for i in range(A):
            if not vis[i]:
                DFS(i,vis,d)
                v = i
        visited = [False]*A
        DFS(v,visited,d)
        if False not in visited:
            return 1

        return 0
```
---
