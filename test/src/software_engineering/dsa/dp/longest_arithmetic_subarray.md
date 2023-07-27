# 🧩 Que
- [Link](https://leetcode.com/problems/arithmetic-slices/)
An integer array is called arithmetic if it consists of **at least three elements** and if the difference between any two consecutive elements is the same.
- For example, `[1,3,5,7,9]`, `[7,7,7,7]`, and `[3,-1,-5,-9]` are arithmetic sequences.
Given an integer array `nums`, return _the number of arithmetic **subarrays** of_ `nums`
```ad-question
title: Test Case
**Input:** nums = [1,2,3,4]
**Output:** 3
**Explanation:** We have 3 arithmetic slices in nums: [1, 2, 3], [2, 3, 4] and [1,2,3,4] itself.
```

---
# Abstract
```ad-abstract
You can do it like [[longest_arithmetic_subsequence]] but the problem there is you are storing a list of maps. But for this question you just want the differences to be same between consecutive elemenet. So you can just store the diff and then find consecutive diff that ends till that index. That will be length of arithmetic sequence to that index, but you don't even need that too you can just store the previous diff. 
```
[[longest_arithmetic_subsequence]]
- Tags 
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
    def numberOfArithmeticSlices(self, nums: List[int]) -> int:
        if len(nums) < 3:
            return 0
        diff = []
        for x,y in zip(nums[1:],nums[:-1]):
            diff.append(x-y)
        prev_diff,ans,curr = None,0,2
        for d in diff:
            if d == prev_diff:
                curr+=1
            else:
                curr = 2
                prev_diff = d
            ans += max([0,curr-2])
        return ans
```
---
