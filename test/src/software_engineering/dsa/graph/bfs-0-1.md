# 0 1 BFS
## Problem Statement
- Shortest path in binary weighted graph
- Binary weighted graph are where weights are either 0 or x

## Solution
- You use Dijkstra for weighted graph that uses a priority queue so your time complexity is higher.
- But since we have the weight is either 0 or x we can take advantage of that. Use a dequeue instead of queue.
- Lets say you are at a node whose current distance is y now for all its neighbor you have two possibilities
	- **Edge distance 0**: Then the distance of the neighbor node will be y+0 = y which will be the smallest for the nodes in queue too so put that at the front of the dequeue.
	- **Edge distance x**: So your distance will be y+x which will be the maximum you can attain so just go ahead and put that at the back of the dequeue. 