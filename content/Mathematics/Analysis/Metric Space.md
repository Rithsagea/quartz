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

# Compact Sets

An <u>open cover</u> of a set $E$ in a metric space $(X,d)$ is a collection $\{G_\alpha\}$ of open subsets of $X$ such that $E\subseteq\bigcup_\alpha G_\alpha$. A subset $K$ of $X$ is <u>compact</u> if every open cover of $K$ contains a finite subcover.

# Connected Sets

Two subsets $A$ and $B$ of a metric space $(X,d)$ are <u>separated</u> if $A\cap\bar B$ and $\bar A\cap B$ are empty. A set $E\subseteq X$ is <u>connected</u> if $E$ is not a union of two nonempty separated sets.