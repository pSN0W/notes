# 🧩 Que
- [Link](https://leetcode.com/problems/subarray-sums-divisible-by-k/)
Given an array and a number k, find the number of subarray in the array divisible by k.
```ad-question
title: Test Case
**Input:** nums = [4,5,0,-2,-3,1], k = 5
**Output:** 7
**Explanation:** There are 7 subarrays with a sum divisible by k = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
```

---
# Abstract
```ad-abstract
The idea is to keep count of the mod of the prefix sum of the array as you continue. There are negative number so use mod carefully. The subarray sum will be 0 when you encountered the same sum again. If you encounter same subarray mod sum at i and j then the subarray (i,j] will have mod sum 0
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Create a map to keep count of mods as you iterate on the array. You can also use a vector of size k as the mod will never exceed k.
- Get the subarray mod sum and see if the same sum was encountered earlier. If yes then add to answer and add the current sum to the map. 

---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution {
public:
    int mod(int n,int m){
        return (n%m + m)%m;
    }
    int subarraysDivByK(vector<int>& nums, int k) {
        map<int,int> mp;
        mp[0]++;
        int curr = 0;
        int ans = 0;
        for(int num:nums){
            curr = mod(curr+num,k);
            ans += mp[curr];
            mp[curr]++;
        }
        return ans;
    }
};
```
---
