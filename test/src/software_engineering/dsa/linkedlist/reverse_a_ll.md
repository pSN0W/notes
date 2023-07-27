# 🧩 Que
- Link
Given a linked list reverse it
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
If you solve by recursion then you can think of that head->next comes reversed so next of that should be the current head.
For iterative you will need to use three pointer so that you don't loose hold of the next
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- 1->2->3->4
- head->next comes reversed 1->2<-3<-4
- You will have to do head->next->next as head and head->next as NULL
- 1 <- 2 <- 3 <- 4

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def reverse(head):
	if head or head.next is None:
		return head
	rest = reverse(head.next)
	head.next.next = head
	head.next = None
	return head
```
---
