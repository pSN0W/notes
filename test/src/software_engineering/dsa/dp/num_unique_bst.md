# 🧩 Que
- [Link](https://leetcode.com/problems/unique-binary-search-trees/)
The question is pretty standard. You are given number of nodes and you need to find out the number of bst from it.

```ad-question
title: Test Case
**Input:** n = 3 <br>
**Output:** 5
```
![[Pasted image 20230629141558.png]]
---
```ad-abstract
You have to consider the root node for your bst. If for bst of size 3 your root node is 2 then to the left of it you will have bst from of size 1 [1] and to right of size 1 [3]. 
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Find number of ways to create a tree with 1 node using the recurrence described in abstract. Once you have number of ways to create bst for 1 you can calculate number of ways for 2 similarly
- dp(0) = 1
- for j in [1..i] -> dp[i] += dp[j-1]* dp[i-j]

---
# ☠️ My thought process
- 
---

# 💻 Code

```cpp
class Solution {
public:
	int numTrees(int n) {
		vector<int> dp(n+1);
		dp[0] = 1;
		for(int i=1;i<=n;i++){
		for(int j=1;j<=i;j++){
		dp[i] += dp[j-1]*dp[i-j];
		}
		}
		return dp[n];
	}
};
```
---
