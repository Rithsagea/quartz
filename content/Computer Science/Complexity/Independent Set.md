Let $G$ be a graph. An independent set is a subset of nodes in $G$ which have no common edges. The language for the decision problem of finding a size $k$ independent set is as follows.
$$
INDEPENDENT\text-SET=\{\langle G,k\rangle:G\text{ has an independent set of size }k\}
$$

##
>[!info]
>$INDEPENDENT\text-SET$ is NP-complete

Given an set of nodes, we can check if it is of size $\ge k$ and is an independent set in polynomial time. Thus $INDEPENDENT\text-SET\in NP$.

To show completeness, we reduce from [[Clique]]. Let $G=(V,E)$ be some graph, and construct the complementary graph $G'$, where $V'=V$ and $E'=V^2\setminus E$. A $k$-clique of $G$ corresponds to a $k$ independent set of $G'$. Thus we have a polytime reduction and $INDEPENDENT\text-SET$ is NP-complete.