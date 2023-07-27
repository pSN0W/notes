# 🧩 Que
- [Link](https://leetcode.com/problems/sum-of-subarray-minimums/)
Given an array of integers arr, find the sum of `min(b)`, where `b` ranges over every (contiguous) subarray of `arr`
```ad-question
title: Test Case
**Input:** arr = [3,1,2,4]
**Output:** 17
**Explanation:** 
Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4]. 
Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1.
Sum is 17.
```

---
# Abstract
```ad-abstract
It looks like a classical case of monotonic stack and it is but problem arises for repeated numbers. For them what we do is for the left we say that we will consider all that is <= curr and for right we consider only till <curr
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- If there were no duplicates you would solve like this
	- arr = [3,1,2,4] -> count number of sub arrays where 1 will be minimum
	- next_smaller to left is at -1 and next smaller to right will be at 4
	- Total to left = 2 (3,1) and total to right = 3(1,2,4). So total number of sub arrays where 1 is minimum is `2*3 = 6`
	- Similar approach can be followed for all integer
- When there are duplicates
	- arr = [2,1,3,1,4,1,5] -> consider index 3
	- To avoid duplicates subset from being generated you can decide that you will consider <= to left and only < to right and vice versa. 
	- so to left smaller = -1 while to right it is 5

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def sumSubarrayMins(self, arr: List[int]) -> int:
        n = len(arr)
        next_smaller = [None]*n
        st = []
        for i in range(n-1,-1,-1):
            while st and arr[st[-1]] > arr[i]:
                st.pop()
            next_smaller[i] = st[-1] if st else n
            st.append(i)
        st = []
        ans = 0
        for i,num in enumerate(arr):
            while st and arr[st[-1]] >= num:
                st.pop()
            curr = st[-1] if st else -1
            ans = ans + (i-curr)*(next_smaller[i]-i)*num
            st.append(i)
        return ans%int(1e9+7)
```
---
