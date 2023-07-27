# 🧩 Que
- [Link](https://leetcode.com/problems/word-ladder-ii/)
A **transformation sequence** from word `beginWord` to word `endWord` using a dictionary `wordList` is a sequence of words `beginWord -> s1 -> s2 -> ... -> sk` such that:
Every si should be part of wordList
```ad-question
title: Test Case
**Input:** beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
**Output:** [ ["hit","hot","dot","dog","cog"],["hit","hot","lot","log","cog"] ]
**Explanation:** There are 2 shortest transformation sequences:
"hit" -> "hot" -> "dot" -> "dog" -> "cog"
"hit" -> "hot" -> "lot" -> "log" -> "cog"
```

---
# Abstract
```ad-abstract
You first need to build a ladder from the startWord to the endWord. you store the parent and then build the path from startWord to endWord
```

- Tags #revise #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- If you will look at constraints you will find that it is better to generate all the possible words and see if they are part of wordList or not instead of checking the difference between the two.
- You can use bfs to find the shortest path. If there are two paths to s1 one from s2 and another from s3 then both of s2 and s3 can be parent if they have the same distance from beginWord. That's why you store as you do
- Once the parents are stored you can build the path easily

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
import string
from queue import Queue
class Solution:
    def findLadders(self, beginWord: str, endWord: str, wordList: List[str]) -> List[List[str]]:
        parent = {word:[] for word in wordList}
        if endWord not in wordList:
            return []
        dis = {word:-1 for word in wordList}
        wordList = set(wordList)
        def gen_poss_words(wrd):
            lst = list(wrd)
            poss_words = []
            for i in range(len(lst)):
                curr = lst[i]
                for ch in string.ascii_lowercase:
                    if ch != curr:
                        lst[i] = ch
                        if "".join(lst) in wordList:
                            poss_words.append("".join(lst))
                        lst[i] = curr
            return poss_words
        
        def create_path(wrd):
            if wrd==beginWord:
                return [[beginWord]]
            curr = []
            for par in parent[wrd]:
                rst_paths = create_path(par)
                for pth in rst_paths:
                    pth.append(wrd)
                    curr.append(pth)
            return curr
        d = 0
        q = Queue()
        q.put(beginWord)
        q.put(None)
        dis[beginWord] = 0

        while not q.empty():
            f = q.get()
            if f is None:
                d += 1
                if not q.empty():
                    q.put(None)
                continue
            if f==endWord:
                break
            for nbr in gen_poss_words(f):
                if dis[nbr] == -1:
                    dis[nbr] = d+1
                    parent[nbr].append(f)
                    q.put(nbr)
                elif dis[nbr] == d+1:
                    parent[nbr].append(f)
        return create_path(endWord)

```
---
