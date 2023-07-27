# 🧩 Que
- [Link](https://leetcode.com/problems/longest-arithmetic-subsequence/)
Given an array `nums` of integers, return _the length of the longest arithmetic subsequence in_ `nums`
```ad-question
title: Test Case
**Input:** nums = [3,6,9,12]
**Output:** 4
**Explanation: ** The whole array is an arithmetic sequence with steps of length = 3.
```

---
# Abstract
```ad-abstract
This is same as LIS. You will need to just keep track of all the differences encountered till now so you will need to make a dp or dictionaries where key value will be the the largest subsequence with given difference
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Create a dp of dictionaries.
- Iterate like lis just for each element find the difference and see the longest subsequence till now with that difference

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def longestArithSeqLength(self, nums: List[int]) -> int:
        dp = [{} for _ in nums]
        ans = 0
        for i,num in enumerate(nums):
            for j,num_2 in enumerate(nums[:i]):
                curr_diff = num - num_2
                dp[i].setdefault(curr_diff,0)
                dp[i][curr_diff] = max(dp[i][curr_diff],1+(0 if curr_diff not in dp[j] else dp[j][curr_diff]))
                ans = max(ans,dp[i][curr_diff])
        return ans + 1
```
---
