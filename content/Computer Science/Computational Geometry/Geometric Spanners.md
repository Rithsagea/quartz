Source: [[10.5555 2031416|Geometric Approximation Algorithms]]

For a weighted graph $G$ with vertices $v_1,v_2\in V$, the <u>graph distance</u> $d_G(v_1,v_2)$ is the weight of the shortest path from $v_1$ to $v_2$.

Let $P$ be a set of points in $\mathbb R^d$. A <u>$t$-spanner</u> of $P$ is a weighted graph $G$ with vertices $P$ where for all $x,y\in P$, $\|x-y\|\le d_G(x,y)\le t\|x-y\|$.

## Construction
Given some point set $P\subseteq\mathbb R^d$ and parameter $\varepsilon$, set $\delta=\varepsilon/16$ and compute the $1/\delta$-[[Well Separated Pair Decomposition|WSPD]] of $P$, $\mathcal W$. For each $\{u,v\}\in\mathcal W$, choose some arbitrary $\mathrm{rep}_u\in U$ and $\mathrm{rep}_v\in v$, and add $\{\mathrm{rep}_u,\mathrm{rep}_v\}$ with weight $\|\mathrm{rep}_u-\mathrm{rep}_v\|$ to our new graph $G$. The resulting graph will be a $(1+\varepsilon)$-spanner of $P$ with $O(n\varepsilon^{-d})$ edges.

### Correctness

Inducting on the edge length of pairs in $G$. Fix $x,y\in P$, and assume for all $z,w\in P$ where $\|z-w\|<\|x-y\|$, we have $d_G(z,w)\le(1+\varepsilon)\|z-w\|$. By construction, there is some $\{u,v\}\in W$ where $x\in P_u$ and $y\in P_v$. By property of WSPD, we know $\max(\Delta(u),\Delta(v))\le\delta\cdot d(u,v)$, therefore
$$
\|\mathrm{rep}_u-\mathrm{rep_v}\|
\le d(u,v)+\Delta(u)+\Delta(v)
\le(1+2\delta)d(u,v)
\le(1+2\delta)\|x-y\|
$$

$$
\max(\|\mathrm{rep}_u-x\|,\|\mathrm{rep}_v-y\|)
\le\max(\Delta(u),\Delta(v))
\le\delta\cdot d(u,v)
\le\delta\|\mathrm{rep}_u-\mathrm{rep}_v\|
$$

Note that $\delta(1+2\delta)<1/4$, thus $\|\mathrm{rep}_u-x\|,\|\mathrm{rep}_v-y\|<\frac14\|x-y\|$. By the inductive hypothesis, we have

$$
d_G(x,\mathrm{rep}_u)\le(1+\varepsilon)\|\mathrm{rep}_u-x\|\qquad
d_G(y,\mathrm{rep}_v)\le(1+\varepsilon)\|\mathrm{rep}_v-y\|
$$

By construction, $d_G(\mathrm{rep}_u,\mathrm{rep}_v)<\|\mathrm{rep}_u-\mathrm{rep}_v\|$, thus we have
$$
\begin{align*}
\|x-y\|&
\le d_G(x,y)
\le d_G(x,\mathrm{rep}_v)
+d_G(\mathrm{rep}_u,\mathrm{rep}_v)
+d_G(\mathrm{rep}_v,y)\\
&\le(1+\varepsilon)(
\|\mathrm{rep}_u-x\|+
\|\mathrm{rep}_v-y\|)
+\|\mathrm{rep}_u-\mathrm{rep}_v\|\\
&\le(1+2\delta(1+\varepsilon))\|\mathrm{rep}_u-\mathrm{rep}_v\|
\le(1+2\delta+2\varepsilon\delta)(1+2\delta)\|x-y\|\\
&\le(1+\varepsilon)\|x-y\|
\end{align*}
$$

Note that the last step is achieved by some simple arithmetic

$$
(1+2\delta+2\varepsilon\delta)(1+2\delta)\le(1+4\delta)(1+2\delta)=1+6\delta+8\delta^2\le1+14\delta\le1+\varepsilon
$$