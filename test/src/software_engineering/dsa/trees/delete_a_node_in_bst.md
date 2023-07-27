# 🧩 Que
- Link
Given a bst and a node. Delete that node from the bst
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract


```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- Lets say you are given this tree and you want to delete 5 ![[Pasted image 20230723040640.png]]
- If you remove 5 then its right part will be greater then all the left part so one way to build the tree is to join the left and to the rightmost of right you join the right part ![[Pasted image 20230723040806.png]]
- Another way you can do is join left to the left most part of right since left will be smaller then all rights ![[Pasted image 20230723040845.png]]
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    TreeNode* deleteNode(TreeNode* root, int key) {
        if (root == NULL) {
            return NULL;
        }
        // if the given node (root) is root
        if (root->val == key) {
            return helper(root);
        }
        TreeNode *dummy = root;
        while (root != NULL) {
            if (root->val > key) {
                if (root->left != NULL && root->left->val == key) {
                    root->left = helper(root->left);
                    break;
                } else {
                    root = root->left;
                }
            } else {
                if (root->right != NULL && root->right->val == key) {
                    root->right = helper(root->right);
                    break;
                } else {
                    root = root->right;
                }
            }
        }
        return dummy;
    }
    TreeNode* helper(TreeNode* root) {
		    // if either left or right child dne then directly connect
            if (root->left == NULL) 
            {
                return root->right;
            } 
            else if (root->right == NULL)
            {
                return root->left;
            } 
	        
            // otherwise connect right to rightmost part of left and return left
            TreeNode* rightChild = root->right;
            TreeNode* lastRight = findLastRight(root->left);
            lastRight->right = rightChild;
            return root->left;
    }
    TreeNode* findLastRight(TreeNode* root) {
        if (root->right == NULL) {
            return root;
        }
        return findLastRight(root->right);
    }
};
```
---
