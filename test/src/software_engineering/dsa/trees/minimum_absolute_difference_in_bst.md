# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-absolute-difference-in-bst/)
Given a bst find the MAD for the tree
```ad-question
title: Test Case
![[Pasted image 20230707192505.png]]
1
```

---
# Abstract
```ad-abstract
It uses a simple approach as [[diameter_of_binary_tree]]. You keep updating the answer while returning something. The idea here is that you will need to compare with the right most node of left subtree and leftmost node of right subtree. So for each subtreee you return these.
```
[[diameter_of_binary_tree]]
- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

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
    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        self.mad = float('inf')
        def solve(node):
            if node is None:
                return None,None
            lt_mn,lt = solve(node.left)
            rt,rt_mx = solve(node.right)
            if rt:
                self.mad = min([self.mad,abs(node.val-rt)])
            if lt:
                self.mad = min([self.mad,abs(node.val-lt)])
            return lt_mn or node.val, rt_mx or node.val
        solve(root)
        return self.mad

```
---
