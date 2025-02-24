---
title: Probability
date: 2024-04-27
---

## Combinatorics
For $n$ objects, there are $n!$ **permutations**, or ordered arrangements. If we want to pick $r$ objects from this, then there are $\binom{n}{r}$ **combinations**.

### Multinomial Coefficients
Taking $n$ distinct items, and dividing them into groups of size $n_1,n_2,\ldots,n_r$ where $\sum n_i=n$, the total number of combinations can be found with a **multinomial coefficient**
$$
\binom{n}{n_1,n_2,\ldots,n_r}=\frac{n!}{n_1!n_2!\ldots n_r!}
$$

## Axioms of Probability
For a given experiment the set of possible outcomes is the **sample space**, $S$.

Subsets of the sample space can be combined with **union** and **intersection**, which are operators that obey commutativity, associativity, and distributivity. Furthermore, the **complement** of a subset $A$ denoted as $A^C$ is the set of all events in $S$ but not in $A$.

### DeMorgan's Laws
Taking the complement will invert the inside of a parenthesis from union to intersect or vice versa.
$$
\left(\bigcup^n_{i=1} E_i\right)^C=\bigcap^n_{i=1}E^C_i
\quad,\quad
\left(\bigcap^n_{i=1} E_i\right)^C=\bigcup^n_{i=1}E^C_i
$$

### Axioms of Probability
Taking an event $E\subset S$, we define $P(E)$ to be the ratio of successes to $n$ total occurrences, when we take the limit $n\rightarrow\infty$. This can also be called the **probability** Then we have the following axioms.
1. $0\le P(E)\le 1$
2. $P(S)=1$
3. $P(\bigcup^\infty_{i=1}E_i)=\sum^\infty_{i=1}P(E_i)$

Note that $P(\varnothing)=0$, $P(E^C)=1-P(E)$.

### Inclusion Exclusion Principle
Note that $P(A\cup B)=P(A)+P(B)-(A\cap B)$. Generalizing this to $n$ different events, we have
$$
P(\bigcup ^n_{i=1})=\sum^n_{i=1}P(A_i)-\sum\sum_{i<j}P(A_iA_j)+\sum\sum\sum_{i<j<k}P(A_iA_jA_k)
$$
$$
+\ldots+(-1)^{n+1}P(A_1\ldots A_n)
$$

## Conditional Probability

The probability that $E$ occurs given $F$ occurs is denoted $P(E|F)$. If $P(F)>0$, then $P(E|F)=\frac{P(E\cap F)}{P(F)}$

For a series of events, $E_1\ldots E_N$, we have
$$
P(E_1E_2E_3\ldots E_n)=P(E_1)P(E_2|E_1)P(E_3|E_1E_2)\ldots P(E_n|E_1\ldots E_{n-1})
$$

**Bayes formula** states that $E=EF\cup EF^C$

## Discrete Random Variables
Let $X$ be some random variable, $F(x)=P\{X\le x\}$ is the **cumulative distribution function** of $X$. If $X$ is discrete, then $p(a)=P\{X=a\}$ is the **probability mass function**. The expectation is effectively the mean of the random variable.
$$
\mathbb E[X]=\sum_{x:p(x)>0}xp(x)
$$
*The expectation is a linear function*

The **variance** of $X$ is defined from the expectation
$$
Var(X)=\mathbb E[(X-\mu)^2]=\mathbb E[X^2]-\mathbb E[X]^2
$$
$$
Var(aX+b)=a^2Var(X)
$$

A **Bernoulli random variable** is a binary variable with value $1$ when success of probability $p$, and $0$ when failure with probability $1-p$.

A **binomial random variable** with parameters $(n,p)$ represents $n$ trials each with probability $p$.
$$
p(i)=\binom{n}{i}p^i(1-p)^{n-i}
$$
$$
\mathbb E[X]=np\quad Var(X)=np(1-p)
$$

