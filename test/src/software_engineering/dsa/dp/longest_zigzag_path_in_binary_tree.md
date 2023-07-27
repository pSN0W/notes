# 🧩 Que
- [Link](https://leetcode.com/problems/longest-zigzag-path-in-a-binary-tree/)
You are given a binary tree find the longest zig zag path in the tree.
```ad-question
title: Test Case
![[Pasted image 20230714140253.png]]
```

---
# Abstract
```ad-abstract
The idea is very similar to [[house_robber_iii]] where instead of finding the path you came from you just return a pair of solution from left and solution from right.
```
[[house_robber_iii]]
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
class Solution:
    def longestZigZag(self, root: Optional[TreeNode]) -> int:
        self.ans = 0
        def solve(node):
            if node is None:
                return (0,0)
            lft_lft,lft_rt = solve(node.left)
            rt_lft, rt_rt = solve(node.right)
            self.ans = max([self.ans,lft_rt+1, rt_lft+1])
            return 1+lft_rt,1+rt_lft
        solve(root)
        return self.ans - 1
```
---
