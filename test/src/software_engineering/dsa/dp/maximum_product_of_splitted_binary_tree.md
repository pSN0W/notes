# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-product-of-splitted-binary-tree/?envType=list&envId=50v8rtm7)
Given the `root` of a binary tree, split the binary tree into two subtrees by removing one edge such that the product of the sums of the subtrees is maximized.

Return _the maximum product of the sums of the two subtrees_. Since the answer may be too large, return it **modulo** `109 + 7`.
```ad-question
title: Test Case
![[Pasted image 20230714134813.png]]
```

---
# Abstract
```ad-abstract
The idea is pretty simple you first calculate the total sum of a tree and then you make a recursion call where you calculate the sum of the subtrees and for each of the sum you update your answer as max([ans,subtree_sum*(tot-subtree_sum)])
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def tsum(root):
    if(root==None):
        return 0
    x= root.val+tsum(root.left)+tsum(root.right)
    return x
def fun(root,sm,mx):
    if(root==None):
        return 0
    a=fun(root.left,sm,mx)
    b=fun(root.right,sm,mx)
    mx[0]=max(mx[0],a*(sm-a),b*(sm-b))
    return a+b+root.val
    
class Solution:
    def maxProduct(self, root: Optional[TreeNode]) -> int:
        mx=[0]
        sm=tsum(root)
        memo={}
        fun(root,sm,mx)
        return mx[0]%(10**9+7)
```
---
