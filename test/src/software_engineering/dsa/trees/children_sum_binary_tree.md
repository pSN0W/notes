# 🧩 Que
- Link
The children sum property is defined as, For every node of the tree, the value of a node is equal to the sum of values of its children(left child and right child).
- The node values can be increased by 1 any number of times but decrement of any node value is not allowed.
- A value for a NULL node can be assumed as 0.
- You are not allowed to change the structure of the given binary tree.
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea here is that you increase the child node value in such a way that they never fall shart of the parent node value. Since it is not required to do minimum changes you can do it in this way
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
void reorder(node * root) {
  if (root == NULL) return;
  int child = 0;
  if (root -> left) {
    child += root -> left -> data;
  }
  if (root -> right) {
    child += root -> right -> data;
  }
  // If sum of child is lesser then set it to parent
  if (child < root -> data) {
    if (root -> left) root -> left -> data = root -> data;
    else if (root -> right) root -> right -> data = root -> data;
  }

  reorder(root -> left);
  reorder(root -> right);
  // set the parent value to sum of them when you come back
  int tot = 0;
  if (root -> left) tot += root -> left -> data;
  if (root -> right) tot += root -> right -> data;
  if (root -> left || root -> right) root -> data = tot;
}
```
---
