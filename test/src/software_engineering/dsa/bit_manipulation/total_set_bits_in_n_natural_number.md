# 🧩 Que
- Link
Given a value A find total number of set bit in the range 1,A
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
Look at the logic for this question
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- You can solve the problem in multiple ways, See [this](https://www.geeksforgeeks.org/count-total-set-bits-in-all-numbers-from-1-to-n/)
- You just iterate from 1 to n and then for each n count number of set bit O(nlgn)
- If you look at the vertical order of the bits then ith bit flips after 2^i position in vertical

| num | binary |
| --- | ------ |
| 0   | 0000   |
| 1   | 0001   |
| 2   | 0010   |
| 3   | 0011   |
| 4   | 0100   |
| 5   | 0101   | 
0th bit get flipped every 1 time 1st bit every 2 and 3rd bit every 4
- Read that again it uses a recursive formula and then something like binary exponentian

---
# ☠️ My thought process
- 
---

# 💻 Code

---
