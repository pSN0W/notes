# 🧩 Que
- [Link](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)
Given root of a binary tree, flatten it
```ad-question
title: Test Case
![[Pasted image 20230708162210.png]]
```

---
# Abstract
```ad-abstract
It looks pretty easy. You solve left you solve right and then you join it. You will have to consider all the cases and better to return both head and tail to facilitate the join operation
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- You have the following 4 cases
- ![[Pasted image 20230708162550.png]]
- For Case 1 head and tail both will be the node.
- For 2 and 3. Solve the non null part and the node->right = head and return node,tail of the solved part
- When both are there you will need to first flatten both the tree then tail of left must point to head of right and node.right = left head and you can return node and right tail.

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
    def flatten(self, root: Optional[TreeNode]) -> None:
        """
        Do not return anything, modify root in-place instead.
        """
        def solve(node):
            if node.left == node.right == None:
                return node,node
            if node.left is None or node.right is None:
                h,t = solve(node.left or node.right)
                node.left = None
                node.right = h
                t.right = None
                return node,t
            h_l,t_l = solve(node.left)
            h_r,t_r = solve(node.right)
            t_l.right = h_r
            node.right = h_l
            node.left = None
            return node, t_r
        if root:
            solve(root)
```
---
