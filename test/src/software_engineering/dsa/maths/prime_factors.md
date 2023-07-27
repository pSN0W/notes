# 🧩 Que
- Link
Given a number n find the prime factors of that number
```ad-question
title: Test Case
20 = 2^2*5
```

---
# Abstract
```ad-abstract
The brute force will be to just go from 1 to sqrt(n) and divide n if it is possible to do so. You should divide n by i as many time as possible.
You can use the idea of [[sieve_of_eranthosis]]. Instead of storing is prime store the factor and then for any n you can retrace back the step
```
[[sieve_of_eranthosis]]
- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Lets create a sieve with the given case
- [0, 1, 2, 3, 2, 5, 2, 7, 2, 9, 2, 11, 2, 13, 2, 3, 2, 17, 2, 19, 2]
- Now to calculate the prime factor

| n   | prime_factor |
| --- | ------------ |
| 20  | 2            |
| 10  | 2            |
| 5   | 5            | 

---
# ☠️ My thought process
- 
---

# 💻 Code

---
