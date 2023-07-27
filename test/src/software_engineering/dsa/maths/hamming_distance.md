# 🧩 Que
- Link
Hamming distance between two numbers is given by the number of position that their bit differs. Given an array find sum of hamming distance for all pairs of integer in an array
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
If you convert the array to binary then the number of 0 at bit i multiplied by number of 1 at bit i will be the difference for that bit. Do this similarly for all bits and sum them.
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Find product of number of set and unset bit for index i.
- Sum the above number for all the i.
---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
for(int i=0;i<32;i++){
	freq[2] = {0};
	for(int num:nums){
		freq[num&1<<i > 0]++
	}
	ans+=freq[0]*freq[1];
}
```
---
