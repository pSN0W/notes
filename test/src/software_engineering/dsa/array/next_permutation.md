# 🧩 Que
- [Link](https://leetcode.com/problems/next-permutation/description/)
- Given an array find next just greater permutation of that array

```ad-question
title: Test Case
**Input:** nums = [1,2,3]
**Output:** [1,3,2]

```

---
```ad-abstract
The idea is to first find out the least signifacnt digit that can be changed to generate a permutation greater then current one. Next order of business is to find out the one number that you are going to replace it with. Perforcm the replace and after replace reverse the numbers after the digit you performed swap. This is done because after the digit you performed swapped the numbers are in descending order
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- To find out the digit which can be changed to create a greater permutation iterate through the array from behind and get the first occurrence of arr[i] < arr[i+1]. 
- ![[Pasted image 20230629184102.png]]
- Next you need to find the smallest element to it's right that you can swap it with to make it greater. This is done because we don't want to touch any elements to the left of the circled one. In this case it will be 4.
- Swap both the elements 2<=>4
- ![[Pasted image 20230629184349.png]]
- Now you can see that after 4 all the elements are in non increasing order. You can reverse them to get the just greater permutation.
- Final answer 7 1 6 4 1 2 5

---
# ☠️ My thought process
- You messed up from where to reverse I will suggest considering such example before coding it out.
---

# 💻 Code
```c++
class Solution {
public:
    int get_change_point(vector<int>& nums){
        int n = nums.size();
        for(int i=n-2;i>=0;i--){
            if(nums[i]<nums[i+1]){
                return i;
            }
        }
        return -1;
    }
    int get_just_greater(vector<int> &nums,int to_check){
        for(int i=nums.size()-1;i>=0;i--){
            if(nums[i]>to_check)    return i;
        }
        return -1;
    }
    void nextPermutation(vector<int>& nums) {
        // find the position where you can perform change
        int change_point = get_change_point(nums);
        if(change_point==-1){
            reverse(nums.begin(),nums.end());
            return;
        }
        int just_greater = get_just_greater(nums,nums[change_point]);
        swap(nums[change_point],nums[just_greater]);
        reverse(nums.begin()+change_point+1,nums.end());
    }
};
```
---
