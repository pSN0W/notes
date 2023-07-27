# 🧩 Que
- [Link](https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target)
You are given a target and cost for adding a number to a string. You need to generate the numerically largest string with cost same as target. If you can't then return 0. The cost array denotes cost of adding i+1 number
```ad-question
title: Test Case
**Input:** cost = [4,3,2,5,6,7,2,5,5], target = 9
**Output:** "7772"
**Explanation:** The cost to paint the digit '7' is 2, and the digit '2' is 3. Then cost("7772") = 2*3+ 3*1 = 9. You could also paint "977", but "7772" is the largest number.
```

---
# Abstract
```ad-abstract
You can devide the question in two parts.
- Find the largest length or largest number of elements you can choose for the cost array to generate target.
- Once you have the length next part is to greedily choose the numerically largest array of that length
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- Get the maximum length to target:
	- base_case -> `target==0 ->1` and `target<0 -> 0`
	- f(target) = `max([ f(target-cost[i]) for i in range(9)])``
- Once you have the maximum length. Then to generate the largest string with this length iterate backwards so that you try to add the largest integers first:
	- To check if you can add the number i you have to check if it is possible to get the sum after taking out that number from the current. so `dp[target] == dp[target - cost[i] ] + 1`
	- If you can add that number else move to the next smaller one

---
# ☠️ My thought process
- Too lazy to implement
---

# 💻 Code
```c++
class Solution {
public:
        string largestNumber(vector<int>& cost, int target) {
        vector<int> dp(target + 1, -10000);
        dp[0] = 0;
        for (int t = 1; t <= target; ++t) {
            for (int i = 0; i < 9; ++i) {
                dp[t] = max(dp[t], t >= cost[i] ? 1 + dp[t - cost[i]] : -10000);
            }
        }
        if (dp[target] < 0) return "0";
        string res = "";
        for (int i = 8; i >= 0; --i) {
            while (target >= cost[i] && dp[target] == dp[target - cost[i]] + 1) {
                res.push_back('1' + i);
                target -= cost[i];
            }
        }
        return res;
    }
};
```
---
