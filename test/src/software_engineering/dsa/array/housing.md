# 🧩 Que
- Link
There is a sequence of vacant plots of land each plot has different non zero area. You want to buy K acres of land you want to find all segment of contiguous plot whose sum is exactly k.
```ad-question
title: Test Case
**Input** [1, 3, 2, 1, 4, 1, 3, 2, 1, 1, 2]
**Output** [ [2, 5], [4, 6], [5, 9] ]
```

---
# Abstract
```ad-abstract
You can use a sliding window. First expand the array til the sum is greater then current and then contract the array
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Make all the subarray and then sum the sub array (O(n^3))
- Make all subarray and use prefix sum for sum (O(n^2))
- Prefix sum with binary search (O(nlgn))
	- One thing that you will find out that prefix sum is sorted so assume then the current index is end and find the value of curr_sum - target_sum using binary search.
- Prefix Sum with lookup table (O(n), O(n))
	- Use an unordered set to see if the curr_sum-target_sum exist. This won't give you index
- Use a sliding window and then expand and contract the window given the sum in the window.
---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int i=0, j = 0, cs = 0;
while(j<n){
	cs += arr[j];
	j++;
	while(cs > k and i<j){
		cs -= arr[i];
		i++;
	}
	if(cs==k)   cout<<i<<" "<<j<<endl;
}
```
---
