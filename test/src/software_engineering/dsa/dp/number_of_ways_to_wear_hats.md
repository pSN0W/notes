# 🧩 Que
- [Link](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/)
There are `n`  n<10 people and `40` types of hats labeled from `1` to `40`. Given a 2D integer array `hats`, where `hats[i]` is a list of all hats preferred by the `ith` person. Return _the number of ways that the `n` people wear different hats to each other_.
```ad-question
title: Test Case
**Input:** hats = [ [3,5,1],[3,5] ]
**Output:** 4
**Explanation:** There are 4 ways to choose hats:
(3,5), (5,3), (1,3) and (1,5)
```

---
# Abstract
```ad-abstract
The simple solution will be to check if a hat is assigned to a person or not and the create a bit mask for that, but then you will have to mask till 40 which is not possible. Instead if you mask on whether all the people have recieved hat or not you will only have to do till 10 bits. To do this you can create another of array of what people prefer hat i.
```

- Tags #unsolved  
--- 
# 🕵️‍♂️ Main Logic
- Convert the hats array to a new array where hp[i] contains all the people that prefer hat[i].
- Now you can index on the hat and then you can choose to give then hat to no one or one of the unassigned person.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def numberWays(self, hats: List[List[int]]) -> int:
        hp = [[] for _ in range(41)]
        for i,available_hat in enumerate(hats):
            for hat in available_hat:
                hp[hat].append(i)
        n = len(hats)
        @cache
        def solve(i, mask):
            if mask == 0:
                return 1
            if i>40:
                return 0
            # skip the current hat
            ans = solve(i+1, mask)
            # give the current hat to one of the person 
            for per in hp[i]:
                if mask&(1<<per):
                    ans += solve(i+1, mask^(1<<per))
            return ans
        return solve(0, (1<<n)-1) % int(1e9+7)
```
---
