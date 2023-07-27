# 🧩 Que
- [Link](https://leetcode.com/problems/k-diff-pairs-in-an-array/)
Given an array return unique pairs with difference k.
```ad-question
title: Test Case
**Input:** nums = [3,1,4,1,5], k = 2
**Output:** 2
**Explanation:** There are two 2-diff pairs in the array, (1, 3) and (3, 5).
Although we have two 1s in the input, we should only return the number of **unique** pairs.
```

---
# Abstract
```ad-abstract
You can use a map to keep the numbers that passed by. You will only need to process numbers not processed before. (This will change for 0). For every new number (number not seen previously) see if you can find num-k and num+k in map. If difference is 0 then the ans is number of elements with freq >= 2
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- You will need to store a map of elements that were seen previously.
- Since you need unique element don't process elements that are part of the map. The reason for this being if something was part of map then the following cases should have happened.
	- It's pair would have been already found in the map. [2,1,1] k = 1
	- If it's counterpart would have come after it then it's counterpart would have formed the pair. [1,2,1] k = 1
	- The counterpart hasn't came so no need to process it [1,1] k = 1
- For each element you need to find the num-k and num+k.

---
# ☠️ My thought process
- Missed edge case of k=0
- You initially though of using set but that wouldn't do well when k = 0
---

# 💻 Code

```c++
class Solution {
public:
    int findPairs(vector<int>& nums, int k) {
        map<int,int> mp;
        int ans = 0;
        for(int num:nums){
            if(mp.count(num)==0){
                ans += mp.count(num-k);
                ans += mp.count(num+k);
            }else if(k==0 and mp[num]==1){
                ans++;
            }
            mp[num] += 1;
        }
        return ans;
    }
};
```
---
