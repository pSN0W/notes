# 🧩 Que
- [Link](https://www.interviewbit.com/problems/useful-extra-edges/)
Given a graph of A nodes. Also given the weighted edges in the form of array B. You are also given starting point C and destination point D. Also given are some extra edges in the form of vector E. You need to find the length of the shortest path from C to D if you can use maximum one road from the given roads in E.
```ad-question
title: Test Case
A = 3
B = [   [1, 2, 1]
        [2, 3, 2]
    ]
C = 1
D = 3
E = [   [1, 3, 2]
    ]
Ans = 2
```

---
# Abstract
```ad-abstract
You can use dijkstra to find path from source to all the nodes and similarly you can find distance from destination to all the nodes. Now you can use one path if needed to compute new distance after adding path A->B you can do dist(src,A) + dist(dest,B).
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
from heapq import heappush,heappop

class Solution:
    # @param A : integer
    # @param B : list of list of integers
    # @param C : integer
    # @param D : integer
    # @param E : list of list of integers
    # @return an integer
    def solve(self, A, B, C, D, E):
        graph = [[] for _ in range(A+1)]
        for f,t,w in B:
            graph[f].append([t,w])
            graph[t].append([f,w])
        def dijkstra(src):
            dist = [float('inf')]*(A+1)
            dist[src] = 0
            pq = []
            heappush(pq,[0,src])
            while pq:
                d,curr = heappop(pq)
                #print(curr,d)
                if dist[curr] < d:
                    continue
                for t,w in graph[curr]:
                    if d+w < dist[t]:
                        dist[t] = d+w
                        heappush(pq,[dist[t],t])
            return dist
                        
        dist_from_source = dijkstra(C)
        dist_from_dest = dijkstra(D)
        ans = dist_from_source[D]
        for f,t,d in E:
            ans = min([ans,dist_from_source[f]+d+dist_from_dest[t],dist_from_source[t]+d+dist_from_dest[f]])
        return ans if ans != float('inf') else -1           
```
---
