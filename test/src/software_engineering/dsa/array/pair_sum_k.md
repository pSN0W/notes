# 🧩 Que
- Link
You are given an array and the aim is to find pairs for which the sum is given target
```ad-question
title: Test Case

```

---
# Abstract
```ad-abstract
You can use a set to keep the numbers that we are iterating. If you are at index i then check that target - arr[i] is equal to sum or not
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- You can use two for loops and then check that if their are two indices whose sum is target. T.C = O(n^2)
- You can sort the array and then use two pointers. One at the starting and another at the end. If curr sum is greater then target then increase the starting index else decrease the end index. O(nlgn)
- You can use unordered set to keep a track of all the elements already encountered and then check for the target-arr[i]

---
# ☠️ My thought process
- 
---

# 💻 Code

---
