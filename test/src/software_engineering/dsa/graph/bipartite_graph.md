# Bipartite Graph
```ad-abstract
You can devide all the vertices of the graph in two sets such that all edges of the graph are from set 1 to set 2.
```

![[Pasted image 20230720014350.png]]

## Check for bipartite graph
- Cycle with odd number of nodes
- Backedge with same color.
The way to solve this problem is by coloring the alternate edges

## Code
```cpp
bool dfs(int node,int color,int parent){
	visited[node] = color;
	for(int nbr:graph[node]){
		if(nbr!=parent and visited[nbr]==color){
			return false
		}
		else if(visited[nbr]==0){
		// 3-color because we want color to be 1 or 2 0 means not visited
			bool subProb = dfs(nbr,3-color,node);
			if(!subProb){
				return false;
			}
		}
	}
	return true;
}
```