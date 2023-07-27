# 🧩 Que
- [Link](https://leetcode.com/problems/ones-and-zeroes/)
You are given an array of binary strings `strs` and two integers `m` and `n`.

Return _the size of the largest subset of `strs` such that there are **at most**_ `m` `0`_'s and_ `n` `1`_'s in the subset_.
```ad-question
title: Test Case
**Input:** strs = ["10","0001","111001","1","0"], m = 5, n = 3
**Output:** 4
**Explanation:** The largest subset with at most 5 0's and 3 1's is {"10", "0001", "1", "0"}, so the answer is 4.
Other valid but smaller subsets include {"0001", "1"} and {"10", "1", "0"}.
{"111001"} is an invalid subset because it contains 4 1's, greater than the maximum of 3.
```

---
# Abstract
```ad-abstract
An easy knapsack approach. First convert the strings to dictionaries and then its just choose or not choose i
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Since the transition you are doing only involves then next or previous state you can reduce it 2d DP check this [solution](https://leetcode.com/problems/ones-and-zeroes/solutions/3668890/memoization-tabulation-space-optimization-3d-dp-to-2d-dp/)

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def findMaxForm(self, strs: List[str], m: int, n: int) -> int:
        lst = [Counter(s) for s in strs]
        @lru_cache(None)
        def solve(i,num_0,num_1):
            if i>=len(lst):
                return 0
            ans = solve(i+1,num_0,num_1)
            if lst[i].get('0',0)+num_0<=m and lst[i].get('1',0)+num_1 <= n:
                ans = max([ans,1+solve(i+1,lst[i].get('0',0)+num_0,lst[i].get('1',0)+num_1)])
            return ans
        return solve(0,0,0)
```
---
