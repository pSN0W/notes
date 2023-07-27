# 🧩 Que
- [Link](https://leetcode.com/problems/wildcard-matching/?envType=list&envId=50wroh7h)
Given an input string (`s`) and a pattern (`p`), implement wildcard pattern matching with support for `'?'` and `'*'` where:

- `'?'` Matches any single character.
- `'*'` Matches any sequence of characters (including the empty sequence).
```ad-question
title: Test Case
**Input:** s = "aa", p = "*"
**Output:** true
**Explanation:** '*' matches any sequence.
```

---
# Abstract
```ad-abstract
It is very similar to [[regex_matching]]
```
[[regex_matching]]
- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- You forgot the if i>=0 part in `if i>=0: ans = ans or solve(i-1,j) # skip current` which caused the recursion to not reach base case for test cases like `c*a*b` matched with `aab`
---

# 💻 Code
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        def is_match(i,j):
            if i<0:
                return p[j] == "*"
            return s[i]==p[j] or p[j] in "?*"
        @lru_cache(None)
        def solve(i,j):
            if i<0 and j<0:
                return True
            if j<0:
                return False
            if i<0 and p[j]!="*":
                return False
            ans = False
            if is_match(i,j):
                if p[j] == "*":
                    ans = ans or solve(i,j-1) #skip *
                    if i>=0:    
                        ans = ans or solve(i-1,j) # skip current
                else:
                    ans = solve(i-1,j-1)
            return ans
        return solve(len(s)-1,len(p)-1)
```
---
