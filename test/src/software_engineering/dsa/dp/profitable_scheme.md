# 🧩 Que
- [Link](https://leetcode.com/problems/profitable-schemes/)
There is a group of `n` members, and a list of various crimes they could commit. The `ith` crime generates a `profit[i]` and requires `group[i]` members to participate in it. If a member participates in one crime, that member can't participate in another crime.

Let's call a **profitable scheme** any subset of these crimes that generates at least `minProfit` profit, and the total number of members participating in that subset of crimes is at most `n`
```ad-question
title: Test Case
**Input:** n = 5, minProfit = 3, group = [2,2], profit = [2,3]
**Output:** 2
**Explanation:** To make a profit of at least 3, the group could either commit crimes 0 and 1, or just crime 1.
In total, there are 2 schemes.
```

---
# Abstract
```ad-abstract
A classic knap sack problem
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
class Solution:
    def profitableSchemes(self, n: int, minProfit: int, group: List[int], profit: List[int]) -> int:
        @lru_cache(None)
        def solve(i,num_in,curr_profit):
            if num_in>n:
                return 0
            if i>=len(group):
                return int(curr_profit>=minProfit)
            return sum([solve(i+1,num_in,curr_profit), solve(i+1,num_in+group[i],curr_profit+profit[i])])
        return solve(0,0,0)
```
---
