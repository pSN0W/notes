# 🧩 Que
- [Link](https://leetcode.com/problems/subtree-of-another-tree/)
Given two tree check if one tree is part of another tree or not
```ad-question
title: Test Case

```

---
# Abstract
```ad-abstract
The easiest way to do this will be to define a util function is same that checks if two trees are same. And then for each subtree in the tree check if it is same as the tree given to check T.C of O(n*m)
An optimised solution will be to serialize the tree and check. T.C = O(n+m)
```

- Tags #unsolved #standard_que 
--- 
# 🕵️‍♂️ Main Logic
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```python
def isMatch(self, s, t):
    if not(s and t):
        return s is t
    return (s.val == t.val and 
            self.isMatch(s.left, t.left) and 
            self.isMatch(s.right, t.right))

def isSubtree(self, s, t):
    if self.isMatch(s, t): return True
    if not s: return False
    return self.isSubtree(s.left, t) or self.isSubtree(s.right, t)
```
---
# 🔬 Optimisation
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        string rootStr = serialize(root);
        string subRootStr = serialize(subRoot);
        
        return rootStr.find(subRootStr) != string::npos;
    }
    
    string serialize(TreeNode* node) {
        if (!node)
            return "null";
        
        return "#" + to_string(node->val) + " " + serialize(node->left) + " " + serialize(node->right);
    }
};
```
---