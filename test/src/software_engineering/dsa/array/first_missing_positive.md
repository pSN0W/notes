# 🧩 Que
- [Link](https://leetcode.com/problems/first-missing-positive/)
Given an unsorted array. Find the first missing positive integer from it.
```ad-question
title: Test Case
**Input:** nums = [3,4,-1,1]
**Output:** 2
**Explanation:** 1 is in the array but 2 is missing.
```

---
# Abstract
```ad-abstract
You can use the array as hash map or one other thing that you can try out is to perform swapping to rearrange the number to their actual position. You will have to take care of loops formation and stuff
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- The idea is to reorder the array such that index i stores value i+1
- You can iterate through the array and perform swap to move it to the correct position the following thing should be considered.
	- Take care of skipping out of range values <0 and >n
	- Skipping a number because of swap. For example [0, 3, 1]. When you swap to move 3 to its correct position [0, 1, 3] and then you move forward then you are skipping ordering 1 correctly. This can be done by not incrementing i when swapping.
	- Take care of formation of loop. Consider this case [1, 1].

---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int i = 0;
        int n = nums.size();
        while(i<n){
            if(nums[i]!=i+1 and nums[i]>0 and nums[i]<=n and nums[i]!=nums[nums[i]-1]){
                swap(nums[i],nums[nums[i]-1]);
            }
            else{
                i++;
            }
        }
        for(int i=0;i<n;i++)    if(nums[i]!=i+1)  return i+1;
        return n+1;
    }
};
```
---
