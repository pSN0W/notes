# 🧩 Que
- [Link](https://leetcode.com/problems/interleaving-string/)
Given strings `s1`, `s2`, and `s3`, find whether `s3` is formed by an **interleaving** of `s1` and `s2`.
```ad-question
title: Test Case
**Input:** s1 = "aabcc", s2 = "dbbca", s3 = "aadbbcbcac"
**Output:** true
**Explanation:** One way to obtain s3 is:
Split s1 into s1 = "aa" + "bc" + "c", and s2 into s2 = "dbbc" + "a".
Interleaving the two splits, we get "aa" + "dbbc" + "bc" + "a" + "c" = "aadbbcbcac".
Since s3 can be obtained by interleaving s1 and s2, we return true.
```

---
# Abstract
```ad-abstract
At each step you have two option either take a character from s1 or take a character from s2 and match
```

- Tags #unsolved #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- **Initialize** the **interleaved** table of size (m+1) x (n+1).
- Iterate through each cell of the interleaved table using two nested loops.
- For each cell (i, j), there are following cases:
    1. If both **s1 and s2 are empty strings** (i.e., i == 0 and j == 0), then **interleaved[i][j] is set to true** since there are no characters to interleave.
    2. If **s1 is empty** (i.e., i == 0), then **interleaved[i][j]** is determined by **comparing s2[j-1] with s3[i+j-1]** and the **previous cell interleaved[i][j-1]**.
    3. If **s2 is empty** (i.e., j == 0), then **interleaved[i][j]** is determined by comparing **s1[i-1] with s3[i+j-1]** and the **previous cell interleaved[i-1][j]**.
    4. If both **s1 and s2 are non-empty**, **interleaved[i][j]** is determined by **comparing s1[i-1] with s3[i+j-1]** and the **previous cell interleaved[i-1][j]**, as well as **comparing s2[j-1] with s3[i+j-1]** and the **previous cell interleaved[i][j-1]**.

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    bool isInterleave(string s1, string s2, string s3) {
    if (s1.size() + s2.size() != s3.size()) {
        return false;
    }
    
    int m = s1.size();
    int n = s2.size();
    bool interleaved[m + 1][n + 1];

    for (int i = 0; i <= m; i++) {
        for (int j = 0; j <= n; j++) {
            if (i == 0 && j == 0) {
                interleaved[i][j] = true;
            } else if (i == 0) {
                interleaved[i][j] = interleaved[i][j - 1] && s2[j - 1] == s3[i + j - 1];
            } else if (j == 0) {
                interleaved[i][j] = interleaved[i - 1][j] && s1[i - 1] == s3[i + j - 1];
            } else {
                interleaved[i][j] = (interleaved[i - 1][j] && s1[i - 1] == s3[i + j - 1]) ||
                                    (interleaved[i][j - 1] && s2[j - 1] == s3[i + j - 1]);
            }
        }
    }
    
    return interleaved[m][n];
    }
};
```
---
