Given a graph $G$, a <u>Hamiltonian path</u> from nodes $s$ to $t$ is a directed path from $s$ to $t$ that traverses every node exactly once. We define the language.
$$
HAMPATH=\{\langle G,s,t\rangle:G\text{ is a directed graph with a Hamiltonian path from }s\text{ to }t\}
$$

## NP-Complete
>[!info]
>$HAMPATH$ is NP-complete

Given a path, we can verify if it is Hamiltonian by checking if it traverses every node exactly once. Thus $HAMPATH\in NP$. To show completeness, we reduce from [[3SAT]].

Let $\phi=\bigwedge_{l=1}^k(a_l\lor b_l\lor c_l)$ be a 3cnf formula with $k$ clauses. Each character $a,b,c$ represents some literal $x_i$ or $\bar x_i$. For each variable $x_i$, create a line of $3k+1$ nodes, with a path going left and right. For every 3 nodes from left to right, assign the last 2 nodes from the $i$th group to the $i$th clause.

![[Hamiltonian Path Variable Gadget.png]]

Now for each clause $c_j$, create a corresponding node. If $c_j$ contains $x_i$, add a edges to form a clockwise loop with the previously assigned nodes. If it contains $\bar x_i$, make a counterclockwise loop instead. (below is an example of a clockwise loop)

![[Hamiltonian Path Clockwise Loop.png]]

Now we add intermediate nodes to connect each of the variable gadgets as follows, and link the top and bottom of these gadgets to start node $s$ and end node $t$.

![[Hamiltonian Path Summary.png | center | 500]]

Any path from $s$ to $t$ must traverse every horizontal strip of nodes. This is because we cannot use the clause gadgets to take a detour, as the adjacent separator nodes in each horizontal strip could not be traversed.

If we walk from left to right for $x_i$, we assign true to that variable. Otherwise, we assign false. When a path travels through a clause gadget, that indicates the current strip's assignment satisfies that clause. Thus there is a correspondence between Hamiltonian paths of $G$ and satisfying assignments to $\phi$. This reduction is done in polynomial time, so $HAMPATH$ is NP-complete.

# Undirected Hamiltonian Path

If we replace undirected graph with a directed graph, we have a new language $UHAMPATH$.

## NP-Complete

>[!info]
>$UHAMPATH$ is NP-complete

By similar reasoning to $HAMPATH$, $UHAMPATH\in NP$.

Let $G$ be a directed graph with nodes $s$ and $t$. We will construct an undirected graph $G'$, where a path $s\to t$ corresponds exactly to some path $s'\to t'$ for $s',t'\in G'$. For every node $u\in G$ add $u^{in}$, $u^{mid}$, and $u^{out}$ to $G'$, while adding edges $u^{in}\to u^{mid}\to u^{out}$. Set $s':=s^{out}$ and $t':=t^{in}$. For every edge $u\to v$ in $G$, add an edge $u^{out}\to v^{in}$. Any resulting path from $s'\to t'$ must follow the pattern

$$
s^{in},s^{mid},s^{out},u_1^{in},u_1^{mid},u_1^{out},u_2^{in},u_2^{mid},u_2^{out},\ldots,t^{in},t^{mid},t^{out}
$$

The edges inside each $u^{in}\to u^{mid}\to u^{out}$ gadget are forced, thus the remaining edges will give a path from $s\to t$ in $G$. The Hamiltonian property is transitive through this, thus we have a polytime reduction to $HAMPATH$ and $UHAMPATH$ is NP-complete.