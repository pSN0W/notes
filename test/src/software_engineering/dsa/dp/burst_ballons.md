# 🧩 Que
- [Link](https://leetcode.com/problems/burst-balloons/)
You are given `n` balloons, indexed from `0` to `n - 1`. Each balloon is painted with a number on it represented by an array `nums`. You are asked to burst all the balloons.
If you burst the `ith` balloon, you will get `nums[i - 1] * nums[i] * nums[i + 1]` coins. If `i - 1` or `i + 1` goes out of bounds of the array, then treat it as if there is a balloon with a `1` painted on it.
Return _the maximum coins you can collect by bursting the balloons wisely_.
```ad-question
title: Test Case
**Input:** nums = [3,1,5,8]
**Output:** 167
**Explanation:**
nums = [3,1,5,8] --> [3,5,8] --> [3,8] --> [8] --> []
coins =  3*1*5    +   3*5*8   +  1*3*8  + 1*8*1 = 167
```

---
# Abstract
```ad-abstract
You can't directly use MCM dp with this because when you burst a ballon the order of the ballon changes. So you need to think differently, assume what will happen if this is the last ballon. So you basicall solve backward.
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- It will be good to solve this que opposite. let solve(i,j) denotes the maximum value you can get if there is only one balloon between them and you pop that ballon
- If there is just one balloon and you pop the Kth balloon then you will get a total number of `nums[i-1] * nums[k] * nums[j+1]` coins.
- Once you have popped that ballon just think how will pop the second last ballon. You can pop from left or right so call solve(i,k-1) + solve(k+1,j)

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def maxCoins(self, nums: List[int]) -> int:
        nums = [1] + nums + [1]
        @cache
        def solve(st,ed):
            if st > ed:
                return 0
            ans = 0
            for j in range(st,ed+1):
                ans = max([ans,
                    nums[st-1]*nums[j]*nums[ed+1]+solve(st,j-1)+solve(j+1,ed)
                ])
            return ans
        return solve(1,len(nums)-2)
```
---
