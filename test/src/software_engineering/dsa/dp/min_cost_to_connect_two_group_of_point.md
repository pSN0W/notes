# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-cost-to-connect-two-groups-of-points/)
You are given two groups of points where the first group has `size1` points, the second group has `size2` points, and `size1 >= size2`.
The `cost` of the connection between any two points are given in an `size1 x size2` matrix where `cost[i][j]` is the cost of connecting point `i` of the first group and point `j` of the second group. The groups are connected if **each point in both groups is connected to one or more points in the opposite group**. In other words, each point in the first group must be connected to at least one point in the second group, and each point in the second group must be connected to at least one point in the first group.
Return _the minimum cost it takes to connect the two groups_.
```ad-question
title: Test Case
![[Pasted image 20230716133505.png]]
**Input:** cost = [ [1, 3, 5], [4, 1, 1], [1, 5, 3] ]
**Output:** 4
**Explanation**: The optimal way of connecting the groups is:
1--A
2--B
2--C
3--A
This results in a total cost of 4.
Note that there are multiple points connected to point 2 in the first group and point A in the second group. This does not matter as there is no limit to the number of points that can be connected. We only care about the minimum total cost.
```

---
# Abstract
```ad-abstract
You need to connect one group to the other to get the minimum value if you current group ends then for the left of another group you need to choose connection that gets you the minimum value
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- Get the minimum connection from for all nodes in A for A -> B
- Now for all the nodes in b
	- Make a connection with any of the node in A and set the mask to set
	- Even if the node in A has a connection you can add another connection to it so you don't need to check if the bit is set at that position just set it anyway. Done using `mask & ~(1<<i)`
	- When you are done connecting all the nodes from B some node of A will still be left for them just connect them to the minimum path in B
	- The answer there will be min_cost(A->B) for all the non reached A.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def connectTwoGroups(self, cost: List[List[int]]) -> int:
        n, m = len(cost), len(cost[0])
        mn_for_first_gp = [min(x) for x in cost]
        @cache
        def solve(idx, mask):
            if idx>=m:
                return sum([mn_for_first_gp[i] for i in range(n) if mask&(1<<i)!=0]) if mask else 0
            else:
                return min([cost[i][idx]+solve(idx+1, mask&~(1<<i)) for i in range(n)])
        return solve(0,(1<<n)-1)
```
---
