# 🧩 Que
- [Link](https://leetcode.com/problems/delete-and-earn/)
Given an integer nums you want to maximize the number of points you get by performing the following operations. 
- Pick any nums[i] and delete it to earn nums[i] points. Afterwards, you must delete every element equal to nums[i] - 1 and every element equal to nums[i] + 1.
```ad-question
title: Test Case
**Input:** nums = [3,4,2]
**Output:** 6
**Explanation:** You can perform the following operations:
- Delete 4 to earn 4 points. Consequently, 3 is also deleted. nums = [2].
- Delete 2 to earn 2 points. nums = [].
You earn a total of 6 points.
```

---
# Abstract
```ad-abstract
The approach here is similar to [[combination_sum_ii]]. You first sort and then skip the elements depending on the condition you follow. First sort the numbers now your problem has reduced to two cases:
- Take current element. Skip the next one
- Skip current element and take the next one
You will get the combination with max
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- First you sort the array and this removes the complications of dealing with number lower then current one or removing the arr[i] - 1. Because consider the array [1,2,3]. You could only come to 2 if you skipped 1 because if you have considered one you would have gone to 3.
- Now for each element you have two cases. Take this array as example: [2,2,3,3,3,4]
	- If you choose to skip index 0 then you must skip all the element with value 2. So you will call index 2
	- If you choose to consider index 0 then you will have to skip all 2 and 3 and will have to call index 5. The gain of considering 2 is 2* 2 = 4

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def deleteAndEarn(self, nums: List[int]) -> int:
        nums.sort()
        @lru_cache(None)
        def solve(idx):
            if idx >= len(nums):
                return 0
            i = j = idx # i to leave current one and j to take current one leave nums[idx]+1
            while i<len(nums) and nums[i]==nums[idx]:
                i+=1
            while j<len(nums) and nums[j]-nums[idx]<=1:
                j+=1
            return max([solve(i), solve(j)+nums[idx]*(i-idx)])
        return solve(0)
        
```
---
