# 🧩 Que
- [Link](https://leetcode.com/problems/stone-game-iii/)
Alice and Bob play a game. On each player turn he can take 1/2/3 stone from beginning. Th e player with the most stone value wins. Alice starts first determine who wins 
```ad-question
title: Test Case
**Input:** stoneValue = [1,2,3,7]
**Output:** "Bob"
**Explanation:** Alice will always lose. Her best move will be to take three piles and the score become 6. Now the score of Bob is 7 and Bob wins.
```

---
# Abstract
```ad-abstract
This is a classic question where you calculate the answer for only one participant. If we consider Alice than he will choose stone in such a way that their sum is maximum while Bob will choose it in such a way that alice gets minimum. Also beware that the stone value only get summed for the case of Alice.
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Consider only one player. Determine what will be the value that Alice can attain if both the players play optimally.
- You reduce your problem to solve for only one participant. For that problem:
	- Alice will choose stones in such a way that his sum become maximum
	- Bob will choose in such a way that Alice's sum is minimum and the stone chosen by him will contribute nothing to the value of Alice
- Once you have for Alice you can find Bob's by simply doing sum(stone) - Alice

---
# ☠️ My thought process
- You made the mistake of adding to sum when bobs turn too.
---

# 💻 Code
```python
class Solution:
    def stoneGameIII(self, stone: List[int]) -> str:
        def get(idx,i):
            return sum(stone[idx:min(i,len(stone))])
        @lru_cache(None)
        def solve(idx,alice):
            if idx>=len(stone):
                return 0
            poss =[solve(i,not alice)+(get(idx,i) if alice else 0) for i in range(idx+1,idx+4)]
            return max(poss) if alice else min(poss)
        al = solve(0,True)
        bob = sum(stone) - al
        ans = {
            True: "Alice",
            False: "Bob"
        }
        return "Tie" if al==bob else ans[al>bob]
```
---
