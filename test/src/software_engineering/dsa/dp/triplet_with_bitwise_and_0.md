# 🧩 Que
- [Link](https://leetcode.com/problems/triples-with-bitwise-and-equal-to-zero/)
Given an array find all triplets with and sum 0
```ad-question
title: Test Case
**Input:** nums = [2,1,3]
**Output:** 12
**Explanation:** We could choose the following i, j, k triples:
(i=0, j=0, k=1) : 2 & 2 & 1
(i=0, j=1, k=0) : 2 & 1 & 2
(i=0, j=1, k=1) : 2 & 1 & 1
(i=0, j=1, k=2) : 2 & 1 & 3
(i=0, j=2, k=1) : 2 & 3 & 1
(i=1, j=0, k=0) : 1 & 2 & 2
(i=1, j=0, k=1) : 1 & 2 & 1
(i=1, j=0, k=2) : 1 & 2 & 3
(i=1, j=1, k=0) : 1 & 1 & 2
(i=1, j=2, k=0) : 1 & 3 & 2
(i=2, j=0, k=1) : 3 & 2 & 1
(i=2, j=1, k=0) : 3 & 1 & 2
```

---
# Abstract
```ad-abstract
You can generate all the and of the pairs in O(n^2) time. Store it in a hash map along with its frequency. Iterate through the two again and then find all the triplets with and 0. Its just brute force with mapping as the and of two numbers can't be > max(arr[i]) which is 2^16
```

- Tags #unsolved #revise 
--- 
# 🕵️‍♂️ Main Logic
- First, we process all tuples `A[i]` and `A[j]`, and store the result of `A[i] & A[j]` in the hash map `tuples`. We also count there how many times each result was produced.
- Then, we go through the array again, and check each element against all tuples. If it produces zero, we add the tuple counter to the result.
- Time: _O(n * n)_. We can have 2^16 tuples at most. When n is large, n * n will dominate n * 2^16. So it is O(n * n) in the big O notation.  
- Memory: _O(n)_ for the first solution; _O(2 ^ 16)_, or, stricter, _O(1)_ for the second one.
---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    int countTriplets(vector<int>& A, int cnt = 0) {
        int tuples[1 << 16] = {};
        for (auto a : A)
            for (auto b : A) ++tuples[a & b];
        for (auto a : A)
            for (auto i = 0; i < (1 << 16); ++i)
            if ((i & a) == 0) cnt += tuples[i];
        return cnt;
    }
};
```
---
