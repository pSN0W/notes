# 🧩 Que
- [Link](https://leetcode.com/problems/binary-tree-cameras/)
You are given the `root` of a binary tree. We install cameras on the tree nodes where each camera at a node can monitor its parent, itself, and its immediate children.

Return _the minimum number of cameras needed to monitor all nodes of the tree_.
```ad-question
title: Test Case
![[Pasted image 20230709135407.png]]
```

---
# Abstract
```ad-abstract
The idea is to do a greedy dfs traversal. and choose the best place to keep the camera
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- You can place a camera at the following places
	- If you place at root it will cover itself,left and right child
	- If you place at leave it will cover itself and parent
	- If you place at any other node that it will cover parent itself and its two children
- Now the idea is to greedily place a camera on the parent of a leaf and then remove all the nodes covered by the camera and repeat this process.
- For this we use 3 variables
	- **covered** : The node is covered
	- **to_be_covered**: Its parent of the covered nodes and a camera can be set on its parent to cover it
	- **covering**: This is where you set the camera. it will cover both its children and parent
- The way traversal will happen
- ![[Pasted image 20230709140515.png]]
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def minCameraCover(self, root: TreeNode) -> int:
        self.res = 0
        def dfs(node):
            if node is None:
                return 'covered'
            l, r = dfs(node.left), dfs(node.right)
            if l==r=='covered':
                return 'to_be_covered'
            if l=='to_be_covered' or r=='to_be_covered':
                self.res += 1
                return 'covering'
            if l=='covering' or r=='covering':
                return 'covered'
        return (dfs(root)=='to_be_covered') + self.res
```
---
