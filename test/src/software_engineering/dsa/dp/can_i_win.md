# 🧩 Que
- [Link](https://leetcode.com/problems/can-i-win/)
You are given a set of numbers that can be chosen and a target sum you start first and the first to reach or exceed target wins. Once you choose a number you can not choose that number again
```ad-question
title: Test Case
**Input:** maxChoosableInteger = 10, desiredTotal = 11
**Output:** false
**Explanation:**
No matter which integer the first player choose, the first player will lose.
The first player can choose an integer from 1 up to 10.
If the first player choose 1, the second player can only choose integers from 2 up to 10.
The second player will win by choosing 10 and get a total = 11, which is >= desiredTotal.
Same with other integers chosen by the first player, the second player will always win.
```

---
# Abstract
```ad-abstract
An ideal case for DP with bit masking. You can choose from a pool of allowed indexes denoted by the mask. You choose all the possible numbers and see if you can win. 
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Initially you compute curr_sum which basically tells the if the sum  has been reached by previous. If it has then you return false as the previous player already won.
- If for all the possible number you can choose a number that will result in loss of the next player then you automatically win.
- To keep track of all the numbers that has been chosen you can use a bit mask.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def canIWin(self, maxChoosableInteger: int, desiredTotal: int) -> bool:
        if desiredTotal == 0:
            return True
        if maxChoosableInteger*(maxChoosableInteger+1)//2 < desiredTotal:
            return False
        dp = [None]*(1<<maxChoosableInteger)
        def get_sum(mask):
            sm = 0
            for i in range(maxChoosableInteger):
                if (mask & (1<<i)) == 0:
                    sm += (i+1)
            return sm
    
        def solve(mask):
            curr_sum = get_sum(mask)
            if curr_sum >= desiredTotal:
                return False 
            if dp[mask] is not None:
                return dp[mask]
            poss = False
            for i in range(maxChoosableInteger):
                if (mask & (1<<i)):
                    poss = poss or not solve(mask^(1<<i))
            dp[mask] = poss
            return poss

        return solve((1<<maxChoosableInteger) - 1)
```
---
