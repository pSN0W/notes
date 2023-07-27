# 🧩 Que
- [Link](https://leetcode.com/problems/integer-break/)
Given an integer n, you have to break it into smaller integers such that the sum is equal to n and the product of them is maximum

```ad-question
title: Test Case
**Input:** n = 2
**Output:** 1
**Explanation:** 2 = 1 + 1, 1 × 1 = 1.
```

---
```ad-abstract
Its really same for max of n you can choose any integer from 1..n-1 and then for the other you can get max_mul using dp[i] = `j * dp[i-j]`. The only edge case you will need to consider is when you are not breaking the integer that means the n is broken into only 2 integer. so you will need to check max with j * (i-j) too.
**MATHS**
If you will look at the break you will find out that it is majorily made with 2 and 3. You want to have as much 3 as possible.
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- dp[2] = 1
- for j in [1..i] dp[i] = max(max(dp[i],j*(i-j)), dp[j]* (i-j))

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    int integerBreak(int n) {
        vector<int> dp(n+1,-1);
        dp[2] = dp[1] = 1;
        for(int i=3;i<=n;i++){
            for(int j=1;j<i;j++){
                dp[i] = max(max(dp[i],j*(i-j)),dp[j]*(i-j));
            }
        }
        return dp[n];
    }
};
```
---
# 🔬 Optimized Code
```python
class Solution:
    def integerBreak(self, n: int) -> int:
        if n==2:
            return 1
        if n==3:
            return 2
        num_3 = n//3
        ans = pow(3,num_3)
        if n%3==2:
            ans*=2
        elif n%3==1:
            ans = ans*4//3
        return ans
```