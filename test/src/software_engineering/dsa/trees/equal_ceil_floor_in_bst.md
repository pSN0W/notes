# 🧩 Que
- Link
Find equal ceil and floor given a binary search tree
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
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int val) {
         while(root != NULL && root->val != val){
            root = val<root->val? root->left:root->right;
        }
        return root;
    }
};

int findCeil(BinaryTreeNode<int> *root, int key){
	int ceil = -1; 
	while (root) {
	
		if (root->data == key) {
			ceil = root->data;
			return ceil;
		}
	
		if (key > root->data) {
			root = root->right;
		}
		else {
			ceil = root->data; 
			root = root->left;
		}
	}
	return ceil; 
}

int floorInBST(TreeNode<int> * root, int key)
{
    int floor = -1; 
    while (root) {
 
        if (root->val == key) {
            floor = root->val;
            return floor;
        }
 
        if (key > root->val) {
            floor = root->val;
            root = root->right;
        }
        else {
            root = root->left;
        }
    }
    return floor;
}
```
---
