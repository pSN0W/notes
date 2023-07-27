# 🧩 Que
- [Link](https://www.interviewbit.com/problems/dice-throw/)
Given A dices with faces from 1 to B. Find number of way to get sum C
```ad-question
title: Test Case
A = 2
B = 4
C = 5
Ans = 4
```

---
# Abstract
```ad-abstract
Its not a very hard problem you can use 3 loop to solve this question but the big thing is removing one of the array using the prefix sum. 
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- First solve the question using three loop. The code is provided in the commented out section
	- `dp[i][j]` = number of ways to get sum j using i dices
	- `dp[0][0] ` = 1 since you can achieve 0 with o dice in one way
	- for all other use a for loop to go from 1 to k and then `dp[i][j] = dp[i-1][j-k]`
- To optimize this what you do is remove the last for loop with prefix sum of dp[i-1]

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int Solution::findDiceSum(int A, int B, int C) {
    vector<vector<long long>> dp(A+1,vector<long long>(C+1,0));
    dp[0][0] = 1;
    long long md = 1e9+7;
    for(int i=1;i<=A;i++){
        for(int j=1;j<=C;j++){
            dp[i-1][j] = dp[i-1][j]+dp[i-1][j-1];
        }
        for(int j=1;j<=C;j++){
            // for(int k=1;k<=B;k++){
            //     if(j-k<0)   break;
            //     dp[i][j] += dp[i-1][j-k];
            //     dp[i][j] %= md;
            // }
            dp[i][j] = dp[i-1][j-1] - (j-B-1>=0 ? dp[i-1][j-B-1] : 0);
            dp[i][j] = ((dp[i][j]%md)+md)%md;
        }
    }
    return dp[A][C];
}
```
---
