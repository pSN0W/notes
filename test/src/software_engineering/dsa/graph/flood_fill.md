# 🧩 Que
- Link
You are given a grid and you want to find total number of island in that grid. 1 denotes land and 0 denotes water
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You find a land cell and then go in all four directions from there.
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Questions derived from this
	- Check two cordinates belong to same island or not
		- Just color each of the island by passing in a color and then check if the two coordinates have the same color.
		- When you go to any node `colors[x][y] = col`
	- You want to know the size of each island too
		- Create one for array for colour count and populate it.
		- When you go to any node `col_count[colors]+=1`
	- You can flip one water to land find the largest island now.
		- Color then compute size and then for each water point just flip it and check its four nearest neighbor and see if you can combine them.
		- **NOTE** check that its four neighbor have different color it might be possible that same island is connected from left as well as from top.


---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int n,m;
int a[n][m];
int dx[4] = {0,0,1,-1}, dy[4] = {1,-1,0,0};
void flood_fill(int x,int y){
	a[x][y] = 0; // mark it as visited
	for(int i=0;i<4;i++){
		for(int j=0;j<4;j++){
			int xx = x+dx, yy = y +dy;
			if(inbound(xx,yy) and a[xx][yy]==1){
				flood_fill(xx,yy);
			}
		}
	}
}
int main(){
	int tot_count = 0;
	for(int i=0;i<n;i++){
		for(int j=0;j<m;j++){
			if(a[i][j]==1){
				flood_fill(i,j);
				tot_count+=1;
			}
		}
	}
}
```
---
