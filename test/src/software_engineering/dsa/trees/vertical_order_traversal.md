# 🧩 Que
- Link
Given a tree return its vertical order traversal
```ad-question
title: Test Case
![[Pasted image 20230721173251.png]]
[
    [2],
    [3],
    [6, 5],
    [7],
    [9]
 ]
```
---
# Abstract
```ad-abstract
The idea is to hash the horizantal distance from the palindromic subsequence. For a node to the right the distance is h+1 while for the one at the left it is h-1 and since you want to have it sorted vertically you can have a level order traversal of the three too.  
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
import collections
class Solution:
	# @param A : root node of tree
	# @return a list of list of integers
	def verticalOrderTraversal(self, A):
	    if(A==None):
	        return []
        queue = []
        m = {}
        hd_node = {} 
        queue.append(A) 
        hd_node[A] = 0
  
        m[0] = [A.val]
        while len(queue) > 0:
            temp = queue.pop(0) 
  
            if temp.left:
                queue.append(temp.left) 
                hd_node[temp.left] = hd_node[temp] - 1
                hd = hd_node[temp.left] 
  
                if m.get(hd) is None:
                    m[hd] = [] 
  
                m[hd].append(temp.left.val) 
  
            if temp.right:
                queue.append(temp.right)
                hd_node[temp.right] = hd_node[temp] + 1
                hd = hd_node[temp.right] 
  
                if m.get(hd) is None: 
                    m[hd] = [] 
                m[hd].append(temp.right.val) 
        sorted_m = collections.OrderedDict(sorted(m.items())) 
        ans=[]
        for i in sorted_m.values():
            temp=[]
            for j in i: 
                temp.append(j) 
            ans.append(temp)
        return ans
```
---
