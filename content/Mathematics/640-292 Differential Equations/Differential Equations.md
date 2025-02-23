---
title: Differential Equations
---

## First Order Linear Differential Equations

For a simple equation $y^\prime(x)=f(x)$, the solution can be computed by directly taking the integral $y(x)=y(x_0)+\int^x_{x_0}f(z)\text dz$.

A **separable equation** is of the form $f(y)y^\prime=g(x)$, where having some antiderivative $F$
​￼# Differential Equations
 and $G$ gives the rearrangement $F(y(x))^\prime=g(x)$, solving $F(y(x))=G(x)+C$

Given a continuous function $\mathbf v:U\subset\mathbb R^n\rightarrow\mathbb R^n$, a general **first order autonomous system** is $\mathbf x(t)^\prime=\mathbf v(\mathbf x(t))$, while a **first order non-autonomous** system is $\mathbf x(t)^\prime=\mathbf v(t,\mathbf x(t))$. Additionally, solutions of this equation $\mathbf x(t)$ are called the **integral curves** of the vector field $\mathbf v(\mathbf x)$

In general, a first order linear equation is of the form $x^\prime(t)=p(t)x(t)+q(t)$. After finding the antiderivative $P^\prime(t)=p(t)$, a general solution can be found
$$
e^{-P(t)}x^\prime(t)-e^{-P(t)}p(t)x(t)=\frac{\text d}{\text dt}e^{-P(t)}x(t)=q(t)e^{-P(t)}
$$
$$
(x(t)e^{-P(t)})-(x(t_0)e^{-P(t_0)})=\int^t_{t_0}e^{-P(s)}q(s)\text ds
$$
$$
x(t)=e^{P(t)-P(t_0)}x(t_0)+\int^t_{t_0}e^{P(t)-P(s)}q(s)\text ds
$$
$$
x(t)=e^{\int^t_{t_0}p(s)\text ds}x(t_0)+\int^t_{t_0}e^{\int^t_sp(r)\text dr}q(s)\text ds
$$

Furthermore, so long as $p$ and $q$ are continuous over the bound $(a,b)$, the above solution is unique given a fixed $x(t_0)$

### Bernoulli Equations

An equation of the following form is a **Bernoulli equation**.
$$
x^\prime(t)=p(t)x(t)+q(t)x^n(t)
$$

By taking a substitution $y(t)=x^{1-n}(t)$, this can be solved with some computation.

### Logistic Equation

In order to model the growth of a population, we can use a **logistic equation** $x^\prime=r(x)x$, where $r(x)$ is a proportionality factor related to population.

### Ricatti Equations
An equation of the following from is a **Ricatti equation**
$$
x^\prime(t)=p(t)+q(t)x(t)+r(t)x^2(t)
$$
This equation cannot be explicitly solved, but given an existing solution $x_1(t)$, we can come up with a general solution of the form $x(t)=x_1(t)+u(t)$.
$$
(x_1+u)^\prime-p-q(x_1+u)-r(x_1+u)^2=0
$$
$$
=\cancel{[x_1^\prime-p-qx_1-rx_1^2]}+[u^\prime-(q+2rx_1)u-ru^2]
$$
$$
u^\prime=(q+2rx_1)u+ru^2
$$

This is a Bernoulli equation with $u$. Solving as such, we can find a solution for $x$. *A useful guess for $x_1$ is $ct^\alpha$*.

### Reduction of Order
For a second order equation, if it only depends on $t,x^\prime,x^{\prime\prime}$, then the substitution $y=x^\prime$ allows for a simple solution.

In the more case that it depends on $x$ instead of $t$, take the same definition of $y$. Then let $\mathbf x(t)=(x(t),y(t))$ and $\mathbf v(x,y)=(y,f(x,y))$. A solution would satisfy $\mathbf x^\prime(t)=\mathbf v(\mathbf x(t))$.

We let $y=x^\prime$ be a function of $x$. From the chain rule, we have
$$
x^{\prime\prime}=\frac{\text d}{\text dt}y=\frac{\text dy}{\text dx}\frac{\text dy}{\text dt}=y\frac{\text dy}{\text dx}=f(x,y)
$$

### Autonomous
**Maximal Interval** for $v(x)$ is one where monotone on $(a,b)$ and $v(a)=v(b)=0$

