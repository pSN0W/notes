# 🧩 Que
- [Link](https://leetcode.com/problems/combination-sum/)
You are given an array you can use any element desired number of time to generate the target sum.

```ad-question
title: Test Case
**Input:** candidates = [2,3,6,7], target = 7
**Output:** [ [2,2,3], [7] ]
**Explanation:**
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.

```

---
```ad-abstract
This type of question is same as one you have previously solved. You first find number of ways to generate 1 and then use it to generate 2. respectively. Here you can also store all the parents to give final output. You use index of the array to avoid duplicate
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Store the parent of the array that can be used to generate the output

---
# ☠️ My thought process
- 
---

# 💻 Code

---
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