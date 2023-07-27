# 🧩 Que
- Link
Given 2n+2 numbers where every number comes twice except those two numbers find those two numbers
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You know if you take XOR then all the repeated number will be 0. You will be left with only the XOR of non repeated numbers.
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- Lets say the non repeated number are 5 and 7
- When you take cummulative XOR then all repeated number goes to 0 and you are left with 5^7 = (101)^(111) = (010). 
- XOR of two unequal number will always be > 0. Now for two number the bit will be non zero if that bit is set for only one of the number.
- Find one of the ith bit that is set for 5^7 = 1.
- Take out all the number whose first bit is set. This will result in one of the unique number and rest repeated if take XOR of this array you will be left with one of the unique number.
- To get the second unique number. You have unique1^unique2 take xor of this with unique number

---
# ☠️ My thought process
- 
---

# 💻 Code

---
