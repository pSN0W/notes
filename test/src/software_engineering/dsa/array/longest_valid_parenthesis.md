# 🧩 Que
- [Link](https://leetcode.com/problems/longest-valid-parentheses/)
Given a string containing just `(` and `)` return the length of the longest valid parenthesis
```ad-question
title: Test Case
**Input:** s = "(()"
**Output:** 2
**Explanation:** The longest valid parentheses substring is "()".
```

---
# Abstract
```ad-abstract
Since its a valid paranthesis problem you will use stack. Consider the largest subarray for the current index i. You will need to keep track of the last index which is making the current one invalid
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Keep the index of the last character that is causing the invalid parenthesis. Do this for all the index.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        sol = 0
        st = []
        for i,ch in enumerate(s):
            if ch == ")" and st and s[st[-1]] == "(":
                st.pop()
                sol = max([sol,i - (st[-1] if st else -1)])
            else:
                st.append(i)
        return sol
```
---
