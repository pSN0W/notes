# 🧩 Que
- [Link](https://leetcode.com/problems/number-of-operations-to-make-network-connected/)
You are given a network. In one operation you can take an existing wire and connect two other computers. Find the minimum operation to create a connected network
```ad-question
title: Test Case
![[Pasted image 20230709174807.png]]
```

---
# Abstract
```ad-abstract
The idea is to create a MST and get the number of spare wires. You also count the total number of such grouped network. Now see if you have enough wire to connect there clusters. Using UF to do this can simplify implementation
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
    def makeConnected(self, n: int, connections: List[List[int]]) -> int:
        UF = list(range(n))
        def find(x):
            if UF[x] != x:
                UF[x] = find(UF[x])
            return UF[x]
        def uni(x,y):
            if find(x) == find(y):
                return 1
            UF[find(x)] = find(y)
            return 0
        num_left = sum([uni(x,y) for x,y in connections])
        num_par = sum([int(x==find(x)) for x in range(n)])
        return num_par-1 if num_par-1<=num_left else -1
```
---
