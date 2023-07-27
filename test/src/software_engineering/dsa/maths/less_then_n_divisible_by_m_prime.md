# 🧩 Que
- Link
Find total number of which are less then n and are divisible by the first m prime numbers
```ad-question
title: Test Case
n = 500, m = 3
```

---
# Abstract
```ad-abstract
The idea is to use inclusion exclusion here. 
Let Ni = Number of integer <n and divisible by ith prime number
You want to find N1 uni N2 uni N3 ...
You can use exclusion inclusion for it
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- Lets solve for the above case
| Ni  | logic                | Number divisible |
| --- | -------------------- | ---------------- |
| 2   | div by 2             | 500/2 = 250      |
| 3   | div by 3             | 500/3 = 166      |
| 5   | div by 5             | 500/5 = 100      |
| 6   | N2 inter N3          | 500/6(lcm) = 83  |
| 10  | N2 inter N5          | 500/10 = 50      |
| 15  | N3 inter N5          | 500/15 = 33      |
| 30  | N2 inter N3 inter N5 | 500/30 = 16      | 
- Using inclusion Exclusion 250 + 166 + 100 - 83 - 50 - 33 + 16
- If n is really large and m is small you can generate all the subset of the primes and then for each subset you can check if the number of element in that is positive or negative and then do + or - 
---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
vector<int> primes = {2, 3, 5, 7, 11, ....};
// use bit mask to generate subset
for(int i=1;i<(1<<m);i++){
	int lcm = 1;
	for(int j=0;j<m;j++){
		if((i>>j)&1){
			lcm *= primes[j]; // just multiply as all numbers are prime
		}
	}
	// if number of set bits are even then subtract else plus
	if(__builtin_popcount(i)%2==1){
		ans += n/lcm;
	}
	else{
		ans -= n/lcm;
	}
}
```
---
