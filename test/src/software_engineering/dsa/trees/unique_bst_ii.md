# 🧩 Que
- [Link](https://leetcode.com/problems/unique-binary-search-trees-ii/)
Given an integer `n`, return _all the structurally unique **BST's** (binary search trees), which has exactly_ `n` _nodes of unique values from_ `1` _to_ `n`. Return the answer in **any order**.
```ad-question
title: Test Case
![[Pasted image 20230708173513.png]]
```

---
# Abstract
```ad-abstract
The idea is to recursively build the tree
```

- Tags 
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
    def generateTrees(self, n: int) -> List[Optional[TreeNode]]:
        def solve(i,j):
            if i>j:
                return [None]
            heads = []
            for k in range(i,j+1):
                lft = solve(i,k-1)
                rt = solve(k+1,j)
                for l in lft:
                    for r in rt:
                        root = TreeNode(k)
                        root.left = l
                        root.right = r
                        heads.append(root)
            return heads
        
        return solve(1,n)
```
---
