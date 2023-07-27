# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-width-of-binary-tree/)
Given root of a tree return the maximum width of the given tree
```ad-question
title: Test Case
![[Pasted image 20230708165847.png]]
4
```

---
# Abstract
```ad-abstract
The idea is to properly index the nodes that are available to avoid using too much memory. The main logic is taken from striver but your thought process was better so check that out too.
```

- Tags #unsolved #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- One of the indexing you can do is for child node of a node with index i you can assign value `of 2*1+1 and 2*i+2 `
- ![[Pasted image 20230708164937.png]]
- The problem with this type of indexing is that you will get overflow error if all the nodes are in the same branch. To avoid this what you can do is before doing this at each level you can subtract the min index at that level before performing such indexing
- ![[Pasted image 20230708165134.png]]
- Once you have an strategy like this just do a level order traversal and get the max width
---
# ☠️ My thought process
- You thought of an indexing similar to this but for each i you were indexing something like pow(2,i) and pow(2,i) + 1. This is obviously better but you couldn't come up with strategy to remove indices
- ![[Pasted image 20230708165433.png]]
- If we follow a similar idea of subtracting the minimum we can avoid overflow here too.
- ![[Pasted image 20230708165630.png]]
---

# 💻 Code

---
