# 🧩 Que
- [Link](https://leetcode.com/problems/validate-binary-search-tree/)
Given a binary tree check if it is BST or not
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
Its combination of [[minimum_absolute_difference_in_bst]] -> Use this for traversal and [[height_balanced_tree]] for returning and manipulating the values
```
[[minimum_absolute_difference_in_bst]] [[height_balanced_tree]]
- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- See Striver one too

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
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        
        def solve(node):
            if node is None:
                return None,None,True
            lt_min,lt_max,lt_bst = solve(node.left)
            rt_min,rt_max,rt_bst = solve(node.right)
            valid = lt_bst and rt_bst
            if lt_max is not None:
                valid = valid and  (lt_max < node.val)
            if rt_min is not None:
                valid = valid and (rt_min > node.val)
            return lt_min or node.val, rt_max or node.val, valid
        return solve(root)[-1]
```
---
