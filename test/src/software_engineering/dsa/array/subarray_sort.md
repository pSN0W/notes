# 🧩 Que
- Link
Given an array find the smallest sub array that must be sorted so that entire array becomes sorted
```ad-question
title: Test Case
**Input** [1,2,3,4,5,8,6,7,9,10,11]
**Output** [5,7]
```

---
# Abstract
```ad-abstract
The idea is to find the largest and smallest numbers that are out of order and then keep them at their corrrect order. Their correct position will be the subarray that we will need to sort
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- The easiest way to solve this problem is sort the array and then check the subarray where indices do not match. T.C = O(n)
- However to find the solution in O(n) what you can do is find the smallest and largest number that are out of order. If the number are not out of order then they are at their correct place. (out of order = smaller then prev | greater then next)
- For the above array when you iterate through the array 
	- The first element that is out of order and will be your both high and low will be 8
	- The second element that's out of order is 6 so lo = 6 and hi = 8
- Now you put them at their correct place
	- [1, 2, 3, 4, 5, |6|, 7, |8|, 9, 10, 11]
	- So your answer is [5,7]
---
# ☠️ My thought process
- 
---

# 💻 Code

---
