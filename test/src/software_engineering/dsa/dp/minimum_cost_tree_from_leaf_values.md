# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/)
Given an array `arr` of positive integers, consider all binary trees such that:

- Each node has either `0` or `2` children;
- The values of `arr` correspond to the values of each **leaf** in an in-order traversal of the tree.
- The value of each non-leaf node is equal to the product of the largest leaf value in its left and right subtree, respectively.

Among all possible binary trees considered, return _the smallest possible sum of the values of each non-leaf node_. It is guaranteed this sum fits into a **32-bit** integer.

A node is a **leaf** if and only if it has zero children.
```ad-question
title: Test Case
![[Pasted image 20230708172318.png]]
```

---
# Abstract
```ad-abstract
The idea is to check all the possible trees and then return the answer using mcm dp
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- define solve(i,j) as the minimum answer you can get after solving a tree with leave nodes as the ones in arr[i:j+1]
- To solve this what you can do is have
	- 1 leave to left rest to right
	- 2 leave to left rest to right
	- ...
- The function also returns the max tree leaf value in that range as that is needed to compute cost for the node

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def mctFromLeafValues(self, arr: List[int]) -> int:
        @lru_cache(None)
        def solve(i,j):
            if i==j:
                return 0,arr[i]
            ans = float('inf')
            mx = float('-inf')
            for k in range(i,j):
                lft,lft_mx = solve(i,k)
                rt,rt_mx = solve(k+1,j)
                curr = lft+rt+lft_mx*rt_mx
                if curr < ans:
                    ans = curr
                    mx = max([lft_mx,rt_mx])
            return ans,mx
        return solve(0,len(arr)-1)[0]
```
---
