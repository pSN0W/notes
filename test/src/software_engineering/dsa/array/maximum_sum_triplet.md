# 🧩 Que
- [Link](https://www.interviewbit.com/problems/maximum-sum-triplet/)
Given an unsorted array find triplet `i<j<k and A[i] < A[j] < A[k]` such that the sum of the triplet is maximum
```ad-question
title: Test Case
Input 1:
A = [2, 5, 3, 1, 4, 9]
Output 1:
16
```

---
# Abstract
```ad-abstract
The idea is to cosider the current index as the middle element. Now to get the largest just less then current to the left you can use a set and then apply binary search in it while for the right you can have a suffix max array.
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
int getLowValue(set<int>& lowValue, int& n)
{
    auto it = lowValue.lower_bound(n);
 
    // Since 'lower_bound' returns the first
    // iterator greater than 'n', thus we
    // have to decrement the pointer for
    // getting the minimum value
    --it;
 
    return (*it);
}
int Solution::solve(vector<int> &arr) {
    int n = arr.size();
     int maxSuffArr[n + 1];
 
    // Set the last element
    maxSuffArr[n] = 0;
 
    // Calculate suffix-array containing maximum
    // value for index i, i+1, i+2, ... n-1 in
    // arr[i]
    for (int i = n - 1; i >= 0; --i)
        maxSuffArr[i] = max(maxSuffArr[i + 1], arr[i]);
 
    int ans = 0;
 
    // Initialize set container
    set<int> lowValue;
 
    // Insert minimum value for first comparison
    // in the set
    lowValue.insert(INT_MIN);
 
    for (int i = 0; i < n - 1; ++i) {
        if (maxSuffArr[i + 1] > arr[i]) {
            ans = max(ans, getLowValue(lowValue,
                                       arr[i])
                               + arr[i] + maxSuffArr[i + 1]);
 
            // Insert arr[i] in set<> for further
            // processing
            lowValue.insert(arr[i]);
        }
    }
    return ans;
}
```
---
