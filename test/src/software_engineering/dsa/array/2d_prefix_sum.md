# 🧩 Que
- [Link](https://leetcode.com/problems/range-sum-query-2d-immutable/)
Given a 2D matrix. You will be given row1,col1,row2,col2. You have to find the sum of subarray made by the square using (row1,col1) as top left corner and (row2,col2) at bottom right corner
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You will need to keep your pewfix sum in such a way that (row,col) gives the sum of all numbers between (0,0) and (row,col). To do this you can first calculate prefix sum from left to right and for that prefix sum you can calculate top to down
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230701184233.png]]

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class NumMatrix:
    def __init__(self, matrix: List[List[int]]):
        n,m = len(matrix),len(matrix[0])
        dp = [[0]*m for _ in range(n)]
        for i in range(n):
            for j in range(m):
                if j==0:
                    dp[i][j] = matrix[i][j]
                else:
                    dp[i][j] = dp[i][j-1] + matrix[i][j]
        
        for i in range(1,n):
            for j in range(m):
                dp[i][j] = dp[i][j] + dp[i-1][j]
        self.prefix = dp

    def find_square_sum(self,row1,row2,col):
        return self.prefix[row2][col] - (self.prefix[row1-1][col] if row1 > 0 else 0)
    def sumRegion(self, row1: int, col1: int, row2: int, col2: int) -> int:
        return self.find_square_sum(row1,row2,col2) - (self.find_square_sum(row1,row2,col1-1) if col1>0 else 0)
```
---
