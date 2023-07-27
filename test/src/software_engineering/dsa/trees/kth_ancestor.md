# 🧩 Que
- Link
Given a tree in form of parent array and then multiple queries to get the Kth ancestor of the tree. Find the those ancestor
```ad-question
title: Test Case
![[Pasted image 20230722125931.png]]
**Input**
["TreeAncestor", "getKthAncestor", "getKthAncestor", "getKthAncestor"]
[ [7, [-1, 0, 0, 1, 1, 2, 2]], [3, 1], [5, 2], [6, 3] ]
**Output**
[null, 1, 0, -1]

**Explanation**
TreeAncestor treeAncestor = new TreeAncestor(7, [-1, 0, 0, 1, 1, 2, 2]);
treeAncestor.getKthAncestor(3, 1); // returns 1 which is the parent of 3
treeAncestor.getKthAncestor(5, 2); // returns 0 which is the grandparent of 5
treeAncestor.getKthAncestor(6, 3); // returns -1 because there is no such ancestor
```

---
# Abstract
```ad-abstract
You can use binary lifting to solve this problem
```

- Tags
--- 
# 🕵️‍♂️ Main Logic
- If you try a brute force approach then you can use the parents of the tree to traverse back one step at a time to go to the kth ancestor of it.
- Now lets say you try to memoise it so what you can do is create a matrix where `mat[i][j]` tells the jth ancestor of ith node and for every node we can just do `mat[i][j] = mat[par[i]][j-1]` ![[Pasted image 20230722130521.png]]
- This way you can precompute the ancestors and then answer the queries in O(1) time. For pre-computation the dimensions of matrix will be `n*max(height of tree)` If the tree is just in one line then in worse case it will be `O(n^2)`. So you will reach MLE as well as TLE.
- **The idea of binary lifting**
	- The main logic is that instead of storing all the k parents you just store the k parents that are power of 2. 
	- You can exploit binary numbers property for this 10 = 1010. So 10 ancestor can be found using 2nd ancestor current and then 8th ancestor of the second ancestor
	- Now you reduce your memory complexity for building to O(nlgn) while time complexity for query will be O(n)
	- To build the matrix now you can do something like this ![[Pasted image 20230722131205.png]]
	- The ith row represents 2^i ancestor If you want to get 4th ancestor of 7 as 2nd ancestor of 2nd ancestor of 7 so 7 2nd ancestor is 3 and 3 2nd ancestor is 0
	- So its just `mat[i][j] = mat[mat[i][j-1]][j]`
	- For query you will have to use binary numbers. If you want to get 11 the ancestor of 7 then 11 = 1011. So first get 1st ancestor of 7 = 6 then get 2nd ancestor of 6 which will be 1 and then get 8th ancestor of 1.

---
# ☠️ My thought process
- Forgot when parent becomes -1 thing and then due to negative indexing everything messes up
---

# 💻 Code
```python
class TreeAncestor:

    def __init__(self, n: int, parent: List[int]):
        self.binaryParents = [[-1]*n for _ in range(21)]
        for i in range(n):
            self.binaryParents[0][i] = parent[i]
        for i in range(1,21):
            for j in range(n):
                if self.binaryParents[i-1][j] != -1:
                    self.binaryParents[i][j] = self.binaryParents[i-1][self.binaryParents[i-1][j]]
        

    def getKthAncestor(self, node: int, k: int) -> int:
        par = node
        for i in range(21):
            if (k&(1<<i)) != 0:
                par = self.binaryParents[i][par]
                if par==-1:
                    return -1
        return par

```
---
