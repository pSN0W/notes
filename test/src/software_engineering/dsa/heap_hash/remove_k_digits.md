# 🧩 Que
- [Link](https://leetcode.com/problems/remove-k-digits)
Given string num representing a non-negative integer `num`, and an integer `k`, return _the smallest possible integer after removing_ `k` _digits from_ `num`.
```ad-question
title: Test Case
**Input:** num = "1432219", k = 3
**Output:** "1219"
**Explanation:** Remove the three digits 4, 3, and 2 to form the new number 1219 which is the smallest.
```

---
# Abstract
```ad-abstract
The idea is pretty simple for each index does it make sense to remove it. You can reamove a msb index if you can bring something smaller at its place there. You can use a monotonic stack to decide this
```

- Tags #unsolved #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Use a monotonic stack to get the index of the next smaller integer for each index.
- Iterate over the index and see if it makes sense to drop that index. That means drop it if you can get the next smaller with k removal

---
# ☠️ My thought process
- You thought it with time. But you didn't think of test case like this "9" k=1. Here next smaller for 9 is -1 so you don't remove it. solved by `if k: ans = ans[:-k]`
---

# 💻 Code
```python
class Solution:
    def removeKdigits(self, num: str, k: int) -> str:
        st = []
        n = len(num)
        nxt_smaller = [-1]*n
        for i in range(n-1,-1,-1):
            while st and num[st[-1]] >= num[i]:
                st.pop()
            if st:
                nxt_smaller[i] = st[-1]
            st.append(i)
        left = [False]*n
        i = 0
        while i<n:
            poss = nxt_smaller[i]
            if poss == -1 or poss-i>k:
                i+=1
                continue
            while i<poss:
                left[i] = True
                i+=1
                k-=1
            if k==0:
                break
        ans = ""
        for ch,val in zip(num,left):
            if val == False:
                ans += ch
        if k:
            ans = ans[:-k]
        ans = ans.lstrip("0")
        return ans if ans else "0"
```
---
