# 🧩 Que
- [Link](https://leetcode.com/problems/maximal-rectangle/)
Given a `rows x cols` binary `matrix` filled with `0`'s and `1`'s, find the largest rectangle containing only `1`'s and return _its area_.
```ad-question
title: Test Case
**Input:** matrix = [ 
["1","0","1","0","0"],
["1","0","1","1","1"],
["1","1","1","1","1"],
["1","0","0","1","0"]
 ]
**Output:** 6
**Explanation:** The maximal rectangle is shown in the above picture.
```

---
# Abstract
```ad-abstract
It uses the idea of [[largest_rectangle_histogram]]. At each row you can use 1s to form a histogram and then find max for each row and your answer will be max of all rows
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- At each level we can make histogram like this and the solve the [[largest_rectangle_histogram]] problem
- ![[Pasted image 20230702024017.png]]

---
# ☠️ My thought process
- You thought of something [[maximal_square]] and got stuck in it
---

# 💻 Code
```python
class Solution:
    def maximalRectangle(self, matrix: List[List[str]]) -> int:
        if not matrix:
            return 0
        maxarea=0
        height=[0]*(len(matrix[0]))
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                if matrix[i][j]=="1":
                    height[j]+=1
                else:
                    height[j]=0
				stack=[]
            for i,h in enumerate(height):
                start=i
                while stack and h<stack[-1][1]:
                    index,hi=stack.pop()
                    start=index
                    maxarea=max(maxarea,(i-index)*hi)
                stack.append([start,h])
            for i,h in stack:
                maxarea=max(maxarea,(len(height)-i)*h)
        return maxarea
```
---
