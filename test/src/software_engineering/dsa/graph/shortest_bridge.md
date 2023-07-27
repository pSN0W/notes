# 🧩 Que
- [Link](https://leetcode.com/problems/shortest-bridge/)
Given two island return the shortest length bridge to connect the two
```ad-question
title: Test Case
**Input:** grid = [ [0,1],[1,0] ]
**Output:** 1
```

---
# Abstract
```ad-abstract
One you find any of the is element 1 you perform a dfs to mark that island as 2. From all the index part of that island you start a multi source bfs to get the nearest distance to next 1
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
from queue import Queue
class Solution:
    def shortestBridge(self, grid: List[List[int]]) -> int:
        n,m = len(grid),len(grid[0])
        q = Queue()
        directions = [[0,1],[0,-1],[1,0],[-1,0]]
        def in_bound(x,y):
            return x>=0 and y>=0 and x<n and y<m
        def dfs(x,y):
            q.put((x,y))
            grid[x][y] = 2
            for dx,dy in directions:
                new_x,new_y = x+dx,y+dy
                if in_bound(new_x,new_y) and grid[new_x][new_y]==1:
                    dfs(new_x,new_y)
        def bfs():
            q.put((None,None))
            d = 0
            while not q.empty():
                x,y = q.get()
                if x is None:
                    d += 1
                    if not q.empty():
                        q.put((None,None))
                    continue
                for dx,dy in directions:
                    nbr_x,nbr_y = x+dx,y+dy
                    if in_bound(nbr_x,nbr_y):
                        if grid[nbr_x][nbr_y] == 1:
                            return d
                        elif grid[nbr_x][nbr_y] == 0:
                            grid[nbr_x][nbr_y] = 2
                            q.put((nbr_x,nbr_y))
            return -1
        
        for i in range(n):
            for j in range(m):
                if grid[i][j] == 1:
                    dfs(i,j)
                    return bfs()
        return -1
```
---
