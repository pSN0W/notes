# 🧩 Que
- [Link](https://leetcode.com/problems/roman-to-integer/)
You are given a roman numeral convert it to integer
```ad-question
title: Test Case
**Input:** s = "LVIII"
**Output:** 58
**Explanation:** L = 50, V= 5, III = 3.
```

---
# Abstract
```ad-abstract
In roman numeral if a if a number with lower value comes before higher then you will have to subtract it. Will be good to iterate it backwards.
IV -> 5 and then -1 = 4
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Iterate the array backwards
- If you are following the order from lower to higher and then sum it otherwise subtract it.
- VI -> 1 + 5 from backward lower to higher
- IV -> 5 - 1 from backward higher then lower.
- So multiply -1 with the current i if i+1 is greater then i

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def build_dict(self):
        self.dict = {
            'I' : 1,
            'V' : 5,
            'X' : 10,
            'L' : 50,
            'C' : 100,
            'D' : 500,
            'M' : 1000
        }
    def romanToInt(self, s: str) -> int:
        self.build_dict()
        ans = self.dict[s[-1]]
        for i in range(len(s)-2,-1,-1):
            sign = 1 if self.dict[s[i]] >= self.dict[s[i+1]] else -1
            ans += sign*self.dict[s[i]]
        return ans
```
---
