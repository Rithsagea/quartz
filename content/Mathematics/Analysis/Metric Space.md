Source: [[9780070542358|Principles of Mathematical Analysis]]

Given some set $X$, a function $d:X\to\mathbb R$ is a <u>metric</u> if it satisfies the following properties.
1. $d(p,q)>0$ if $p\ne q$; $d(p,p)=0$.
2. $d(p,q)=d(q,p)$
3. $d(p,q)\le d(p,r)+d(r,q)$, for any $r\in X$.

With this presentation, $(X,d)$ is a <u>metric space</u>

# Definitions

Let $(X,d)$ be a metric space and $E\subseteq X$. Then we have the following definitions

- An <u>$\varepsilon$-neighborhood</u> of $p\in X$ is $N_\varepsilon(p)=\{q\in X|d(p,q)<\varepsilon\}$
- A point $p\in E$ is a <u>limit point</u> if every neighborhood of $p$ contains a point $q\ne p$ such that $q\in E$.
- If a point $p\in E$ is not a limit point, then it is an <u>isolated point</u>
- $E$ is <u>closed</u> if every limit point of $E$ is a point of $E$
- A point $p$ is an <u>interior</u> point of $E$ if there is a neighborhood $N$ of $p$ such that $N\subseteq E$.
- The <u>complement</u> of $E$ is $E^C=\{p\in X|p\not\in E\}$
- $E$ is <u>perfect</u> if $E$ is closed and if every point of $E$ is a limit point of $E$
- $E$ is <u>bounded</u> if there is a real number $M$ and point $q\in X$ such that $d(p,q)<M$ for all $p\in E$
- $E$ is <u>dense</u> in $X$ if every point $X$ is a limit point of $E$, or a point of $E$.

# Complete Spaces
A subset $E$ of a metric space $(X,d)$ is <u>complete</u> if every Cauchy sequence in $E$ converges and its limit is in $E$.

# Compact Sets

An <u>open cover</u> of a set $E$ in a metric space $(X,d)$ is a collection $\{G_\alpha\}$ of open subsets of $X$ such that $E\subseteq\bigcup_\alpha G_\alpha$. A subset $K$ of $X$ is <u>compact</u> if every open cover of $K$ contains a finite subcover.

Let $(X,d)$ be a metric space. $E\subseteq X$ is <u>totally bounded</u> if for every $\varepsilon>0$, the set $E$ can be covered by finitely many balls of radius $\varepsilon$. That is, there are $x_1,\ldots,x_n\in X$ such that $E\subseteq\bigcup^n_{i=1}N_\varepsilon(x_i)$.

## Characterizations of Compactness
>[!info]
>If $E$ is a subset of a metric space $(X,d)$, the following are equivalent
>1. $E$ is complete and totally bounded
>2. Every sequence in $E$ has a convergent subsequence.
>3. Every open cover of $E$ has a finite subcover.

$(1)\Rightarrow(2)$. Let $(x_n)\subseteq E$. Since $E$ is totally bounded, it can be covered in finitely many balls of radius $2^{-1}$. Let $B_1$ be one of these balls that contain infinitely many points of $x_n$. Recursively, note $B_i\cap E$ can be covered with finitely balls of radius $2^{-i-1}$. Pick $B_{i+1}$ to be one of these balls such that $B_{i+1}$ has infinitely points of $x_n$. Pick $(x_{n_k})$ such that $x_{n_k}\in B_k$, so this sequence is Cauchy and converges (by completeness).

$(2)\Rightarrow (1)$. If $E$ is not complete, then there is some Cauchy sequence which does not converge in $E$, violating (2). If $E$ is not totally bounded, then there is some $\varepsilon>0$ where $E$ cannot be covered in finitely many $\varepsilon$-balls. Pick $x_1\in E$, and $x_{i+1}\in E\setminus\bigcup_{j\in[i]}V_\varepsilon(x_i)$. Clearly $d(x_n,x_m)>\varepsilon$ for $n\ne m$, thus no subsequence can converge. By contraposition we have proved the claim.

$(1)\land(2)\Rightarrow(3)$. Let $(V_\alpha)$ be an open cover of $E$. It suffices to show that there exists $\varepsilon>0$ where every $\varepsilon$-ball intersecting $E$ is contained in some $V_\alpha$.  Suppose this is not true. Then for every $n\in\mathbb N$, there is a $2^{-n}$ ball $B_n$ where $B_n\cap E\ne\varnothing$ and not contained in any $V_\alpha$. Pick $x_n\in B_n\cap E$, which has a subsequence converging to $x\in E$. There is some $V_\alpha$ where $N_\varepsilon(x)\subseteq V_\alpha$ for some $\varepsilon>0$. For large enough $n$, $d(x_n,x)<\frac\varepsilon3$ and $2^{-n}<\frac\varepsilon3$. Fixing $n$, for any $y\in B_n$, $d(y,x)\le d(y,x_n)+d(x_n,x)<\varepsilon$. Thus $B_n\subseteq V_\alpha$, giving a contradiction.

$(3)\Rightarrow(2)$. If $(x_n)\subseteq E$ has no convergent subsequence, then for every $x$, there is a neighborhood of $x$ containing finitely many points. These form an infinite cover of $E$, which clearly has no finite subcover.

# Connected Sets

Two subsets $A$ and $B$ of a metric space $(X,d)$ are <u>separated</u> if $A\cap\bar B$ and $\bar A\cap B$ are empty. A set $E\subseteq X$ is <u>connected</u> if $E$ is not a union of two nonempty separated sets.