# 🧩 Que
- [Link](https://leetcode.com/problems/count-complete-tree-nodes/)
Given the `root` of a **complete** binary tree, return the number of the nodes in the tree.
```ad-question
title: Test Case
![[Pasted image 20230723033933.png]]
```

---
# Abstract
```ad-abstract
If you apply brute force then you can just write a recursion to get the count of tree O(n) but here we will use property of complete tree. Since the tree is balanced it will only have 2 types of subtree
- One that is complete and for that number of node will be 2^h - 1
- One that is incomplete for that you will have to do 1 + solve(left) + solve(right)

To check if a tree is complete or not
- Find height of the left subtree and find height of the right subtree if they are same then it is complete otherwise not

To get the height you can just traverse the left and right pointer respectively
TC = O((lg(n)^2)
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
```python
class Solution {
public:
    int countNodes(TreeNode* root) {
        if(root == NULL) return 0; 
        
        int lh = findHeightLeft(root); 
        int rh = findHeightRight(root); 
        
        if(lh == rh) return (1<<lh) - 1; 
        
        return 1 + countNodes(root->left) + countNodes(root->right); 
    }
    int findHeightLeft(TreeNode* node) {
        int hght = 0; 
        while(node) {
            hght++; 
            node = node->left; 
        }
        return hght; 
    }
    int findHeightRight(TreeNode* node) {
        int hght = 0; 
        while(node) {
            hght++; 
            node = node->right; 
        }
        return hght; 
    }
};
```
---
