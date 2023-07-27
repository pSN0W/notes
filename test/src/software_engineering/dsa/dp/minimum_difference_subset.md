# 🧩 Que
- [Link](https://www.interviewbit.com/problems/minimum-difference-subsets/)
Given an array divide it into two subset such that the MAD between them is minimum.
```ad-question
title: Test Case
A = [1, 6, 11, 5]
Subset1 = {1, 5, 6}, sum of Subset1 = 12
```

---
# Abstract
```ad-abstract
This is a standard extension of subset sum possible problem. In the last row there see all the subset sum that is possible and then MAD will be `abs(sum(arr)-1-2*(curr_sum))`
```

- Tags #standard_que 
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
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        n,m = len(A)+1,sum(A)+1
        dp = [[False]*m for _ in range(n)]
        dp[0][0] = True
        for i in range(1,n):
            dp[i][0] = True
            for j in range(1,m):
                dp[i][j] = dp[i-1][j] | (dp[i-1][j-A[i-1]] if A[i-1]<=j else False)
        ans = m-1
        for i,val in enumerate(dp[-1]):
            if val:
                ans = min([ans,abs(m-1-2*(i))])
        return ans

```
---
