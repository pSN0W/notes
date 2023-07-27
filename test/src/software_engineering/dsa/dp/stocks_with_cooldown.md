# 🧩 Que
- [Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)
You are given prices of stock you can make as many transaction as you want but there is a catch if you sell today then you can't buy again the next day that means there is a cool down period of 1 day

```ad-question
title: Test Case

**Input:** prices = [1,2,3,0,2] <br>
**Output:** 3 <br>
**Explanation:** transactions = [buy, sell, cooldown, buy, sell]
```

---
```ad-abstract
It is really simple just decide if you want to buy today or not if you have already bought then decide if you should sell today or not. Whenever you can sell you can repeat the process after skipping one more index
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Your function takes two argument f(day,buy?) that is if today you want to buy or sell
- if buy f(day,buy) = max(f(day+1,buy)//don't buy today, f(day+1,!buy) - price[idx]// buy today)
-  if !buy f(day,!buy) = max(f(day+1,!buy)//don't sell today, f(day+2,buy) - price[idx]// sell today and then repeat the process for day+2)

---
# ☠️ My thought process
- 
---

# 💻 Code

```c++
class Solution {
public:
    vector<int> price;
    int n;
    vector<vector<int>> dp;
    int solve(int idx,int buy){
        if(idx>=n)  return 0;
        if(dp[idx][buy]!=-1)    return dp[idx][buy];
        if(buy){
            return dp[idx][buy] = max(solve(idx+1,buy),solve(idx+1,1-buy) - price[idx]);
        }else{
            return dp[idx][buy] = max(solve(idx+1,buy),solve(idx+2,1-buy) + price[idx]);
        }
        return 0;
    }
    int maxProfit(vector<int>& prices) {
        price = prices;
        n = price.size();
        dp.resize(n,vector<int>(2,-1));
        return solve(0,1);
    }
};
```
---
