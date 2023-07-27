# 🧩 Que
- [Link](https://leetcode.com/problems/accounts-merge/)
Given user name and list of email associated with it. If for two user any of the email are common then merge the two user
```ad-question
title: Test Case
**Input:** accounts = [ ["John","johnsmith@mail.com","john_newyork@mail.com"],["John","johnsmith@mail.com","john00@mail.com"],["Mary","mary@mail.com"],["John","johnnybravo@mail.com"] ]
**Output:** [ ["John","john00@mail.com","john_newyork@mail.com","johnsmith@mail.com"],["Mary","mary@mail.com"],["John","johnnybravo@mail.com"] ]
**Explanation:**
The first and second John's are the same person as they have the common email "johnsmith@mail.com".
The third John and Mary are different people as none of their email addresses are used by other accounts.
We could return these lists in any order, for example the answer [['Mary', 'mary@mail.com'], ['John', 'johnnybravo@mail.com'], 
['John', 'john00@mail.com', 'john_newyork@mail.com', 'johnsmith@mail.com']] would still be accepted.
```

---
# Abstract
```ad-abstract
The idea is to take one of the email as pivot and merge all the emails using DSU. Look at the code its really well written
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
class DSU:
    def __init__(self):
        self.parent = {}
    def add(self,x):
        if x not in self.parent:
            self.parent[x] = x
    def find(self,x):
        if self.parent[x] == x:
            return x
        self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
    def union(self,x,y):
        self.add(x)
        self.add(y)
        par_x,par_y = self.find(x),self.find(y)
        self.parent[par_y] = par_x
    def merge(self,lst):
        fst = lst[0]
        self.add(fst)
        for x in lst[1:]:
            self.union(fst,x)
    def gen_dir(self):
        dr = {}
        for k in self.parent:
            par = self.find(k)
            dr.setdefault(par,[])
            dr[par].append(k)
        return dr

class Solution:
    def accountsMerge(self, accounts: List[List[str]]) -> List[List[str]]:
        dsu = DSU()
        ans = {}
        for act in accounts:
            ans[act[1]] = act[0]
            dsu.merge(act[1:])
        dr = dsu.gen_dir()
        sol = []
        for k in dr:
            curr = [ans[k]]
            curr += sorted(dr[k])
            sol.append(curr)
        return sorted(sol)   
```
---
