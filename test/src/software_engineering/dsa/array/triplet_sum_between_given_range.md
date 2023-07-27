# 🧩 Que
- [Link](https://www.interviewbit.com/problems/triplets-with-sum-between-given-range/)
Given floats determine if their are triplets in the range (1,2)
```ad-question
title: Test Case
A = ["0.6", "0.7", "0.8", "1.2", "0.4"]
Ans = 1
```

---
# Abstract
```ad-abstract
The easiest solution will be to sort and then keep two pointer at start and end for the third pointer you can choose either the just greater from smaller index or just smaller then largest on.
The idea is to use bucket. Divide the elements into various buckets and see if you can use these buckets to get the answer. For example if you divide it into bucket of 0 < A < 0.5 < B < 1.0 < C. Then the possible answer can come from
- Min of C and 2 Min of A
- Sum of 3 max of A
- Sum of 3 min of B
- 2 min of B and min of A
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- https://github.com/joric/interviewbit/blob/master/programming/arrays/triplets-with-sum-between-given-range.md
- 

---
# ☠️ My thought process
- 
---

# 💻 Code

---
