# 🧩 Que
- [Link](https://leetcode.com/problems/subsets-ii/)
Given an array containing duplicates return all the unique subsets
```ad-question
title: Test Case
**Input:** nums = [1,2,2]
**Output:** [ [],[1],[1,2],[1,2,2],[2],[2,2] ]
```

---
# Abstract
```ad-abstract
This is similar to [[permutation_ii]]. Here you can also use the concept of [[subset]] too. If you draw the tree you will figure out that if you ignore a number then you will have to ignore it in the whole tree.
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- If you draw the tree you will see that if you ignore a specific number in one subtree then it will be ignored throughout that subtree.
- See the commons arising when you chose to take 2 in a branch you ignored earlier. The solution for this is to keep a ignored array and only add if it is not previously. You can use set for this too.
![[Pasted image 20230630205920.png]]

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    vector<vector<int>> ans;
    vector<int> nums;
    void solve(int idx,vector<int> &curr,vector<int> &ignored){
        if(idx==nums.size()){
            ans.push_back(curr);
            return;
        }
        // ignore current
        ignored.push_back(nums[idx]);
        solve(idx+1,curr,ignored);
        ignored.pop_back();

        // take current
        for(int ig:ignored){
            if(ig==nums[idx])   return;
        }
        curr.push_back(nums[idx]);
        solve(idx+1,curr,ignored);
        curr.pop_back();
    }
    vector<vector<int>> subsetsWithDup(vector<int>& num) {
        nums = num;
        vector<int> ignored,curr;
        solve(0,curr,ignored);
        return ans;
    }
};
```
---
