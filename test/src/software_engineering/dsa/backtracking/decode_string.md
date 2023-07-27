# 🧩 Que
- [Link](https://leetcode.com/problems/decode-string/)
Given an encoding string return its decoded string 
The encoding rule is: `k[encoded_string]`, where the `encoded_string` inside the square brackets is being repeated exactly `k` times. Note that `k` is guaranteed to be a positive integer.
```ad-question
title: Test Case
**Input:** s = "3[a2[c]]"
**Output:** "accaccacc"
```

---
# Abstract
```ad-abstract
The question is very similar to basic calculator. You use recursion to solve just for just one `[]` and whenever you get a new `[` you call the recursive function again
```
[[basic_calculator]]
- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- solve(i) -> decodes the string starting form i and returns (decoded_string,index till decoded)
- Inside solve(i) you want to solve for every operations that are at same level
	- Iterate through the array
	- collect digits and your current string
	- Whenever you find a `[` call the function again and the attach it with current string after multiplying it by the digits
	- Upon finding `]` return what you have generated

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def decodeString(self, s: str) -> str:
        def solve(i):
            if i>=len(s):
                return "",i
            dig = 0
            curr_st = ""
            while i<len(s):
                if s[i].isdigit():
                    dig = dig*10 + int(s[i])
                    i+=1
                elif s[i] == '[':
                    ret_st,i = solve(i+1)
                    curr_st = curr_st + ret_st*max(dig,1)
                    dig = 0
                elif s[i] == ']':
                    return curr_st,i+1
                else:
                    curr_st = curr_st + s[i]
                    i+=1
            return curr_st,i
        return solve(0)[0]
        
```
---
