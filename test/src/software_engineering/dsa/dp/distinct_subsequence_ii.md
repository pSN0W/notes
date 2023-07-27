# 🧩 Que
- [Link](https://leetcode.com/problems/distinct-subsequences-ii/)
Given a string s, return _the number of **distinct non-empty subsequences** of_ `s`
```ad-question
title: Test Case
**Input:** s = "abc"
**Output:** 7
**Explanation:** The 7 distinct subsequences are "a", "b", "c", "ab", "ac", "bc", and "abc".
```

---
# Abstract
```ad-abstract
The main idea is to keep track of all the subsequence that end with a particular character. So basically you just want to count total number of subsequence ending with a given character. So if you have something like aba
initially with a you can build a
now with b you can build b, ab
now with the new a you can build a aa ab aba. You will have to remove the one that you previously built ending with a. 
So basically you can add the current character to the last of each of each subsequence generated till now to get the number of subsequence ending with current
```
This might look like [[subset_ii]] but it is not because there [1,2] and [2,1] are treated as same but not here
- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- https://leetcode.com/problems/distinct-subsequences-ii/solutions/192017/java-c-python-dp-4-lines-o-n-time-o-1-space/
- https://leetcode.com/problems/distinct-subsequences-ii/editorial/
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def distinctSubseqII(self, S):
        end = [0] * 26
        for c in S:
            end[ord(c) - ord('a')] = sum(end) + 1
        return sum(end) % (10**9 + 7)
```
---
