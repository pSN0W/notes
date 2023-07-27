# 🧩 Que
- [Link](https://leetcode.com/problems/course-schedule-ii/)
You are given a course and the pre requisite for taking the course. Return the correct order of taking the course
```ad-question
title: Test Case
**Input:** numCourses = 2, prerequisites = [ [1,0] ]
**Output:** [0,1]
**Explanation:** There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1].
```

---
# Abstract
```ad-abstract
You can create a graph of the dependencies and then topo sort that graph to get the correct answer
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
```python
from queue import Queue
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        graph = {i:[] for i in range(numCourses)}
        in_node = [0]*numCourses
        for course,depend_on in prerequisites:
            graph[depend_on].append(course)    
            in_node[course]+=1
        q = Queue()
        for i,nm in enumerate(in_node):
            if nm == 0:
                q.put(i)
        order = []
        while not q.empty():
            tp = q.get()
            order.append(tp)
            for nbr in graph[tp]:
                in_node[nbr]-=1
                if in_node[nbr] == 0:
                    q.put(nbr)
        return order if len(order) == numCourses else []
        
```
---
