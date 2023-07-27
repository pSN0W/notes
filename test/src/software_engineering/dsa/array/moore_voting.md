# 🧩 Que
- [Link](https://practice.geeksforgeeks.org/problems/majority-element-1587115620/1)
- Given an array on len n return the number with frequency greater than n/2. If there are no such elements return -1.

```ad-question
title: Test Case
**Input:**
N = 3 
A[] = {1,2,3} 
**Output:**
-1
**Input:**
N = 5 
A[] = {3,1,3,3,2} 
**Output:**
3

```

---
```ad-abstract
The idea is pretty simple you assume that the current element that you have is the desired one. You maintain a count for it too. You iterate the array if the element is same as the number you thought of increament the count otherwise decrement it. If count reaches 0 change the expected to the current one.
At the end check if your curr is actually the answer if not return -1.
```

- Tags #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- The intuition is pretty simple assume that you know the answer and apart from that answer make all the other element as -1. Make that element as 1. Now you are just checking if the sum is > 0.

---
# ☠️ My thought process
- 
---

# 💻 Code
```c++
//User function template for C++

class Solution{
  public:
     // Function to find majority element in the array
    // a: input array
    // size: size of input array
    int majorityElement(int a[], int size)
    {
        
        int choice = a[0], freq = 1;
        for(int i=1;i<size;i++){
            if(a[i]==choice)    freq++;
            else{
                freq--;
                if(freq==0) choice = a[i], freq = 1;
            }
        }
        freq = 0;
        for(int i=0;i<size;i++){
            if(choice==a[i])    freq++;
        }
        if(freq<=(size/2))  return -1;
        return choice;
    }
};
```
---
z