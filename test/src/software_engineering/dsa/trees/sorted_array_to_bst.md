# 🧩 Que
- [Link](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)
Given a sorted array convert it to height balanced bst
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is to first decide the root of the bst and then recursively build the bst. For a height balanced you must choose the middle element.
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
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        def gen(i,j):
            if i>j:
                return None
            m = (i+j)//2
            node = TreeNode(nums[m])
            node.left = gen(i,m-1)
            node.right = gen(m+1,j)
            return node
        return gen(0,len(nums)-1)
```
---
