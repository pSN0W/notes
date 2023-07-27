# 🧩 Que
- Link
Given a,b and mod find (a^b)%mod
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea here is that you can use mod to break something in smaller parts. 9 (1001) can be written as 8 + 1. 
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Lets say you are given 3^9
- You can write 9 as (8+1) so `3^9 = 3^8*3`
- The good thing about this is you can multiply res with itself to get the second power 3 -> 3^2 -> 3^4 -> 3^8

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int power(int a,int b){
	int res = 1
	while(b){
		if(b&1){
			res*=a;
			res%=mod;
		}
		a*=a;
		a%=mod;
		b>>=1;
	}
	return res;
}
```
---
