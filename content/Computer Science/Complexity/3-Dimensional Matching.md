Let $X,Y,Z$ be sets, and consider $T\subseteq X\times Y\times Z$. $M\subseteq T$ is a <u>3-dimensional matching</u> if for all $(x_1,y_1,z_1)\ne(x_2,y_2,z_2)\in M$, $x_1\ne x_2$, $y_1\ne y_2$, and $z_1\ne z_2$. The language for the decision problem is as follows
$$
3DM=\{\langle T,k\rangle:T\text{ has a 3-dimensional matching }M\subseteq T\text{ with }|M|\ge k\}
$$

## NP-Complete
>[!info]
>$3DM$ is NP-complete

We can check if a subset of $T$ is a 3-dimensional matching by looking for conflicts in polynomial time. Thus $3DM\in NP$.

To show completeness, we reduce from [[3SAT]]. Given a Boolean formula $\phi=\bigvee_{i=1}^la_i\lor b_i\lor c_i$ with variables $x_1\ldots x_j$. For each variable, construct a "rose" gadget as below with $2l$ petals. The even petals represent a true assignment, while the odd petals represent a false assignment.

![[3-Dimensional Matching Variable Gadget.excalidraw.svg | center]]

For each clause $a_i\lor b_i\lor c_i$, create two additional nodes, and attach it to the outer nodes of the respective true / false petals for each $a_i,b_i,c_i$. Let $k=2lj+l$, so any 3-dimensional matching corresponds to picking a parity for the false literal in the rose gadget, and matching each clause gadget with the unused petal nodes. This gives a satisfying assignment to $\phi$, so $3DM$ is NP-complete.