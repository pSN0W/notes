# Cycle Detection
## Un-directed Graph
- We just have to make sure that a particular node is not visited more than once
- One small check to ensure that you are not visiting the parent again

```cpp
bool dfs(int node, int parent){
	visited[node] = true;
	for(int nbr:graph[node]){
		if(nbr!=parent and visited[node]){
			return true;
		}
		else{
			bool nbrFoundCycle = dfs(nbr,node);
			if(nbrFoundCycle){
				return true;
			}
		}
	}
	return false;
}
```

## Directed Graph
- #unsolved 
- You have to ensure that same node is not visited twice in the same branch that is you have to ensure no back edges
- You will have to create one more visited that tracks the visited in this branch. Why do you need one to keep global context is that you do not iterate over the same node again.
```cpp
bool dfs(int node){
	visited[node] = true;
	stack[node] = true;
	for(int nbr:graph[node]){
		if(stack[nbr])    return true;
		if(!visited[nbr]){
			if(dfs(nbr)){
				return true;
			}
		}
	}
	stack[node] = false;
	return false;
}
```