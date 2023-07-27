# Minimum Spanning tree
Given a connected undirected and weighted graph select a subset of edges such that graph G is connected and total weight of selected edges are minimum.
![[Pasted image 20230720024251.png]]

You can solve it using greedy algorithms
## Algorithms
### Prim's Algorithm
- It's a greedy algorithm where the idea is that each step you choose a node with minimum edge value.
- Terms
	- MST Set : All the vertices that have been included in MST
	- Active Edges : Edge from a vertex in MST set to v
	- MST edge : Edge part of MST
- The algorithm goes as following
	- Start from any source vertex. (Put all edges in inactive)
	- Out of all active edges pick one with the smallest weight
	- Put the terminal of smartest weight in MST
	- Add edges starting from Y in active edges
- In the above example it will go as follows
	- Start from 1 put {1,0} and {1,2} in active edges.
	- Choose the min {1,2} put 2 in MST take out the edge 1,2 from active edge.
	- Put all the element from 2 to other vertices not in MST in active edges {2,0}, {2,8} in active edges take out the min

```cpp
class Graph{
	int v;
	vector<pair<int,int>> *l;
public:
	Graph(int v_){
		v = v_;
		l = new vector<pair<int,int>>[v];
	}
	void addEdge(int i,int j, int w){
		l[i].push_back({j,w});
		l[j].push_back({i,w});
	}
	int prim_mst(){
		priority_queue<pi,vector<pi>,greater<pi>> Q; // min heap {w,j}
		vector<bool> visited(v,false);
		int ans = 0;
		Q.push({0,0});
		while(!q.empty()){
			auto best = q.top();
			q.pop();
			int to = best.first;
			int weight = best.second;
			if(vis[to])   continue;
			vis[to] = 1;
			for(auto x:l[to]){
				if(vis[x.first]==0){
					q.push({x.second,[x.first](x.first)});
				}
			}
		}
		return ans;
	}
}
```

### Kruskal's Algorithm
- It's a greedy algorithm where you choose the smallest edge that doesn't form a cycle so you basically want to avoid an edge that takes you to one of the node that you have already visited.
- Store graph as edge list and then sort them based on their weight. Take edge one by one from sorted and add them to MST if they are from different set.

```cpp
class DSU{
	vector<int> parent;
	vector<int> rank;
public:
	DSU(int n){
		parent.resize(n);
		rank.resize(n,1);
		for(int i=0;i<n;i++){
			parent[i] = i;
		}
	}

	int find(int x){
		if(parent[x]==x){
			return x;
		}
		return parent[x] = find(parent[x]);
	}

	void unite(int x,int y){
		int par_x = find(x);
		int par_y = find(y);
		if(par_x!=par_y){
			if(rank[par_x]>rank[par_y]){
				parent[par_y] = par_x;
				rank[par_x]+=rank[par_y];
			}
			else{
				parent[par_x] = par_y;
				rank[par_y] += rank[par_x];
			}
		}
	}
}

class Graph{
	vector<vector<int>> edgeList;
	int v;
public:
	Graph(int v_){
		v = v_;
	}

	void addEdge(int x,int y,int w){
		edgeList.push_back({w,x,y});
	}

	int kruskal_mst(){
		sort(edgeList.begin(),edgeList.end());
		DSU s(v);
		int ans = 0;
		for(auto edge:edgeList){
			int w = edge[0];
			int x = edge[1];
			int y = edge[2];
			if(s.find(x)!=s.find(y)){
				s.unite(x,y);
				ans+=w;
			}
		}
		return ans;
	}
}
```