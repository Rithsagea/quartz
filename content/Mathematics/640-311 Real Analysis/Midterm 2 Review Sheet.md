---
title: Midterm 2 Review Sheet
---

# Sequences
A sequence $(a_n)$ converges to $a$, or $(a_n)\rightarrow a$ if
- for all $\epsilon>0$, there is $N$ such that $n\ge N\Rightarrow |a_n-a|<\epsilon$
- the sequence is Cauchy, i.e. for all $\epsilon>0$ there is $N$ such that $n,m\ge N\Rightarrow |a_n-a_m|<\epsilon$

A bounded monotone sequence is convergent


# Topology DLC+
A set $K\subseteq\mathbb R$ is <u>compact</u> if
- every sequence in $K$ has a convergent subsequence with a limit contained in $K$
- $K$ is a subset of $\mathbb R$, and is also closed and bounded
- every open cover of $K$ has a finite subcover

A set $P\subseteq\mathbb R$ is <u>perfect</u> if it is closed and has no isolated points. These sets are always uncountable.

Two sets $A,B$ are <u>separated</u> if $\overline A\cap B$ and $A\cap\overline B$ are both empty. A set $E$ is <u>disconnected</u> if can be written as a union of two separated sets. A set that is not disconnected is <u>connected</u>

A set $E\subseteq \mathbb R$ is connected if and only if for all $a<c<b$ with $a,b\in E$, then $c\in E$.

# Examples
Dirichlet's nowhere continuous function, $g(x)=\left\{\array{1&\text{if }x\in\mathbb Q\\0&\text{if }x\not\in\mathbb Q}\right.$

Thomae's function $t(x)=\left\{\array{1&\text{if }x=0\\1/n&\text{if }x=m/n\in\mathbb Q\setminus\{0\}\\0&\text{if }x\not\in\mathbb Q}\right.$

Altered Sine function $f(x)=\left\{\array{x\sin(1/x)&\text{if }x\ne 0\\0&\text{if }x=0}\right .$

# Functional Limits
<u>Functional Limit</u> For $f:A\rightarrow\mathbb R$, $\lim_{x\rightarrow c}f(x)=L$ implies that
$$(\forall\epsilon>0)(\exists\delta>0)x\in V_\delta(c)\Rightarrow f(x)\in V_\epsilon(L)$$

<u>Sequential Criterion</u> For a function $f:A\rightarrow\mathbb R$ and a limit point $c$, $\lim_{x\rightarrow c}f(x)=L$ is equivalent to the following statement: for all $(x_n)\subseteq A$ where $(x_n)\rightarrow c$ and $x_n\ne c$, $f(x_n)\rightarrow L$.

<u>Functional Algebraic Limit Theorem</u> For functions $f,g$ defined on $A$, let $\lim_{x\rightarrow c}f(x)=L$ and $\lim_{x\rightarrow c}g(x)=M$.
1. $\lim_{x\rightarrow c}kf(x)=kL$ for all $k\in\mathbb R$
2. $\lim_{x\rightarrow c}[f(x)+g(x)]=L+M$
3. $\lim_{x\rightarrow c}[f(x)g(x)]=LM$
4. $\lim_{x\rightarrow c}f(x)/g(x)=L/M$ with $M\ne 0$

<u>Divergence Criterion</u> The limit $\lim_{x\rightarrow c}f(x)$ does not exist if there are two sequences $(x_n)$ and $(y_n)$ such that $\lim x_n=\lim y_n$ and $\lim f(x_n)\ne \lim f(y_n)$

A function is <u>monotone</u> increasing if $f(x)\ge f(y)$ or decreasing $f(x)\le f(y)$ for all $x<y$

# Continuity
A function $f:A\rightarrow\mathbb R$ is <u>continuous</u> at $c\in A$ if
$$(\forall\epsilon>0)(\exists \delta>0)x\in V_\delta(c)\Rightarrow f(xx)\in V_\epsilon(c)$$

The function is continuous on $A$ if it is continuous at every point.

<u>Discontinuity Criterion</u> If there is a sequence $(x_n)\rightarrow c$ where $f(x_n)$ does not converge to $f(c)$, then $f$ is not continuous at $c$.

<u>Algebraic Continuity Theorem</u> Let $f:A\rightarrow\mathbb R$ and $g:A\rightarrow\mathbb R$ be continuous at a point $c\in A$.
1. $kf(x)$ is continuous at c for all $k\in\mathbb R$
2. $f(x)+g(x)$ is continuous at $c$
3. $f(x)g(x)$ is continuous at $c$
4. $f(x)/g(x)$ is continuous at $c$, given the quotient is defined

<u>Composition of continuous functions</u> for $f:A\rightarrow\mathbb R$ and $g:B\rightarrow\mathbb R$, assume $f(A)\subseteq B$ so that $g\circ f$ is defined. If $f$ is continuous at $c$ and $g$ continuous at $f(c)$, then $g\circ f$ is continuous at $c$.

<u>Preservation of Compactness</u> for a continuous function $f$, if $A$ is compact, then $f(A)$ is also compact.

<u>Extreme Value Theorem</u> let $f$ be continuous on a compact set $K$. Then there exists $x_0,x_1\in K$ such that $f(x_0)\le f(x)\le f(x_1)$ for all $x\in K$

## Uniform Continuity
A function $f:A\rightarrow\mathbb R$ is <u>uniformly continuous</u> if we have
$$(\forall\epsilon>0)(\exists\delta>0)(\forall x,y\in A), |x-y<|\delta\Rightarrow|f(x)-f(y)|<\epsilon$$

The sequential criterion for nonuniform continuity is similar to previous criterion.

A function that is continuous on a compact set $K$ is uniformly continuous on $K$

# Intermediate Value Theorem
> [!info] oops
> i don't remember if this is actually going to be on the midterm, but still worth studying.

<u>Intermediate Value Theorem</u> For $f:[a,b]\rightarrow\mathbb R$ continuous, if $L$ satisfies $f(a)<L<f(b)$ or $f(a)>L>f(b)$, there is $c\in(a,b)$ such that $f(c)=L$.

<u>Preservation of Connected Sets</u> for $f:G\rightarrow\mathbb R$ continuous, if $E\subseteq G$ is continuous, then $f(E)$ is connected.