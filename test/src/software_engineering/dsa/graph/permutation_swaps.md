# 🧩 Que
- [Link](https://www.interviewbit.com/problems/permutation-swaps/)
Rishabh has a permutation of N integers 1..N A he wants to change it to B. Rishabh has M good pairs 1 indexed array whose indexes he can swap. Find if it is possible to get B  
```ad-question
title: Test Case
Input 1:

 A = [1, 3, 2, 4]
 B = [1, 4, 2, 3]
 C = [ 
        [3, 4]
     ]
Input 2:

 A = [1, 3, 2, 4]
 B = [1, 4, 2, 3]
 C = [
        [2, 4]
     ] 
Output 1:

 0
Output 2:

 1
Explanation 1:

 As A != B you have to perform operations on A but there is only good pair available i,e (3, 4) so if you swap
 A3 with A4 you get A = [1, 3, 4, 2] which is not equal to B so we will return 0.
Explanation 2:

 As A != B you have to perform operations on A but there is only good pair available i,e (2, 4) so if you swap
 A2 with A4 you get A = [1, 4, 2, 3] which is equal to B so we will return 1.
```

---
# Abstract
```ad-abstract
If you group all the swap indexes then you can go from any index in that group to another with n number of swaps, that means lets say you have pair of 1-2 and 2-3 and 4-5. You can create two connected graoh 1-2-3 and 4-5. By performing swaps you can take any index of one component to another i.e you can go from 1-3 too. So you just is DSU to create groups of connected components and if the mismatch are both part of the same group than you can possibly perform swaps to get the desired answer
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- Create a DSU with the elements in C.
- Wherever there is mismatch between A and B. Find index of that B in A and if both the indexes have same parent then you can have what you want.

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class DisjointSet
{
    vector<int> rank, parent, size;

public:
    DisjointSet(int n)
    {
        // n+1 so that it can work for 1 based indexing
        rank.resize(n + 1, 0);
        size.resize(n + 1, 0);
        parent.resize(n + 1);
        for (int i = 0; i <= n; i++){
            parent[i] = i;
            size[i] = 1;
        }
    }

    int findParent(int node){
        if (node == parent[node]){
            return parent[node];
        }
        // path compression step
        return parent[node] = findParent(parent[node]);
    }

    void unionByRank(int u, int v){
        int ulp_u = findParent(u);
        int ulp_v = findParent(v);
        if (ulp_u == ulp_v)
            return;
        if (rank[ulp_u] < rank[ulp_v]){
            parent[ulp_u] = ulp_v;
        }
        else if (rank[ulp_u] > rank[ulp_v]){
            parent[ulp_v] = ulp_u;
        }
        else{
            parent[ulp_v] = ulp_u;
            rank[ulp_u]++;
        }
    }

    void unionBySize(int u, int v)
    {
        int ulp_u = findParent(u);
        int ulp_v = findParent(v);
        if (ulp_u == ulp_v)
            return;
        if (size[ulp_u] < size[ulp_v]){
            parent[ulp_u] = ulp_v;
            size[ulp_v] += size[ulp_u];
        }
        else{
            parent[ulp_v] = ulp_u;
            size[ulp_u] += size[ulp_v];
        }
    }

    int getSize(int x){
        return size[x] = size[findParent(x)];
    }
};

int Solution::solve(vector<int> &A, vector<int> &B, vector<vector<int> > &C) {
    int n=A.size();
    DisjointSet ds(n+1);
    
    for(auto it : C){
        int u=it[0], v=it[1];
//since C contains index of elements of vector A which can be swapped
        ds.unionBySize(A[u-1], A[v-1]);
    }
    
    for(int i=0; i<n; i++){
        if(A[i] != B[i] && ds.findParent(A[i]) != ds.findParent(B[i])){
            return 0;
        }
    }
    return 1;
}
```
---
