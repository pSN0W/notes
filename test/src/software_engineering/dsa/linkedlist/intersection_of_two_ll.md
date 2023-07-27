# 🧩 Que
- [Link](https://leetcode.com/problems/intersection-of-two-linked-lists/)
Given the heads of two singly linked-lists `headA` and `headB`, return _the node at which the two lists intersect_.
```ad-question
title: Test Case
![[Pasted image 20230709232731.png]]
```

---
# Abstract
```ad-abstract
You can iterate once to get length of both the lists. Once you have the compensate the length of the larger array by moving it to a distance.
Another way to solve is that you can just compensate the diffrence by iterating twice. The idea is that when you reach end of the current node start from the begining of other. This will help you compensate the difference 
```

- Tags #unsolved 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        a,b = headA,headB
        while a!=b:
            a = headB if a is None else a.next
            b = headA if b is None else b.next
        return a
```
---
