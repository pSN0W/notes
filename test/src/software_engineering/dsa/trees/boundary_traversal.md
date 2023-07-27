# 🧩 Que
- Link
Given a tree traverse the boundary of the tree
```ad-question
title: Test Case
![[Pasted image 20230722115133.png]]
```

---
# Abstract
```ad-abstract
The idea is to first store all the left node in a data structure and then traverse for the leaf nodes and the store all the right nodes in a data structure too. 
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- First we perform a traversal where we go to left all the time and only go right if left is not present. This is done until we reach the leaf node[1, 2, 3, 4]![[Pasted image 20230722114528.png]]
- For the leaf node preorder traversal is done and then if a node is leaf then it is added. We can't do level order as in that case the leaves at the higher level will come first we want them to come as bottom left and then top right. [1, 2, 3, 4, 5, 6, 10, 11]![[Pasted image 20230722114818.png]]
- We want the right boundary in reverse order. It is very similar to the left part we just go right and then we reverse and append the answer ![[Pasted image 20230722114934.png]]
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
void addLeftBoundary(node * root, vector < int > & res) {
  node * cur = root -> left;
  while (cur) {
    if (!isLeaf(cur)) res.push_back(cur -> data);
    if (cur -> left) cur = cur -> left;
    else cur = cur -> right;
  }
}
void addRightBoundary(node * root, vector < int > & res) {
  node * cur = root -> right;
  vector < int > tmp;
  while (cur) {
    if (!isLeaf(cur)) tmp.push_back(cur -> data);
    if (cur -> right) cur = cur -> right;
    else cur = cur -> left;
  }
  for (int i = tmp.size() - 1; i >= 0; --i) {
    res.push_back(tmp[i]);
  }
}

void addLeaves(node * root, vector < int > & res) {
  if (isLeaf(root)) {
    res.push_back(root -> data);
    return;
  }
  if (root -> left) addLeaves(root -> left, res);
  if (root -> right) addLeaves(root -> right, res);
}

vector < int > printBoundary(node * root) {
  vector < int > res;
  if (!root) return res;

  if (!isLeaf(root)) res.push_back(root -> data);

  addLeftBoundary(root, res);

  // add leaf nodes
  addLeaves(root, res);

  addRightBoundary(root, res);
  return res;
}
```
---
