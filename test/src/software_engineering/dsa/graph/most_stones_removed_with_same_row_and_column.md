# 🧩 Que
- [Link](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/)
You are given cordinates of stones. A stone can be removed if it shares either **the same row or the same column** as another stone that has not been removed.

```ad-question
title: Test Case
**Input:** stones = [ [0,0],[0,1],[1,0],[1,2],[2,1],[2,2] ]
**Output:** 5
**Explanation:** One way to remove 5 stones is as follows:
1. Remove stone [2,2] because it shares the same row as [2,1].
2. Remove stone [2,1] because it shares the same column as [0,1].
3. Remove stone [1,2] because it shares the same row as [1,0].
4. Remove stone [1,0] because it shares the same column as [0,0].
5. Remove stone [0,1] because it shares the same row as [0,0].
Stone [0,0] cannot be removed since it does not share a row/column with another stone still on the plane.
```

---
# Abstract
```ad-abstract
You can easily see using induction that you can remove all the stones from a fully connected island excepth a single one. So the question reduces to total number of island in the graph. You can use a dfs to achieve this or you can use a union find
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- The idea is to use union find to merge the points together. 
- What you do is find all the points in the same row or in the same column and then merge those rows in dsu.
- A other implementation can be seen [here](https://leetcode.com/problems/most-stones-removed-with-same-row-or-column/solutions/197668/count-the-number-of-islands-o-n/) where you just merge the i and j cordinate of the point. To differentiate between the x and y cordinates you can take y to another cordinate system. The problem with doing just `-1*y` is that 0 will be same for both so use `~x = -1-x`

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class DSU:
    def __init__(self):
        self.parent = {}
        self.size = {}

    def find(self,x):
        if self.parent[x] == x:
            return x
        self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
    def add(self,x):
        if x in self.parent:
            return
        self.parent[x] = x
        self.size[x] = 1
    def union(self,x,y):
        self.add(x)
        self.add(y)
        par_x = self.find(x)
        par_y = self.find(y)
        if par_x == par_y:
            return
        if self.size[par_x] >= self.size[par_y]:
            self.parent[par_y] = par_x
            self.size[par_x] += self.size[par_y]
        else:
            self.parent[par_x] = par_y
            self.size[par_y] += self.size[par_x]
    def merge(self,lst):
        if len(lst) == 1:
            self.add(lst[0])
        for x,y in zip(lst[:-1],lst[1:]):
            self.union(x,y)
    def get_num_parent(self):
        return sum([1 for k in self.parent.keys() if k==self.find(k)])

class Solution:
    def removeStones(self, stones: List[List[int]]) -> int:
        dsu = DSU()
        row_dic = {}
        column_dic = {}
        for x,y in stones:
            row_dic.setdefault(x,[])
            column_dic.setdefault(y,[])
            row_dic[x].append((x,y))
            column_dic[y].append((x,y))
        for v in list(row_dic.values()) + list(column_dic.values()):
            dsu.merge(v)
        return len(stones) - dsu.get_num_parent()
```
---
# 🔬 Optimized
```python
def removeStones(self, points):
	UF = {}
	def find(x):
		if x != UF[x]:
			UF[x] = find(UF[x])
		return UF[x]
	def union(x, y):
		UF.setdefault(x, x)
		UF.setdefault(y, y)
		UF[find(x)] = find(y)

	for i, j in points:
		union(i, ~j)
	return len(points) - len({find(x) for x in UF})
```
---