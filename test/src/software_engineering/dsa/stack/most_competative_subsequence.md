# 🧩 Que
- [Link](https://leetcode.com/problems/find-the-most-competitive-subsequence/)
Given an integer array `nums` and a positive integer `k`, return _the most **competitive** subsequence of_ `nums` _of size_ `k`.
We define that a subsequence `a` is more **competitive** than a subsequence `b` (of the same length) if in the first position where `a` and `b` differ, subsequence `a` has a number **less** than the corresponding number in `b`. For example, `[1,3,4]` is more competitive than `[1,3,5]` because the first position they differ is at the final number, and `4` is less than `5`.
```ad-question
title: Test Case
**Input:** nums = [3,5,2,6], k = 2
**Output:** [2,6]
**Explanation:** Among the set of every possible subsequence: {[3,5], [3,2], [3,6], [5,2], [5,6], [2,6]}, [2,6] is the most competitive.
```

---
# Abstract
```ad-abstract
The idea is to maintain a monotonic increasing stack. If current element is smaller than top of the stack then we can pop from the stack but before poppoing we will need to check if we can generate a subsequence of length k.
we have `stack.size() - 1` in the stack,  there are `A.size() - i` can still be pushed.  if `stack.size() - 1 + A.size() - i >= k`, we can pop the stack.
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
```python
def mostCompetitive(self, A, k):
	stack = []
	for i, a in enumerate(A):
		while stack and stack[-1] > a and len(stack) - 1 + len(A) - i >= k:
			stack.pop()
		if len(stack) < k:
			stack.append(a)
	return stack
```
---
