# 🧩 Que
- Link
You are given two positive integer A & B. You need to find the maximum valued integer X such that
- X divides A
- X and B are coprime
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The thing to notice here is that we want the largest factor of A but we don't want it to be factor of B so basically we want A divided by all the common factors
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
```cpp
while(__gcd(a,b)!=1){
	a = a/__gcd(a,b)
}
```
---
