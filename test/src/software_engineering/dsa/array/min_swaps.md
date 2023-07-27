# 🧩 Que
- Link
Given an array find the minimum number of swaps that is needed to make the array sorted
```ad-question
title: Test Case
**Input**: [10, 11, 5, 4, 3, 2, 1]
**Output**: 4
```

---
# Abstract
```ad-abstract
The idea is that you have to find out what swaps you will have to make to get the numbers to their correct position. You will find out that these number form a circle and number of swap to fix that circle is len(circle) - 1 
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Lets look at what positions the elements of the array will take in the sorted order
![[Pasted image 20230715195204.png]]
- You see the circles getting formed you can perform swap in that order to get the number of swap.
- To calculate this what you can do is sort the array with indexes and then see how thse indexes form circle. 
- Look at the code to see how this is implemented
---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int countMinSwap(vector<int> arr){
	int ans = 0
	pair<int,int> ap[n];
	for(int i=0;i<n;i++){
		ap[i].first = arr[i];
		ap[i].second = i;
	}
	sort(ap,ap+n);
	vector<bool> visited(n,false);
	for(int i=0;i<n;i++){
		int old_index = ap[i].second;
		if(visited[i] || old_index==i)   continue;
		int node = i;
		int cycle = 0;
		while(!visited[node]){
			visited[node] = true;
			node = ap[node].second;
			cycle+=1;
		}
		ans += cycle;
	}
	return ans;
}
```
---
