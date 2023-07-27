# 🧩 Que
- [Link](https://www.interviewbit.com/problems/evaluate-expression-to-true/)
Given an expression, A, with operands and operators (OR , AND , XOR), in how many ways can you evaluate the expression to true, by grouping in different ways?
Operands are only true and false.
Return the number of ways to evaluate the expression modulo 103 + 3.
```ad-question
title: Test Case
Input 1:
    A = "T|F"
Output 1:
    1
```

---
# Abstract
```ad-abstract
Create a function solve where solve(i,j,"True or False") find out the number of ways you can evealuate an expression to true or false. Now for each of the expression you can find the number of ways to get all possible solution for example if you want true numer of ways can be True^False and False^True.
Use MCM to break it for all the the possible operators between i and j
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
from functools import lru_cache

class Solution:
	# @param A : string
	# @return an integer
	def cnttrue(self, A):
        @lru_cache(None)
        def solve(i,j,sign):
            if i==j:
                return 1 if A[i] == sign else 0
            ans = 0
            for k in range(i+1,j,2):
                if sign == "T":
                    if A[k] == "|":
                        ans += solve(i,k-1,"T")*solve(k+1,j,"T")
                        ans += solve(i,k-1,"F")*solve(k+1,j,"T")
                        ans += solve(i,k-1,"T")*solve(k+1,j,"F")
                    elif A[k] == "&":
                        ans += solve(i,k-1,"T")*solve(k+1,j,"T")
                    else:
                        ans += solve(i,k-1,"F")*solve(k+1,j,"T")
                        ans += solve(i,k-1,"T")*solve(k+1,j,"F")
                else:
                    if A[k] == "&":
                        ans += solve(i,k-1,"F")*solve(k+1,j,"F")
                        ans += solve(i,k-1,"F")*solve(k+1,j,"T")
                        ans += solve(i,k-1,"T")*solve(k+1,j,"F")
                    elif A[k] == "|":
                        ans += solve(i,k-1,"F")*solve(k+1,j,"F")
                    else:
                        ans += solve(i,k-1,"F")*solve(k+1,j,"F")
                        ans += solve(i,k-1,"T")*solve(k+1,j,"T")
                ans %=int(1e3+3)
            return ans
        return solve(0,len(A)-1,"T")
```
---
