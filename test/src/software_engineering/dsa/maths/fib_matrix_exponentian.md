# 🧩 Que
- Link
Find nth fibonocci number in log n time
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You can use matrix exponentian to achieve this. Check [[matrix_exponentian]]for details. This only contains code
```
[[matrix_exponentian]]
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
// define matrix class
int fib(int n){
	Mat res = Mat(2);
	res.identity();
	Mat T = Mat(2);
	T[0][0] = T[0][1] = T[1][0] = 1;
	if(n<=2)   return 1;
	n-=2;
	while(n){
	    if(n&1)    res*=T;
	    T*=T;
	    n>>=1;
	}
	return (res.m[0][0]+res.m[0][1])%mod;
}
```
---
