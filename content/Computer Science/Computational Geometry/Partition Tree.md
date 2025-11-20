# 2-Dimensional Case
Source: [[10.1007 978-3-540-77974-2|Computational Geometry: Algorithms and Applications]]

Let $S\subset\mathbb R^2$ be a set of $n$ points. A <u>simplicial partition</u> for $S$ is a collection $\Psi(S):=\{(S_1,t_1),\ldots,(S_r,t_r)\}$, where $S=\bigsqcup_rS_i$ and $t_i$ is a triangle containing $S_i$. For some line $\ell$, the <u>crossing number</u> is the number of triangles in $\Psi(S)$ crossed by $\ell$. A simplicial partition is <u>fine</u> if $|S_i|<2n/r$ for every $i\in[r]$.

## Theorem 1
>[!info]
>For any set $S\subset\mathbb R^2$ with $n$ points and parameter $1\le r\le n$, a fine simplicial partition of size $r$ and crossing number $O(\sqrt r)$ exists. Furthermore, for any $\varepsilon>0$, this partition can be computed in $O(n^{1+\varepsilon})$.

<u>TODO: Find proof. Martousek (?)</u>

