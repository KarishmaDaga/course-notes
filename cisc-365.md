# CISC 365: Algorithms

- [Breadth First Search](#breadth-first-search)


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

