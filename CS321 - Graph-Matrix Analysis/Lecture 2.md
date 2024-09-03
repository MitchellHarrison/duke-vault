# Lecture 2

## Homework questions

### Question 1

#### 1A
Let $G$ be an undirected graph and $A$ be its adjacency matrix. Because $G$ is *undirected*, then $A^T =A$. This is not necessarily the case for directed graphs due to the method in which adjacency matrices are constructed (see previous lecture). **TRUE**

#### 1B
We can use the notation $A(U,U)$ for subset $U$ in an adjacency matrix $A$. Say for instance that $U = \{u_1,u_2\}$, then $A(U,U)$ is a smaller matrix that only contains rows and columns corresponding to node $u_1$ and $u_2$. **TRUE**

#### 1C
Because $V_1 \cap V_2 = \emptyset$, then $V_1$ and $V_2$ are disjoint subset. If $V_1 \cup V_2 = V$, this is a **covering** relationship. If $V_1 \cap V_2 = \emptyset$, then $V_1$ and $V_2$ are **partitions**. Partitions must be non-overlapping.

> [!definition]
> A **bipartite graph** can be partitioned into subsets where all vertices are included (but only once among all partitions), and $E \subset V_1 \times V_2$ (that is, each subset has edges between all others). These are the **covering** and **edge** properties respectively. *There may not be edges between vertices within the same set.* Therefore, **bipartite graphs are triangle-free by definition**.

> [!definition]
> A **K-partite** graph is similar to a bipartite graph, but can be partitioned into $K$ subsets.

For example, if there is a graph with three nodes but only two edges, there is a pair of nodes that are not connected. This cannot be a **tripartite** graph, since the nodes with no connections could not satisfy the edge property.

Because we can turn any adjacency matrix into its corresponding graph (and vice-versa), we can represent this using the notation $A(V_1,V_2)$. **TRUE**

#### 1D
Here, $m = |E|$ and $nnz(A)$ is the number of non-zero values in adjacency matrix $A$. Because 

#### 1E

### Question 2

#### 2A
The notation $G[v]$ refers to a **closed** set and $G(v)$ refers to an **open** set. Closed sets include the reference node and open sets do not consider the reference node.

#### 2B

#### 2C

### Question 3

#### 3A
> [!definition]
> A node is **incident** on an edge if it is one of the nodes connected by the edge. A edge can also be incident on a vertex, or a subgraph can be incident.

> [!definition]
> A **neighborhood graph** of a node is the subgraph made of all nodes that that node is connected to, but without the reference node. Edges may be connected between neighbor nodes, but the reference node is not present.

Thus, **TRUE**

#### 3B
