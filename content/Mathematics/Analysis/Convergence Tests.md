Source: [[9780070542358|Principles of Mathematical Analysis]]

Let $\{a_n\}$ be a sequence. We call $s_n=\sum^n_{k=1}a_k$ the <u>partial sums</u> of the series $s=\sum^\infty_{n=1}a_n$. If $\{s_n\}$ converges to $s$, then the series <u>converges</u>.

## Cauchy Criterion
>[!info]
>$\sum a_n$ converges if and only if for every $\varepsilon>0$, there is an integer $N$ such that $|\sum^m_{k=n}a_k|\le\varepsilon$ if $m\ge n\ge N$.

A sequence converges iff it is Cauchy. This follows by definition of a Cauchy sequence.

## Comparison Test
>[!info]
>1. If $|a_n|\le c_n$ for $n\ge N_0$ where $N_0$ is a fixed integer, $\sum c_n$ converging implies $\sum a_n$ converges
>2. If $a_n\ge d_n\ge 0$ for $n\ge N_0$, $\sum d_n$ diverging implies $\sum a_n$ diverges.

(1) By [[#Cauchy Criterion]], for $\varepsilon>0$, there is $N\ge N_0$ where $m\ge n\ge N$ implies
$$
\left|\sum^m_{k=n}a_k\right|
\le\sum^m_{k=n}|a_k|
\le\sum^m_{k=n}c_k\le\varepsilon
$$

(2) This follows by contraposition

## Cauchy Condensation Test
>[!info]
>Suppose $a_n$ is monotone decreasing. Then $\sum a_n$ converges if and only if the following series converges.
>$$
>\sum^\infty_{k=0}2^ka_{2^k}=a_1+2a_2+4a_4+8a_8+\ldots
>$$

Define the following sequences, $s_n=a_1+a_2+\ldots+a_n$, $t_k=a_1+2a_2+\ldots+2^k_{a_{2^k}}$. We have the following cases

$$
\begin{aligned}
n<2^k&\qquad
s_n\le a_1+(a_2+a_3)+\ldots+(a_{2^k}+\ldots+a_{2^{k+1}-1})
\le a_1+2a_2+\ldots+2^ka_{2^k}=t_k\\
n>2^k&\qquad
s_n\ge a_1+a_2+(a_3+a_4)+\ldots+(a_{2^{k-1}+1}+\ldots+a_{2^k})
\ge\frac12a_1+a_2+\ldots+2^{-1}a_{2^k}=\frac12t_k
\end{aligned}
$$

Thus by [[#Comparison Test]] (with some reindexing), $\{t_k\}$ and $\{s_n\}$ are either both bounded or unbounded.

## Root Test
>[!info]
>Let $\sum a_n$ and $\alpha=\lim\sup_{n\to\infty}\sqrt[n]{|a_n|}$.
>1. if $\alpha<1$, $\sum a_n$ converges.
>2. if $\alpha>1$, $\sum a_n$ diverges
>3. if $\alpha=1$, the test gives no information

If $\alpha<1$, pick $\beta\in(\alpha,1)$ and integer $N$ such that $\sqrt[n]{|a_n|}<\beta$ for $n\ge N$. Then $|a_n|<\beta^n$, but $\sum\beta^n$ converges by geometric series and $\sum a_n$ converges by [[#Comparison Test]].

If $\alpha>1$ there is a sequence $\{n_k\}$ such that $\sqrt[n_k]{|a_{n_k}|}\to\alpha$, and $|a_n|>1$ for infinitely many values of $n$. Thus $\sum a_n$ diverges.

Note $\sum\frac1n$ diverges, while $\sum\frac1{n^2}$ converges. Both of these have $\alpha=1$.

## Ratio Test
>[!info]
>The series $\sum a_n$
>1. Converges if $\lim\sup_{n\to\infty}\left|\frac{a_{n+1}}{a_n}<1\right|$
>2. Diverges if $\left|\frac{a_{n+1}}{a_n}\right|\ge1$ for all $n\ge n_0$, where $n_0$ is some fixed integer.

(1) There is $\beta<1$ such that $|\frac{a_{n+1}}{a_n}|<\beta$ for $n\ge N$. Then $|a_{N+p}|<\beta^p|a_N|$, so $|a_n|<|a_N|\beta^{-N}\beta^n$. By [[#Comparison Test]] this converges.

(2) Similar bounding can be performed to show the sequence diverges.

