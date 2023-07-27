# 🧩 Que
- [Link](https://leetcode.com/problems/max-value-of-equation/)
Given an array of points sorted by x values return the maximum value of equation `yi + yj + |xi - xj|` where `|xi - xj| <= k` and `1 <= i < j <= points.length`.
```ad-question
title: Test Case
**Input:** points = [ [1,3],[2,0],[5,10],[6,-10] ], k = 1
**Output:** 4
**Explanation:** The first two points satisfy the condition |xi - xj| <= 1 and if we calculate the equation we get 3 + 0 + |1 - 2| = 4. Third and fourth points also satisfy the condition and give a value of 10 + -10 + |5 - 6| = 1.
No other pairs satisfy the condition, so we return the max of 4 and 1.
```

---
# Abstract
```ad-abstract
Since xj > xi the equation can be broken into yj + xj + yi - xi. You can just iterate through the array compute the value of yj+xj on fly and store the value of yi-xi in a heap. You should check if top of heap satisfies the condition |xi-xj| <= k
```

- Tags #unsolved #revise 
--- 
# 🕵️‍♂️ Main Logic
- Break the equation first.
- If you are at an index j you can compute yj+xj what is left is getting max of yi-xi such that |xi - xj| <= k. You can use heap for this.
- Iterate through the array and for any index j lookup the heap top element. If top element doesn't follow the constraints on x then drop it as this constrain will not be followed for future members too given the array is sorted. 
- Compute current value using heap top element and current index insert yj-xj, xj in the heap.

---
# ☠️ My thought process
- Couldn't think of using heap for this
---

# 💻 Code
```c++
class Solution {
public:
    int findMaxValueOfEquation(vector<vector<int>>& points, int k) {
        priority_queue<pair<int,int>> pq;
        int ans = INT_MIN;
        for(auto v:points){
            int x = v[0];
            int y = v[1];
            while(!pq.empty() and x - pq.top().second>k)    pq.pop();
            if(!pq.empty()) ans = max(ans,x+y+pq.top().first);
            pq.push({y-x,x});
        }
        return ans;
    }
};
```
---
