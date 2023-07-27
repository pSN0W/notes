# 🧩 Que
- Link
Perform inorder traversal of a tree
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is to first go the left element then look at the current element and then finally to the right element.
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- You can solve it with stack too. For each node first put all its left node in a stack if you are left with no node then take one from the top of the stack put it in answer and then go to its right.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
# using recursion
def inorder(root):
  return  inorder(root.left) + [root.val] + inorder(root.right) if root else []

# using stack
class Solution:
    # @param A : root node of tree
    # @return a list of integers
    def inorderTraversal(self, A):
        node, stack, result = A, list(), list()
        while node or stack:
            if node:
                stack.append(node)
                node = node.left
            else:
                node = stack.pop()
                result.append(node.val)
                node = node.right
        return result
```
---
