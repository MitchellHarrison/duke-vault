# Lecture 5

> [!definition]
> When say that a matrix $A$ is **irreducible**, this is equivalent to saying that the corresponding graph $G$ is **strongly connected**. In a strongly connected graph, it is possible to get from any node $u$ to any other node $v$.

Say that we have a network of the best $k$ friends. An edge from $u$ to $v$ means that $u$ considers $v$ among their best $k$ friends. Note that this graph is not symmetrical in the general case because $v$ may not consider $u$ among their best friends in return. A similar structure exists for citation graphs among research publications.

We can represent these graphs with matrices as well. In the citation graph, for example, we can consider the columns to be the paper that are doing the citing, and the rows would be the papers being cited. This matrix would not be symmetric and could not be strongly connected. For example, if the columns only include articles published since 2000, they may cite papers from before then, but those papers wouldn't be represented in the columns of $A$ since they are pre-2000.

> [!definition]
> An **indexing** is a way of ordering the columns of our matrix $A$. This involves permuting the columns in any number of orders. This process is *re-indexing*.

> [!definition]
> A **block-triangular matrix** is one in which there is a block of zeros that reach from the bottom-left entry to the diagonal. This could be the lower-left quadrant of the matrix, or it could be the first $n-1$ entries of the bottom row. In any combination in between, we can divide the graph into 4 pieces (equal or not), the bottom-left of which is all $0$s up to the diagonal.

> [!definition]
> Similar to a block-triangular matrix, a **block-diagonal matrix** has zero values in the upper-right *and* the bottom left quadrants. Thus, all entries are on the "diagonal" quadrants.

We can permute the columns using indexing. If we have an un-directed graph, if we can permute to arrive at a block-triangular matrix, it is strongly connected. For directed graphs, it is strongly connected if we can permute until we arrive at a block-diagonal one.

> [!note]
> Transposing a matrix representation of a graph has the effect of flipping all of the edges in the graph (i.e., reversing the arrows). Clearly, doing so for an un-directed graph has no effect because $A^T=A$.

