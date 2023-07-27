# 🧩 Que
- Link

```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The whole thing is that you have to reach to the right node first
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def postorder(root):
  return  postorder(root.left) + postorder(root.right) + [root.val] if root else []

# stack
class Solution:
    # @param A : root node of tree
    # @return a list of integers
    def postorderTraversal(self, A):
        result = []; d = [A]
        while d:
            node = d.pop()
            if node:
                result.append(node.val)
                d.append(node.left)
                d.append(node.right)
        return result[::-1]
```
---
