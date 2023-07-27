# Shortest Path Algos

## Single Source Shortest Path
Your main goal here is to find distance of all the point from a single source
1. BFS : for unweighted graph
2. Dijkstra: for weighted graph, fails for negative weight
3. Bellman Ford: For weighted graph, works for negative weight also

### Dijkstra
- We greedily choose the closest node.
- Initially you have distance for all nodes as inf.
- You take the initial node and put all the neighbors of that node in a set
```cpp
class Graph{
// ... for weighted adjacency list

	int dijkstra(int source,int dest){
		vector<int> dist(v,INT_MAX);
		set<pair<int,int>> s;
		dist[source] = 0; 
		st.insert({0, source});
		while(!st.empty()){
			auto it = st.begin();
			int node = it->second;
			int distTillNow = it->first;
			
			// optional for set
			if(distTillNow>dist[node]){
				continue;
			}
			s.erase(it);
			for(auto nbrPair:graph[node]){
				int nbr = nbrPair.second;
				int wt = nbrPair.first;
				if(distTillNow+wt<dist[nbr]){
					auto f = st.find({dist[nbr], nbr});
					if(f!=st.end()){
						s.erase(f);
					}
					dist[nbr] = distTillNow + wt;
					s.insert({dist[nbr], nbr});
				}
			}
		}
		return dist[dest];
	}
}
```

### Bellman Ford
- You initially have all the distance set to INT_MAX except the source one.
- Relax all edges V-1 times
	- In relaxation what you do is `if dist[v] > dist[u] + wt => dist[v] = dist[u] + wt`
	- ![[Pasted image 20230720033814.png]]
- The intuition behind bellman ford is quite cool. In each iteration of relaxation we are just updating the nodes that are i away from the source
- In the above example we updated distance as per the 1 edge distance node. In the second iteration of relaxation we update distance at 2 edge distance and ..
- **Negative Weight Cycle**: It is not possible to find the shortest distance in this case because with each iteration you can reduce the distance. To detect this we can run Bellman Ford algo V times and if the distance in V-1 relaxation step and V relaxation step differ then we have got a negative wt cycle.

```cpp
vector<int> bellman_ford(int v,int src, vector<vector<int>> edges){
	vector<int> dist(n+1, INT_MAX);
	dist[src] = 0;
	for(int i=0;i<V-1;i++){
		for(auto edge:edges){
			int u = edge[0];
			int v = edge[1];
			int wt = edge[2];
			if(dist[u]!=INT_MAX and dist[u]+wt < dist[v]){
				dist[v] = dist[u] + wt;
			}
		}
	}
	for(auto edge:edges){
		int u = edge[0];
		int v = edge[1];
		int wt = edge[2];
		if(dist[u]!=INT_MAX and dist[u]+wt < dist[v]){
			cout<<"Negative wt cycle"<<endl;
		}
	}
	return dist;
}
```

## Shortest Path between all nodes
### Floyd Warshall Algorithm
- Works with negative edges too
- DP Based O(n^3)
- Use adjacency matrix for this solution. Where unconnected node have distance of inf.
- The idea is simple for every i,j we try to compute the minimum distance it will take to go from i to j while going via k.
- Where is DP being used?
	- Lets say the shortest path from 1 to 4 is 1->2->3->4
	- Generally we would have to check all such path but now `dp[1][3]` contains all such path that takes you from 1 to 3 via any other node.

```cpp
vector<vector<int>> floyd_warshal(vector<vector<int>> graph){
	vector<vector<int>> dist(graph);
	for(int via=0;via<n;via++){
		for(int i=0;i<n;i++){
			for(int j=0;j<n;j++){
				dist[i][j] = min(dist[i][j], dist[i][via]+dist[via][j]);
			}
		}
	}
	return dist;
}
```