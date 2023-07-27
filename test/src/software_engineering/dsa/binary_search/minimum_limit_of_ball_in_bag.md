# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/)
You are given a list containing balls on one operation you can take divide a bag into two bags containing positive number of balls. Minimize the max balls 
```ad-question
title: Test Case
**Input:** nums = [2,4,8,2], maxOperations = 4
**Output:** 2
**Explanation:**
- Divide the bag with 8 balls into two bags of sizes 4 and 4. [2,4,**8**,2] -> [2,4,4,4,2].
- Divide the bag with 4 balls into two bags of sizes 2 and 2. [2,**4**,4,4,2] -> [2,2,2,4,4,2].
- Divide the bag with 4 balls into two bags of sizes 2 and 2. [2,2,2,**4**,4,2] -> [2,2,2,2,2,4,2].
- Divide the bag with 4 balls into two bags of sizes 2 and 2. [2,2,2,2,2,**4**,2] -> [2,2,2,2,2,2,2,2].
The bag with the most number of balls has 2 balls, so your penalty is 2, and you should return 2.
```

---
# Abstract
```ad-abstract
The idea is to search for answer using binary search. 
```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Your answer will range between 1 and max(nums) aplly binary search on it
- To check if a number is possible.
	- lets say you need to check number of operation required for breaking 8 to max 3
	- 8 -> 3,3,2 => num operation required = ceil(num/val) - 1

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
import math
class Solution:
    def minimumSize(self, nums: List[int], maxOperations: int) -> int:
        def check(val):
            curr = sum([math.ceil(num/val)-1 for num in nums])
            return curr <= maxOperations
        ans = 0
        lo,hi = 1,max(nums)
        while lo<=hi:
            m = (lo+hi)//2
            if check(m):
                ans = m
                hi = m-1
            else:
                lo = m+1
        return ans
```
---
