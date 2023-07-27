# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-length-of-pair-chain/)
You are given an array of n pairs. A pair `p2 = [c, d]` **follows** a pair `p1 = [a, b]` if `b < c`. A **chain** of pairs can be formed in this fashion.
Return _the length longest chain which can be formed_.
```ad-question
title: Test Case
**Input:** pairs = [ [1,2],[2,3],[3,4] ]
**Output:** 2
**Explanation:** The longest chain is [1,2] -> [3,4].
```

---
# Abstract
```ad-abstract
For a pair c<d. First sort the pair. Sorting ensures that if an index i follows index j then it will follow all the pairs after index j too. Now you can use a similar idea to [[jump_game_2]]. And you can greedily find the minimum pais[1] for each jump and this will ensure that you get the maximum number of chains
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Sort the array using left and then right.
- If you want to achieve the maximum length then for new pair you choose to join to your chain try to minimise its right part.
- You iterate through the array you add a new pair to the chain if the left value of new pair is greater then right value of the chain. Else you try to replace the last pair in current chain with a new pair with lower right value.
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def findLongestChain(self, pairs: List[List[int]]) -> int:
        pairs.sort()
        curr_lim = pairs[0][1]
        ans = 1
        for x,y in pairs:
            if x > curr_lim:
                ans+=1
                curr_lim=y
            else:
                curr_lim = min([y,curr_lim])
        return ans
```
---
