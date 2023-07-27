# 🧩 Que
- [Link](https://leetcode.com/problems/basic-calculator/)
You have to evaluate a string. The string can contain `+-() ` and digits
```ad-question
title: Test Case
**Input:** s = "(1+(4+5+2)-3)+(6+8)"
**Output:** 23
```

---
# Abstract
```ad-abstract
You can use recursion to evaluate the string. Wherever you find a ( just call the recursive function to evaluate the content inside the bracket
```

- Tags #unsolved #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- evaluate(i) -> solution of substring i to the first closing bracket found.
- Look at code its easy

---
# ☠️ My thought process
- You used your naive approach as [[basic_calculator_ii]] but you got stuck with case like `1-(-2)`
---

# 💻 Code
```python
class Solution:
    def calculate(self, s):
        def evaluate(i):
            res, digit, sign = 0, 0, 1
            
            while i < len(s):
                if s[i].isdigit():
                    digit = digit * 10 + int(s[i])
                elif s[i] in '+-':
                    res += digit * sign
                    digit = 0
                    sign = 1 if s[i] == '+' else -1
                elif s[i] == '(':
                    subres, i = evaluate(i+1)
                    res += sign * subres
                elif s[i] == ')':
                    res += digit * sign
                    return res, i
                i += 1

            return res + digit * sign
        
        return evaluate(0)
```
---
