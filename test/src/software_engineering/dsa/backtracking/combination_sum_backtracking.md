# 🧩 Que
- [Link](https://leetcode.com/problems/combination-sum/)
It's the same question as [[combination_sum]]. We will just use backtracking to solve this
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
At one step you can either choose the number at the current index or ignore it.You can repeat this process until you find the final sum.
```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- The thing to keep in find is that you want to avoid duplicates. So your tree should consider index at all cost. You can look at [[duplicates_and_non_duplicates]] for more detailed discussing about the discussion between the two.
- The idea is pretty simple you choose current index or you don't you run this tree unti you have all the possible combination

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
    
        def dfs(i, cur, total):
            if total == target:
                res.append(cur.copy())
                return
            if i >= len(candidates) or total > target:
                return
            
            cur.append(candidates[i])
            dfs(i, cur, total + candidates[i])
            cur.pop()
            dfs(i+1, cur, total)
            
        
        dfs(0, [], 0)     
        return res
```
---
