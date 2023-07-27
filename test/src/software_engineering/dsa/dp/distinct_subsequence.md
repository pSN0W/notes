# 🧩 Que
- [Link](https://leetcode.com/problems/distinct-subsequences/)
Given two string s and t return the number of distinct sub sequence of s which equals to t. 
```ad-question
title: Test Case
**Input:** s = "rabbbit", t = "rabbit"
**Output:** 3
**Explanation:**
As shown below, there are 3 ways you can generate "rabbit" from s.
`rabb_b_it`
`ra_b_bbit**`
`rab_b_bit**`
```

---
# Abstract
```ad-abstract
Lets see for two indexes x and y if they match you have two choices
- decreament x and y
- decreament x and keep y same in hope that there is one more subsequence in s which match the target up to that
```

- Tags 
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
    def numDistinct(self, s: str, t: str) -> int:
        @lru_cache(None)
        def solve(i,j):
            if j<0:
                return 1
            if i<0:
                return 0
            ans = 0
            if s[i] == t[j]:
                ans += solve(i-1,j-1)
            ans += solve(i-1,j)
            return ans
        return solve(len(s)-1,len(t)-1)
```
---
