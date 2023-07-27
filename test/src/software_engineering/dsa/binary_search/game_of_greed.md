# 🧩 Que
- Link
You are playing a game with k friend and you are given an array with coins.  You need to divide the array into k parts and you will get the one whose sum is minimum.
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The minimum you can get is min(coins[i]) and the max you can get is sum(coins) you want to maximize this
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
```python
def solve(coins, k):
	def possible(sm):
		num_seg = 0
		curr_sm = 0
		for coin in coins:
			curr_sm += coin
			if curr_sm >= sm:
				num_seg+=1
				curr_sm = 0
		return num_seg >= k
	lo,hi = min(coins), sum(coins)
	while lo<=hi:
		m = (lo+hi)//2
		if(possible(m)):
			ans = m
			lo = m+1
		else:
			h = m-1
	return ans
```
---
