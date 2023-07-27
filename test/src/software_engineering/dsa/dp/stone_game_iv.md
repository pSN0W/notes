# 🧩 Que
- [Link](https://leetcode.com/problems/stone-game-iv)
There are n stones in a bag and Alice and Bob take turn removing **squared number** stones from the bag. The person who is left with no moves loses. Alice starts first
```ad-question
title: Test Case
**Input:** n = 1
**Output:** true
**Explanation:** Alice can remove 1 stone winning the game because Bob doesn't have any moves.
```

---
# Abstract
```ad-abstract
This is just a smiple problem. Consider all the possible path you can have at a state and if it leads to any state that Bob loses then Alice will win.
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- If you are at i. You can make moves `1...j* j<=i` If any of the moves you can send to a loosing state than the current state is the winning one.
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def winnerSquareGame(self, n: int) -> bool:
        dp = [False]*(n+1)
        for i in range(1,n+1):
            j = 1
            while j*j <= i:
                dp[i] = dp[i] | ~dp[i-j*j]
                j += 1
        return dp[n]
```
---
