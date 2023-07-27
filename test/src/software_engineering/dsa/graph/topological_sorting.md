# Topo Sort
Topo sort of DAG is linear ordering of vertices of a graph such that for all u -> v u comes before v 
```ad-warning
Only works for DAG.(Directed Acyclic Graph). Directed acyclic graph is directed and does not have any cycle in it.
```

## Topo Sorting Algos
### Kahn's
- You basically have a vector of innode that keeps track of number of nodes the current nodes depends on. You first take the node that depends on no other node and then remove 1 edge from all the node that depended on it repeat this process.
- If the graph contain cycle then the number of elements in topo sort won't be same as number of element node in the graph
```cpp
void topo_sort(){
	vector<int> dependencies(n,0);
	for(int i=0;i<n;i++){
		for(int nbr:graph[i]){
			dependencies[nbr]++;
		}
	}

	queue<int> q;
	for(int i=0;i<n;i++){
		if(dependencies[nbr]==0){
			q.push(i);
		}
	}

	while(!q.empty()){
		int curr = q.front();
		cout<<curr<<" ";
		q.pop();
		for(int nbr:graph[curr]){
			dependencies[nbr]--;
			if(dependencies[nbr]==0){
				q.push(nbr);
			}
		}
	}
}
```

## Using DFS
- If you perform dfs the last node of the current branch does not depend on any other node should it should be the one that comes at the end
- ![[Pasted image 20230720021003.png]]
- You start with 1->4->5. From 5 you can't go anywhere so add 5 to list
- From 4 you can't go anywhere else so add 4 to front of list 4, 5
- From 1 you can go again to 2->3.
- From 3 you can't go anywhere so add 3 to the front of the list 3, 4, 5.
- From 2 you can't go anywhere so add 2 to start of the list 2, 3, 4, 5
- All the path from 1 has been covered so add it 1, 2, 3, 4, 5
- From 0 no unvisited path so add that 0, 1, 2, 3, 4, 5.
```cpp
dequeue<int> ordering;
void dfs(int node){
	visited[node] = true;
	for(int nbr:graph[node]){
		if(!visited[nbr]){
			dfs(nbr);
		}
	}
	ordering.push_front(node);
}
```