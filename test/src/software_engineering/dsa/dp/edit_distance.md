# 🧩 Que
- [Link](https://leetcode.com/problems/edit-distance/)
Given two string word1 and word2 return the minimum number of operation to convert word1 to word2. You are permitted to do the following
- Insert a character
- Delete a character
- Replace a character
```ad-question
title: Test Case
**Input:** word1 = "intention", word2 = "execution"
**Output:** 5
**Explanation:** 
intention -> inention (remove 't')
inention -> enention (replace 'i' with 'e')
enention -> exention (replace 'n' with 'x')
exention -> exection (replace 'n' with 'c')
exection -> execution (insert 'u')
```

---
# Abstract
```ad-abstract
The idea is pretty simple if the two indexes matches then you can just go ahead to match the next two otherwise perform the given operations and return the minimum.
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- dp[i][j] represents minimum edit distance between word1[:i] and word2[:j].
- if word1[i] == word2[j] -> dp[i][j] = dp[i-1][j-1]
- else it will be minimum of
	- dp[i-1][j] // delete a character
	- dp[i][j-1] // insert a character
	- dp[i-1][j-1] // replace a character

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def minDistance(self, word1: str, word2: str) -> int:
        @lru_cache(None)
        def solve(i,j):
            if i<0 or j<0:
                return max([i+1,j+1,0])
            if word1[i] == word2[j]:
                return solve(i-1,j-1)
            else:
                return 1 + min([solve(i,j-1),solve(i-1,j),solve(i-1,j-1)])
        #return solve(len(word1)-1,len(word2)-1)
        n,m = len(word1),len(word2)
        dp = [[0]*(m+1) for _ in range(n+1)]
        for i in range(n+1):
            for j in range(m+1):
                if i==0:
                    dp[i][j] = j
                elif j==0:
                    dp[i][j] = i
                else:
                    if word1[i-1] == word2[j-1]:
                        dp[i][j] = dp[i-1][j-1]
                    else:
                        dp[i][j] = 1 + min([dp[i][j-1],dp[i-1][j],dp[i-1][j-1]])
        return dp[n][m]
```
---
