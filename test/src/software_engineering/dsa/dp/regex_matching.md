# 🧩 Que
- [Link](https://leetcode.com/problems/regular-expression-matching/)
Given a string and a pattern check if string matches the pattern. Pattern contains 2 special characters:
- `'.'` Matches any single character.​​​​
- `'*'` Matches zero or more of the preceding element.
```ad-question
title: Test Case
**Input:** s = "aa", p = "a"
**Output:** false
**Explanation:** "a" does not match the entire string "aa".
```

---
# Abstract
```ad-abstract
The idea is to match from behind. As you might need to skip the character before `*` depending on the situation. Its really simple start from behind. if there is a match between current index of string and pattern then check for the next one. If the current char is * then you can have multiple option you can match the prev character 0..inf times. To simplify it what you can do is skip the number preceding * or match it again in next iteration too. See code
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- First thing you need to figure out the base cases
	- If i<0 and j<0 then return True -> obvious
	- If j<0 return False -> obvious
	- if i<0 and p[j] != `*` return false. This is because with *  you can skip chars too consider. `aab` with `c*a*b`
- Next for non star its pretty simple for star there are two cases:
	- Skip matching with number before star. call f(i,j-2)
	- Match if it is matching and have possibility to match again f(i-1,j)

---
# ☠️ My thought process
- You didn't get the skip thing and started from begining
- You used the method you were looking at previously like [[book_shelf_ordering]] and you added a loop and then matched with all possible something like the one shown below. This was correct too but more prone.
```python
if p[j] == "*":
	idx = i
	while idx>=0 and is_match(idx,j-1):
		idx-=1
		ans = ans or solve(idx,j-2)
	# skip the current *
	ans = ans or solve(i,j-2)
```
---

# 💻 Code
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        n,m = len(s),len(p)
        def is_match(i,j):
            if i<0 or j<0:
                return False
            return s[i] == p[j] or p[j] == '.'
        @lru_cache(None)
        def solve(i,j):
            #print(i,j)
            if i<0 and j<0:
                return True
            if j<0:
                return False
            if i<0 and p[j]!="*":
                return False
            ans = is_match(i,j) and solve(i-1,j-1)
            # consider the match
            if p[j] == "*":
                # skip current one
                ans = ans or solve(i,j-2)
                # if match then consider the current one
                if is_match(i,j-1):
                    ans = ans or solve(i-1,j)
            return ans
        return solve(n-1,m-1)
```
---
