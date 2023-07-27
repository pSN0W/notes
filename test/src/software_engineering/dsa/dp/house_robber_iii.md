# 🧩 Que
- [Link](https://leetcode.com/problems/house-robber-iii/?envType=list&envId=50v8rtm7)
Given a tree a thief can not rob adjacent nodes. Return the max money he can make
```ad-question
title: Test Case
![[Pasted image 20230714130253.png]]
```

---
# Abstract
```ad-abstract
The idea is really simple you can either rob the current house or you don't. You used a variable can_rob to tackle this but a more optimised version will be to return a pair of max you can make with robbing that house or without robbing
```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- solve(root) returns pair< max you can make without robbing this, max you can make with robbing this >
- You call your children to get the same.
- The max you can make without robbing is max(Left) + max(Right)
- The max you can make with robbing current is curr.val + Left[0] + Right[0]

---
# ☠️ My thought process
- You had a basic idea of calling root with can rob or not which takes more space and has more number of calls
```python
class Solution:
    def rob(self, root: Optional[TreeNode]) -> int:
        @lru_cache(None)
        def solve(node,can_rob):
            if node is None:
                return 0
            return max([
                solve(node.left,True) + solve(node.right,True),
                solve(node.left,False) + solve(node.right,False) + node.val if can_rob else 0
            ])
        return solve(root,True)
```
---

# 💻 Code
```python
class Solution:
    def rob(self, root):
        def dfs(root):
            if not root: return (0, 0)
            L, R = dfs(root.left), dfs(root.right)
            return (max(L) + max(R), root.val + L[0] + R[0])
        return max(dfs(root))
```
---
