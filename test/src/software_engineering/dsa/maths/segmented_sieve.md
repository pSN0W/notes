# 🧩 Que
- Link
Find all the prime numbers between n and m. n-m < 1e5
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The problem with sieve is that it takes a lot of memory so here we will utilise the fact that difference is small. So first generate all the prime till sqrt(n) using sieve and then in the array of size n-m mark i if i+m is divisible by prime
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
vector<int> primes = sieve(sqrt(n));
vector<int> segment(n-m+1,0);
for(int p:primes){
	if(p*p > n)  break;
	// start from the nearest divisible
	int start = (m/p)*p;
	for(int j=start; j<=n; j+=p){
		if(j<m)   continue;
		segment[j-m] = 1;
	}
}
```
---
