# 🧩 Que
- [Link](https://leetcode.com/problems/word-break-ii/)
Given a string s and a dictionary of strings wordDict, add spaces in s to construct a sentence where each word is a valid dictionary word. Return all such possible sentences in any order.
```ad-question
title: Test Case
Input: s = "catsanddog", wordDict = ["cat","cats","and","sand","dog"]
Output: ["cats and dog","cat sand dog"]
```

---
# Abstract
```ad-abstract
Its same idea as [[palindrome_partitioning]] you just do forward partition that means for an index i check all the possible words that match and for them generate the subset
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- Code

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> List[str]:
        n = len(s)
        @lru_cache(None)
        def solve(idx):
            if idx==n:
                return [""]
            curr = []
            for word in wordDict:
                if idx+len(word)<=n and s[idx:idx+len(word)]==word:
                    sub_prob = solve(idx+len(word))
                    if len(sub_prob) > 0:
                        for poss_sub in sub_prob:
                            curr.append(word+" "+poss_sub)
            return curr
        return [x.strip() for x in solve(0)]
```
---
