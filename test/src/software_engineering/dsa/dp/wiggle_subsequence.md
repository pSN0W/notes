# 🧩 Que
- [Link](https://leetcode.com/problems/wiggle-subsequence/)

```ad-question
title: Test Case
**Input:** nums = [1,7,4,9,2,5]
**Output:** 6
**Explanation:** The entire sequence is a wiggle sequence with differences (6, -3, 5, -7, 3).
```

---
# Abstract
```ad-abstract
You tried to do it using dp and succeded too. But the problem was simple of counting number of peak and number of valleys
```

- Tags #unsolved #revise 
--- 
# 🕵️‍♂️ Main Logic
- The idea is to count the number of peak and valley. The red denotes peak value and blue denotes valley value. See how you do not increase your peak or valley when the array is monotonic
![[Pasted image 20230630131305.png]]

---
# ☠️ My thought process
- You thought of using something like LCS. You created a dp[n]  [2] array where dp [i]  [0] tells then longest wiggling sequence till now considering the present one is increasing and similarly dp [i]  [1] considers current to be decreasing.
```c++
class Solution {
public:
    int wiggleMaxLength(vector<int>& arr) {
        int n = arr.size();
        vector<vector<int>> dp(n,vector<int>(2,1));
        int ans = 1;
        for(int i=1;i<n;i++){
            for(int j=0;j<i;j++){
                if(arr[i]==arr[j])  continue;
                if(arr[i]>arr[j]){
                    dp[i][0] = max(dp[i][0],dp[j][1]+1);
                }
                else{
                    dp[i][1] = max(dp[i][1],dp[j][0]+1);
                }
            }
            ans = max(ans,max(dp[i][0],dp[i][1]));
        }
        return ans;
    }
};
```
---

# 💻 Code

---
```cpp
class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        int size=nums.size(), peak=1, valley=1;
        for(int i=1; i<size; ++i){
                 if(nums[i]>nums[i-1]) peak = valley + 1;
            else if(nums[i]<nums[i-1]) valley = peak + 1;
        }
        return max(peak , valley );
    }
};
```