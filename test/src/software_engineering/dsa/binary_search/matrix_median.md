# 🧩 Que
- Link
Given a matrix A of size `N*M` in which each row is sorted. Find the overall median of A
```ad-question
title: Test Case
[
	[1, 3, 5],
	[2, 6, 9],
	[3, 6, 9]
]
Ans = 5
```

---
# Abstract
```ad-abstract
Since the row are sorted you can use it to your advantage. We can search for the median in min(A) to max(A). For each possible median you can just find the number of elements greater or less that that in each row. **To deal with duplicates hi=m**
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- You can solve it using priority queue, Just ensure that length of pq does not increase n//2.

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int Solution::findMedian(vector<vector<int> > &matrix) {
    int r=matrix.size();
    int c=matrix[0].size();
    int k = (r * c + 1) / 2;
        int a = INT_MAX;
        int b = INT_MIN;
        for(int i = 0; i < r; i++){
            a = min(a, matrix[i][0]);
            b = max(b, matrix[i][c-1]);
        }
        while(a < b){
            int m = (a + b) / 2;
            int count = 0;
            for(int i = 0; i < r; i++)
                count = count + upper_bound(matrix[i].begin(), matrix[i].end(), m) - matrix[i].begin();
            if(count < k) a = m + 1;
            else b = m;
        }
        return a;
}
```
---
