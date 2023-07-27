# 🧩 Que
- Link
Perform preorder, inorder and postorder traversal in on traversal
```ad-question
title: Test Case


```

---
# Abstract
```ad-abstract
The idea is to push a num along with the value you are pushing in the stack. So you basically push {curr_val, num} in the stack. When you pop if num is 1 then you push it into pre order you push {curr_val, num+1} in stack and if there is left then push {curr.left,1} in stack.
If `num==2` then put the curr_val in inorder and then put {curr, num+1} in stack and if there is right then you put {curr.right, 1} in stack.
If `num==3` then put it in postorder.
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230722015357.png]]
- Continue this effort
---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
void allTraversal(node * root, vector < int > & pre, vector < int > & in , vector < int > & post) {
  stack < pair < node * , int >> st;
  st.push({
    root,
    1
  });
  if (root == NULL) return;

  while (!st.empty()) {
    auto it = st.top();
    st.pop();

    // this is part of pre
    // increment 1 to 2 
    // push the left side of the tree
    if (it.second == 1) {
      pre.push_back(it.first -> data);
      it.second++;
      st.push(it);

      if (it.first -> left != NULL) {
        st.push({
          it.first -> left,
          1
        });
      }
    }
    // this is a part of in 
    // increment 2 to 3 
    // push right 
    else if (it.second == 2) {
      in .push_back(it.first -> data);
      it.second++;
      st.push(it);

      if (it.first -> right != NULL) {
        st.push({
          it.first -> right,
          1
        });
      }
    }
    // don't push it back again 
    else {
      post.push_back(it.first -> data);
    }
  }
}
```
---
