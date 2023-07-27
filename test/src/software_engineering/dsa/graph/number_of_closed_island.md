# 🧩 Que
- [Link](https://leetcode.com/problems/number-of-closed-islands/)
Given a 2D `grid` consists of `0s` (land) and `1s` (water).  An _island_ is a maximal 4-directionally connected group of `0s` and a _closed island_ is an island **totally** (all left, top, right, bottom) surrounded by `1s.`

Return the number of _closed islands_.
```ad-question
title: Test Case
![[Pasted image 20230709172701.png]]
```

---
# Abstract
```ad-abstract
The idea is to visit the land islands at the boundary of the grid. Once you do this rest of the island are your answer
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- First visit all the islands/lands that are at the border of the matrix.
- Left of the islands were shielded from not being at the border of matrix or being part of disallowed islands because they were shielded by 1. So these are the required answer

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:

    void dfs(vector<vector<int>>&gr , int i, int j){
        if(i==gr.size() || j == gr[0].size() || j<0 || i<0 ) return;
        if(gr[i][j]==1) return;
        gr[i][j]=1;
        dfs(gr,i+1,j);
        dfs(gr,i-1,j);
        dfs(gr,i,j-1);
        dfs(gr,i,j+1);
    }

    int closedIsland(vector<vector<int>>& gr) {
        int n= gr.size();
        int m = gr[0].size();
        for(int i=0;i<n;i++){
            if(gr[i][0]==0){
                dfs(gr,i,0);
            }
            if(gr[i][m-1]==0){
                dfs(gr,i,m-1);
            }
        }
        for(int i=0;i<m;i++){
            if(gr[0][i]==0){
                dfs(gr,0,i);
            }
            if(gr[n-1][i]==0){
                dfs(gr,n-1,i);
            }
        }
        int c=0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(gr[i][j]==0){
                    c++;
                    dfs(gr,i,j);
                }
            }
        }
        return c;
    }
};
```
---
