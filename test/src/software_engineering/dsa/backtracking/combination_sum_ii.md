# 🧩 Que
-[Link](https://leetcode.com/problems/combination-sum-ii/)
Given a collection of candidate number and an integer target. Find all unique combination in candidate that can sum upto target. Each number in the candidate must be used only once.
```ad-question
title: Test Case
**Input:** candidates = [10,1,2,7,6,1,5], target = 8
**Output:** 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

---
# Abstract
```ad-abstract
The idea is basically a combination of [[combination_sum_backtracking]] and [[subset_ii]]. If you choose to skip an element than skip it throughout the subtree. In subset_ii you had an array for this but here since order doesn't matter you can sort it and skip all the element with the same value altogether.

```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- The logic will be same you can choose a number or you can leave it.
- If you leave a number in a subtree then make sure that same number at different element does not get chosen in that subset.
- To do this you can sort the array and if you are skipping an element skip all with the same value.
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        ans = []
        candidates.sort()
        def solve(idx,curr,curr_sum):
            if curr_sum == target:
                ans.append(curr.copy())
                return
            if curr_sum > target or idx>=len(candidates):
                return
            # choose current one
            curr.append(candidates[idx])
            solve(idx+1,curr,curr_sum+candidates[idx])
            curr.pop()
            # skip the current element
            i = idx
            while i<len(candidates) and candidates[i] == candidates[idx]:
                i += 1
            solve(i,curr,curr_sum)
        solve(0,[],0)
        return ans
```
---
