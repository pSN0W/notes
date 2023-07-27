# 🧩 Que
- [Link](https://leetcode.com/problems/shortest-common-supersequence/)
Given two strings `str1` and `str2`, return _the shortest string that has both_ `str1` _and_ `str2` _as **subsequences**_.
```ad-question
title: Test Case
**Input:** str1 = "abac", str2 = "cab"
**Output:** "cabac"
**Explanation:** 
str1 = "abac" is a subsequence of "cabac" because we can delete the first "c".
str2 = "cab" is a subsequence of "cabac" because we can delete the last "ac".
The answer provided is the shortest such string that satisfies these properties.
```

---
# Abstract
```ad-abstract
The idea is to first get the LCS and then to that add the characters that are not common. Keep it up until you generate the final supersequence. 
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- The idea is to first use dp to get longest common sub-sequence.
- Now to generate the super sequence
	- If dp[i-1][j-1] + 1 = dp[i][j] and str1[i-1] == str2[j-1] then that means that the two characters are common so you can choose any one of them and reduce i and j
	- Otherwise if dp[i-1][j-1] == dp[i][j] then you are going to skip the ith character so add it and reduce i
	- Else dp[i][j-1] == dp[i][j] so you are skipping the jth character. so add it to your answer and reduce j.

---
# ☠️ My thought process
- You forgot to compare str1[i-1] == str[j-1]. You just did dp[i-1][j-1] + 1 == dp[i][j], this creates problem in some cases because of the way the dp matrix is populated
---

# 💻 Code

---
