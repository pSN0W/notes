# 🧩 Que
- [Link](https://leetcode.com/problems/largest-rectangle-in-histogram/)
You are given a histogram you need to find the largest rectangle formed in the histogram.
![[Pasted image 20230630175232.png]]
```ad-question
title: Test Case
**Input:** heights = [2,1,5,6,2,3]
**Output:** 10
**Explanation:** The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.
```

---
# Abstract
```ad-abstract
The idea is to use [[monotonic_stack]]. Consider iterating through the array and find out the maximum rectangle you can form with the height of the rectangle as the current histogram height and considering that bar. You will need to find the index of the bar just smaller then current to left and right. The distance between the two will be the width for the rectangle
```

- Tags #revise #standard_que #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- For each element calculate the next smaller element to the right using [[monotonic_stack]].
- Iterate through the array and calculate the prev smaller element and compute area of rectangle and get maximum area.

---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        stack<int> st;
        int n = heights.size();
        vector<int> rt(n,n);
        for(int i=n-1;i>=0;i--){
            while(!st.empty() and heights[st.top()]>=heights[i]) st.pop();
            rt[i] = st.empty() ? n : st.top();
            st.push(i);
        }
        int ans = INT_MIN;
        while(!st.empty())  st.pop();
        for(int i=0;i<n;i++){
            while(!st.empty() and heights[st.top()]>=heights[i]) st.pop();
            int lft = st.empty() ? -1 : st.top();
            st.push(i);
            int curr = (rt[i]-lft-1)*heights[i];
            ans = max(ans,curr);
        }
        return ans;
    }
};
```
---
