# 🧩 Que
- Link
You are given n nest and b birds. You want to put birds in the nest such that min distance between any two nest is maximised
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The maximu possible distance can be nest[n-1] - nest[0] while the minimu can be 1. Search for the answer in this interval.
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
def possible(sep):
	birds = 1, loc = nests[0]
	for nest in nests[1:]:
		if nest - loc >= sep:
			birds += 1
			loc = nest
	return birds >= B
```
---
