# 🧩 Que
- Link
Given preorder traversal of a bst. Construct a tree from that
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
You can use the folowing algos to achieve that
- Do a brute force where you insert each node at bst [[insert_a_node_in_bst]] O(n^2)
- You can sort the preorder and then you will get inorder [[from_inorder_and_preorder]] O(nlgn)
- The last idea is something like [[validate_bst]] where you keep track of the upperbound at each node. O(3N)
```
[[validate_bst]] [[from_inorder_and_preorder]]
- Tags 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230723043007.png]]
- You initial ub for root is inf that is for 8.
- You get 5 since it is smaller then 8 add it to left. UB for this node is 8
- You get 1 which is lower then 5 so you add it to left UB here becomes 5
- You get 7 which is greater then 1 you check its upper bound since 7 > 5 you go above to the parent of 1
- 7 is greater then 5 but less then UB at 5 so you add it to right and the UB becomes same as UB of 5

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class Solution {
public:
    TreeNode* bstFromPreorder(vector<int>& A) {
        int i = 0;
        return build(A, i, INT_MAX);
    }

    TreeNode* build(vector<int>& A, int& i, int bound) {
        if (i == A.size() || A[i] > bound) return NULL;
        TreeNode* root = new TreeNode(A[i++]);
        root->left = build(A, i, root->val);
        root->right = build(A, i, bound);
        return root;
    }
};z
```
---
