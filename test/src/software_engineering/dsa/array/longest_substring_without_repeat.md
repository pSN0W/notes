[# 🧩 Que
- Link
Given a string find largest substring with unique character.
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is to maintain a hash map for the current window we extend the window if the character does not exist and make a new window in case of occurence. Store the last index of each character
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
Check the run for the algorithm
| String | i   | j   | map              | reason|
| ------ | --- | --- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| aabcb  | -1  | 0   | a: 0             | Store a in map as its first occurence|
| aabcb  | 0   | 1   | a: 1             | Since a is in map and its index is greater then i move i to index of map|
| aabcb  | 0   | 2   | a: 1, b: 2       | Append bo to the map|
| aabcb  | 0   | 3   | a: 1, b: 2, c: 3 | Append c to map|
| aabcb  | 2   | 4   | a: 1, b: 4, c: 3 | Update for b|
| aabcba | 2   | 5   | a: 5, b: 4, c: 3 | Even if a is in map but its index is less then a so current length will continue and update the map for latest position of a | 

---
# ☠️ My thought process

---

# 💻 Code

---](<# 🧩 Que
- [Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract


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

--->)