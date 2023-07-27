# 🧩 Que
- [Link](https://leetcode.com/problems/cheapest-flights-within-k-stops/)
There are `n` cities connected by some number of flights. You are given an array `flights` where `flights[i] = [fromi, toi, pricei]` indicates that there is a flight from city `fromi` to city `toi` with cost `pricei`.

You are also given three integers `src`, `dst`, and `k`, return _**the cheapest price** from_ `src` _to_ `dst` _with at most_ `k` _stops._ If there is no such route, return `-1`.
```ad-question
title: Test Case
**Input:** n = 4, flights = [[0,1,100],[1,2,100],[2,0,100],[1,3,600],[2,3,200]], src = 0, dst = 3, k = 1
**Output:** 700
**Explanation:**
The graph is shown above.
The optimal path with at most 1 stop from city 0 to 3 is marked in red and has cost 100 + 600 = 700.
Note that the path through cities [0,1,2,3] is cheaper but is invalid because it uses 2 stops.
```

---
# Abstract
```ad-abstract
The idea is to use dijkstra with the number of stops as the first parameter. This is because you can reach to an intermediate point with less distance in more number of stops but that will reduce your chance to reach target
```

- Tags #solved #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- k = 1 ![[Pasted image 20230710141655.png]]
- In the above pic if you consider distance for dijkstra then you can reach 1 with a min distance of 4 but you have already exhausted the one stop you could make.
- Use simple dijkstra just at you push (k,dist,node) in your queue.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
from heapq import heappush,heappop
class Solution:
    def findCheapestPrice(self, n: int, flights: List[List[int]], src: int, dst: int, k: int) -> int:
        graph = {i:[] for i in range(n)}
        for s,d,t in flights:
            graph[s].append((d,t))
        dist = [float('inf')]*n
        dist[src] = 0
        pq = []
        heappush(pq,(0,dist[src],src))
        while pq:
            curr_k,d,node = heappop(pq)
            if curr_k > k:
                continue
            for nbr,wt in graph[node]:
                if dist[nbr] > d+wt:
                    dist[nbr] = d+wt
                    heappush(pq,(curr_k+1,dist[nbr],nbr))
        return dist[dst] if dist[dst] != float('inf') else -1
```
---
