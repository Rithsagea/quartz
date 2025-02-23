---
title: Analysis Definitions
---


# Real Numbers
Let $B\subseteq\mathbb R$, and $s\in R$.

<u>upper bound</u> $s\ge B\iff(\forall x\in B)\ s\ge x$
<u>lower bound</u> $s\le B\iff(\forall x\in B)\ s\le x$
$B$ <u>bounded</u> if it has both lower and upper bound
<u>maximum</u> $s$ upper bound and $s\in B$
<u>minimum</u> $s$ lower bound and $s\in B$
<u>supremum</u> $\sup B\ge B$, $(\forall s\ge B)\ \sup B\le s$
<u>infimum</u> $\inf B\le B$, $(\forall s\le B)\ \inf B\ge s$

<u>Axiom of Completeness</u> a nonempty set of real numbers has an $\inf$ or $\sup$ if it is bounded below or above

<u>Archimedean Property</u> $(\forall x\in\mathbb R)(\exists n\in\mathbb N)\ n>x$, $(\forall y>0)(\exists n\in\mathbb N)$

<u>Nested Interval Property</u> $(\forall (I_n)|I_1\supseteq I_2\supseteq\cdots)\ \bigcap^\infty_{n=1} I_n\ne\varnothing$

# Sequences
$(a_n)$ <u>converges</u> if $(\forall\epsilon>0)(\exists N\in\mathbb N)\ n\ge N\implies|a_n-a|<\epsilon$, or $a_n\in V_\epsilon(a)$
$(a_n)$ <u>bounded</u> if $(\exists M>0)\ |a_n|<M$
$(a_n)$ <u>Cauchy</u> if $(\forall \epsilon>0)(\exists N\in\mathbb N)\ m,n\ge N\implies |a_m-a_n|<\epsilon$
$(a_n)$ <u>monotone</u> if $(\forall n\in\mathbb N)\ a_n\le a_{n+1}\lor a_n\ge a_{n+1}$

<u>Monotone Convergence</u> a monotone bounded sequence is convergent

<u>Bolzano-Weierstrass</u> a bounded sequence has a convergent subsequence

# Topology
Let $K\subseteq\mathbb R$

<u>limit point</u> $x\in K$, $(\forall \epsilon>0)\ (V_\epsilon(x)\cap K-\{x\})\ne\varnothing$
<u>isolated point</u> $x\in K$ is not a limit point

<u>open</u> $(\forall x\in K)(\exists r\in\mathbb R)\ V_r(x)\subseteq K$
<u>closed</u> $K^C$ is open, $K$ contains all its limit points
<u>compact</u> <u>Heine-Borel Theorem</u>
- $K$ is bounded and closed
- $(\forall (x_n)\subset K)(\exists (x_{n_k}))x_{n_k}\rightarrow x$
- Every open cover of $K$ has a finite subcover

<u>closure</u> $\bar K$ the union of $K$ with its limit points

<u>connected</u> $A\cap\bar B=\bar A\cap B=\varnothing$
<u>perfect</u> every point of $A$ is a limit point.

Union of arbitrarily many open sets is open.
Union of finitely many closed sets is closed.
Intersection of arbitrarily many closed sets is closed.
Intersection of finitely many open sets is open.

# Functions
Let $f:A\rightarrow\mathbb R$

<u>continuous</u> 
- $(\forall\epsilon>0)(\exists\delta>0)\ |x-x'|<\delta\implies|f(x)-f(x')|<\epsilon$
- $(x_n)\rightarrow c\implies f(x_n)\rightarrow f(c)$
- $\lim_{x\rightarrow c}f(x)=f(c)$

<u>uniformly continuous</u> $(\forall\epsilon>0)(\exists\delta>0)(\forall x,y\in A), |x-y|<\delta\Rightarrow|f(x)-f(y)|<\epsilon$

<u>monotone</u> $(\forall x<y)\ f(x)\ge f(y)\lor f(x)\le f(y)$
<u>composition</u> for $f,g$ continuous, $g\circ f$ is continuous
<u>compactness</u> $A$ compact then $f(A)$ compact.
<u>connectedness</u> $A$ connected then $f(A)$ connected.

<u>Extreme Value Theorem</u> $(\exists x_0,x_1)(\forall x)\ f(x_0)\le f(x)\le f(x_1)$

<u>Intermediate Value Theorem</u> $(\forall L|f(a)<L<f(b)\lor f(a)>L>f(b))$, $(\exists c\in(a,b))\ f(c)=L$.

# Derivative
<u>Differentiability</u> Let $f:A\rightarrow\mathbb R$. For $c\in A$, the derivative of $f$ at $c$ is $g^\prime(c)=\lim_{x\rightarrow c}\frac{g(x)-g(c)}{x-c}$. If this exists, then $f$ is differentiable at $c$. If $g^\prime$ exists for all $c\in A$, then $f$ is differentiable on $A$.

If $f$ is differentiable at $c$, then it is continuous at $c$.

<u>Sequential Criterion</u> $f$ differentiable at $a$ if and only if $(\forall(x_n)\subseteq A-\{a\})$, $x_n\rightarrow a$ implies $\frac{f(x_n)-f(a)}{x_n-a}$ converges

$f$ has a <u>relative extrema</u> at $c\in(a,b)$ if $\exists\delta>0$ where $V_\delta(c)\subseteq(a,b)$ implies $f(c)$ is an upper or lower bound for $f(V_\delta(c))$

If $f^\prime(c)$ exists and $c$ is a relative extrema, then $f^\prime(c)=0$

- $(f+g)^\prime(c)=f^\prime(c)+g^\prime(c)$
- $(kf)^\prime(c)=kf^\prime(c)$
- $(fg)^\prime(c)=f^\prime(c)g(c)+f(c)g^\prime(c)$
- $(f/g)^\prime(c)=\frac{g(c)f^\prime(c)-f(c)g^\prime(c)}{[g(c)]^2}$
- $(g\circ f)^\prime(c)=g^\prime(f(c))\cdot f^\prime(c)$

<u>Interior Extremum Theorem</u> Let $f$ be differentiable on $(a,b)$. If $f$ has max or min value at $c\in(a,b)$, then $f^\prime(c)=0$.

<u>Darboux Theorem</u> If $f$ differentiable on $[a,b]$ and $f^\prime(a)<\alpha<f^\prime(b)$, then there is $c\in(a,b)$ where $f^\prime(c)=a$.

<u>Rolle's Theorem</u> Let $f$ differentiable on $(a,b)$. If $f(a)=f(b)$, then there is a point $c\in(a,b)$ where $f^\prime(c)=0$.

<u>Mean Value Theorem</u> If $f:[a,b]\rightarrow\mathbb R$ is continuous on $[a,b]$ and differentiable on $(a,b)$, then there exists $c\in (a,b)$ such that $f^\prime(c)=\frac{f(b)-f(a)}{b-a}$

<u>Generalized Mean Value Theorem</u> If $f$ and $g$ are continuous, then
$$\frac{f'(c)}{g'(c)}=\frac{f(b)-f(a)}{g(b)-g(a)}$$
