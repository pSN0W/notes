# 🧩 Que
- Link
Find all prime numbers from 2 to n
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is to sieve to solve the problem
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- If you want to get all prime number till n you can run a for loop from 1 to n and then check if a number is prime of not. You can run the for loop only till sqrt(i)
- The most optimised version is to use sieve. 
	- Initially you mark all the number as prime 
	- For each prime you go to all its multiple and mark them as non prime
	- You can start from `i*i` as before that the elements are marked by its predecessor

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def sieve(n):
	is_prime = [True]*(n+1)
	for i in range(2,n+1):
		if is_prime(i):
			for j in range(i*i,n+1,i):
				is_prime[i] = False
	return [i for i in range(2,n+1) if is_prime[i]]
```
---
