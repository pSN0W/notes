# 🧩 Que
- Link

```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You first take the current node then go to its left and then right.
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
# recursion
def preorder(root):
  return [root.val] + preorder(root.left) + preorder(root.right) if root else []

# with stack
class Solution:
	# @param A : root node of tree
	# @return a list of integers
	def preorderTraversal(self, A):
        node,stack,ans = A,list(),list()
        while node or stack:
            if node:
                ans.append(node.val)
                stack.append(node.right)
                node = node.left
            else:
                node = stack.pop()
        return ans
```
---
