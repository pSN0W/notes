# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-moves-to-equal-array-elements/)
Given an integer array `nums` of size `n`, return _the minimum number of moves required to make all array elements equal_.

In one move, you can increment `n - 1` elements of the array by `1`.
```ad-question
title: Test Case
**Input:** nums = [1,2,3]
**Output:** 3
**Explanation:** Only three moves are needed (remember each move increments two elements):
[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]
```

---
# Abstract
```ad-abstract
You can approach the que in different way instead of increasing n-1 elements with 1 you can decrease 1 just 1 element at each step
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
import numpy as np
class Solution:
    def minMoves(self, nums: List[int]) -> int:
        mn = min(nums)
        return sum([x-mn for x in nums])
```
---
