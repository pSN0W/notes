# Intro To Graphs 
## Type of Graphs
1. Weighted Graph:
	Edges have some value
2. Unweighted Graph:
	Edges do not have any value
3. Directed Graph:
	Edges are unidirectional
4. Undirected Graph:
	Edges are bidirectional.

## Graph Representation
Graph can be represented in various ways
1. Adjacency List
	For each node you store the neighbor of that node. You can use `vector<vector<int>>` to represent a graph like that.
2. Adjacency Matrix
	We will use a matrix and to show connection between node i and node j we will mark `mat[i][j] = 1` 
3. Edge List
	We store the edges in a vector so if there is an edge between i and j then you store i and j in the vector.
4. Implicit Graph
	You will be given a grid and you can access its four or eight neighbors

### Adjacency List Representation
```cpp
class Graph{
	vector<vector<int>> adj;
	int n;
	Graph(int _n){
		n = _n;
		adj.resize(n);
	}
	void add_edge(int i,int j,bool undir=true){
		adj[i].push_back(j);
		if(undir){
			adj[j].push_back(i);
		}
	}
}
```

### Representation with node class
```cpp
class Node{
public:
	string name;
	list<string> nbrs;
	Node(string name){
		this->name = name;
	}
}

class Graph{
	unordered_map<string,Node*> m;
public:
	Graph(vector<string> cities){
		for(auto city:cities){
			m[city] = new Node(city);
		}
	}
	void addEdge(string a,string b,bool undic=false){
		m[a].nbrs.push_back(b);
		if(undir)    m[b].nbrs.push_back(a);
	}
}

```

## Traversals of Graph
### BFS
We maintain a queue and do a level order traversal of the nodes
- BFS can be used to find the shortest path in un-directed graph.

```cpp
void bfs(int source){
	queue<int> q;
	vector<bool> visited(n,false);
	q.push(source);
	visited[source] = true;
	while(!q.empty()){
		int f = q.front();
		q.pop();
		for(int nbr:l[f]){
			if(!visited[nbr]){
				visited[nbr] = true;
				q.push(nbr);
			}
		}
	}
}
```

### DFS
We make a recursive call to all the children of source and continue doing it
```cpp
void dfs(int node){
	visited[node] = true;
	for(int nbr:graph[node]){
		if(!visited[node]){
			dfs(nbr);
		}
	}
}
```