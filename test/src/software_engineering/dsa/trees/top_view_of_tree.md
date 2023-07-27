# 🧩 Que
- Link
Given a tree find its top view
```ad-question
title: Test Case
![[Pasted image 20230722115437.png]]
```

---
# Abstract
```ad-abstract
The idea is to use the line concept same as [[vertical_order_traversal]] too but here you will do level order traversal as you are only interested in top elements.  
```

- Tags 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230722115551.png]]
- 

---
# ☠️ My thought process
- 
---

# 💻 Code
```cpp
vector<int> topView(Node *root)
{
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
		if(mpp.find(line) == mpp.end()) mpp[line] = node->data; 
		
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
