# 🧩 Que
- Link
Given an integer of array find the the value obtained by xoring the subarray followed by xoring the value obtained
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is simple you need to sount the number of times a number will appear in a subarray. If it is even then it will not affect answer else it will. 
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- To find the number if times an element will appear in subarray
	- If length of the array is n then you can form `n*(n+1)/2` subarray with it.
	- Number of occurence of index i = num_sub(n) - num_sun(i) - num_sub(n-i-1)
	- i will not be part of subarray which ends at i-1 or starts from i+1

---
# ☠️ My thought process
- 
---

# 💻 Code

---
