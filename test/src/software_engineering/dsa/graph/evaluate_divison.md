# 🧩 Que
- [Link](https://leetcode.com/problems/evaluate-division/)
You are given an array of variable pairs `equations` and an array of real numbers `values`, where `equations[i] = [Ai, Bi]` and `values[i]` represent the equation `Ai / Bi = values[i]`. Each `Ai` or `Bi` is a string that represents a single variable.

You are also given some `queries`, where `queries[j] = [Cj, Dj]` represents the `jth` query where you must find the answer for `Cj / Dj = ?`.
```ad-question
title: Test Case
**Input:** equations = [ ["a","b"],["b","c"] ], values = [2.0,3.0], queries = [ ["a","c"],["b","a"],["a","e"],["a","a"],["x","x"] ]
**Output:** [6.00000,0.50000,-1.00000,1.00000,-1.00000]
**Explanation:** 
Given: _a / b = 2.0_, _b / c = 3.0_
queries are: _a / c = ?_, _b / a = ?_, _a / e = ?_, _a / a = ?_, _x / x = ?_
return: [6.0, 0.5, -1.0, 1.0, -1.0 ]
```

---
# Abstract
```ad-abstract
The idea is to create a graph of these pairs and for each of the query traverse this graph to get the answer
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
class Solution:
    def calcEquation(self, equations: List[List[str]], values: List[float], queries: List[List[str]]) -> List[float]:
        graph = {}
        for (f,t),v in zip(equations,values):
            graph.setdefault(f,{})
            graph.setdefault(t,{})
            graph[f][t] = v
            graph[t][f] = 1/v
        
        def eval(f,t):
            if f not in graph or t not in graph:
                return -1.0
            visited = set()
            def solve(idx):
                if idx == t:
                    return 1
                for k,v in graph[idx].items():
                    if k not in visited:
                        visited.add(idx)
                        sol = solve(k)
                        if sol != -1.0:
                            return v*sol
                return -1.0
            visited.add(f)
            return solve(f)
        return [eval(f,t) for f,t in queries]
```
---
