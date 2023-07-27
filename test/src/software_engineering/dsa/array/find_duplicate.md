# 🧩 Que
- [Link](https://leetcode.com/problems/find-the-duplicate-number/)
Given an array of size n containing number in the range of [1,n+1]. 1 number is duplicated find that number

```ad-question
title: Test Case
**Input:** nums = [1,3,4,2,2]
**Output:** 2
```

---
```ad-abstract
These question are part of using the array itself as hash map. You use the index as the hash map.
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Convert each element to num_freq_i*(n+1)+element and then find the value of the element.

---
# ☠️ My thought process
- 
---

# 💻 Code

---
```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int n=nums.size();
        for(int i=0;i<n;i++)
        {
            nums[nums[i]%n]+=n;
        }
        for(int i=0;i<n;i++)
        {
            if(nums[i]/n>1)
                return i;
        }
        return 0;
    }
};
```