# 🧩 Que
- [Link](https://www.interviewbit.com/problems/reorder-list/)
Given a singly linked list
    L: L0 → L1 → … → Ln-1 → Ln,
reorder it to:
    L0 → Ln → L1 → Ln-1 → L2 → Ln-2 → …
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is pretty simple. You first find the mid then reverse the later half and then join the two lists
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
    # @param A : head node of linked list
    # @return the head node in the linked list
    def reorderList(self, head):
        """ Modifies input linked list in-place. Returns head of a new list.
        Time complexity: O(n). Space complexity: O(1), n is len(linked list).
        """
        # modifiy the list only if it has more than one node
        if not head or not head.next:
            return head
            
        # find the middle of the list using slow and fast pointers algorithm
        prev = None  # last node of the left half of the list
        slow = fast = head
        while fast and fast.next:
            prev = slow
            slow = slow.next
            fast = fast.next.next

        prev.next = None  # detach left half of the list from the right half
        # reverse right half of the list
        prev = None
        curr = slow  # slow is the start of the right half
        while curr:
            link = curr.next
            curr.next = prev
            prev = curr
            curr = link
        # prev now points to the head of reversed right half
        # combine left and right half, attach it to dummy node
        dummy = ListNode(None)
        tail = dummy  # current tail of a new list
        while head:  # left list is always gonna be shorter
            link = head.next  # save link to the next node in the left list
            head.next = prev
            tail.next = head  # attach connected 2 nodes to the tail
            tail = prev  # update tail
            head = link  # move to the next node in left list
            prev = prev.next
        # if the length of the original list was odd, right half is gonna have
        # 1 node more than the left half
        if prev:
            tail.next = prev
        return dummy.next  # return new head
```
---
