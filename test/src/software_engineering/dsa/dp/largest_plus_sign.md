# 🧩 Que
- [Link](https://leetcode.com/problems/largest-plus-sign/)
You are given a matrix of `n*n` containing 0 and 1 figure out the largest plus sign you can create.
```ad-question
title: Test Case
![[Pasted image 20230709020619.png]]
```

---
# Abstract
```ad-abstract
You can use 4 grids to keep track of top bottom left and right and then compute your answer accordingly but we want to just use 1 dp grid
For each position `(i, j)`, we are only concerned with the minimum length of `1`'s out of the four directions. This implies we may combine the four matrices into one by only keeping track of the minimum length.
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
1. Create an `N-by-N` matrix `grid`, with all elements initialized with value `N`.
2. Reset those elements to `0` whose positions are in the `mines` list.
3. For each position `(i, j)`, find the maximum length of `1`'s in each of the four directions and set `grid[i][j]` to the minimum of these four lengths. Note that there is a simple recurrence relation relating the maximum length of `1`'s at current position with previous position for each of the four directions (labeled as `l`, `r`, `u`, `d`).
4. Loop through the `grid` matrix and choose the maximum element which will be the largest axis-aligned plus sign of `1`'s contained in the grid.
5. Appreciate the code and if you don't understand check [here](https://leetcode.com/problems/largest-plus-sign/solutions/113314/java-c-python-o-n-2-solution-using-only-one-grid-matrix/)
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def orderOfLargestPlusSign(self, N: int, mines: List[List[int]]) -> int:
	dp = [[N] * N for _ in range(N)]
	for r, c in mines:
		dp[r][c] = 0
	for i in range(N):
		l, r, t, b = 0, 0, 0, 0
		for j, k in zip(range(N), reversed(range(N))):
			l = 0 if dp[i][j] == 0 else l + 1
			dp[i][j] = min(dp[i][j], l)
			r = 0 if dp[i][k] == 0 else r + 1
			dp[i][k] = min(dp[i][k], r)
			t = 0 if dp[j][i] == 0 else t + 1
			dp[j][i] = min(dp[j][i], t)
			b = 0 if dp[k][i] == 0 else b + 1
			dp[k][i] = min(dp[k][i], b)
	return max(map(max, dp))
```
---
