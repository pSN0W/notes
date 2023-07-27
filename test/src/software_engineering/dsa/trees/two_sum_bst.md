# 🧩 Que
- [Link](https://www.interviewbit.com/problems/2sum-binary-tree/)
Given a binary search tree A, where each node contains a positive integer, and an integer B, you have to find whether or not there exist two different nodes X and Y such that X.value + Y.value = B.
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
If you had O(n) space then this problem would have been easy but you want to solve it in O(h) space for this you can use something like BSTIterator and then use two pointers one at max and another at min
```

- Tags #unsolved #standard_que #revise 
--- 
# 🕵️‍♂️ Main Logic
- https://www.youtube.com/watch?v=ssL3sHwPeb4&list=PLgUwDviBIf0q8Hkd7bK2Bpryj2xVJk8Vk&index=52

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
class BST{
    public:
        stack<TreeNode*> mys1,mys2;
        TreeNode * cur1, * cur2;

        BST(TreeNode *root) {
            cur1=cur2=root;
        }
        bool hasNext() {
            if(cur1==NULL and mys1.empty())return false;
            return true;
        }
        bool hasPrev() {
            if(cur2==NULL and mys2.empty())return false;
            return true;
        }
        int next(){
            if(cur1!=NULL){
                mys1.push(cur1);
                cur1=cur1->left;
                next();
            }
            else{
                if(not mys1.empty()){
                    cur1=mys1.top();
                    int ans=cur1->val;
                    mys1.pop();
                    cur1=cur1->right;
                    return ans;
                }
            }
        }
        int prev(){
            if(cur2!=NULL){
                mys2.push(cur2);
                cur2=cur2->right;
                prev();
            }
            else{
                if(not mys2.empty()){
                    cur2=mys2.top();
                    int ans=cur2->val;
                    mys2.pop();
                    cur2=cur2->left;
                    return ans;
                }
            }
        }
};

int Solution::t2Sum(TreeNode* A, int B) {
    BST a(A);
    int x1=a.next();
    int x2=a.prev();
    while(x1<x2){
        if(x1+x2==B)return 1;
        if(x1+x2<B)
            x1=a.next();
        else x2=a.prev();
    }
    return 0;
}
```
---
