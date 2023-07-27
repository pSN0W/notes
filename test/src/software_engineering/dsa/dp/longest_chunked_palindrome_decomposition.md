# 🧩 Que
- [Link](https://leetcode.com/problems/longest-chunked-palindrome-decomposition/)
You are given a string `text`. You should split it to k substrings `(subtext1, subtext2, ..., subtextk)` such that:

- `subtexti` is a **non-empty** string.
- The concatenation of all the substrings is equal to `text` (i.e., `subtext1 + subtext2 + ... + subtextk == text`).
- `subtexti == subtextk - i + 1` for all valid values of `i` (i.e., `1 <= i <= k`).

Return the largest possible value of `k`.
```ad-question
title: Test Case
**Input:** text = "ghiabcdefhelloadamhelloabcdefghi"
**Output:** 7
**Explanation:** We can split the string on "(ghi)(abcdef)(hello)(adam)(hello)(abcdef)(ghi)".
```

---
# Abstract
```ad-abstract
You can solve this problem in two ways.
- One is to iterate with an index i and whenever you see a valid partition you send call to solve for i+1. This continue for all the valid i. Something like forward partitioning.
- Next you can approach this question greedly as a smaller partition will always give you more number of such chunk because for a bigger partition you can break it into two smaller ones
```
[[palindrome_partitoning_ii]]
- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- For the first approach 
	- dp[i,j] -> whats the largest number of partiton between i and j.
	- To calculate it you can use an approach like [[palindrome_partitoning_ii]]. Just match the string both from front and back when you get correct one just call again
	- Now since you are matching j = n-i. so you can make do with just dp[i]. This is what you didn't do
- For the second approach
	- ![[Pasted image 20230705204815.png]]
	- And then the code is pretty simple just move from forward and backward and then compare when they are correct. If they match just do res++.
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def longestDecomposition(self, S):
	res, l, r = 0, "", ""
	for i, j in zip(S, S[::-1]):
		l, r = l + i, j + r
		if l == r:
			res, l, r = res + 1, "", ""
	return res
```
---
