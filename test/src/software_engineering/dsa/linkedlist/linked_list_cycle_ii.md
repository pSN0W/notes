# 🧩 Que
- [Link](https://leetcode.com/problems/linked-list-cycle-ii/)
Given the `head` of a linked list, return _the node where the cycle begins. If there is no cycle, return_ `null`.
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
To get the starting point of the loop when. You can use floyd warshal to get them meet at a place once they meet. You can move one of the pointer to head now noth of them move with the same pace, the next time they meet it will be start of the loop.
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Lets call your fast pointer as hare and slow pointer as tortoise. 
- Move hare two step and move the tortoise one step if there is a loop in list then they will meet.
- Now take the hare to the head of the list and then move both the hare and tortoise at the same pace then next time where they will meet will be your ans.
- Lets say the loop starts after a distance from head, the loop is of length c and then they meet at some position b in the loop ![[Pasted image 20230718032108.png]]
- When they meet the hare would have covered a+lc+b distance while the tortoise would have covered a+mc + b distance. But since the hare move twice fast
	- a + lc +b = 2*(a+mc+b)
	- lc-2mc = a+b
	- kc = a+b where k is non negative
	- a = kc - b
- This means that if you start from head then by the time you reach at the start of loop, the other one with the same speed would have looped the loop c times - b distance.
- But since we are already at b then we can add b more distance. So by the time hare comes from head to the starting of loop. The tortoise will have looped loop k times and come to the starting too.

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow = head
        fast = head
        while fast is not None and fast.next is not None:
            fast = fast.next.next
            slow = slow.next
            if fast is slow:
                # reset it to head again and move until they both meet
                slow = head
                while slow != fast:
                    slow = slow.next
                    fast = fast.next
                return slow
        return None
```
---
