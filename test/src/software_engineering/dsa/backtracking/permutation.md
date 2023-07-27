# 🧩 Que
- Link
Given an array generate all possible permutation for that array.
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is to swap i with index from j to n.
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- You want to get all the elements at the first index so what you do is perform swaps for 0 with all the possible index you recursively increase the index ![[Pasted image 20230717203105.png]]
- Here backtracking becomes important as if you swap 0,1 you will get bac and then you swap 0,2 you get cab which is different from cba you aspired

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def permute(arr):
	n = len(arr)
	ans = []
	def solve(i,curr):
		if i == n:
			ans.append(curr.copy())
		for j in range(i,n):
			swap(curr[i],curr[j])
			solve(i+1, curr)
			swap(curr[i],curr[j])
	solve(0,arr)
	
```
---
