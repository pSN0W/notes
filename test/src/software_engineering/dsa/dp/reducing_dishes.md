# 🧩 Que
- [Link](https://leetcode.com/problems/reducing-dishes/)
A chef has collected data on the `satisfaction` level of his `n` dishes. Chef can cook any dish in 1 unit of time.

**Like-time coefficient** of a dish is defined as the time taken to cook that dish including previous dishes multiplied by its satisfaction level i.e. `time[i] * satisfaction[i]`.

Return _the maximum sum of **like-time coefficient** that the chef can obtain after dishes preparation_.
```ad-question
title: Test Case
**Input:** satisfaction = [-1,-8,0,5,-9]
**Output:** 14
**Explanation:** After Removing the second and last dish, the maximum total **like-time coefficient** will be equal to (-1*1 + 0*2 + 5*3 = 14).
Each dish is prepared in one unit of time.
```
---
# Abstract
```ad-abstract
The idea is simple first sort the list as you want to prepare the most satisfactory one at the end and then just decide the place from where to start
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
-> sort as to take the maximum satisfaction at the end whole time  
-> just to find from where we have to start the time  
-> firstly check for whole array  
-> let i is starting point and from j=i take sum of Like-time coefficient  
-> just to compare the till maximum sum and temp sum that start from i

---
# ☠️ My thought process
- too lazy
---

# 💻 Code
```cpp
class Solution {
public:
    int maxSatisfaction(vector<int>& s) 
    {
        int n=s.size();
        // sort to take maximum satisfaction at the end whole time 
        sort(s.begin(),s.end());
        // just to find from where we have to start the time 
        int sum=0,temp=0,cnt=0;
        //check for whole array
        for(auto e:s)
        {
            temp+=e*(cnt++);
        }
        
        sum=max(sum,temp);
        // let i is starting point and from j=i take sum of Like-time coefficient 
        for(int i=0;i<n;i++)
        {
            cnt=1;
            temp=0;
            for(int j=i;j<n;j++)
            {
                temp+=(s[j])*(cnt++);
            }
            // just to compare the till maximum sum and temp sum start from i
            sum=max(sum,temp);
        }
        return sum;
    }
};
```
---
