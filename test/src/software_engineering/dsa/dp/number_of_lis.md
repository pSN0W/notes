# 🧩 Que
- [Link](https://leetcode.com/problems/number-of-longest-increasing-subsequence/)
Given an array find the total number of lis
```ad-question
title: Test Case
**Input:** nums = [1,3,5,4,7]
**Output:** 2
**Explanation:** The two longest increasing subsequences are [1, 3, 4, 7] and [1, 3, 5, 7].
```

---
# Abstract
```ad-abstract
You build an lis and for each of it you keep track of the total number of ways to reach at that lis
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Add a big number to the end of the list to ensure that your lis ends there.
- You must perform the computation in two steps
	- Compute the lis for the given i
	- Iterate for j again and check how many of them could have contributed to it. That is nums[j] < nums[i] and dp[i] == dp[j] + 1

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def findNumberOfLIS(self, nums: List[int]) -> int:
        nums.append(int(1e7))
        dp = [1]*len(nums)
        num_way = [0]*len(nums)
        ans = 1
        for i,num in enumerate(nums):
            for j,num2 in enumerate(nums[:i]):
                if num>num2:
                    dp[i] = max(dp[i],dp[j]+1)
            for j in range(i):
                if nums[i] > nums[j] and dp[i] == dp[j]+1:
                    num_way[i]+=num_way[j]
            num_way[i] = max([1,num_way[i]])
        return num_way[-1]
```
---
