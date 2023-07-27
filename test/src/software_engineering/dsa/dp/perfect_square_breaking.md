# 🧩 Que
- [Link](https://leetcode.com/problems/perfect-squares/)
Given a number you have to break it into the least number of perfect squares that sums to it.
```ad-question
title: Test Case
**Input:** n = 12 <br>
**Output:** 3 <br>
**Explanation:** 12 = 4 + 4 + 4. <br>
```

---
```ad-abstract
You just have to see how you can solve it by breaking it into smaller counterparts. ans[12] = 1 + ans[3]. (considering we are taking 3*3 as one of the squares)

```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Have an array that will tell you the solution for arr[i]. Now you are solving for i consider all the squares less then i and find number of solution with arr[i-square]. The minimum of this for all the possible square will be your answer

---
# ☠️ My thought process
- 
---

# 💻 Code

```c++
class Solution {
public:
    int numSquares(int n) {
        vector<int> dp(n+1,INT_MAX);
        dp[0] = 0;
        for(int i=1;i<=n;i++){
            for(int j=1;j*j<=i;j++){
                if(dp[i-j*j]!=INT_MAX){
                    dp[i] = min(dp[i],1+dp[i-j*j]);
                }
            }
        }
        return dp[n];
    }
};
```
---
