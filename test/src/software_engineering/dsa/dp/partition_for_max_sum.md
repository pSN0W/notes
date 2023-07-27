# 🧩 Que
- [Link](https://leetcode.com/problems/partition-array-for-maximum-sum/)
Given an integer array `arr`, partition the array into (contiguous) subarrays of length **at most** `k`. After partitioning, each subarray has their values changed to become the maximum value of that subarray.

Return _the largest sum of the given array after partitioning.
```ad-question
title: Test Case
**Input:** arr = [1,15,7,9,2,5,10], k = 3
**Output:** 84
**Explanation:** arr becomes [15,15,15,9,10,10,10]
```

---
# Abstract
```ad-abstract
The idea is to see for the current element which of the partiton will create the maximum ans. That means for [1,k] for each index which value should be chosen for partitioning. Once you have done it just choose the best one. You can precompute the maximum too 
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Precompute a maximum array which tells the maximum for range [i,j].
- For each i you have to choose what size of partition will be best. For example for idx i and partition size 3. You can choose the max of 
	- f(i+1) + max[i,i]* 1 // for partition size 1
	- f(i+2) + max[i,i+1]* 2 // for partition size 2
	- f(i+3) + max[i,i+2]* 3 // for partition size 3
- The max of these will be your answer

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def maxSumAfterPartitioning(self, arr: List[int], k: int) -> int:
        if k==1:
            return sum(arr)
        n = len(arr)
        mx_arr = [[-1]*n for _ in range(n)]
        for i in range(n):
            for j in range(i,n):
                if j==i:
                    mx_arr[i][j] = arr[i]
                else:
                    mx_arr[i][j] = max([arr[j],mx_arr[i][j-1]])
        def get_max(i,j):
	        # because you are computiong for [i,j)
            j-=1
            return 0 if j>=n else mx_arr[i][j]
        @lru_cache(None)
        def solve(idx):
            if idx>=n:
                return 0
            return max([solve(i+idx)+get_max(idx,i+idx)*i for i in range(1,k+1)])
        return solve(0)
```
---
