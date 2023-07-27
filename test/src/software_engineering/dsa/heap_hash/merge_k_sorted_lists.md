# 🧩 Que
- [Link](https://leetcode.com/problems/merge-k-sorted-lists/)
You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order.

_Merge all the linked-lists into one sorted linked-list and return it._
```ad-question
title: Test Case
**Input:** lists = [ [1,4,5],[1,3,4],[2,6] ]
**Output:** [1,1,2,3,4,4,5,6]
**Explanation:** The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted list:
1->1->2->3->4->4->5->6
```

---
# Abstract
```ad-abstract
The idea is to maintain a heap with all the node. Check code to understand better
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
from heapq import heappush,heappop
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        hd = tl = None
        pq = []
        for i,node in enumerate(lists):
            if node:
                # i is pushed so that you don't compare with node when val is same
                heappush(pq,(node.val,i,node)) 
        while pq:
            _,i,node = heappop(pq)
            if node.next:
                heappush(pq,(node.next.val,i,node.next))
            node.next = None
            if hd is None:
                hd = tl = node
            else:
                tl.next = node
                tl = tl.next
        return hd
```
---
