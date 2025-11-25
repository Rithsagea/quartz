Source: [[10.5555 524279|Introduction to the Theory of Computation]]

A <u>clique</u> is a complete subgraph of some undirected graph. A clique of size $k$ is called a $k$-clique. We define the following language
$$
CLIQUE=\{\langle G,k\rangle:G\text{ is an undirected graph with a }k\text{-clique}\}
$$

## NP-Complete
>[!info]
>$CLIQUE$ is $NP$-complete

It is known that [[3SAT]] is $NP$-complete. A moment's thought shows that $CLIQUE\in NP$, as we can check in polynomial time whether a subgraph is complete.

Take some 3cnf-formula $\phi$ with $k$ clauses
$$
\phi=(a_1\lor b_1\lor c_1)
\land(a_2\land b_2\land c_2)
\land\cdots
\land(a_k\land b_k\land c_k)
$$

Define a graph $G$, with nodes $a_i,b_i,c_i$ (unique for each clause). Start with the complete graph, and remove any edges between $a_i,b_i,c_i$ (within one group) and nodes with contradicting values ($x$ and $\bar x$).

If $\phi$ has satisfying assignment, then we have a $k$-clique by picking a node corresponding to some true variable in each clause. None of these choices duplicate clauses or form contradiction, thus this subgraph is indeed complete.

If $G$ has a $k$-clique, each of the $k$ nodes must be contained in some unique clause. Furthermore none of these nodes have contradicting truth values, so passing the chosen node ($x$ or $\bar x$) into $\phi$ and picking arbitrary values for the unused variables will give a satisfying assignment.