# 🧩 Que
- [Link](https://practice.geeksforgeeks.org/problems/merge-two-sorted-arrays-1587115620/1)
- You are given two sorted array and your job is to merge them without using extra space

```ad-question
title: Test Case
**Input**: 
n = 4, arr1[] = [1 3 5 7] 
m = 5, arr2[] = [0 2 6 8 9]
**Output**: 
arr1[] = [0 1 2 3]
arr2[] = [5 6 7 8 9]

```

---
```ad-abstract
This question uses [[shell_sort]] to sort the two arrays in O(nlgn) time with no extra space
```

- Tags #unsolved #revise 
--- 
# 🕵️‍♂️ Main Logic
- If an interviewer ask you this question first use extra space to put the sorted union of the two and then copy the values back in the original array. O(n) and O(n)
- Next what you can do is use two pointers and swap in case of incorrect ordering and then when you swap put the element at its correct position so something like [[insertion_sort]]. O(n* m), O(m)
- Next what you need to do is perform [[shell_sort]]. Which is also called as graph method.
- Make sure that your initial gap is ceil((n+m)/2) and assume that the two arrays are placed one after another.
- Perform [[shell_sort]] on [1, 3, 5, 7, 0, 2, 6, 8, 9]
---
# ☠️ My thought process
- I was able to think the first two algorithm but shell sort was out of my reach
- Yous still have problem with coding this out
---

# 💻 Code
```c++
class Solution{
    public:
        void swapIfGreater(long long arr1[], long long arr2[], int ind1, int ind2) {
            if (arr1[ind1] > arr2[ind2]) {
                swap(arr1[ind1], arr2[ind2]);
            }
        }
        //Function to merge the arrays.
        void merge(long long arr1[], long long arr2[], int n, int m) {
            // len of the imaginary single array:
            int len = n + m;
        
            // Initial gap:
            int gap = (len / 2) + (len % 2);
        
            while (gap > 0) {
                // Place 2 pointers:
                int left = 0;
                int right = left + gap;
                while (right < len) {
                    // case 1: left in arr1[]
                    //and right in arr2[]:
                    if (left < n && right >= n) {
                        swapIfGreater(arr1, arr2, left, right - n);
                    }
                    // case 2: both pointers in arr2[]:
                    else if (left >= n) {
                        swapIfGreater(arr2, arr2, left - n, right - n);
                    }
                    // case 3: both pointers in arr1[]:
                    else {
                        swapIfGreater(arr1, arr1, left, right);
                    }
                    left++, right++;
                }
                // break if iteration gap=1 is completed:
                if (gap == 1) break;
        
                // Otherwise, calculate new gap:
                gap = (gap / 2) + (gap % 2);
            }
        }
};
```
---
