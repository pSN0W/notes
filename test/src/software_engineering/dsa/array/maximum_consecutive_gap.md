# 🧩 Que
- [Link](https://www.interviewbit.com/problems/maximum-consecutive-gap/)
Given an unsorted array, find the maximum difference between successive element in its sorted form. 
```ad-question
title: Test Case
[1,10,5]
5
```

---
# Abstract
```ad-abstract
The easiest solution is to sort and compare. The idea is to use bucketing to deal with this
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- Lets say that we already know the maximum and minimum value of of the array of size n.
	- The gap will be maximum when all the elements are either min or max in that case the value for gap will be max-min
	- The gap will be minimum when all the elements in the array are equally spaced that means that they are as `[min, min+gap, min+2*gap,..., mx]` then the value of the gap will be gap = (max-min)/(n-1)
- So now we know that the gap can lie between `[(max-min)/(n-1), max-min]`
- Now we create bucket from ranges `[min,min+gap], [min,min+2*gap] ... ` and there will be n-1 such buckets.
- If you pick two numbers from the bucket they will never constitute to the max gap as their difference is less then gap. So you actually only need to store the max and min for the bucket.
- Now we just go through the bucket sequentially as they are already sorted and then we just need to subtract max of current bucket from min of previous.

---
# ☠️ My thought process
- 
---

# 💻 Code

---
