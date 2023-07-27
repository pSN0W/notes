# 🧩 Que
- [Link](https://leetcode.com/problems/divisor-game/)
Alice and bob take turn playing a game with alice starting first. The player with no moves left loses. On each turn the player chooses a number x such that `1<x<n` and `n%x==0`. Return if Alice can win the game.
```ad-question
title: Test Case
**Input:** n = 2
**Output:** true
**Explanation:** Alice chooses 1, and Bob has no more moves.
```

---
# Abstract
```ad-abstract
If N is even Alice wins if N is odd alice loses. The base is that when there is 1 you loose. So if you are at 2 you can get it to 1 and win. Now if N is even then we can chose 1 and move it to odd. If N is odd then you will have to choose an odd number because of divisibility and then you move your opponent to even which is a winning position. So N will change alternatively until you reach 1
```

- Tags #unsolved #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
For N <= n, we have find that:  
If `N` is even, can win.  
If `N` is odd, will lose.

**For the case `N = n + 1`**  
**If `N` is even**, we can win choosing `x = 1`,  
give the opponent an odd number `N - 1 = n`,  
force him to lose,  
because we have found that all odd `N <= n` will lose.

**If `N` is odd**, there is no even `x` that `N % x == 0`.  
As a result, we give the opponent a even number `N - x`,  
and the opponent can win,  
because we have found that all even `N <= n` can win.

Now we prove that, for all `N <= n`,  
If `N` is even, can win.  
If `N` is odd, will lose.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def divisorGame(self, n: int) -> bool:
        return 1-n%2
        
```
---
