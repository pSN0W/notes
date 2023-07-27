# 🧩 Que
- [Link](https://leetcode.com/problems/palindrome-partitioning-ii/)
Given a string s partition s such that every partition is a palindrome. Return the minimum number of cuts required.
```ad-question
title: Test Case
**Input:** s = "aab"
**Output:** 1
**Explanation:** The palindrome partitioning ["aa","b"] could be produced using 1 cut.
```

---
# Abstract
```ad-abstract
This is very similar to [[palindrome_partitioning]]. Here you just have to return the minimum. You solved the question but there are some good optimisations. The main idea is to use the middle element to remove the need of storeing if [i..j] is a palindrome. Check main_logic
```

- Tags #unsolved #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- The simplest way to solve this problem is to do as you did in [[palindrome_partitioning]], but there you were wasting extra O(n) time to check if the number is partition or not. To reduce that you can pre-compute where `arr[i][j]` tells if s[i:j] is palindrome or not.
- Now this will require O(n * n) extra space. To solve this without the extra space and with pre-computation you can do the following.
- cuts[i] denotes the number of minimum cuts required to partition from 0->i
- Let's think for a single i and assume that it is in the middle of the sub string. You increase the pointer in left and right direction of it if the chars there match
	- if the left points to k and right points to l then we can update cuts[l] as cuts[k]+1
- Apply a similar approach for when the number of palindrome substring is even
---
# ☠️ My thought process
- When you thought of this you thought of how to solve for the middle element that is you were using f(i,j) which represents minimum cuts between i and j.
- For an element i you can move left and right to reach k and l. and the you answer for there will be f(0,k) + f(l,n) + 1
---

# 💻 Code
```c++
class Solution {
public:
    int minCut(string s) {
        int n = s.size();
        vector<int> cut(n+1, 0);  // number of cuts for the first k characters
        for (int i = 0; i <= n; i++) cut[i] = i-1;
        for (int i = 0; i < n; i++) {
            for (int j = 0; i-j >= 0 && i+j < n && s[i-j]==s[i+j] ; j++) // odd length palindrome
                cut[i+j+1] = min(cut[i+j+1],1+cut[i-j]);

            for (int j = 1; i-j+1 >= 0 && i+j < n && s[i-j+1] == s[i+j]; j++) // even length palindrome
                cut[i+j+1] = min(cut[i+j+1],1+cut[i-j+1]);
        }
        return cut[n];
    }
};
```
---
