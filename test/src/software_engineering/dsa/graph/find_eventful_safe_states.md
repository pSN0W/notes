# 🧩 Que
- [Link](https://leetcode.com/problems/find-eventual-safe-states/)
You are given a graph of outgoing edges from each node. A node is said to be safe if it doesn't have any outgoing edge or it is part of a terminal node 
```ad-question
title: Test Case
![[Pasted image 20230709154342.png]]
```

---
# Abstract
```ad-abstract
A pure question of topological_sort. You first reverse the graph so that you can go from a terminal node to a non terminal and reduce number of edges for it. Collect all the safe node
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
    def eventualSafeNodes(self, graph: List[List[int]]) -> List[int]:
        n = len(graph)
        new_graph = [[] for _ in range(n)]
        num_out = [len(arr) for arr in graph]
        for i in range(n):
            for child in graph[i]:
                new_graph[child].append(i)
        q = Queue()
        print(num_out)
        for i,cnt in enumerate(num_out):
            if cnt==0:
                q.put(i)
        ans = []
        while not q.empty():
            f = q.get()
            ans.append(f)
            for node in new_graph[f]:
                num_out[node] -= 1
                if num_out[node] == 0:
                    q.put(node)
        return sorted(ans)
```
---
