# 🧩 Que
- [Link](https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/)
Given a `matrix` and a `target`, return the number of non-empty submatrices that sum to target.
```ad-question
title: Test Case
**Input:** matrix = [ [0,1,0],[1,1,1],[0,1,0] ], target = 0
**Output:** 4
**Explanation:** The four 1x1 submatrices that only contain 0.
```

---
# Abstract
```ad-abstract
You should know how to solve num of sub array sum equal to target. The idea is to first have a prefix row sum of all the matrix and then you can do the same for top to bottom and get your answer
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230711150331.png]]

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def numSubmatrixSumTarget(self, matrix: List[List[int]], target: int) -> int:
        n,m = len(matrix),len(matrix[0])
        def num_eq(lst):
            dic = {0:1}
            ans = 0
            for num in lst:
                ans += dic.get(num-target,0)
                dic[num] = dic.get(num,0) + 1
            return ans

        def add(lst1,lst2):
            fin_lst = [0]*m
            for k in range(m):
                fin_lst[k] = lst1[k] + lst2[k]
            return fin_lst

        for i in range(n):
            for j in range(1,m):
                matrix[i][j] = matrix[i][j-1] + matrix[i][j]
        ans = 0
        for i in range(n):
            lst = matrix[i].copy()
            ans += num_eq(lst)
            for j in range(i-1,-1,-1):
                lst = add(lst,matrix[j])
                ans += num_eq(lst)
        return ans
```
---
