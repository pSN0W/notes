# 🧩 Que
- [Link](https://leetcode.com/problems/distribute-repeating-integers/)
You are given an array of `n` integers, `nums`, where there are at most `50` unique values in the array. You are also given an array of `m` customer order quantities, `quantity`, where `quantity[i]` is the amount of integers the `ith` customer ordered. Determine if it is possible to distribute `nums` such that:
- The `ith` customer gets **exactly** `quantity[i]` integers,
- The integers the `ith` customer gets are **all equal**, and
- Every customer is satisfied.
Return `true` _if it is possible to distribute_ `nums` _according to the above conditions_.
```ad-question
title: Test Case
**Input:** nums = [1,1,2,2], quantity = [2,2]
**Output:** true
**Explanation:** The 0th customer is given [1,1], and the 1st customer is given [2,2].
```

---
# Abstract
```ad-abstract
Since the number of unique nums can only be upto 50 hence for each unique num calculate the customers you can satisfy. You can find frequency of each number and number of customer demand less then that frequency can be used to satusfy that customer. Then you can solve the que like [[number_of_ways_to_wear_hats]] or I think greedy will work too. (It might not since you can given the same number to two customers)
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code

---
