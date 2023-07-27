# 🧩 Que
- [Link](https://leetcode.com/problems/make-array-strictly-increasing/)
Given two integer arrays `arr1` and `arr2`, return the minimum number of operations (possibly zero) needed to make `arr1` strictly increasing.

In one operation, you can choose two indices `0 <= i < arr1.length` and `0 <= j < arr2.length` and do the assignment `arr1[i] = arr2[j]`.
```ad-question
title: Test Case
**Input:** arr1 = [1,5,3,6,7], arr2 = [1,3,2,4]
**Output:** 1
**Explanation:** Replace `5` with `2`, then `arr1 = [1, 2, 3, 6, 7]`.
```

---
# Abstract
```ad-abstract
The main idea is to keep array 2 sorted. Keep track of index in arr1 and arr2 if you need to switch the index of arr1 then do it with the upperbound of previous smaller
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- solve(i,j,lft) -> Solution for arr1 index i, arr2 index j when coming from i
- First get the previous minimum element. This can be done using the variable lft which basically tells that you are coming after a switch or not. Fun fact you don't need to memoise it. Check out this [solution](https://leetcode.com/problems/make-array-strictly-increasing/solutions/3647949/2d-dp-easy-c-solution-with-approach/)
- Now you have two option:
	- If the current element is greater then go to next
	- Swap it with the smallest just greater than in arr2

---
# ☠️ My thought process
- First thought you won't need to memoise index of arr2
- Then you were using prev = min([arr1[i-1],arr2[j]])
---

# 💻 Code
```python
from bisect import bisect_right
class Solution:
    def makeArrayIncreasing(self, arr1: List[int], arr2: List[int]) -> int:
        arr2.sort()
        arr1 = [-1] + arr1
        arr2 = [-1] + arr2
        n,m = len(arr1),len(arr2)
        @lru_cache(None)
        def solve(i,j,lft):
            if i>=n:
                return 0
            ans = int(1e6)
            prev = arr1[i-1] if lft else arr2[j]
            # leave if possible
            if arr1[i] > prev:
                ans = min([ans,solve(i+1,j,True)])
            # switch the current one
            nw_idx = bisect_right(arr2[j+1:],prev)
            if nw_idx+j+1<m:
                ans = min([ans,1 + solve(i+1,nw_idx+j+1,False)])
            return ans
        ans = solve(1,0,True)
        return ans if ans<int(1e6) else -1
```
---
