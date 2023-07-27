# 🧩 Que
- [Link](https://leetcode.com/problems/satisfiability-of-equality-equations/)
Given a list of equality conditions return true if they satisfy else false
```ad-question
title: Test Case
**Input:** equations = ["a==b","b!=a"]
**Output:** false
**Explanation:** If we assign say, a = 1 and b = 1, then the first equation is satisfied, but not the second.
There is no way to assign the variables to satisfy both equations.
```

---
# Abstract
```ad-abstract
You want to grop all the numbers that are equal in one bucket and then for all non equality you must ensure that they aren't part of the same bucket. The data structure that comes to mind is DSU
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Whatever abstract says but you should consider cases like `a!=a`
- The find function returns None if while inequality you try to find something that wasn't seen in equality
- Both of the above can be avoided if you setdefault for unequality too.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def equationsPossible(self, equations: List[str]) -> bool:
        parent = {}
        def find(x):
            if x not in parent:
                return None
            if parent[x] != x:
                parent[x] = find(parent[x])
            return parent[x]
        def uni(x,y):
            parent.setdefault(x,x)
            parent.setdefault(y,y)
            parent[find(y)] = find(x)
        
        for s in equations:
            if s[1:-1] == "==":
                uni(s[0],s[-1])

        for s in equations:
            if s[1:-1] == "!=" and (s[0]==s[-1] or (find(s[0])==find(s[-1])!=None)):
                return False
        return True
```
---
