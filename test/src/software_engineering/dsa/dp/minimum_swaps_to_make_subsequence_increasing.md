# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-swaps-to-make-sequences-increasing/)
Given two array arr1 and arr2. In one operation you can swap arr1[i] and arr2[i]. Find the minimum swaps required to make both array strictly increasing
```ad-question
title: Test Case
**Input:** nums1 = [1,3,5,4], nums2 = [1,2,3,7]
**Output:** 1
**Explanation:** 
Swap nums1[3] and nums2[3]. Then the sequences are:
nums1 = [1, 3, 5, 7] and nums2 = [1, 2, 3, 4]
which are both strictly increasing.
```

---
# Abstract
```ad-abstract
The idea is pretty simple for each i check if you can perform swap or not and then get minimum from both these. You will also need to keep track of if you have performed swap on the previous index to find which one to compare to
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
    def minSwap(self, nums1: List[int], nums2: List[int]) -> int:
        nums1 = [-1] + nums1
        nums2 = [-1] + nums2
        @lru_cache(None)
        def solve(idx,prev_swapped):
            if idx==len(nums1):
                return 0
            prev1,prev2 = (nums2[idx-1],nums1[idx-1]) if prev_swapped else (nums1[idx-1],nums2[idx-1])
            #print(idx,prev_swapped,prev1,prev2)
            ans = int(1e6)
            if nums1[idx]>prev1 and nums2[idx]>prev2:
                ans = min([ans,solve(idx+1,False)])
            if nums2[idx]>prev1 and nums1[idx]>prev2:
                ans = min([ans,1+solve(idx+1,True)])
            return ans
        return solve(1,False)
```
---