For $x^\prime(t)=v(x(t))$, **Barrow's Formula** gives
$$
t(x)=t_0+\int_{x_0}^x\frac{1}{v(z)}\text dz
$$
Taking the limit as $x$ goes to endpoints of $(a,b)$, if they are defined, then solution is not unique and will reach equilibrium point eventually.

If $v$ is **Lipschitz**, then any solution is unique and exists for all time on the maximum interval.

For a flow transform of some autonomous DE,
$$
\frac{\text d}{\text dx}\Psi_s(x)=\frac{v(\Psi_s(x))}{v(x)}
$$

### Non-Autonomous
Lipschitz continuity also implies uniqueness for non autonomous DEs

### Equilibrium
For $\mathbf v$, some $\mathbf x_0$ where $\mathbf v(\mathbf x_0)=\mathbf 0$ is an **equilibrium point**, and a solution $\mathbf x(t)=\mathbf x_0$ is a **steady state solution**.

### Flow Transformation
For a given IVP $x^\prime=px+q$, a solution $x(t)$ where $x(t_0)=x_0$ has a corresponding **flow transformation** $\Phi_{t_1,t_0}(x_0)=x(t_1)$. These can be composed, with
$$
\Phi_{t_2,t_1}(\Phi_{t_1,t_0}(x))=\Phi_{t_2,t_0}(x)
$$

By differentiating the flow transform with respect to $x$, we can get the **sensitivity function**, which tells us how much the solution will change as we vary the initial conditions. For a FOLDE, this would be
$$
\frac{\text d}{\text dx}\Phi_{t_1,t_0}(x)=e^{\int_{t_0}^tp(s)\text ds}
$$

This can be also defined for an autonomous system $\mathbf x^\prime=\mathbf v(\mathbf x(t))$.


## Linear Systems
A linear vector field is one that can be represented by a matrix $\mathbf v(\mathbf x)=A\mathbf x$.

A general solution can be represented as a **superposition** of linear independent solutions. Suppose we have $\{\mathbf v_1,\ldots,\mathbf v_n\}$ eigenvectors of $A$, then taking
$$M(t)=[e^{t\mu_1}\mathbf v_1,\ldots,e^{t\mu_n}\mathbf v_n]$$
A solution with the initial position $\mathbf x_0$ is then
$$\mathbf x(t)=M(t)M(0)^{-1}\mathbf x_0$$

Furthermore, we can define a flow on this solution
$$\Psi_{t,s}(\mathbf x)=M(t)M(s)^{-1}\mathbf x$$

For a complex solution $\mathbf x(t)=\Re(\mathbf x(t))+\Im(\mathbf x(t))i$, these are two unique solutions $\mathbf x_1=\Re(\mathbf x)$ and $\mathbf x_2=\Im(\mathbf x)$.

If all the eigenvalues are strictly negative, the solution will converge to $0$, otherwise it may go to infinity.

### Duhamel's Formula
$$
\mathbf x^\prime(t)=A\mathbf x(t)+\mathbf g(t)
$$
$$
\mathbf x(t)=e^{(t-t_0)A}\mathbf x_0+\int^t_{t_0}e^{(t-s)A}\mathbf g(s)\text ds
$$

### Stability
For equilibrium point $\mathbf x_*$ of vector field $\mathbf v$. It is **Lyapunov stable** if for every $\epsilon>0$, there is a $\delta>0$ where solutions $\mathbf x(t)$ with $\|\mathbf x(t_0)-\mathbf x_*\|<\delta$, there is a solution for all $t>t_0$ where $\|\mathbf x(t)-\mathbf x_*\|<\epsilon$.

An equilibrium point is **asymptotically stable** if there is a $\delta>0$ where all solutions $\mathbf x(t)$ with $\|\mathbf x(t_0)-\mathbf x_*\|<\delta$ have $\lim_{t\rightarrow\infty}\mathbf x(t)=\mathbf x_*$.

The key difference here is that Lyapunov stability allows for solutions to remain a fixed distance away from the equilibrium point, while asymptotically stable means it will reach the equilibrium point at the limit.

When the eigenvalues have strictly negative real parts, then the equilibrium is asymptotically stable