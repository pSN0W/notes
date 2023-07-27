# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/)
Given a **binary tree** `root`, return _the maximum sum of all keys of **any** sub-tree which is also a Binary Search Tree (BST)_.
```ad-question
title: Test Case
![[Pasted image 20230714194008.png]]
```

---
# Abstract
```ad-abstract
The idea is to do traversal like [[validate_bst]] to check if current is bst and then [[diameter_of_binary_tree]] to get the maximum answer
```
[[validate_bst]] [[diameter_of_binary_tree]]
- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Traverse and keep returning subtree_sum, subtree_is_bst, max_in_subtree and min_in_subtree. Wherever you find a bst update your answer

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def maxSumBST(self, root: Optional[TreeNode]) -> int:
        self.ans = 0
        def solve(node):
            if node is None:
                return 0,True,None,None
            lft_sum, is_lft_bin, lft_mn, lft_mx = solve(node.left)
            rt_sum, is_rt_bin, rt_mn, rt_mx = solve(node.right)
            is_bin = is_lft_bin and is_rt_bin
            if lft_mx is not None and lft_mx >= node.val:
                is_bin = False
            if rt_mn is not None and rt_mn <= node.val:
                is_bin = False
            if is_bin:
                self.ans = max([self.ans, lft_sum+rt_sum+node.val])
            if lft_mn is None:
                lft_mn = node.val
            if rt_mx is None:
                rt_mx = node.val
            return lft_sum+rt_sum+node.val, is_bin, lft_mn, rt_mx
        solve(root)
        return self.ans
```
---
