# 🧩 Que
- [Link](https://leetcode.com/problems/ugly-number-ii/)
An **ugly number** is a positive integer whose prime factors are limited to `2`, `3`, and `5`.

Given an integer `n`, return _the_ `nth` _**ugly number**_
```ad-question
title: Test Case
**Input:** n = 10
**Output:** 12
**Explanation:** [1, 2, 3, 4, 5, 6, 8, 9, 10, 12] is the sequence of the first 10 ugly numbers.
```

---
# Abstract
```ad-abstract
The idea is to maintain the index at which you are for each of 2,3 and 5 and the choose the one that's multiplication gives minimum
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Create an array for ans of size n and add 1 as the first answer
- Now if you need to choose your next answer what you can do is choose:
	- min of `2*1, 3*1, 5*1`
	- for next it should be min of `2*2,3*1,5*1`
	- After that it will be `2*2,3*2,5*1`
- You see how we need to keep index for each of the number we want to multiply.
- Put that index in a dictionary. Get the minimum and update the one that gives you minimum. (we need to update all since we don't want duplicates)

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def nthUglyNumber(self, n: int) -> int:
        ans = [1]*n
        dic = {2:0,3:0,5:0}
        for i in range(1,n):
            curr = min([k*ans[v] for k,v in dic.items()])
            dic = {k:v+(1 if ans[v]*k==curr else 0) for k,v in dic.items()}
            ans[i] = curr
        return ans[-1]
```
---
