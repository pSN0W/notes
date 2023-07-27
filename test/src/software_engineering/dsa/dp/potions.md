# 🧩 Que
- [Link](https://www.interviewbit.com/problems/potions/)
You are given N potions arranged in a row in the form of an array A. At each step, you are going to take two potions that stand next to each other and mix them together, When mixing two mixtures of colors X and Y, the resulting mixture will have the color (X + Y) mod 100.Also, there will be some smoke in the process. The amount of smoke generated when mixing two mixtures of colors X and Y is X * Y. Find out what is the minimum amount of smoke that you can get when mixing all the potions together.
```ad-question
title: Test Case
A = [2, 3, 4, 5]
Ans = 71
```

---
# Abstract
```ad-abstract
Assume that you have mixed all the potions and you are left with only two. If you are index i then to your left you will be left with sum(0,i) and to your right sum(i+1,ed). You can choose any index. So you can frame this question as mcm and then use prefix sum to get the value after solving st,i or i to ed.
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
    # @param A : list of integers
    # @return an integer
    def minSmoke(self, A):
        n = len(A)
        prefix_sum = [0]*(n+1)
        for i,val in enumerate(A):
            prefix_sum[i+1] = (prefix_sum[i] + val)

        def get_sum(i,j):
            return (prefix_sum[j+1] - prefix_sum[i])%100
        
        @lru_cache(None)
        def solve(st,ed):
            if st == ed:
                return 0
            smoke = float('inf')
            for i in range(st,ed):
                curr_sum = get_sum(st,i)*get_sum(i+1,ed)
                curr_sum += solve(st,i) + solve(i+1,ed)
                smoke = min([smoke,curr_sum])
            return smoke
        
        return solve(0,n-1)
```
---
