# 🧩 Que
- Link
Given a number n find total set bit in n
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The easiest solution will be to go from 1 to 32 and check if ith bit is set or not and sum them.
But when you take n & (n-1) then it removes the last set bit.
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def get_bit(n):
	ans = 0:
	while n:
		n = n&(n-1)
		ans += 1
	return ans
```
---
