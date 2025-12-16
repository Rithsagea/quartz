Source: [[10.5555 524279|Introduction to the Theory of Computation]]

For some undirected graph $G$, a <u>vertex cover</u> is a subset of nodes where every edge of $G$ touches at least one of those nodes. The vertex cover problem looks for membership in the following language
$$
VERTEX\text-COVER=\{\langle G,k\rangle:G\text{ is an undirected graph that has a }k\text{-node vertex cover}\}
$$

## NP-Complete

>[!info]
>$VERTEX\text-COVER$ is NP-Complete

Given a graph $G$, a nondeterministic Turing machine can enumerate through all subsets of nodes with size $\le k$ and check if one of them gives a vertex cover. Thus $VERTEX\text-COVER\in NP$.

To prove membership in NP-hard, we reduce from [[3SAT]]. We map each boolean formula $\phi$ to some graph $G$. For each variable $x$, add nodes $x_v$ and $\bar x_v$ to $G$ and connect them with an edge. Next, for each clause $C=x\lor y\lor x$, add nodes $x_C,y_C,z_C$ to $G$, and connect all of these together. Next we add edges between $x_v\to x_C$, $y_v\to y_C$, and $z_v\to z_C$.

If $\phi$ has $m$ variables and $l$ clauses, then our construction of $G$ will have $2m+3l$ nodes. Let $k=m+2l$, and note that every clause gadget requires two nodes, while each variable gadget needs one in order to cover every edge.

For a true assignment of $\phi$, add the $m$ nodes corresponding to true literals to our vertex cover. Next, for each clause, fix one true literal, and add nodes corresponding to the other two literals to our cover. The edges in each gadget are covered, while the edges between the gadgets will be covered, as any false literals will be covered by the two literals in each clause.

If $G$ has a vertex cover with $k$ nodes, each variable gadget will only have one node set. Take this as our assignment, and observe each clause will have two nodes set. The unset node must have an edge covered by a node from a variable gadget, thus this will correspond to a true assignment of $\phi$.

This reduction gives a graph of size $O(ml)$, so we have a polytime reduction and $VERTEX\text-COVER$ is NP-complete.