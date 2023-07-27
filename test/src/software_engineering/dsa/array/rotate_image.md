# 🧩 Que
- [Link](https://leetcode.com/problems/rotate-image/)
Given an matrix rotate it in place
```ad-question
title: Test Case

![[Pasted image 20230629190656.png]]
```

---
```ad-abstract
The main idea is to look how one of the number traverse in the array and then build your algorithm according to that. It also helps to look at the matrix in parts like first decide how you can solve for the outer part [1,2,3,6,9,8,7,4] and then extend the solution to lower part. In this case.
swap(1,3) -> 1 reaches correct place
swap(3,7) -> 7 reaches correct place
swap(3,9) -> all reach correct place.
You can use a loop to revolve all the boundary element. Change the boundary to solve the inside one.
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Abstract explains it
- The main point is to think how everything works in term of indices.

---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution {
public:
    void print(vector<vector<int>>& arr){
        for(auto v:arr){
            for(int num:v)  cout<<num<<" ";
            cout<<endl;
        }
        cout<<endl;
    }
    void rotate(vector<vector<int>>& matrix) {
        int l = 0, r = matrix.size() - 1;
        while(l<r){
            int k = r;
            while(k>l){
                swap(matrix[l][k],matrix[r-k+l][l]);
                swap(matrix[r-k+l][l],matrix[r][r-k+l]);
                swap(matrix[r][r-k+l],matrix[k][r]);
                k--;
            }
            l++;
            r--;
        }
    }
};
```
---
