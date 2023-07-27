# 🧩 Que
- [Link](https://leetcode.com/problems/palindrome-partitioning/)
Given a string s partition it in such a way that every sub string is a palindrome.
```ad-question
title: Test Case
**Input:** s = "aab"
**Output:** [ ["a","a","b"],["aa","b"] ]
```

---
# Abstract
```ad-abstract
It is same as you have seen for questions like [[regex_matching]] where you find all the valid state from the current state and then apply dp on them. In this case we start with index 0 and for all the valid palindrome partition from a we see if a valid partition for others is possible too
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- f(i) -> valid partition from i to n
- To compute f(i) you will do the following
	- for j in [i...n]
		- if s[i:j] is palindrome and f(j) also has a valid one then that can be your one such partition


---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        sol = []
        n = len(s)
        def is_palindrome(st):
            return st == st[::-1]
        def solve(idx,curr):
            if idx>=n:
                sol.append(curr.copy())
                return
            for i in range(idx+1,n+1):
                if is_palindrome(s[idx:i]):
                    curr.append(s[idx:i])
                    solve(i,curr)
                    curr.pop()
        solve(0,[])
        return sol
```
---
