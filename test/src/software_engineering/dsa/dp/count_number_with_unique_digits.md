# 🧩 Que
- [Link](https://leetcode.com/problems/count-numbers-with-unique-digits/)
Given an integer n you have to return numbers from 0 to 10^n. Whose all digits are unique
```ad-question
title: Test Case
**Input:** n = 2
**Output:** 91
**Explanation:** The answer should be the total numbers in the range of 0 ≤ x < 100, excluding 11,22,33,44,55,66,77,88,99
```

---
# Abstract
```ad-abstract
YOUR DUMBASS THOUGHT OF DP. It is really simple think in term of permutation. 3 places and ways to fill it is `9*9*8`
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- Figuring out it is a permutation question and not a dp.
- When building dp with integers in a range always take care of 00

---
# ☠️ My thought process
- You thought out to figure the number of repeating numbers and subtract from whole.
- For this you thought of how do you insert the first character. The possibilities were. At 1 insert 1-9 and then see number of non unique from [n-2]. Next possibility was to create unique yourself so insert 1-9 to 1 and then insert the same at 1 more place and for rest it's just 10C(n-2)* (n-2)!
- You missed out for 0 repeated
---

# 💻 Code

---
```c++
class Solution {
public:
	// you can compute this in one go too
    int get(int n){
        if(n==1)    return 10;
        int ans = 9;
        for(int i=0;i<n-1;i++)    ans*=(9-i);
        return ans;
    }
    int countNumbersWithUniqueDigits(int n) {
        if(n==0)    return 1;
        int ans = 0;
        for(int i=1;i<=n;i++)   ans+=get(i);
        return ans;
    }
};
```