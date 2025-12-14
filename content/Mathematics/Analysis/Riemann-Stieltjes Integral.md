Source: [[9780070542358|Principles of Mathematical Analysis]]

# Riemann Integral
Let $f$ be a bounded real function defined on $[a,b]$. A <u>partition</u> $P$ of $A$ is a finite set of points
$$
a=x_0\le x_1\le\cdots\le x_{n-1}\le x_n=b
$$

Write $\Delta x_i=x_i-x_{i-1}$. The upper and lower <u>Riemann sums</u> are given by
$$
\begin{aligned}
U(P,f)=\sum^n_{i=1}M_i\Delta x_i\qquad&M_i=\sup f(x)&(x_{i-1}\le x\le x_i)\\
L(P,f)=\sum^n_{i=1}m_i\Delta x_i\qquad&m_i=\inf f(x)&(x_{i-1}\le x\le x_i)
\end{aligned}
$$

The upper and lower <u>Riemann integrals</u> are the extrema of these values
$$
\overline{\int^b_a}f\,\mathrm dx=\inf U(P,f)\qquad
\underline{\int^b_a}f\,\mathrm dx=\sup L(P,f)
$$

When these integrals are equal, $f$ is <u>Riemann integrable</u> on $[a,b]$, and $f\in\mathscr R$. The common value of these integrals is written as

$$
\int^b_af\,\mathrm dx
$$

# Riemann-Stieltjes Integral
Let $\alpha$ be monotonically increasing on $[a,b]$. Given a partition $P$ of $[a,b]$, write $\Delta\alpha_i=\alpha(x_i)-\alpha(x_{i-1})$. We define the analogous sums and integrals with the same $M_i$ and $m_i$ from before.

$$
\begin{aligned}
&U(P,f,\alpha)=\sum^n_{i=1}M_i\Delta\alpha_i
&\overline{\int^b_a}f\,\mathrm d\alpha=\inf U(P,f,\alpha)
\\
&L(P,f,\alpha)=\sum^n_{i=1}m_i\Delta\alpha_i
&\underline{\int^b_a}f\,\mathrm d\alpha=\sup L(P,f,\alpha)
\end{aligned}
$$

Once again, when these are equal, $f$ is integrable with respect to $\alpha$, and $f\in\mathscr R(\alpha)$. Note that setting $\alpha(x)=x$ recovers the original Riemann integral. We denote the common value of this integral as
$$
\int^b_a f\,\mathrm d\alpha
$$