# 🧩 Que
- Link
Given two sorted linked list merge them to create a new one
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You can do it very easily with recursion. You normally think iterative but linked list is solved easily with recursion.
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
def merge(l1,l2):
	if l1 is None:   return l2
	if l2 is None:   return l1
	if l1.val > l2.val:
		c = l2
		c.next = merge(l1,l2.next)
	else:
		c = l1
		c.next = merge(l1.next,l2)
	return c
```
---
