# 🧩 Que
- Link
Count the number of ways binary strings with no consecutive 1 can be found using a binary string of length N
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is that after every 1 you need to add one 0. And then proceed accordingly. 
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- [                                          f(n) ] -> [1, 0,                               f(n-2)] + [0,                         f(n-1)]
- With recursion = O(2^n)
- With DP = O(n)
- With linear recurrence = O(k^3lgn)

---
# ☠️ My thought process
- 
---

# 💻 Code

---
