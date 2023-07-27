# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-subarray/)
Given an array nums find max subarray sum arr.
```ad-question
title: Test Case
**Input:** nums = [-2,1,-3,4,-1,2,1,-5,4]
**Output:** 6
**Explanation:** The subarray [4,-1,2,1] has the largest sum 6.
```

---
# Abstract
```ad-abstract
The idea is pretty simple for each array decide if it should be part of the previous subarray or it should start its own subarray.
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
    def maxSubArray(self, nums: List[int]) -> int:
        ans = curr = nums[0]
        for num in nums[1:]:
            curr = max([num,curr+num])
            ans = max([ans,curr])
        return ans
```
---
