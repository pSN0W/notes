# 🧩 Que
- Link
Given an array containing integer. You need to count the total number of inversion.
**Inversion**: Two element a[i] and a[j] form inversion if a[i] > a[j] and `i<j`
```ad-question
title: Test Case
[0, 5, 2, 3, 1]
5
```

---
# Abstract
```ad-abstract
Brute force implementation will be to find number of element that follows the condition for each number. Complexity = O(n^2)
Dividing and conquering will be the optimal one so you do something like merge sort and when you merge, everytime you take stuff from the right subarray add the number of element left in left array
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230718012624.png]]
- When you merge you need to count inversion like this
	- [0, 2, 5] merge with [1, 3]
	- First you put 0 then when you put 1 there are 2 in left array so num inversion is 2
	- Then you  do 0, 1, 2 and then when time comes for 3 you are left with 1 element in left so one more inversion
	- Total inversion = 1+2 = 3

---
# ☠️ My thought process
- 
---

# 💻 Code

---
