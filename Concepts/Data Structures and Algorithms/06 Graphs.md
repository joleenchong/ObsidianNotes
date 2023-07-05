Lecture 06: Graphs

**Main Topics**
- terminology
- representation
- algorithms
- time complexity
---------------------
# Terminology
- *graph* - a data structure that represents connections between items made up of set **V** of vertices and set **E** of edges
- *vertex* - a labelled node in graph
	- vertices are adjacent if connected by an edge
	- *degree* - number of edges that point to / from a vertex, denoted by d(v)
		- Directed graphs:
			- Outdegree - number of edges where vertex is source
			- Indegree - number of edges where vertex is sink
- *edge* - an arc joining two vertices
	- edges can be directed {node, node} / undirected (source, sink)
- *multigraph* - allows multiple edges between same pair of vertices (opposite is simple graph)
- size of V / E= |V|, denoted by n / |E|, denoted by m
- *path* - a sequence of vertices connected by edges
	- considered simple if each vertex only appears once
	- vertex u is reachable from v if there is a path for u to v

ok this is not gonna get tested so if i ever want to look through this again i'll redo this part

# Implementation
- put together through a set of nodes linking to other notes
- each node has zero or more links
- Format of adjacency list / matrix:
![[Pasted image 20230414134540.png]]
- Big-O Analysis:
![[Pasted image 20230414134201.png]]
## Adjacency List
- uses **[[04 Linked Lists |linked list]] within each node** to connect to other nodes
- 3 implementations:
	- lists and links (no data)
	- lists of GraphNodes (data in nodes)
	- lists of GraphNodes and Lists of Edges
//continue from slide 49
## Adjacency Matrix
- uses an **n x n matrix** of Booleans / ones and zeroes / values to represent weight
- maintains array to lookup labels (O(1) operation)
- adding vertex means to increase size of array or start with default capacity and track size
- list of vertices, then list of connections (edges)
``` java
public class DSAGraph
{
	int[][] matrix; //stores vertices
	//labels(?) need to figure out what data type this is

	public DSAGraph(int n) //n is number of vertices
	{
		int[][] matrix = new int[n][n];
	}

	public void addVertex(String label)
	{
		//add code
	}

	public void addEdge(String label1, String label2)
	{
		//add code
	}

	public boolean hasVertex(String label)
	{
		//add code
	}

	public int getVertexCount()
	{
		//add code
	}

	public int getEdgeCount()
	{
		//add code
	}

	public boolean isAdjacent(String labe1, String label2)
	{
		//add code
	}

	public String[] getAdjacent(String label)
	{
		//add code
	}

	public void displayAsList()
	{
		//add code
	}

	public void displayAsMatrix()
	{
		//add code
	}
}
```

# Search and Traversal
- no leaf nodes / tail to determine end of graph -> need to keep track of vertices visited
- Approach:
	- move through graph, marking vertices as visited
	- on each step, continue through not visited vertices until all vertices have been visited
- Two traversal algorithms
	- Depth-First Search - go as deep along each path as possible before returning
	- Breadth-First Search - goes level by level as you move away from starting point

## Depth-first

## Breadth-first
