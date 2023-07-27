# 🧩 Que
- [Link](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)
You guess number if you guess wrong I say higher or lower. For a guessing a wrong number the cost is the value of that number. If I can choose from any number from 1 to n find the strategy that will result in min cost no matter the number I choose
```ad-question
title: Test Case
**Input:** n = 10
**Output:** 16
**Explanation:** The winning strategy is as follows:
- The range is [1,10]. Guess 7.
    - If this is my number, your total is $0. Otherwise, you pay $7.
    - If my number is higher, the range is [8,10]. Guess 9.
        - If this is my number, your total is $7. Otherwise, you pay $9.
        - If my number is higher, it must be 10. Guess 10. Your total is $7 + $9 = $16.
        - If my number is lower, it must be 8. Guess 8. Your total is $7 + $9 = $16.
    - If my number is lower, the range is [1,6]. Guess 3.
        - If this is my number, your total is $7. Otherwise, you pay $3.
        - If my number is higher, the range is [4,6]. Guess 5.
            - If this is my number, your total is $7 + $3 = $10. Otherwise, you pay $5.
            - If my number is higher, it must be 6. Guess 6. Your total is $7 + $3 + $5 = $15.
            - If my number is lower, it must be 4. Guess 4. Your total is $7 + $3 + $5 = $15.
        - If my number is lower, the range is [1,2]. Guess 1.
            - If this is my number, your total is $7 + $3 = $10. Otherwise, you pay $1.
            - If my number is higher, it must be 2. Guess 2. Your total is $7 + $3 + $1 = $11.
The worst case in all these scenarios is that you pay $16. Hence, you only need $16 to guarantee a win.
```

---
# Abstract
```ad-abstract
You can use MCM dp as it is. You guess a number from 1 to n and then reduce you seach space depending on the number you chose is smaller or bigger but since you don't know the answer just take max of both
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def getMoneyAmount(self, n: int) -> int:
        @cache
        def solve(st,ed):
            if st>=ed:
                return 0
            return min([k+max([solve(st,k-1),solve(k+1,ed)]) for k in range(st,ed+1)])
        return solve(1,n)
```
---