A **Poisson random variable** with parameters $(\lambda)$ is an approximation of a binomial with $\lambda=np$ for big $n$ and small $p$.
$$
p(i)=e^{-\lambda}\frac{\lambda^i}{i!}
$$
$$
\mathbb E[X]=\lambda\quad Var(X)=\lambda
$$

A **geometric random variable** is the number of trials needed for a success, given the probability of success $p$.
$$
P\{X=n\}=(1-p)^{n-1}p
$$
$$
\mathbb E[X]=\frac{1}{p}\quad Var(X)=\frac{1-p}{p^2}
$$

A **negative binomial variable** with parameters $(r,p)$ is the number of trials needed for $r$ successes with chance of success $p$. A binomial variable is a negative binomial with $(1,p)$. Equivalent to chance of $r-1$ successes, followed by a success on the $n$th trial.
$$
P\{X=n\}=\binom{n-1}{r-1}p^r(1-p)^{n-r}
$$
$$
\mathbb E[X]=\frac{r}{p}\quad Var(X)=\frac{r(1-p)}{p^2}
$$

A **hypergeometric random variable** with parameters $(n,N,m)$ is expected number white balls, when $n$ are drawn from a selection of $N$ balls with $m$ white ones.
$$
P\{X=i\}=\dfrac{\binom{m}{i}\binom{N-m}{n-i}}{\binom{N}{n}}
$$

## Continuous Random Variables

For a continuous random variable $X$ defined on the real line, the probability density function and distribution function are the following
$$
P\{X\in B\}=\int_B f(x)\text dx\quad P\{a\le X\le b\}=\int^b_af(x)\text dx
$$
$$
F(a)=\int^a_{-\infty}f(x)\text dx
$$

Furthermore, the expectation and is defined to be
$$
\mathbb E[X]=\int_{-\infty}^\infty xf(x)\text dx\quad \mathbb E[g(X)]=\int^\infty_{-\infty} g(x)f(x)\text dx
$$

Note the same rules for expectation and variance hold in the continuous case similar to discrete.

A variable is **uniformly distributed** if over $(\alpha,\beta)$, $f(x)=(\beta-\alpha)^{-1}$

A variable is **normally distributed** with parameters $(\mu,\sigma^2)$ if the density of $X$ is
$$
f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-(x-\mu)^2/2\sigma^2}
$$

Furthermore, $Z=(X-\mu)/\sigma$ is a **standard** normal variable.
$$
\mathbb E[X]=\mu\quad Var(X)=\sigma^2
$$

The cumulative distribution function will be denoted as
$$
\Phi(x)=\frac{1}{\sqrt{2\pi}}\int^x_{-\infty}e^{-y^2/2}\text dy\quad\Phi(-x)=1-\Phi(x)
$$

A binomial random variable can be approximated with a normal of $\mu=np$, $\sigma=\sqrt{np(1-p)}$. Note that the endpoints must be shifted to account for **continuity correction**

$$
P\left\{a\le\frac{S_n-np}{\sqrt{np(1-p)}}\le b\right\}=\Phi(b)-\Phi(a)\quad P\{X=i\}=P\{i-\frac{1}{2}<X<i+\frac{1}{2}\}
$$

An **exponential random variable** with parameters $\lambda$ has density function $f(x)=\lambda e^{-\lambda x}$ for nonnegative $x$.
$$
\mathbb E[X]=\frac{1}{\lambda}\quad Var(X)=\frac{1}{\lambda^2}
$$

This type of variable represents the amount of time before an event occurs, and is uniquely **memoryless**, (past does not affect future)

For a continuous RV $X$ with $F$ and $f$, the **hazard rate** is
$$
\lambda(t)=\frac{f(t)}{1-F(t)}
$$

We can recover the distribution function if we integrate from $0$ to $t$

The **gamma function** is a generalization of factorial to the reals, defined
$$
\Gamma(\alpha)=\int^\infty_0e^{-y}y^{\alpha-1}\text dy\quad\Gamma(n)=(n-1)!
$$

A **gamma distribution** with parameters $(a,\lambda)$ is defined
$$
f(x)=\frac{\lambda e^{-\lambda x}(\lambda x)^{\alpha-1}}{\Gamma(\alpha)}
$$

