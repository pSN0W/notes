# 🧩 Que
- [Link](https://leetcode.com/problems/filling-bookcase-shelves/)
You are given books with height and width. You are also given a shelfWidth. Find the minimum height of shelf required to accommodate all the books. The order of the book on the shelf should be maintained.
![[Pasted image 20230701155412.png]]
```ad-question
title: Test Case
**Input:** books = [ [1,1],[2,3],[2,3],[1,1],[1,1],[1,1],[1,2] ], shelfWidth = 4
**Output:** 6
**Explanation:**
The sum of the heights of the 3 shelves is 1 + 3 + 2 = 6.
Notice that book number 2 does not have to be on the first shelf.
```

---
# Abstract
```ad-abstract
For each book you have two option you can either keep it in the current shelf or start a new shelf with it. A better way to arrange your function will be to deal with each shelf level. Arrange all possible books in the current shelf and start a new shelf everytime you call the function
```

- Tags #revise 
--- 
# 🕵️‍♂️ Main Logic
- f(i) denotes minimum height required to keep all the books starting from index i in a new shelf level.
- Now for the current level you can keep 1 book and start a new shelf, keep 2 book and start a new shelf ... up until the width of sum is less than or equal to shelfwidth

---
# ☠️ My thought process
- You initially thought of having f(i,k) where i is current shelf number and k is space remaining in the current shelf and then for each book you could either put it in the same shelf or start a new shelf with that book.
- The problem with this is that you will have to keep track of the height too as height is the max of all the books you keep in a shelf which further complicates the problem.
---

# 💻 Code
```python
class Solution:
    def minHeightShelves(self, books: List[List[int]], shelfWidth: int) -> int:
        n = len(books)
        @lru_cache(None)
        def solve(idx):
            if idx>=n:
                return 0
            ht = books[idx][1]
            curr_w = 0
            h = 0
            ans = int(1e6)
            for i in range(idx,n):
                w,ht = books[i]
                curr_w += w
                if curr_w > shelfWidth:
                    break
                h = max([ht,h])
                ans = min([ans,solve(i+1)+h])
            return ans
        return solve(0)
```
---
