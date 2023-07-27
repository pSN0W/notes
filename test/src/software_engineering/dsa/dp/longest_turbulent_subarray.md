# 🧩 Que
- [Link](https://leetcode.com/problems/longest-turbulent-subarray/)
An array is called turbulent if it follows pattern of peak, trough, peak .. or trough, peak, trough.  Find the size of the longest turbulent subarray
```ad-question
title: Test Case
**Input:** arr = [9,4,2,10,7,8,8,1,9]
**Output:** 5
**Explanation:** arr[1] > arr[2] < arr[3] > arr[4] < arr[5]
```

---
# Abstract
```ad-abstract
It's same as lis. Define dp as a 2d matrix. dp[i][0] = max turbulent subarray ending at i where arr[i-1]<arr[i]. Whereas dp[i][1] is max turbulent with arr[i-1]>arr[i]
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
    def maxTurbulenceSize(self, arr: List[int]) -> int:
        n = len(arr)
        dp = [[1]*2 for _ in range(n)]
        for i in range(1,n):
            dp[i][0] = 1 + dp[i-1][1] if arr[i-1] > arr[i] else 1
            dp[i][1] = 1 + dp[i-1][0] if arr[i-1] < arr[i] else 1
        return max([max(x) for x in dp])
```
---
