# 🧩 Que
- [Link](https://www.interviewbit.com/problems/stepping-numbers/)
Given A and B you have to find all stepping numbers in the range A to B (both inclusive).
The stepping number:
A number is called as a stepping number if the adjacent digits have a difference of 1.
```ad-question
title: Test Case
10,20
[10,12]
```

---
# Abstract
```ad-abstract
The idea is to generate all number up to the length of B and for each number check if it lies between A and B. What you can do for this is to the current number add last_dog -+ 1. See code
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
vector<int> Ans;
void dfs(int len, int N, int M, int num = 0) {
    if(num >= N && num <= M) {
            Ans.push_back(num);
     }
     if(len == 0)
        return;
    

    if(num == 0) {
        for(int i = 1; i <= 9; ++i) {
            dfs(len - 1, N, M, i);
        }
        return;
    }

    int last_dig = num%10;
    if(last_dig == 0) {
    
        dfs(len - 1, N, M, (num * 10) + (last_dig + 1));
    
    } else if(last_dig == 9) {
    
        dfs(len - 1, N, M, (num * 10) + (last_dig - 1));
    
    } else {
        dfs(len - 1, N, M, (num * 10) + (last_dig - 1));
        dfs(len - 1, N, M, (num * 10) + (last_dig + 1));
    }
}

vector<int> Solution:: stepnum(int N, int M) {
    int len = 0;
    int temp = M;
    Ans.clear();
    while(temp) {
        temp /= 10;
        len++;
    }

    Ans.clear();
    dfs(len, N, M);
    sort(Ans.begin(), Ans.end());
    return Ans;
}

```
---
