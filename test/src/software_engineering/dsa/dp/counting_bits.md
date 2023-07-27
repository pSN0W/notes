# 🧩 Que
- [Link](https://leetcode.com/problems/counting-bits/)
Given an integer n return the number of set bits from 0 to n.

```ad-question
title: Test Case
**Input:** n = 2 
**Output:** [0,1,1] 
**Explanation:** 
0 --> 0
1 --> 1
2 --> 10
```

---
```ad-abstract
It will be good if you can think of it in binary. Number of bits at n is equal to set bit at position 0 and then number of bits after removing the last bit.
num_bit[7] = 1 (last bit is 1) + num_bit[3]
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int> dp(n+1);
        dp[0] = 0;
        for(int i=1;i<=n;i++){
            dp[i] = dp[i/2] + i%2;
        }
        return dp;
    }
};
```
---
