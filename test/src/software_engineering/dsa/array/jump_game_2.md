# 🧩 Que
- [Link](https://leetcode.com/problems/jump-game-ii/)
You are given an array. The element of the array tells the maximum jump that you can perform from that position you have to tell the min jumps required to reach the end of the array.
```ad-question
title: Test Case
**Input:** nums = [2,3,1,1,4]
**Output:** 2
**Explanation:** The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

---
# Abstract
```ad-abstract
The idea is pretty simple. Get the index that you can reach in the current jump and go till that index and find out the maximum index that you can reach in the next jump. Do this until convergence
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Initially you can only jump till 0th index. Find out how far you can go by performing 1 jump from you present index to the one reachable in the current jump.

---
# ☠️ My thought process
- You made a silly mistake of comparing at the end instead of begining
---

# 💻 Code
```c++
class Solution {
public:
    int jump(vector<int>& nums) {
        int num_jump = 0;
        int curr_reachable = 0;
        int i = 0;
        while(i<nums.size()){
            if(curr_reachable>=nums.size()-1){
                return num_jump;
            }
            num_jump++;
            int next_reachable = curr_reachable;
            while(i<=curr_reachable){
                next_reachable = max(next_reachable,i+nums[i]);
                i++;
            }
            curr_reachable = next_reachable;
        }
        return -1;
    }
};
```
---
