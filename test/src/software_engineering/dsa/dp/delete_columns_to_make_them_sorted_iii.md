# 🧩 Que
- [Link](https://leetcode.com/problems/delete-columns-to-make-sorted-iii/)
You are given an array of `n` strings `strs`, all of the same length.

We may choose any deletion indices, and we delete all the characters in those indices for each string.

For example, if we have `strs = ["abcdef","uvwxyz"]` and deletion indices `{0, 2, 3}`, then the final array after deletions is `["bef", "vyz"]`.
Suppose we chose a set of deletion indices `answer` such that after deletions, the final array has **every string (row) in lexicographic** order. (i.e., `(strs[0][0] <= strs[0][1] <= ... <= strs[0][strs[0].length - 1])`, and `(strs[1][0] <= strs[1][1] <= ... <= strs[1][strs[1].length - 1])`, and so on). Return _the minimum possible value of_ `answer.length`.
```ad-question
title: Test Case
**Input:** strs = ["babca","bbazb"]
**Output:** 3
**Explanation:** After deleting columns 0, 1, and 4, the final array is strs = ["bc", "az"].
Both these rows are individually in lexicographic order (ie. strs[0][0] <= strs[0][1] and strs[1][0] <= strs[1][1]).
Note that strs[0] > strs[1] - the array strs is not necessarily in lexicographic order.
```

---
# Abstract
```ad-abstract
You are basically tasked to find the lis. You just have to compare for different i and j. Check the code for details
```

- Tags #standard_que 
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
    def minDeletionSize(self, strs: List[str]) -> int:
        n,m = len(strs),len(strs[0])
        dp = [1]*m
        def follows_order(i,j):
            for k in range(n):
                if strs[k][i] > strs[k][j]:
                    return False
            return True
        for i in range(m):
            for j in range(i):
                if follows_order(j,i):
                    dp[i] = max([dp[i],dp[j]+1])
        return m - max(dp)
```
---
