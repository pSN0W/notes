# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-subarray-sum-with-one-deletion/)
Given an array find max subarray sum with 1 or no deletion
```ad-question
title: Test Case
**Input:** arr = [1,-2,0,3]
**Output:** 4
**Explanation:** Because we can choose [1, -2, 0, 3] and drop -2, thus the subarray [1, 0, 3] becomes the maximum value.
```

---
# Abstract
```ad-abstract
The big idea is to create two arrays one denote the max subarray sum starting from index i and another denotes ending at index i-1. Use a for loop to perform one deletion and get value
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
    def maximumSum(self, arr: List[int]) -> int:
        n = len(arr)
        start_from = [0]*n
        end_from = [0]*n
        end_from[0] = curr = arr[0]
        for i in range(1,n):
            curr = max([curr+arr[i],arr[i]])
            end_from[i] = curr
        start_from[-1] = curr = arr[-1]
        for i in range(n-2,-1,-1):
            curr = max([curr+arr[i],arr[i]])
            start_from[i] = curr
        ans = max(start_from)
        for i in range(1,n-1):
            curr = start_from[i+1] + end_from[i-1]
            ans = max([ans,curr])
        return ans
```
---
