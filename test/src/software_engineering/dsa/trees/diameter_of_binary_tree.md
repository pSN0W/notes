# 🧩 Que
- [Link](https://leetcode.com/problems/diameter-of-binary-tree/)
The **diameter** of a binary tree is the **length** of the longest path between any two nodes in a tree.
```ad-question
title: Test Case
**Input:** root = [1,2,3,4,5]
**Output:** 3
**Explanation:** 3 is the length of the path [4,2,1,3] or [5,2,1,3].
```

---
# Abstract
```ad-abstract
The idea is to have a global variable for max and update it while returning the height of the binary tree from the function
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Any of the node can create the diameter so at each node try to update and with height of left tree, height of right tree plus 1

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
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.ans = 0
        def solve(node):
            if node is None:
                return 0
            lft = solve(node.left)
            rt = solve(node.right)
            self.ans = max([self.ans,lft+rt+1])
            return max([lft,rt])+1
        solve(root)
        return self.ans - 1
```
---
