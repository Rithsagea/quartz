Source: [[10.1017 CBO9780511976667|Quantum Computation and Quantum Information]]

Let $N=2^n$ be a set of inputs to some function $f$. Out of these inputs, $M\le N$ inputs are solutions. We define $f(x)=1$ if $x$ is a solution, and $f(x)=0$ otherwise. Assume we have an <u>oracle</u> $O$ that applies this function

$$
\ket x\ket q\xrightarrow O\ket x\ket{q\oplus f(x)}
$$

If we take $\ket q=\ket-$, then $O\ket x\ket q=(-1)^{f(x)}\ket x\ket q$. Abstractly, we can say $O\ket x=(-1)^{f(x)}\ket x$.
Prepare the initial state into the $N$-fold superposition $\ket\psi=\frac1{N^{1/2}}\sum^{N-1}_{x=0}\ket x$. A <u>Grover iteration</u> is given by $G=H^{\otimes n}(2\ket0\bra0-I)H^{\otimes N}O=(2\ket\psi\bra\psi-I)O$

## Mean Inversion Operator
>[!info]
>Applying $(2\ket\psi\bra\psi-I)$ to $\sum_k\alpha_k\ket k$ produces $\sum_k[-\alpha_k+2\langle\alpha\rangle]\ket k$, where $\langle\alpha\rangle:=\sum_k\alpha_k/N$.

$$
(2\ket\psi\bra\psi-I)\sum_k\alpha_k\ket k
=\sum_k\frac{2\alpha_k}{N^{1/2}}\ket\psi-\alpha_k\ket k
=\sum_k(2\langle\alpha\rangle-\alpha_k)\ket k
$$

## Analysis
Let $|S|=M$ be the solutions to the search problem, and $T$ be non-solutions. Additionally, write the following states
$$
\ket\alpha:=\frac1{\sqrt{N-M}}\sum_{x\in S}\ket x\qquad
\ket\beta:=\frac1{\sqrt M}\sum_{x\in T}\ket x
$$

Here, we can view the oracle as a reflection $O(a\ket\alpha+b\ket\beta)=a\ket\alpha-b\ket\beta$ in the space spanned by $\ket\alpha$, $\ket\beta$. The superposition can be rewritten $\ket\psi=\sqrt{\frac{N-M}N}\ket\alpha+\sqrt{\frac MN}\ket\beta$, thus the mean inversion operator is a reflection about $\ket\psi$ in this space. Let $\ket\psi=\cos\frac\theta2\ket\alpha+\sin\frac\theta2\ket\beta$ where $\cos\frac\theta2=\sqrt{\frac{N-M}N}$. Thus $G\ket\psi=\cos\frac{3\theta}2\ket\alpha+\sin\frac{3\theta}2\ket\beta$, and in general $G^k\ket\psi=\cos\left(\frac{2k+1}2\theta\right)\ket\alpha+\sin\left(\frac{2k+1}2\theta\right)\ket\beta$.

![[Grover Iteration Rotation.png | center | 300]]

The angle between $\ket\psi$ and $\ket\beta$ is $\arccos\sqrt{M/N}$, while applying a Grover iteration rotates the state $\theta$ radians. Thus rotating by $R=\lfloor\frac{\arccos\sqrt{M/N}}{\theta}+\frac12\rfloor$ takes us within $\theta/2\le\pi/4$ of $\ket\beta$, so $R\le\lceil\pi/2\theta\rceil$. If $M\le N/2$, then $\frac\theta2\ge\sin\frac\theta2=\sqrt{\frac MN}$, giving a nice bound $R\le\left\lceil\frac\pi4\sqrt{\frac NM}\right\rceil$. If this is not the case, we are better of simply guessing randomly. <u>If we don't know which case is true ahead of time, there is a solution counting algorithm (TODO)</u>