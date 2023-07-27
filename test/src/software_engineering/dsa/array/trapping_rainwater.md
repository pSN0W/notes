# 🧩 Que
- [Link](https://www.interviewbit.com/problems/rain-water-trapped/)
Given an integer array A of non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.
```ad-question
title: Test Case
A = [0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]
Ans = 6
```

---
# Abstract
```ad-abstract
The idea is pretty simple. You compute the right max pillar and left max pillar and then the amount of trapped rainwater is the min between them. The current implementation reduces the space complexity by using two pointers one from the left and another from the right. Check it out.
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int Solution::trap(const vector<int> &A) {
    int len=A.size();
    int min=0,prev=0,i=0,j=len-1,ans=0;
    while(i<=j){
        min=A[i]<=A[j]?i++:j--;
        if(prev>A[min]){
            ans+=prev-A[min];
        }
        else
            prev=A[min];
    }
    return ans;
}
```
---
