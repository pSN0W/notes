# 🧩 Que
- [Link](https://leetcode.com/problems/coin-change-ii/)
You are given coins and an amount. You need to find the number of combinations that makes up that amount. You can assume having inf number of each coin.
```ad-question
title: Test Case
**Input:** amount = 5, coins = [1,2,5]
**Output:** 4
**Explanation:** there are four ways to make up the amount:
5=5
5=2+2+1
5=2+1+1+1
5=1+1+1+1+1
```

---
# Abstract
```ad-abstract
The whole idea is not too look backward. That means you want to create combination such that you do not go back to previous index. In the above example. If you are using coin 2 then you can't go back to use coin 1. So we are defining an order to remove duplicates. 1->2->5 and not any other
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- It is really simple the main problem comes out to be that you may run into duplicates. That means 5 can be 1,1,1,2 or 2,1,1,1. 
- Imagine how you will solve this problem if you need to write all the combination on a paper. You will forbid yourself from using lower coin after using higher coin. This should keep the order maintained.
- dp[idx][sum] = number of ways to create sum using coins starting from index idx

---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution {
public:
    vector<vector<int>> dp;
    vector<int> c;
    int solve(int idx,int sum){
        if(sum==0)  return 1;
        if(sum<0 or idx>=c.size())   return 0;
        if(dp[idx][sum]!=-1)    return dp[idx][sum];
        return dp[idx][sum] = solve(idx,sum-c[idx]) + solve(idx+1,sum);
    }
    int change(int amount, vector<int>& coins) {
        c = coins;
        dp.resize(c.size(),vector<int>(amount+1,-1));
        return solve(0,amount);
    }
};
```
---
