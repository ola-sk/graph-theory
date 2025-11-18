## Definitions
Vertex: Node; vertices: nodes.\
Edges: lines connecting the nodes.
## Warm up exercises
### Exercise 1
Think about: 
3 neighbouring houses that need to be connected to supply of electricity, water and gas. Can we run the pipes/cables in a way that they do not cross each other vertically?

*Answer: No, we cannot they will always cross.*

### Exercise 2
Travelling Salesman Problem\
Given:\
<img width="317" height="317" alt="tRbgvhcZxLcwQjxv" src="https://github.com/user-attachments/assets/2e222ec8-d1d3-4b7a-9d56-0b15919fb669" />\
What is the shortest path a salesman can choose to visit all nodes?\
*Answer:*\
$A \xrightarrow{3} B \xrightarrow{1} D \xrightarrow{1} C \xrightarrow{1} D \xrightarrow{2} A$


## Types of Graphs
### Simple Graph
is a graph that has:
- no loops,
- no multiple edges between 2 vertices.

> [!IMPORTANT]
> Assumption: Throughout this lesson we'll be talking about graphs that are
> - undirected
> - unweighted

### Connected graph
A graph in which any vertex can be reached from any other vertex, i.e. there exists a path—**either direct or indirect**—between any 2 vertices.

### Complete graph
In such a graph every vertex has a **direct** edge to any other vertex. \
<img width="356" height="325" alt="Pasted image 20251118202610" src="https://github.com/user-attachments/assets/c4c393b4-09b1-4fd9-a6ee-1829622b6f61" />\
*Notation:*\
$K_{n}$\
where:
- $K$ means *connected* from German,
- $n$ is the number of vertices.\
*Properties:*
- Every vertex in a complete graph with n vertices has $n-1$ edges; that is because from each vertex there is a connection to any other vertex except itself.
- Number of connections is $n(n-1)$; n multiple because we count sum of all nodes (vertices), and $n-1$ is because there is $n-1$ connections from each single vertex. **connection $\neq$ edge
- Total number of edges is $\frac{n(n-1)}{2}$. $n(n-1)$ is number of connections (see point above) and we divide them by 2 because every connection repeats between 2 vertices, e.g. if we counted one connection from $a \to B$ we have also counted a connection from $B \to A$.

### Regular graph
Every vertex has the same degree (see section Degree of a vertex below).\

Q.: Does there exist a 5-regular graph with 9 vertices?\

## Degree of a vertex
number of edges connected to that vertex.

*Notation:*\
$deg(vertix)$

*Properties:*
- connected to the number of edges in "sum of vertices" formula.\
### Sum of vertices
Sum of degrees for **all** vertices of any graph:\
$\sum deg(v)=2\cdot number\ of\ edges$\
where:\
- $v$: stands for a set of all vertices\
- $number\ of\ edges$: concerns the total number of edges in the whole graph.\

from that follows that the $\sum deg(v)$ is always even.\

### Degree sequence
<img width="347" height="241" alt="Pasted image 20251118205821" src="https://github.com/user-attachments/assets/61c3a814-2e9a-4a3c-b5cd-c7252527e371" />\
For a graph above we can list degree of each single node (vertex) in a list and sort it in decreasing order:\
\[4, 3, 3, 2, 2]\
Such a list is called a *degree sequence*.\

#### Havel-Hakimi algorithm
Is applied to make a quick check if you have a degree sequence that you can actually draw.\
- From the degree sequence, e.g. the \[4, 3, 3, 2, 2] look at the first element—4—this number tells you how many elements after it are gonna be subject to the operation.\
- Remove the first element (number 4) from the list, then we have \[3, 3, 2, 2].\
- Subtract 1 from the **first 4 elements** of the list. Why 4? because that was the number we removed. We get \[2, 2, 1, 1].\
- Sort entries to maintain the descending order.\
- Repeat the same procedure until we get a pair in the list. If we have a pair of 0s $\implies$ we can draw a graph.\

Lets check if our example degree sequence can be drawn:\
\[4, 3, 3, 2, 2]\
4 \[3, 3, 2, 2]    |-1\
\[2, 2, 1, 1]\
2 \[2, 1, 1]    |-1\
\[1, 0, 1]    | {reorder}\
\[1, 1, 0]\
1 \[1, 0]    |-1\
\[0, 0]    $\implies$ can be drawn.\

> [!TIP]
> Too high degree?
> If the highest degree in the degree sequence is bigger than the length of list -1, then we know that such graph cannot exist (or not be 'drawable'): list's length corresponds to the number of vertices in a graph, so if any particular node (vertex) has number of "connections" higher than there are other vertices, then we know that this is not possible because we assume that there is only a single edge between each vertex.

## Adjacency Matrix

<img width="355" height="241" alt="Pasted image 20251118212331" src="https://github.com/user-attachments/assets/da9b31c6-66a5-454f-9c8c-fa5e17edd550" />

Adjacency Matrix for the above graph ⬆️ \
*0* where there is no direct connection (edge) between 2 vertices\
*1* where there is a direct connection (edge) between 2 vertices.\

|     | A   | B   | C   | D   | E   |
| --- | --- | --- | --- | --- | --- |
| A   | 0   | 1   | 0   | 1   | 0   |
| B   | 1   | 0   | 1   | 1   | 1   |
| C   | 0   | 1   | 0   | 1   | 1   |
| D   | 1   | 1   | 1   | 0   | 0   |
| E   | 0   | 1   | 1   | 0   | 0   |

*Adjacency Matrices are symmetrix across the main diagonal (principal diagonal).*

## Exercises
1. Give all possible connected graphs with 4 vertices. Exclude different [isomorphs](https://en.wikipedia.org/wiki/Graph_isomorphism)—one of each of the isomorphs is good.
