# 🧩 Que
- [Link](https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/)
You are given an array of `events` where `events[i] = [startDayi, endDayi]`. Every event `i` starts at `startDayi` and ends at `endDayi`.

You can attend an event `i` at any day `d` where `startTimei <= d <= endTimei`. You can only attend one event at any time `d`.

Return _the maximum number of events you can attend_.
```ad-question
title: Test Case
**Input:** events = [ [1,2],[2,3],[3,4] ]
**Output:** 3
**Explanation:** You can attend all the three events.
One way to attend them all is as shown.
Attend the first event on day 1.
Attend the second event on day 2.
Attend the third event on day 3.
```

---
# Abstract
```ad-abstract
The idea is single for each day have all the even that you could attend and then attend the one that ends the earliest
```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- Have a priority queue that will tell which have all the events sorted by their end time.
- A variable d which tells the current day and res which tells number of event attended.
- Sort the array in increasing order of the start day and iterate over it
	- If your pq is empty then you don't have any event left to attend so set your current day as the one on which the current event start.
	- Put all the events with start day before or on d day in the heap.
	- Take out the one with the closest end date and ensure that its end date is of after d and increment d as well as answer
---
# ☠️ My thought process
- Too lazy
---

# 💻 Code
```python
class Solution:
    def maxEvents(self, A):
        A.sort(reverse=1)
        h = []
        res = d = 0
        while A or h:
            if not h: d = A[-1][0]
            while A and A[-1][0] <= d:
                heapq.heappush(h, A.pop()[1])
            heapq.heappop(h)
            res += 1
            d += 1
            while h and h[0] < d:
                heapq.heappop(h)
        return res
```
---
