# Abstract
```ad-abstract
This is used to get the middle element in a list with just one iteration. The idea is that you have two pointers one take one step and the another one takes two step when the fast pointer is at None then slow will be at mid.

```

# Code
```python
def get_mid(head):
	slow = head
	fast = head
	while fast.next is not None and fast.next.next is not None:
		fast = fast.next.next
		slow = slow.next
	return slow
```