# 🧩 Que
- [Link](https://leetcode.com/problems/reverse-nodes-in-k-group/)
Reverse linked list in a group of k
```ad-question
title: Test Case
**Input:** head = [1,2,3,4,5], k = 2
**Output:** [2,1,4,3,5]
```

---
# Abstract
```ad-abstract
The big idea is to reverse the linked list and return both head and tail. Once you have reversed all part you can join tail of one with head of other forming a chain.
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Write a function to reverse ll and return both head and tail
- Look at the code and abstract

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        def rev(node):
            if node is None or node.next is None:
                if node:
                    node.next = None
                return node,node
            hd,_ = rev(node.next)
            node.next.next = node
            node.next = None
            return hd,node
        hd = tl = None
        to_sol = head
        cnt = k
        itr = head
        while itr is not None:
            cnt-=1
            if cnt==0:
                cnt = k
                # store curr so you can do next = None for reverse
                curr = itr
                itr = itr.next
                curr.next = None
                curr_hd,curr_tl = rev(to_sol)
                to_sol = itr
                if hd is None:
                    hd = curr_hd
                    tl = curr_tl
                else:
                    tl.next = curr_hd
                    tl = curr_tl
            else:
                itr = itr.next
        tl.next = to_sol
        return hd 
```
---
