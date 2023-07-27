# 🧩 Que
- [Link](https://leetcode.com/problems/find-peak-element/)
Given an array return any of the peak element
```ad-question
title: Test Case
**Input:** nums = [1,2,1,3,5,6,4]
**Output:** 5
**Explanation:** Your function can return either index number 1 where the peak element is 2, or index number 5 where the peak element is 6.
```

---
# Abstract
```ad-abstract
At any index you just have to decide whether to go left or right and you are guarenteed to find your answer. Reduce the search space as such
- num[m-1] < num[m] < num[m+1] // increasing so go right
- num[m-1] > num[m] > num[m+1] // decreasing so go left
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
    def findPeakElement(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return 0
        if nums[0] > nums[1]:
            return 0
        if nums[-1] > nums[-2]:
            return len(nums) - 1
        lo,hi = 1,len(nums) - 2
        while lo<=hi:
            m = (lo+hi)//2
            if nums[m-1] < nums[m] > nums[m+1]:
                return m
            elif nums[m-1] < nums[m] < nums[m+1]:
                lo = m+1
            else:
                hi = m-1
        return 0

        
```
---
