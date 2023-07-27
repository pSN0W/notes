# 🧩 Que
- [Link](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/)
You are given a tree and a target node you have to find out all the nodes at distance k from the target node
```ad-question
title: Test Case
![[Pasted image 20230708133728.png]]
```

---
# Abstract
```ad-abstract
The idea is to use a hash map to store the parents node and then from the target node you iterate to all directions [left,right,parent] and find node at distance k
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Use dfs traversal to store the parent nodes.
- Traverse starting from the target now. Use par to keep track of where you are coming from. Look at code

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def distanceK(self, root: TreeNode, target: TreeNode, k: int) -> List[int]:
        parent = {}
        dist_k = []
        def create_parent(node,par):
            if node is None:
                return
            parent[node] = par
            create_parent(node.left,node)
            create_parent(node.right,node)
        
        def getAtDistK(node,par,dist):
            if node is None or dist<0:
                return
            if dist == 0:
                dist_k.append(node.val)
                return
            if parent[node] is not par:
                getAtDistK(parent[node],node,dist-1)
            if node.left is not par:
                getAtDistK(node.left,node,dist-1)
            if node.right is not par:
                getAtDistK(node.right,node,dist-1)
        create_parent(root,None)
        getAtDistK(target,None,k)
        return dist_k
```
---
