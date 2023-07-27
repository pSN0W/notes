# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-ascii-delete-sum-for-two-strings/)
Given two string s1 and s2 return the lowest ascii sum of deleted characters to make string equal
```ad-question
title: Test Case
**Input:** s1 = "sea", s2 = "eat"
**Output:** 231
**Explanation:** Deleting "s" from "sea" adds the ASCII value of "s" (115) to the sum.
Deleting "t" from "eat" adds 116 to the sum.
At the end, both strings are equal, and 115 + 116 = 231 is the minimum sum possible to achieve this
```

---
# Abstract
```ad-abstract
dp[i][j] denotes the maximum ascii sum you can get by making s1[:i] equal to s2[:j]. Everything is like lcs just to update when you get equal element
dp[i][j] = dp[i-1][j-1] + 2*ord(s[i-1])
```
This is a complete like [[lcs]]
- Tags #revise #standard_que 
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
    def minimumDeleteSum(self, s1: str, s2: str) -> int:
        n1,n2 = len(s1),len(s2)
        dp = [[0]*(n2+1) for _ in range(n1+1)]
        for i in range(1,n1+1):
            for j in range(1,n2+1):
                if s1[i-1] == s2[j-1]:
                    dp[i][j] = 2*ord(s1[i-1]) + dp[i-1][j-1]
                dp[i][j] = max([dp[i-1][j],dp[i][j-1],dp[i][j]])
        return sum([ord(x) for x in s1]) + sum([ord(x) for x in s2]) - dp[n1][n2]
```
---
