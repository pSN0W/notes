# 🧩 Que
- [Link](https://leetcode.com/problems/permutations-ii/)
You are given an array of integers which contain duplicates. You need to return the unique pwermutations.
```ad-question
title: Test Case
**Input:** nums = [1,1,2]
**Output:**
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

---
# Abstract
```ad-abstract
You can't use the swapping technique like [[permutation]] here because it will reusult in duplicates. What you will need to do is maintain a counter of unique value and at each level of tree you add a unique node. That means for array [1,1,2]. You can have it as hash map
1 -> 2, 2 -> 1. And since you only have 2 unique numbers the first element of the array can be any one of them only
```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- If you do swaps you will always have duplicates. [1,1,2] -> [ [1,1,2], [1,1,2], [2,1,1] ]. So swapping methods can not be adopted. What you can do is think of building the array. You first choose which index to put then what to put next. To remove duplicates what you do is that you say I won't put same number at an idx or at a depth of the tree.
- First you make a map of all the unique elements and then at each level of the tree you only add unique nodes.
![[Pasted image 20230630204307.png]]

---
# ☠️ My thought process
- Could do it with set.
- Tried swap when non equal that failed.
---

# 💻 Code
```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        results = []
        def backtrack(comb, counter):
            if len(comb) == len(nums):
                # make a deep copy of the resulting permutation,
                # since the permutation would be backtracked later.
                results.append(list(comb))
                return

            for num in counter:
                if counter[num] > 0:
                    # add this number into the current combination
                    comb.append(num)
                    counter[num] -= 1
                    # continue the exploration
                    backtrack(comb, counter)
                    # revert the choice for the next exploration
                    comb.pop()
                    counter[num] += 1

        backtrack([], Counter(nums))

        return results
```
---
