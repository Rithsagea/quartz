---
title: Differentiability
---

<u>Differentiability</u> Let $f:A\rightarrow\mathbb R$. For $c\in A$, the derivative of $f$ at $c$ is $g^\prime(c)=\lim_{x\rightarrow c}\frac{g(x)-g(c)}{x-c}$. If this exists, then $f$ is differentiable at $c$. If $g^\prime$ exists for all $c\in A$, then $f$ is differentiable on $A$.

If $f$ is differentiable at $c$, then it is continuous at $c$.

<u>Sequential Criterion</u> $f$ differentiable at $a$ if and only if $(\forall(x_n)\subseteq A-\{a\})$, $x_n\rightarrow a$ implies $\frac{f(x_n)-f(a)}{x_n-a}$ converges

$f$ has a <u>relative extrema</u> at $c\in(a,b)$ if $\exists\delta>0$ where $V_\delta(c)\subseteq(a,b)$ implies $f(c)$ is an upper or lower bound for $f(V_\delta(c))$

If $f^\prime(c)$ exists and $c$ is a relative extremum, then $f^\prime(c)=0$

$c$ is a <u>two-sided limit</u> if for every $\delta>0$, the set $A\cap(c-\delta,c)\ne\varnothing$ and $A\cap(c,c+\delta)\ne\varnothing$ 

- $(f+g)^\prime(c)=f^\prime(c)+g^\prime(c)$
- $(kf)^\prime(c)=kf^\prime(c)$
- $(fg)^\prime(c)=f^\prime(c)g(c)+f(c)g^\prime(c)$
- $(f/g)^\prime(c)=\frac{g(c)f^\prime(c)-f(c)g^\prime(c)}{[g(c)]^2}$
- $(g\circ f)^\prime(c)=g^\prime(f(c))\cdot f^\prime(c)$

<u>Interior Extremum Theorem</u> Let $f$ be differentiable on $(a,b)$. If $f$ has max or min value at $c\in(a,b)$, then $f^\prime(c)=0$.

<u>Darboux Theorem</u> If $f$ differentiable on $[a,b]$ and $f^\prime(a)<\alpha<f^\prime(b)$, then there is $c\in(a,b)$ where $f^\prime(c)=a$.

<u>Rolle's Theorem</u> Let $f$ differentiable on $(a,b)$. If $f(a)=f(b)$, then there is a point $c\in(a,b)$ where $f^\prime(c)=0$.

<u>Mean Value Theorem</u> If $f:[a,b]\rightarrow\mathbb R$ is continuous on $[a,b]$ and differentiable on $(a,b)$, then there exists $c\in (a,b)$ such that $f^\prime(c)=\frac{f(b)-f(a)}{b-a}$
