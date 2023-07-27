# 🧩 Que
- [Link](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.
```ad-question
title: Test Case
![[Pasted image 20230723024343.png]]
```

---
# Abstract
```ad-abstract
You can do it in the following ways
- Use left and right if one node exist in left and another in right than the current become lca
- You can lift the node on the following manner
	- First lift the lower node to the level of top node
	- Move both of them one by one until you reach a common node
- For lifting you can use binary lifting too
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
Implementations of the three discussed approaches
- Using left right and recursion
```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def solve(node):
            if node is None:
                return None
            if node.val in [p.val,q.val]:
                return node
            lft = solve(node.left)
            rt = solve(node.right)
            if lft is not None and rt is not None:
                return node
            return lft if rt is None else rt
        return solve(root)
```
- Lifting the node one by one.
	- Lift them to be at same level. For this for each node you will have to store parent and the level lift the one at lower level to the higher one
	- Once they are at the same level you can lift them one by one
- Using Binary lifting
	- The lift in the approach can be minimised by the use of binary lifting
	- For the first you can get the difference between the level of two. So if b is lower then a then to get them to same level you have to get level[a] - level[b] ancestor of b. You can do something similar to [[kth_ancestor]]
	- Now for lifting one by one you can reduce it too. The main idea here is that you want to get the nodes just below the parent from both side so if the parents match then reduce the jump size if they don't then go to the new node.
	- Lets say the max possible bit is 8 so you try a jump of 8 both parent match. Then try a jump of 7 you do this continuously and lets say at jump of 4 parent do not match.
	- Take a jump of 2^4 for both and from there try jump of 3. Continue this process
```cpp
for(int i=MAX_BIT;i>=0;i--){
	int up = table[i][u];
	int vp = table[i][v];
	if(up!=vp){
		u = up;
		v = vp;
	}
}
return parent[u];
```

---
# ☠️ My thought process
- 
---

# 💻 Code

---
