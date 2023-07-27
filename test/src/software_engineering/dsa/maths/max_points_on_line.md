# 🧩 Que
- [Link](https://leetcode.com/problems/max-points-on-a-line/)
Given a list of points. Find maximum number of points on a line
```ad-question
title: Test Case
**Input:** points = [[1,1],[2,2],[3,3]]
**Output:** 3
```

---
# Abstract
```ad-abstract
A line is described by (m,c). Use two loops to generate all pairs of m and c and then put all the points with the same slope and intercept
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- You can solve this question with O(1) space and O(n^3) complexity too. Use the first two loop to get m and c and then use the third to find all points that satisfy the m and c

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def maxPoints(self, points: List[List[int]]) -> int:
        if len(points) < 2:
            return 1
        dic = {}
        for x1,y1 in points:
            for x2,y2 in points:
                if (x1,y1) == (x2,y2):
                    continue
                m = (y2-y1)/(x2-x1) if x2!=x1 else 1e6
                c = y1 - m*x1 if x2!=x1 else x1
                dic.setdefault((m,c),set())
                dic[(m,c)].add((x1,y1))
                dic[(m,c)].add((x2,y2))
        return max([len(v) for v in dic.values()])
        
```
---
