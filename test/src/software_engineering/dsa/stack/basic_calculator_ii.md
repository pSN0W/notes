# 🧩 Que
- Link
Given a string s which contain `digits " " +-*/` evaluate it to return a number
```ad-question
title: Test Case
**Input:** s = "3+2*2"
**Output:** 7
```

---
# Abstract
```ad-abstract
The first order of business will be to convert seperate the numbers and operation that means "23+4/5" should be turned to [23,"+",4,"/",5].
The next thing that you will do is maintain a stack and iterate over the generated array. Wherever you find + or - add the number succeding it with appropriate sign. While when encontering * or / you must take the top element of the array and perform the operation. This is done for the order precedence.
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- To do the first part of accumulating numbers and operators:
	- Create a stack where you will put both of them and iterate on s:
		- If s is part of operator then add s to stack
		- If s is digit and top of stack is an operator then add the digit to the top of stack else ectract top of the stack multiply it with 10 and then add the current to it then add resulting to top if the stack
- The next thing you need to do is to evaluate this list. There are two precedence order here `(+,-) and (*,/)` We will perform the one with higher priority first and then the lower one
	- To do this create a stack
		- If you encounter a plus or minus operator then just add the number succeeding it with the appropriate sign
		- If you encounter multiply or divide take top of the stack and apply the operator then add the result to the stack
	- At the end just add the stack (you already have appropriate + or -)
---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution:
    def calculate(self, s: str) -> int:
        st = [0]
        sign = 1
        for ch in s:
            if ch == ' ':
                continue
            if ch in "+-*/":
                st.append(ch)
            else:
                if st and str(st[-1]) in "+-*/":
                    st.append(int(ch))
                else:
                    st.append(st.pop()*10+int(ch))
        stt = []
        i = 0
        while i < len(st):
            s = st[i]
            if s == "+":
                sign = 1
            elif s == "-":
                sign = -1
            elif s == "*":
                i += 1
                stt.append(stt.pop()*st[i])
            elif s=="/":
                i += 1
                stt.append(int(stt.pop()/st[i]))
            else:
                stt.append(sign*st[i])
            i += 1
        print(st,stt)
        return sum(stt)
```
---
