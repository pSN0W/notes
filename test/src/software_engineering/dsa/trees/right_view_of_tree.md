# 🧩 Que
- Link
Given a tree find the right view of the tree
```ad-question
title: Test Case
![[Pasted image 20230722120656.png]]
```

---
# Abstract
```ad-abstract
You can certainly do this with level order traversal but the idea is to try it with recursion to reduce complexity. You can have node and level. You will first process current then go right and then go left. You can store a ds where you will put the node if you reach at the level for first time so it can be something like if ds.size() == level then put the node in ds
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
    void recursion(TreeNode *root, int level, vector<int> &res)
    {
        if(root==NULL) return ;
        if(res.size()==level) res.push_back(root->val);
        recursion(root->right, level+1, res);
        recursion(root->left, level+1, res);
    }
    
    vector<int> rightSideView(TreeNode *root) {
        vector<int> res;
        recursion(root, 0, res);
        return res;
    }
};
```
---
