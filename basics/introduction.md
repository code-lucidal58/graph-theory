# Graph Theory - Introduction
Graph theory is the mathematical theory of properties and applications of graphs, or also called networks.
Graph can be found anywhere. Example: combinations of clothes you can wear. The cloth piece will be the node. The 
relationship established will be the edge. Other such example is a social group, where there can be friends of friends. 

## Types of Graphs
* **Undirected**: simple type. Edges have no orientation. edge(u,v) == edge(v,u)
* **Directed graphs or digraphs**: Edges are directed. Edge(u,v) is edge from u to v. There will be arrowheads in the edge representations.
The above mentioned graphs can also have weights to represent arbitrary values like cost, distance, quality, etc.
Hence, an edge with a weight will be represented as (u,v,w). This will mean that the edge is from u to v and has weight w.  

There are some special graphs as well.
* **Tree**: It is an undirected graph with no cycles. It is a connected graph with N nodes and N-1 edges.
* **Rooted Tree**: There is a designated root node, where all other nodes point away (arborescence, out-tree) or point
towards (anti-arborescence, in-tree) from the root node.
* **Directed Acyclic Graph (DAGs)**: these are directed graphs without any cycles. They are important because they represent 
schedulers, build systems, compilers, dependencies, etc.  
***NOTE***: All out-trees are DAGs, but not all DAGs are out-trees. 
* **Bipartite Graph**: Here the vertices/nodes can be split into two independent groups (U and V) such that every edge connects
between U and V. Like in a many-to-many representation, or network flow.
* **Complete Graph**: There is a unique edge between every pair of node. It is denoted by Kn where n is the number of nodes. 
With the large number of edges, these graphs are used for performance testing.

## Representation of Graphs
The way a graph is represented impacts its performance.
### Adjacency Matrix
Most commonly represented as Adjacency Matrix. It is a 2D matrix,
where m[i][j] represents the weight of edge from i to j. Weight of an edge from a node to itself is assumed to be 0. Size
of the matrix will be n*n. 
#### Pros 
They are space efficient for dense graphs. The lookup for edge weight is O(1). This is the simplest graph representation.
#### Cons
For sparse graphs, this takes up a lot of space i.e. O(n^2). Plus, iterating over all edges take O(n^2).

### Adjacency List
This representation is actually a dictionary, where key is the node, and value is a list with all outgoing edges. 
`A -> [(B,4), (C,10)]`. Each item in the list is a tuple with the destination node and the weight of the edge.
This representation is great for sparse graphs.
#### Pros
It is space efficient for sparse graphs. Iterating over all edges is efficient.
#### Cons
Less space efficient for dense graphs. Edge weight lookup is O(E). And, this representation is slightly more complex than the matrix.

### Edge List
This is a list where each item is of the form (u,v,w). Edge from u to v with weight w. This is conceptually simple but
due to lack of structure, it is seldom used.
#### Pros
Space efficient. Iterating over edges is efficient. Very simple structure.
#### Cons
Less space efficient for dense graphs. Edge weight lookup is O(E). 

## Common Graph Problems
There are a number of questions to be asked before the problem is actually tackled. Is it undirected or directed, weighted or not?
Depending on the usecase, the graph will be mostly sparse ot dense? What form of representation is best suited?

### Shortest Path Algorithms
Given a weighted graph, find the shortest path to Node A from Node B. There are a number of algorithms available for the same. 
Depending on the connectivity, negative cycles, strongly connected graphs, an algorithm is chosen. 
**Algorithms**: BFS (unweighted graph), Dijkstra's, Bellman-Ford (for graphs with -ve cycle), Floyd-Warshall (for graphs with -ve cycle), 
A*, DFS, Tarjan's, Kosaraju's.

### Travelling Salesman Problem
This is an NP-hard problem, meaning computationally expensive. A salesman has to travel through all the nodes of the graph
at minimum cost.  
**Algorithms**: Held-Karp, branch and bound, approximation algos. 

### Identify Bridges
Bridges/Cut edges is an edge whose removal increases the number of connected components. For example the connection between Person A
and person B is a brigde in a graph with all friends of A and all friends of B. They hint weak points, bottlenecks, or vulnerabilities.
The nodes in the bridges are called **articulation points/cut vertex**.

### Minimum Spanning Tree
It is a tree with all vertices connected without any cycles. Total weight of the resultant tree should be minimum.  
**Algorithms**: Kruskal's, Prim's, Boruvka's. 

### Network flow: max flow
Given source, sink and infinite input, what is the capacity of the network? For example, number of cars that can fit on a route
to town A from town B.  
**Algorithms**: Ford-Fulkerson, Edmonds-Karp and Dinic's.

## Depth First Search
Fundamental search for traversal through nodes and edges. Time complexity O(V+E), directly proportional to size of graph. 
Often used as the building block for other algorithms. The augmented version can be used to find connected components, bridges, etc.
It plunges into depth first, does not care which node it selects next, and goes on till it cannot move ahead. From here, it backtracks and continues.
The traversal should not go in cycles. Hence, backtracks starts even when a visited node is reached. Adjacency List is 
used for in DFS. Code for DFS can be found [here](dfs.py).

Connected components are a set of nodes forming disjoint graphs. DFS can be used to count the number of components in a
representation. This is done by giving same id to each node in a component. Start DFS at each node, unless it is marked as visited.
Code for component counts is [here](count_components_dfs.py).

