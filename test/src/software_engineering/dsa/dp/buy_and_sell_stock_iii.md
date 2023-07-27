# 🧩 Que
- [Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)
You are given prices of stock you need to find out the maximum profit after two transaction.
```ad-question
title: Test Case

**Input:** prices = [3,3,5,0,0,3,1,4] <br>
**Output:** 6<br>
**Explanation:** Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.
```

---
```ad-abstract
For each day find out the maximum profit you would have earned if you sold for your first transaction on that day.  <br>
For the second transaction what is the maximum profit that you can make if you buy after today.
```

- Tags #revise
--- 
# 🕵️‍♂️ Main Logic
- To calculate the maximum cost for selling today you can have a prefix minimum array and you can check it to get the value of maximum profit for second transaction.
- For the second transaction imagine how much you can earn if you bought today. You can precompute this using suffix maximum array. 
- For this question you are selling at the i day but you can buy in any of the next day so what you can do is create a suffix max of the array computed in the bullet point array this will give you the maximum profit that can be made after buying today

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        vector<int> mn(n),mx(n);
        mn[0] = prices[0];
        mx[n-1] = prices[n-1];
        for(int i=1;i<n;i++) mn[i] = min(mn[i-1],prices[i]);
        for(int i=n-2;i>=0;i--) mx[i] = max(mx[i+1],prices[i]);
        vector<int> sell_today(n,0), buy_today(n,0);
        for(int i=0;i<n;i++)    sell_today[i] = prices[i] - mn[i];
        for(int i=0;i<n;i++)    buy_today[i] = mx[i] - prices[i];
        for(int i=1;i<n;i++)    sell_today[i] = max(sell_today[i-1],sell_today[i]);
        int ans = 0;
        for(int i=0;i<n;i++){
            int curr = buy_today[i] + sell_today[i];
            ans = max(ans,curr);
        }
        return ans;
    }
};
```
---
