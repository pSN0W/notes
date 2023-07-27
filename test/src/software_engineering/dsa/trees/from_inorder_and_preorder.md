# 🧩 Que
- Link
Construct a binary tree given preorder and inorder traversal of the tree
```ad-question
title: Test Case
![[Pasted image 20230722122113.png]]

```

---
# Abstract
```ad-abstract
Preorder will give you the root so you can use it recognise the root while inorder can be used to recognise the left and right parts. Using these we can construct unique binary trees
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- When you look at the pre order traversal then the first element is root you find it in the in order (you can use map) the left of that will belong to left tree and rest to right ![[Pasted image 20230722122412.png]]
- To make things more clear you can make use of variables like preStart, preEnd, inStart, inEnd. Initially you will call for 1 to n ![[Pasted image 20230722122544.png]]
- Next you search the root in preorder and break it into smaller calls. If the left to preorder has k element then then next k of inorder will belong to left![[Pasted image 20230722122657.png]]

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
node * constructTree(vector < int > & preorder, int preStart, int preEnd, vector 
 < int > & inorder, int inStart, int inEnd, map < int, int > & mp) {
  if (preStart > preEnd || inStart > inEnd) return NULL;

  node * root = newNode(preorder[preStart]);
  int elem = mp[root -> data];
  int nElem = elem - inStart;

  root -> left = constructTree(preorder, preStart + 1, preStart + nElem, inorder,
  inStart, elem - 1, mp);
  root -> right = constructTree(preorder, preStart + nElem + 1, preEnd, inorder, 
  elem + 1, inEnd, mp);

  return root;
}

node * buildTree(vector < int > & preorder, vector < int > & inorder) {
  int preStart = 0, preEnd = preorder.size() - 1;
  int inStart = 0, inEnd = inorder.size() - 1;

  map < int, int > mp;
  for (int i = inStart; i <= inEnd; i++) {
    mp[inorder[i]] = i;
  }

  return constructTree(preorder, preStart, preEnd, inorder, inStart, inEnd, mp);
}
```
---
