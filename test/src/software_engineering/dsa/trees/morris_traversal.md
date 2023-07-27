# 🧩 Que
- Link
Given a binary tree traverse it in O(1) time.
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is to make use of threaded binary tree to traverse
- The idea is that you need to go back to root when you have traversed all the nodes to the left. This is done so that you can go right from the root after that.
- Whole idea is that before traversing right you create a thread from the rightmost leaf of the left to the root.
- Once you have traversed then you remove that thread and then go left
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- The threads look something like this
- ![[Pasted image 20230723151654.png]]
- You have two cases
	- When the left has no node. In this case you can directly go to right
	- Tree has a left node.
		- Traverse to the right most part of the tree and create a thread from there to current root.
		- How do you know that you have to go left or right from root.
		- If thread exist then go right else create thread and go left

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
vector < int > inorderTraversal(node * root) {
  vector < int > inorder;

  node * cur = root;
  while (cur != NULL) {
	// if doesn't have left then add current to list and go right
    if (cur -> left == NULL) {
      inorder.push_back(cur -> data);
      cur = cur -> right;
    } else {
      node * prev = cur -> left;
      // create a thread with the rightmost part
      while (prev -> right != NULL && prev -> right != cur) {
        prev = prev -> right;
      }
	  // see if you need to create thread or thread is already there and you need to go right
      if (prev -> right == NULL) {
        prev -> right = cur;
        cur = cur -> left;
      } else {
        prev -> right = NULL;
        // thread is already there add it to innode and then go right
        inorder.push_back(cur -> data);
        cur = cur -> right;
      }
    }
  }
  return inorder;
}
```
---