This represents the amount of time needed for $\alpha$ events to occur.

## Jointly Distributed Random Variables

The **joint cumulative distribution function** of $X$ and $Y$ is $F(a,b)=P\{X\le a,Y\le b\}$. The **joint probability mass function** is $p(x,y)=P(X=x,Y=y)$. In this context, the **marginal probability mass functions** are $p_X$ and $p_Y$

Independence for joint distributions occur when the following conditions are true
$$
P\{X\in A,Y\in B\}=P\{X\in A\}P\{Y\in B\}
$$
$$
F(a,b)=F_X(a)F_Y(b)\quad p(x,y)=p_X(x)p_Y(y)
$$

The **convolution** of $X$ and $Y$ is $F_{X+Y}=\int^\infty_{-\infty}F_X(a-y)f_Y(y)\text dy$. Furthermore, note that $f_{X+Y}(a)=\int^\infty_{-\infty}f_X(a-y)f_Y(y)\text dy$

For $X\sim\Gamma(s,\lambda)$, $Y\sim\Gamma(t,\lambda)$, $X+Y\sim\Gamma(s+t,\lambda)$. A gamma distribution with $(\lambda=1/2,\alpha=n/2)$ is a **chi-square** distribution with $n$ degrees of freedom.

A sum of normal variables $X_1,\ldots,X_n$ then $\sum^n_{i=1}=X_i$ is normally distributed with parameters $\sum^n_{i=1}\mu_i$ and $\sum^n_{i=1}\sigma_i^2$.

The sum of two Poisson random variables is also Poisson with parameter $\lambda_1+\lambda_2$, and binomial random variables sum to a binomial with parameters $(n+m,p)$.

If two variables are independent, then $f(x,y)=f_X(x)f_Y(y)$

Conditional probabilities behave similarly, where 
$$
p_{X|Y}(x|y)=\frac{p(x,y)}{p_Y(y)}\quad F_{X|Y}(x|y)=P\{X\le x|Y=y\}
$$
$$
f_{X|Y}(x|y)=\frac{f(x,y)}{f_Y(y)}\quad F_{X|Y}(a|y)=\int^a_{-\infty}f_{X|Y}(x|y)\text dx
$$

### Joint Probability Distribution Functions

Take $X_1$ and $X_2$ as jointly continuous random variables, with density function $f_{X_1,X_2}$. Let $Y_1=g_1(X_1,X_2)$, $Y_2=g_2(X_1,X_2)$. Note that the Jacobian is defined
$$
J(x_1,x_2)=\left|\matrix{\frac{\partial g_1}{\partial x_1}&\frac{\partial g_1}{\partial x_2}\\\frac{\partial g_2}{\partial x_1}&\frac{\partial g_2}{\partial x_2}}\right|
$$

Then we can come up with a density function for this change of variables
$$
f_{Y_1,Y_2}(y_1,y_2)=f_{X_1,X_2}(x_1,x_2)\det|J(x_1,x_2)|^{-1}
$$

## Expectations
$$
\mathbb E[g(X,Y)]=\sum_y\sum_xg(x,y)p(x,y)
$$
Note that $\mathbb E[X+Y]=\mathbb E[X]+\mathbb E[Y]$

If $X$ and $Y$ are independent, then
$$
\mathbb E[g(X)h(Y)]=\mathbb E[g(X)]\mathbb E[h(Y)]
$$

### Covariance
$$
Cov(X,Y)=\mathbb E[XY]-\mathbb E[X]\mathbb E[Y]
$$
$$
Cov(X,X)=Var(X)
$$

**Correlation** is defined
$$
\rho(X,Y)=\frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}
$$

## Limit Theorems
**Markov's Inequality** 
$$
P\{X\ge a\}\le\frac{\mathbb E[X]}{a}
$$
**Chebyshev's Inequality**
$$
P\{|X-\mu|\ge k\}\le\frac{\mathbb E[(X-\mu)^2]}{k^2}=\frac{\sigma^2}{k^2}
$$