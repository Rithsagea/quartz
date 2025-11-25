Source: [[9780070542358|Principles of Mathematical Analysis]]

Let $f:[a,b]\to\mathbb R$. The <u>derivative</u> of $f$ at $x$ (if it exists) is given $f'(x)=\lim\limits_{t\to x}\frac{f(t)-f(x)}{t-x}$. If $f'$ is defined at $x$, it is <u>differentiable</u> at $x$. Furthermore if $f'$ is defined everywhere on $E\subset[a,b]$, $f$ is differentiable on $E$.

# Continuity
>[!info]
>Let $f$ be defined on $[a,b]$ if $f$ is differentiable at $x\in[a,b]$, then $f$ is continuous at $x$.

As $t\to x$, we have $f(t)-f(x)=\frac{f(t)-f(x)}{t-x}\cdot(t-x)\to f'(x)\cdot 0=0$.

# Arithmetic
>[!info]
>Suppose $f,g:[a,b]\to\mathbb R$ and are differentiable at $x\in[a,b]$. Then $f+g$, $fg$, and $f/g$ are differentiable at $x$ with
>1. $(f+g)'(x)=f'(x)+g'(x)$
>2. $(fg)'(x)=f'(x)g(x)+f(x)g'(x)$
>3. $(\frac fg)'(x)=\frac{g(x)f'(x)-g'(x)f(x)}{g^2(x)}$ (provided $g(x)\ne0$)

(1) Follows by sum of limits.

(2) Let $h=fg$. Then $h(t)-h(x)=f(t)[g(t)-g(x)]+g(x)[f(t)-f(x)]$. Divide by $t-x$ and note $f(t)\to f(x)$ as $t\to x$. Successive application of algebraic limit theorem gives the limit.

(3) Letting $h=f/g$, then $\frac{h(t)-h(x)}{t-x}=\frac1{g(t)g(x)}\left[g(x)\frac{f(t)-f(x)}{t-x}-f(x)\frac{g(t)-g(x)}{t-x}\right]$. As $t\to x$ the desired limit follows.

# Chain Rule
>[!info]
>Let $f$ be continuous on $[a,b]$ and $f'(x)$ defined for $x\in[a,b]$, while $g$ is defined on an interval $I$ containing the range of $f$ and $g$ is differentiable at $f(x)$. If $h(t)=g(f(t))$ for $t\in[a,b]$, then $h$ is differentiable at $x$ and $h'(x)=g'(f(x))f'(x)$.

Let $y=f(x)$, and take $t\in[a,b]$, $s=f(t)\in I$ and $u(t)\to 0$ as $t\to x$, $v(s)\to 0$ as $s\to y$ such that the following holds.
$$
\begin{aligned}
f(t)-f(x)=(t-x)[f'(x)+u(t)]\\
g(s)-g(y)=(s-y)[g'(y)+v(s)]
\end{aligned}
$$

Applying these substitutions and assuming $t\ne x$, we have
$$
\begin{aligned}
h(t)-h(x)&=g(f(t))-g(f(x))\\
&=[f(t)-f(x)]\cdot[g'(y)+v(s)]\\
&=(t-x)\cdot[f'(x)+u(t)]\cdot[g'(y)+v(s)]\\
\frac{h(t)-h(x)}{t-x}&=[g'(y)+v(s)]\cdot[f'(x)+u(t)]
\end{aligned}
$$

Note $t\to x$ gives $s\to y$, and this quantity converges to $g'(f(x))f'(x)$.