<style> h1 a{display:none;} .container-lg {min-width: 200px; max-width: 880px; padding: 45px} </style>

[All notes](http://karishmadaga.com/course-notes) // [About](http://karishmadaga.com)

# CISC 365: Algorithms

## Topics:

- [Breadth First Search](#breadth-first-search)
- [Dijkstra's Algorithm](#dijkstras-algorithm)
- [NP-Complete](#np-complete)

## Breadth First Search 

```
class Graph:
	
	# Constructor
	def __init__(self):
		# default dictionary to store graph
		self.graph = dict(list)
	
	# function to add an edge to the graph
	def addEdge(self, u, v):
		self.graph[u].append(v)

	#Function to print BFS of a graph
	def BFS(self, s):
		
		#Mark all the vertices as not visited 
		visited = [False] * (len(self.graph))
		
		# Mark the source node as visited and enqueue it
		queue.append(s)
		visited[s] = True
		
		while queue:
			
			# Dequeue a vertex from queue and print it
			s = queue.pop(0)
			print(s, end = " ")
			
			# Get all the adjacent vertices of the dequeued vertex s.
			# If a adjacent has not been visited, then mark it as 
			# visited and enqueue it.
			
			for i in self.graph[s]:
				if visited[i] == False:
					queue.append(i)
					visited[i] = True
```

## Exercise: Find all connected components of G in O(n+m) time.

Intuition: 

- Initialize all vertices as not visited
- Do the following for every vertex 'v'
	- If 'v' is not visited before, call BFS(v)

BFS(v):

- Mark 'v' as visited[v] = true
- Print 'v'
- Do the following for every adjacent neighbour 'u' of 'v':
	- if 'u' is not visited, recursively call BFS(u)

## Dijkstra's Algorithm
The algorithm for Dijkstra's Algorithm is synctatically similar to BFS except that we replace the queue with a priority queue (implemented as a min-heap).

Pseudo code:

```
dist(v) = infinite for every v element of V
dist(s) = 0 // where s is the source/start vertex

Q = make-priority-queue(v) 
// all vertices are put into the PQ using dist[v] as the key/priority value of v

while Q is not empty do:
	u = delete-min(Q) //dequeue the vertex with min dist-value
	for each neighbour v of u:
		if dist[u] + length_of_uv < dist[v]:
			dist[v] = dist[u] + length_of_uv
			decrease-key(Q, v)
			parent[v] = u
```
### Complexity: 

- Each vertex is enqueued in the beginning and dequeued when it is removed once.
- When a vertex u is dequeued, we check ever edge uv and may use the value ```dist[u] + length_of_uv``` to update the value of ```dist[v]``` (decr key)
- All the enqueue, dequeue, and update operations can be implemented in O(log n) time using a heap, and thus the total time complexity is O((n + sum(deg(v)) log n) = O((n+m)log n) time. So the cost is only a factor of log n.
- With more advanced data structures (i.e. fibonacci heap), the runtime could be improved to O(nlogn + m).

### Analysis
- You can also think of Dijkstra's as a greedy algorithm
- The idea is to grow a subset R of V (vertices) so that dist[v] for the vertices of R are computing correctly. Initially, R = {s}, and then each vertex we add to R is the closest to R -- so in a sense we are growing R greedily.

## NP-Complete

- 1970: Computers were becoming widely available, and people were starting to find that there were two classes of problems: problems that could be solved very easily and a large class that could not be solved. Steve Cook (Toronto) and S. Lenin independently arrived to the same conclusion: all of these not solvable problems are in the same class.

### Problem Classes

#### Polynomial Time Solvable (P)

