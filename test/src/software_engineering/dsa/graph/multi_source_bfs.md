# 🧩 Que
- Link
There is a rectangular grid of size `n*m` each cell is either black or white. Distance between each cell is defined as the manhattan distance find the nearest white cell for each cell
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
In the brute force you will start bfs from every black cell and then go on until you meet a white cell.
What you can do instead is start a multi source bfs form each of the white cell and see how much distance it take them to reach one of the node.
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Lets say you white cells are a and d so put them in queue and then take them out one by one and then put their neighbors in the queue.
- Similar questions
	- You are given a grid and every second a white square that shares a side with black becomes black find time when all the cells are black.
	- You are given a binary grid where you can travel through 0 but not through 1. You want to start at any column at row 0 and reach at any column of row n. Find minimum distance.
		- Start multi source bfs from all the cell of row 0 with column value > 0.
	

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
// for all white cell push it in queue
while(!q.empty()){
	int x = q.front().first;
	int y = q.front().second;
	q.pop();
	for(int i=0;i<4;i++){
		int xx = dx[i]+x, yy = dy[i]+y;
		if(inbound(xx,yy) and dist[xx][yy]==INT_MAX){// for unvisited
			q.push({xx,yy});
			dist[xx][yy] = 1 + dist[x][y]; // distance is 1 more than parent
		}
	}
}
```
---
