# 🧩 Que
- [Link](https://leetcode.com/problems/restore-the-array-from-adjacent-pairs/)
You are given a pairs of integer that follows each other. You have to create the complete array with it
```ad-question
title: Test Case
**Input:** adjacentPairs = [ [2,1],[3,4],[3,2] ]
**Output:** [1,2,3,4]
**Explanation:** This array has all its adjacent pairs in adjacentPairs.
Notice that adjacentPairs[i] may not be in left-to-right order.
```

---
# Abstract
```ad-abstract
The idea is to create a graph where the neighbors represent the adjacent numbers. You start with a node that has only one neighbor as that will be start or end of the array. You take advantage of a number can have only 2 adjacent number so one will take you to that number and other to the next
```

- Tags #revise #standard_que 
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
    def restoreArray(self, adjacentPairs: List[List[int]]) -> List[int]:
        graph = {}
        for x,y in adjacentPairs:
            graph.setdefault(x,[])
            graph.setdefault(y,[])
            graph[x].append(y)
            graph[y].append(x)
        ans = []
        for x,nbrs in graph.items():
            if len(nbrs) == 1:
                st = x
                break
        visited = set()
        while True:
            ans.append(st)
            visited.add(st)
            poss = [nbr for nbr in graph[st] if nbr not in visited]
            if poss:
                st = poss[0]
            else:
                break
        return ans
```
---
