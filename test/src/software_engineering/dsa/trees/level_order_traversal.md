# 🧩 Que
- Link
Given a tree perform level order traversal
```ad-question
title: Test Case

```

---
# Abstract
```ad-abstract
The idea is to use a queue and then first process all the nodes at the current level to differentiate the level between the nodes you can use None.
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
from queue import Queue
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None:
            return []
        q = Queue()
        q.put(root)
        q.put(None)
        ans = []
        curr = []
        while not q.empty():
            front = q.get()
            if front is None:
                ans.append(curr)
                curr = []
                if not q.empty():
                    q.put(None)
                continue
            curr.append(front.val)
            if front.left is not None:
                q.put(front.left)
            if front.right is not None:
                q.put(front.right)
        return ans
```
---
