# 🧩 Que
- [Link](https://practice.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)
There is a rat in a n * n matrix it is located at 1,1 and it wants to go to n,n. It can only go through places where grid is marked 1.
```ad-question
title: Test Case
**Input**:
N = 4
m[][] = {{1, 0, 0, 0},
         {1, 1, 0, 1}, 
         {1, 1, 0, 0},
         {0, 1, 1, 1}}
**Output:**
DDRDRR DRDDRR
**Explanation**:
The rat can reach the destination at (3, 3) from (0, 0) by two paths - DRDDRR and DDRDRR, when printed in sorted order we get DDRDRR DRDDRR.
```

---
# Abstract
```ad-abstract
The question is pretty standard you go to all the possible places until you reach the desired position the thing to look here is the way you mark your visited array you do it in such a fashion that it marks for the current subtree.
```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- The idea is pretty simple. For any position you go L,R,D,U and append the move to curr and store the curr in your final answer once you have reached desired position.
- The thing to see here is how visited is marked for the current subtree. If we have a global visited then it will result us in missing some cases like
If you mark the red move as visited you miss up on all the green moves
![[Pasted image 20230701021846.png]]
---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution{
    public:
    void getallpath(vector<vector<int>> &matrix,int n,int row,int col,vector<string> &ans,string cur){
        if(row>=n or col>=n or row<0 or col<0 or matrix[row][col] == 0)
        return ;
        
        if(row == n-1 and col == n-1)
        {
            ans.push_back(cur);
            return ;
        }
        
        //now if its one we have 4 calls
        matrix[row][col] = 0;
        
        getallpath(matrix,n,row-1,col,ans,cur+"U");
        getallpath(matrix,n,row,col+1,ans,cur+"R");
        getallpath(matrix,n,row,col-1,ans,cur+"L");
        getallpath(matrix,n,row+1,col,ans,cur+"D");
        
        matrix[row][col] = 1;
        
        return ;
    }
    vector<string> findPath(vector<vector<int>> &m, int n) {
        vector<string> ans;
        getallpath(m,n,0,0,ans,"");
        return ans;
    }
};
```
---
