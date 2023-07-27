# 🧩 Que
- Link
Given a BST find inorder successor
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The brute is to perform an inorder and then find the one just greater. 
What you can do instead is that compare the current node 
- If it is greater then target then it is a potential condidate. Find better candidate by going left
- If it is smaller then you need bigger so go right
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230723044159.png]]

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
        TreeNode* successor = NULL;
        
        while (root != NULL) {
            
            if (p->val >= root->val) {
                root = root->right;
            } else {
                successor = root;
                root = root->left;
            }
        }
        
        return successor;
    }
};
```
---
