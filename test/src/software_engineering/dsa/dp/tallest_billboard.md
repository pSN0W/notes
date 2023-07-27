# 🧩 Que
- [Link](https://leetcode.com/problems/tallest-billboard/submissions/992546893/)
You are installing a billboard. It needs two rods of equal height. You are given rods which you can combine to make a big rod. Find the tallest billboard possible
```ad-question
title: Test Case
**Input:** rods = [1,2,3,4,5,6]
**Output:** 10
**Explanation:** We have two disjoint subsets {2,3,5} and {4,6}, which have the same sum = 10.
```

---
# Abstract
```ad-abstract
The idea is pretty simple for each rod you have three options
- Add it to left side one
- Add it to right side one
- Skip it.
How do you solve it in O(nm) now
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- You are only interested in the rods being of equal height. so you can maintain a variable curr for current distance between the two rods
	- For adding a rod you can increase the curr by current rod height and in turn your rod height will increase by arr[i] too
	- For adding to the other one you can just delete for the current one too
	- Skip to skip
- For base case you can just check that the current difference is 0 when the index is out of range

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def tallestBillboard(self, rods: List[int]) -> int:
        @lru_cache(None)
        def solve(idx,curr):
            if idx>=len(rods):
                return 0 if curr==0 else int(1e6)*-1
            # take current rod
            ans1 = rods[idx] + solve(idx+1,curr+rods[idx])
            # give it to ther one
            ans2 = solve(idx+1,curr-rods[idx])
            # skip the current rod
            ans3 = solve(idx+1,curr)
            return max([ans1,ans2,ans3]) 
        return max([solve(0,0),0])
```
---
