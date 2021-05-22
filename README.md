# Graph Theory - Intro and Overview
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
