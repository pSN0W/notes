# 🧩 Que
- [Link](https://www.interviewbit.com/problems/word-search-board/)
Given a 2D board and a word, find if the word exists in the grid.
```ad-question
title: Test Case
Given board =

[
  ["ABCE"],
  ["SFCS"],
  ["ADEE"]
]
word = "ABCCED", -> returns 1,
```

---
# Abstract
```ad-abstract
The idea is pretty simple you start a dfs call from all the places where and then memoise the i,j and idx at that point to remove repeated computation. This reminds me of a question where there were multiple words to match and there your dfs was guided by a trie.
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
from functools import lru_cache
class Solution:
    # @param A : list of strings
    # @param B : string
    # @return an integer
    def exist(self, A, B):
        n,m = len(A),len(A[0])
        def inbound(i,j,idx):
            return i>=0 and j>=0 and i<n and j<m and (idx>=len(B) or A[i][j] == B[idx])
        
        @lru_cache(None)
        def solve(i,j,idx):
            if idx >= len(B):
                return True
            ans = False
            if inbound(i-1,j,idx+1):
                ans = ans | solve(i-1,j,idx+1)
            if inbound(i+1,j,idx+1):
                ans = ans | solve(i+1,j,idx+1)
            if inbound(i,j+1,idx+1):
                ans = ans | solve(i,j+1,idx+1)
            if inbound(i,j-1,idx+1):
                ans = ans | solve(i,j-1,idx+1)
            return ans
        for i in range(n):
            for j in range(m):
                if A[i][j] == B[0]:
                    if solve(i,j,0):
                        return 1
        return 0
```
---
