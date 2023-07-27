# 🧩 Que
- [Link](https://leetcode.com/problems/path-sum-iii/)
Given a binary tree find total number of path is bst with given target sum
```ad-question
title: Test Case
![[Pasted image 20230708141626.png]]
```

---
# Abstract
```ad-abstract
The idea is to maintain a map for all the sum found when iterating on a branch of the bst. Whenever you reach a node just find out how much times curr_sum - target_sum appeared in tree before
```

- Tags #unsolved #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- For an easier explanation you can think of each branch as a array and you calculate prefix sum of the array and to find how many have target sum that ends at current index just find number of curr_sum - target.
- ![[Pasted image 20230708142035.png]]
- You will have to do this for all the beanch

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> int:
        self.ans = 0
        def traverse(node,curr_sum,mp):
            if node is None:
                return
            #print(node.val,mp,curr_sum)
            curr_sum += node.val
            if curr_sum - targetSum in mp:
                self.ans += mp[curr_sum - targetSum]
            mp.setdefault(curr_sum,0)
            mp[curr_sum] += 1
            traverse(node.left,curr_sum,mp)
            traverse(node.right,curr_sum,mp)
            mp[curr_sum] -= 1
        mp = {
            0: 1
        }
        traverse(root,0,mp)
        return self.ans

```
---
