# 🧩 Que
- [Link](https://leetcode.com/problems/furthest-building-you-can-reach/)
You are given height of building. You can go from one building to another using ladders or brick of the size of difference of the building return the farthest you can reach.
```ad-question
title: Test Case
**Input:** heights = [4,2,7,6,9,14,12], bricks = 5, ladders = 1
**Output:** 4
**Explanation:** Starting at building 0, you can follow these steps:
- Go to building 1 without using ladders nor bricks since 4 >= 2.
- Go to building 2 using 5 bricks. You must use either bricks or ladders because 2 < 7.
- Go to building 3 without using ladders nor bricks since 7 >= 6.
- Go to building 4 using your only ladder. You must use either bricks or ladders because 6 < 9.
It is impossible to go beyond building 4 because you do not have any more bricks or ladders.
```

---
# Abstract
```ad-abstract
If you think rationally you will use ladder to scale the largest building till now so what you can do is. Create a max heap of the size of ladder and then iterate on the difference you put the current difference in heap and take out the minimum one. Use brick to scale that 
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
from heapq import heappush,heappushpop
class Solution:
    def furthestBuilding(self, heights: List[int], bricks: int, ladders: int) -> int:
        diff = [max([x-y,0]) for x,y in zip(heights[1:],heights[:-1])]
        pq = []
        ans = 0
        for num in diff[:ladders]:
            ans += 1
            heappush(pq,num)
        for num in diff[ladders:]:
            req = heappushpop(pq,num)
            if req>bricks:
                return ans
            ans+=1
            bricks -= req
        return ans
```
---
