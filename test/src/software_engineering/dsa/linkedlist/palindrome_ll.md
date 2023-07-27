# 🧩 Que
- [Link](https://leetcode.com/problems/palindrome-linked-list/)
Given a linked list check if its palindrome or not.
```ad-question
title: Test Case
**Input:** head = [1,2,2,1]
**Output:** true
```

---
# Abstract
```ad-abstract
You need to do the following
- Get the mid element
- Reverse from mid
- Check if both the parts are same
```

- Tags #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        def get_mid(head):
            slow = head
            fast = head
            while fast.next is not None and fast.next.next is not None:
                fast = fast.next.next
                slow = slow.next
            return slow
        
        def rev(head):
            if head is None or head.next is None:
                return head
            new_hed = rev(head.next)
            head.next.next = head
            head.next = None
            return new_hed

        def check(h1,h2):
            if h1 is None or h2 is None:
                return True
            if h1.val != h2.val:
                return False
            return check(h1.next,h2.next)

        mid = get_mid(head)
        head_2 = mid.next
        mid.next = None
        head_2 = rev(head_2)
        return check(head,head_2)
```
---
