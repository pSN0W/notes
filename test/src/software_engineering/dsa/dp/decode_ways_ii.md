# 🧩 Que
- [Link](https://leetcode.com/problems/decode-ways-ii/)
The question is similar to [[decode_ways]]. You get an additional character "* ". Which can expand to [1,9]
```ad-question
title: Test Case
**Input:** s = "1*"
**Output:** 18
**Explanation:** The encoded message can represent any of the encoded messages "11", "12", "13", "14", "15", "16", "17", "18", or "19".
Each of these encoded messages have 2 ways to be decoded (e.g. "11" can be decoded to "AA" or "K").
Hence, there are a total of 9 * 2 = 18 ways to decode "1*".

```

---
# Abstract
```ad-abstract
The algo is very similar to [[decode_ways]]. The only case you need to consider is of "* ". If it is at current index then you can simply return 9*solve(idx+1). The main problem comes while comparing [idx:idx+2]. For this just consider the different cases dig,dig and dig,star and star,dig and star,star

```

- Tags #unsolved #revise 
--- 
# 🕵️‍♂️ Main Logic
- for dig,dig you can return 1 if the combination of 2 is <= 26 else 0
- for star,star you can return 15 as it will generate everything from [10,27] - {10,20}
- for star,dig you can return 1 or 2 depending on the dig. (star expanded to 1 or 2)
- for dig,star you can return 9 and 6 for dig == 1 and 2 respectively
- Cleaning things up and putting in function really helps see code

---
# ☠️ My thought process
- 
---

# 💻 Code

---
```python
class Solution:
    def numDecodings(self, s: str) -> int:
        def comp(i):
            if len(s) == i+1:
                return 0
            curr = s[i:i+2]
            if "*" not in curr:
                return int(curr < "27")
            elif curr == "**":
                return 15 # can't create 10, 20
            elif curr[0] == "*":
                return 1 + int(curr[1]<"7")
            elif curr[0]>"2":
                return 0
            else:
                return 9 if curr[0] == "1" else 6
        def solve(idx):
            if idx>=len(s):
                return 1
            if s[idx] == "0":
                return 0
            return (9 if s[idx]=="*" else 1)*solve(idx+1) + comp(idx)*solve(idx+2)
        return solve(0) % int(1e9+7)
```