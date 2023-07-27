# 🧩 Que
- [Link](https://leetcode.com/problems/stickers-to-spell-word/)
We are given n different types of stickers. Each sticker has a lowercase English word on it.
You would like to spell out the given string target by cutting individual letters from your collection of stickers and rearranging them. You can use each sticker more than once if you want, and you have infinite quantities of each sticker.
Return the minimum number of stickers that you need to spell out target. If the task is impossible, return -1.
```ad-question
title: Test Case
**Input:** stickers = ["with","example","science"], target = "thehat"
**Output:** 3
**Explanation:**
We can use 2 "with" stickers, and 1 "example" sticker.
After cutting and rearrange the letters of those stickers, we can form the target "thehat".
Also, this is the minimum number of stickers necessary to form the target string.
```

---
# Abstract
```ad-abstract
Its the simple idea of you can choose one sticker and rearrange its character to create the target or you can choose another one. Now the problem is how do you keep track of characters that have already been found using previous stickers. You can use a count map for it or you can just bit mask the character that has been found
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Create a function that can mask a mask given a word. What this mask will do is for each not found characters of target it will see if it exist in itself. If it does then it will mask it.
- Your recursion will have two cases
	- use the current word again: To avoid infinite loop only use this if masking with this word changes the mask
	- Solve with the rest of idx+1 words
---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def minStickers(self, stickers: List[str], target: str) -> int:
        n = len(target)
        def mask_word(wrd,mask):
            cnt = Counter(wrd)
            for i in range(n):
                curr = target[n-i-1]
                if mask&(1<<i) and cnt.get(curr,0) > 0:
                    cnt[curr] -= 1
                    mask = mask^(1<<i)
            return mask
        @lru_cache(None)
        def solve(idx,mask):
            if mask == 0:
                return 0
            if idx>=len(stickers):
                return int(1e6)
            ans = int(1e6)
            # take current sticker 
            new_mask = mask_word(stickers[idx],mask)
            if new_mask != mask:
                ans = min([ans,solve(idx,new_mask)+1])
            
            # don't take current tsicker
            ans = min([ans,solve(idx+1,mask)])
            return ans
        ans = solve(0,(1<<n)-1)
        return ans if ans < int(1e6) else -1
```
---
