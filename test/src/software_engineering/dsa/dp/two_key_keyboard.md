# 🧩 Que
- [Link](https://leetcode.com/problems/2-keys-keyboard/)
There is only one character `'A'` on the screen of a notepad. You can perform one of two operations on this notepad for each step:

- Copy All: You can copy all the characters present on the screen (a partial copy is not allowed).
- Paste: You can paste the characters which are copied last time.
```ad-question
title: Test Case
**Input:** n = 3
**Output:** 3
**Explanation:** Initially, we have one character 'A'.
In step 1, we use Copy All operation.
In step 2, we use Paste operation to get 'AA'.
In step 3, we use Paste operation to get 'AAA'.
```

---
# Abstract
```ad-abstract
solve(i) denotes the number of iteration it will take to generate n a if you copy i A's
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Copying multiple time doesn't make sense
- For each i copy once and then paste it 1, 2 or ... times
- In solve you add i because 1 copy op and i-1 paste op

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def minSteps(self, n: int) -> int:
        @lru_cache(None)
        def solve(idx):
            if idx == n:
                return 0
            # paste
            i = 2
            ans = int(1e6)
            while idx*i <= n:
                ans = min([ans,solve(i*idx)+i])
                i+=1
            return ans
        return solve(1)
```
---
