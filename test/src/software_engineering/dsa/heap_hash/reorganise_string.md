# 🧩 Que
- [Link](https://leetcode.com/problems/reorganize-string/)
Given a string `s`, rearrange the characters of `s` so that any two adjacent characters are not the same.

Return _any possible rearrangement of_ `s` _or return_ `""` _if not possible_.
```ad-question
title: Test Case
**Input:** s = "aab"
**Output:** "aba"
```

---
# Abstract
```ad-abstract
It is same as [[happy_number]] but the code here is much cleaner
```
[[happy_number]]
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
class Solution:
    def reorganizeString(self, s: str) -> str:
        dic=Counter(s)
        heap=[[-count,char] for char,count in dic.items()]
        heapq.heapify(heap)
        prev,output=None,""
        while prev or heap:
            if prev and not heap:
                return ""
            count,char=heapq.heappop(heap)
            count+=1
            output+=char
            if prev:
                heapq.heappush(heap,prev)
                prev=None
            if count!=0:
                prev=[count,char]
        return output
```
---
