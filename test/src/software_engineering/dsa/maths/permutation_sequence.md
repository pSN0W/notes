# 🧩 Que
- [Link](https://leetcode.com/problems/permutation-sequence/)
By listing and labeling all of the permutations in order, we get the following sequence for `n = 3`:
1. `"123"`
2. `"132"`
3. `"213"`
4. `"231"`
5. `"312"`
6. `"321"`

Given `n` and `k`, return the `kth` permutation sequence.
```ad-question
title: Test Case
**Input:** n = 3, k = 3
**Output:** "213"
```

---
# Abstract
```ad-abstract
The main idea is that you can chose which index will change for example to change the first index you will need to have k > 2! that means first the last 2 index will shuffle then next one
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- First subtract 1 from k so that by 0 you mean no change needs to be done.
- Now start form begining for example in the above case k = 2 and you will need to change the first place by 2/(3-1)! = 1. So you need to increment the first place by 1 so 1->2. now you are left with 0 more increment so just write them in order 213
- Consider n=4 and k = 8
	- k-=1 -> 7 and you have [1,2,3,4]
	- for first place 7/(4-1)! = 1 so you choose the second least number = 2 left [1,3,4]
	- You are left with 1. For the next 1/(4-2)! = 0. So you choose least = 1 left [3,4]
	- You are left with 1. for next 1/(4-3)! = 1 So you choose 4 left 3
	- Final 2134
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def getPermutation(self, n: int, k: int) -> str:
        k -= 1
        done = [False]*n
        def get_val(idx):
            for i,val in enumerate(done):
                if val == False:
                    idx-=1
                if idx<0:
                    done[i] = True
                    return str(i+1)
            return 9
        fact = [1]*n
        for i in range(1,n):
            fact[i] = i*fact[i-1]
        fact = fact[::-1]
        ans = ""
        i = 0
        while k!=0:
            curr_inc = k//fact[i]
            k %= fact[i]
            i += 1
            ans = ans + get_val(curr_inc)
        for i,val in enumerate(done):
            if val == False:
                ans = ans + str(i+1)
        return ans
```
---
