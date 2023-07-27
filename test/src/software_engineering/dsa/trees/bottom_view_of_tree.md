# 🧩 Que
- Link
Given a tree find its bottom view
```ad-question
title: Test Case
![[Pasted image 20230722115753.png]]
```

---
# Abstract
```ad-abstract
The idea is same at [[top_view_of_tree]] but here you will keep traversing level order and then update your map 
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230722115900.png]]

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
vector <int> bottomView(Node *root) {
	vector<int> ans; 
	if(root == NULL) return ans; 
	map<int,int> mpp; 
	queue<pair<Node*, int>> q; 
	q.push({root, 0}); 
	while(!q.empty()) {
		auto it = q.front(); 
		q.pop(); 
		Node* node = it.first; 
		int line = it.second; 
		mpp[line] = node->data; 
		
		if(node->left != NULL) {
			q.push({node->left, line-1}); 
		}
		if(node->right != NULL) {
			q.push({node->right, line + 1}); 
		}
		
	}
	
	for(auto it : mpp) {
		ans.push_back(it.second); 
	}
	return ans;  
}
```
---
