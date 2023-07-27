# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-product-subarray/)
You are given an array and you need to find the maximum subarray product of the array
```ad-question
title: Test Case
**Input:** nums = [2,3,-2,4]
**Output:** 6
**Explanation:** [2,3] has the largest product 6.
```

---
# Abstract
```ad-abstract
This is same as [[maximum_subarray_sum]]. For this problem the answer can come in two ways. First you have positive and multiply it with positive or you have a negative and you multiply it with negative. You keep the subarray max and min as you iterate the array in the values pos and neg respectively. This will let you go through all the cases
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- For any index you will need to keep track of max and min up to that index. 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        ans = float('-inf')
        pos = neg = 1
        for num in nums:
            pos = pos*num
            neg = neg*num
            pos,neg = max([pos,neg,num]),min([pos,neg,num])
            ans = max([ans,pos,neg])
        return ans
```
---
