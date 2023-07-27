# 🧩 Que
- [Link](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/)
Given a string find minimum insertion to make it a palindrome. 
```ad-question
title: Test Case
**Input:** s = "zzazz"
**Output:** 0
**Explanation:** The string "zzazz" is already palindrome we do not need any insertions.
```

---
# Abstract
```ad-abstract
First find the largest common palindrome subsequence and then find the number of insertion required as n - lps
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution {
public:
    int lcs(string s1,string s2){
        int n = s1.size()+1;
        vector<vector<int>> dp(n,vector<int>(n,0));
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(i==0 or j==0)    continue;
                if(s1[i-1]==s2[j-1])    dp[i][j] = 1 + dp[i-1][j-1];
                else    dp[i][j] = max(dp[i-1][j],dp[i][j-1]);
            }
        }
        return dp[n-1][n-1];
    }
    int longest_palindrome_subsequence(string s){
        string s1 = s;
        reverse(s.begin(),s.end());
        return lcs(s,s1);
    }
    int minInsertions(string s) {
        int n = s.size();
        int lps = longest_palindrome_subsequence(s);
        return n - lps;
    }
};
```
---
