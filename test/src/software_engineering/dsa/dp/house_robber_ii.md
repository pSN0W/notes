# 🧩 Que
- [Link](https://leetcode.com/problems/house-robber-ii/)
Houses are placed in circular order that means that first house is adjacent to last. You can't rob adjacent houses, find the max amount you can rob
```ad-question
title: Test Case
**Input:** nums = [2,3,2]
**Output:** 3
**Explanation:** You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.
```

---
# Abstract
```ad-abstract
The idea is simple you first rob for 1->n and then for 0->n-1 and then return the answer. Check the code as it contains as O(1) solution
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- If you would solve this question in top down fashion you will find that you need to just keep track of maximum you can rob after leaving the i-1 house.

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        if (nums.size() == 1) {
            return nums[0];
        }
        
        int robFirstHouse = robHelper(nums, 0, nums.size() - 2); // Rob the first house to the second-to-last house
        int skipFirstHouse = robHelper(nums, 1, nums.size() - 1); // Skip the first house and rob the rest
        
        return max(robFirstHouse, skipFirstHouse);
    }
    
    int robHelper(vector<int>& nums, int start, int end) {
        int currMax = 0;
        int prevMax = 0;
        
        for (int i = start; i <= end; i++) {
            int temp = max(prevMax + nums[i], currMax);
            prevMax = currMax;
            currMax = temp;
        }
        
        return currMax;
    }
};
```
---
