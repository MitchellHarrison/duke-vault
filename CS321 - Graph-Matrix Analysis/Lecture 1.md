# Intro to Graphs

> [!definition]
> We will let $G(V,E)$ be a graph that is constructed with vertices $V$ and edges $E$.

This course is listed as a theoretical computer science (TCS) course, but we will focus on applied problems as well. There will be several types of analysis covered, with an emphasis on using those methods for solving real-world problems.

## Graph Examples.

#### Social networks

If we let people be represented by vertices $V$, we can let social connections (family, social media connections, etc.) be represented by edges $E$. Then, we can construct a graph $G(V,E)$ that represents all social connections among members.

#### Computer networks

If we let $V$ be a set of computer servers, we can let edges $E$ represent routing connections between two such servers. We can build a graph $G(V,E)$ that represents the network in its entirely.

Standard notation for graphs denotes that $n = |V|$ and $m = |E|$.

## Diameters

> [!definition]
> If we have a cycle (i.e., there is a "loop" where a path loops back around on itself), we can find the **diameter** of these cycles/paths. That is, the longest possible path between any two nodes. We will denote it with $diam(G)$.

Say we have a computer network with five edges. If they are connected in a ring, there is a total of five edges which create a cycle. In this case, the diameter of this cycle $C$ is
$$
diam(C) = 2,
$$
because no two machine can use more than two edges to communicate. If we break one of those edges, we no longer have a cycle. We now have a path such that
$$
diam(P) = 4,
$$
where 4 is the maximum number of necessary edges to traverse to facilitate communication between any two nodes.

> [!definition]
> If all vertices are connected to all other vertices, a **clique** is formed. A clique of size 5 will be denoted with $k_5$. For all cliques, $diam(K) = 1$. Cliques are fast, but can be very costly to implement in the real world.

> [!definition]
> A **star** graph is a graph with one central node with edges to all other nodes. It can be represented by a tree. For all star graphs, $diam(G) = 2$, where communications traverse over one edge to get to the central node, then another edge to get to any other.

## Generalizing

### Cycles

In all cycles $C_{n}$, it is true that $m = n = O(n)$, and the $diam(C_{n}) = \lfloor \frac{n-1}{2}\rfloor$.

### Paths
For all paths $P_{n}$, it is the case that $m = n-1 = O(n)$. Observe that because we have $n-1$ edges and the longest path between any two nodes is two traverse all edges (i.e., get from one end of the path to the other), $diam(P) = n-1$.

### Cliques

For all cliques $K_{n}$, it is true that $m = \binom{n}{2} = \frac{n(n-1)}{2} = O(n^2)$. These are perfectly connected graphs. All other example thus far are considered very *sparse*. The diameter of cliques is constant, $diam(C) = 1$.

### Stars

For all star graphs $S_{n}$, it is true that $m = n-1$ and the diameter of stars are constant. That is, $diam(S_{n}) = 2$.

### Other examples

We have discussed several example of graphs so far. We can categorize these graphs and add a few more.

1. Graphs that connect interpersonal relationships are called **social networks**.
2. Graphs like a computer network are usually more difficult for laymen to understand, but simpler for those with technical expertise. These are **technical networks**.
3. Biological brains are made of neurons. These neurons have different biological components that handle inbound and outbound electrical signals. This is a *directed* graph that we will call a **neuron network**.
4. Graphs can be used to predict purchases. For example, if $V$ is made of products and $E$ represents co-purchase frequency, we can model customer behavior with a **co-purchase graph**.
5. Academic authors cite one other in their papers. We can build a **co-author network** to illustrate this or we can build a **co-citation network** to do similar analysis between papers instead of authors themselves. In Hollywood, they could make a **co-acting network** for actors that frequently work together. Similar networks can work in most industries.

The first step in solving any real-world problem is finding the binary relationship involved in the problem. We can use these binary relationships to construct our graph, and we can go to there. Let's consider an example:

## Adjacency Matrix

Let our vertices be integers. That is, $V = \{1, 2, \cdots,n\}$. Our edges are $(i,j) \in E$ where each edge is created when $i$ and $j$ are *co-prime*. That is, they share no factors between each other but 1.

Let $p(n) = \text{number of primes}$. We then have a subgraph $K_{p(n)}$ where all primes are connected to one another. Since all primes have no other factors, then all primes together form a clique (i.e., all primes are also co-primes). 

We can then create a matrix $A$ to represent this graph. This graph will have values

$$
A=
\begin{cases}
1 & (i,j) \in E \\
0 & else.
\end{cases}
$$

> [!definition]
> This is an **adjacency matrix**, and it will always be symmetrical along the diagonal. In a clique $K_{n}$, an adjacency matrix will have all 1's except for the diagonal. 

Now say we have two edges $(i,j)$ and $(j,k)$ in our graph. That is, those pairs of values are co-prime. Crucially, *this does not imply* that $(i,k)$ exists. For example, if $(i,j,k) = (15,16,27)$, then $i$ and $k$ share a common 3 and are not co-prime.

We can **walk** a graph using the adjacency matrix $A$. We will use a query vector $\mathbf{q}$ that is all zeros except for a 1 in position $j$. In this scenario, $A \mathbf{q}$ returns the $j$th column of $A$. In that column, the positions with value 1 are the values to which $j$ has an edge.

We can use multiple query vectors to traverse more steps from $j$. If we use two query vectors $\mathbf{q}_j$ and $\mathbf{q}_k$, then, 
$$
A \mathbf{q}_j + A \mathbf{q}_k = A(\mathbf{q}_j + \mathbf{q}_k)
$$
gives us the values within two steps. Doing this with $n$ vectors allows us to check which values are within $n$ steps of our starting value $j$.
