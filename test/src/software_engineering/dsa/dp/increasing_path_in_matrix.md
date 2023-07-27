# 🧩 Que
- [Link](https://www.interviewbit.com/problems/increasing-path-in-matrix/)
Given a 2D matrix you can go to i+1,j if `A[i+1][j] > A[i][j]` and i.j+1 if `A[i][j+1] > A[i][j]` Find the largest path from 0,0 to N-1,M-1
```ad-question
title: Test Case
 A = [  [1, 2]
        [3, 4]
     ]
Ans = 3
```

---
# Abstract
```ad-abstract
The idea is to iterate from n-1 and m-1 and find out the max way to reach 0,0 given the constraint. initilaize dp(n-1)(m-1) = 1.
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int Solution::solve(vector<vector<int> > &A) {
    int n = A.size(), m = A[0].size();
    vector<vector<int>> dp(n,vector<int>(m,-1e6));
    for(int i=n-1;i>=0;i--){
        for(int j=m-1;j>=0;j--){
            if(i==n-1 and j==m-1)   dp[i][j] = 1;
            else if(i==n-1) dp[i][j] = (A[i][j+1]>A[i][j] ? 1+dp[i][j+1] : -1e6);
            else if(j==m-1) dp[i][j] = (A[i+1][j]>A[i][j] ? 1+dp[i+1][j] : -1e6);
            else{
                dp[i][j] = max((A[i+1][j]>A[i][j] ? 1+dp[i+1][j] : -1e6), (A[i][j+1]>A[i][j] ? 1+dp[i][j+1] : -1e6));
            }
        }
    }
    return max(dp[0][0],-1);
}

```
---
