# 🧩 Que
- Link
Consider lines of slope -1 passing between nodes.

Given a Binary Tree **A** containing **N** nodes, return all diagonal elements in a binary tree belonging to same line.
```ad-question
title: Test Case
![[Pasted image 20230721174548.png]]
 [1, 2, 3, 4, 5, 7, 6, 8, 9]
 ![[Pasted image 20230721174610.png]]
```

---
# Abstract
```ad-abstract
The idea is to store the slope in the map.
- The slope of right child remain the same
- Slope of the left child become x+1
Another option is to use a queue
- Push the element in queue only if its left is available
- Process the node and then move to its right
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
class Solution:
    # @param A : root node of tree
    # @return a list of integers
    def solve(self, A):
        lst = [A]
        ans = []
        while True:
            t = []
            if len(lst) == 0:
                break
            p = []
            for i in lst:
                while i != None:
                    p.append(i)
                    if i.left:
                        t.append(i.left)
                    i = i.right
            ans += p
            lst = t
        ans = [i.val for i in ans]
        return ans
```
---
