# 🧩 Que
- [Link](https://leetcode.com/problems/balanced-binary-tree/)
Given a binary tree check if it is height balanced
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You will have to check if the left tree, right tree and current tree are all height balanced. For height balanced ht_lft - ht_rt <= 1
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- [[]]
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
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        def solve(node):
            if node is None:
                return 0,True
            lt_ht,lt_balanced = solve(node.left)
            rt_ht,rt_balanced = solve(node.right)
            return max([lt_ht,rt_ht]) + 1, lt_balanced and rt_balanced and abs(rt_ht-lt_ht) < 2
        return solve(root)[1]
```
---
