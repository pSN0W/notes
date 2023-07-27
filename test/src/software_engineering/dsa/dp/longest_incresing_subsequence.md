# 🧩 Que
- [Link](https://leetcode.com/problems/longest-increasing-subsequence/)
Given an array return the largest increasing subsequence
```ad-question
title: Test Case
**Input:** nums = [10,9,2,5,3,7,101,18]
**Output:** 4
**Explanation:** The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

---
# Abstract
```ad-abstract
Let dp[i] defines the lis that ends at index i. Now to build dp[i] you can iterate for j in [0..i] and for all j such that arr[j] < arr[i] you can update your lis for i as dp[i] = max([dp[i],dp[j]+1])
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
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = [1]*len(nums)
        for i,num in enumerate(nums):
            for j,tx in enumerate(nums[:i]):
                if tx<num:
                    dp[i] = max(dp[i],dp[j]+1)
        return max(dp)
```
---
