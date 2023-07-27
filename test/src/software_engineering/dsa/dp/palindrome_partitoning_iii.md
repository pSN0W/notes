# 🧩 Que
- [Link](https://leetcode.com/problems/palindrome-partitioning-iii/)
You are given a string `s` containing lowercase letters and an integer `k`. You need to :

- First, change some characters of `s` to other lowercase English letters.
- Then divide `s` into `k` non-empty disjoint substrings such that each substring is a palindrome.

Return _the minimal number of characters that you need to change to divide the string_.
```ad-question
title: Test Case
**Input:** s = "abc", k = 2
**Output:** 1
**Explanation:** You can split the string into "ab" and "c", and change 1 character in "ab" to make it palindrome.
```

---
# Abstract
```ad-abstract
This is complete copy of [[palindrome_partitioning]]. You do a similar forward partitonaning while previously you were calling j+1 only when s[i:j] was palindrome now s[i:j] will have a cost associated with it for converting it to palindrome.
```
[[palindrome_partitioning]]
- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- For base case
	- If your k is 0 and you have completed the array then return 0
	- If your k gets 0 or index out of range return 1e6
- Now for every index you will have to compute cost of s[i:j] which will be just the number of mismatch between them.
- For each of the j you want the one which gives you the minimum answer

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def palindromePartition(self, s: str, k: int) -> int:
        def compute_cost(curr):
            i,j = 0,len(curr)-1
            diff = 0
            while j>i:
                if curr[j]!=curr[i]:
                    diff+=1
                j-=1
                i+=1
            return diff
        n = len(s)
        @lru_cache(None)
        def solve(i,k):
            if i>=n:
                return 0 if k==0 else 1e6
            if k==0:
                return 1e6
            ans = 1e6
            for j in range(i+1,n+1):
                ans = min([ans,compute_cost(s[i:j])+solve(j,k-1)])
            return ans
        return solve(0,k)
```
---
