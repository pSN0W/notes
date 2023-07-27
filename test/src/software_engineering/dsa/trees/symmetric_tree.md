# 🧩 Que
- [Link](https://leetcode.com/problems/symmetric-tree/)
Given a tree check if it is symmetric from the middle
```ad-question
title: Test Case
![[Pasted image 20230707185339.png]]
True
```

---
# Abstract
```ad-abstract
Earlier you use to solve these question by level order traversal but now you have figured it out so proud of you
```

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
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def compare(node1,node2):
            if node1 == node2 == None:
                return True
            if node1 is None or node2 is None:
                return False
            return node1.val == node2.val and compare(node1.left,node2.right) and compare(node1.right,node2.left)
        return compare(root.left,root.right) if root else True
```
---
