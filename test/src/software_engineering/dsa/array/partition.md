# 🧩 Que
- [Link](https://www.interviewbit.com/problems/partitions/)
You are given an array divide it into three parts such that sum of each parts is same
```ad-question
title: Test Case
B = [1, 2, 3, 0, 3]
Ans = 2
There are no 2 ways to make partitions -
1. (1,2)+(3)+(0,3).
2. (1,2)+(3,0)+(3).
```

---
# Abstract
```ad-abstract
If the sum of the array is not divisble by 3 then leave it. If you can make the sum/3 in a ways then for every time you make 2*sum/3 you can divide the array into a segments.
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
int Solution::solve(int A, vector<int> &B) {

    

    if(A < 3) return 0;

    

    int totalSum = 0, sum = 0, ans = 0;

    

    for(int num: B) totalSum+= num;

    if(totalSum%3 != 0) return 0;

    

    int x = totalSum/3;

    int twiceX = x*2;

    int xCount = 0;

    

    for(int idx = 0; idx < A - 1; idx++) {

        

        sum+= B[idx];

        

        if(sum == twiceX) ans+= xCount;

        if(sum == x) xCount++;

    }

    

    return ans;

}
```
---
