Source: [[10.1017 CBO9780511976667|Quantum Computation and Quantum Information]]

Given some orthonormal basis $\ket0,\ldots,\ket{N-1}$, the <u>quantum Fourier transform</u> is given by
$$
U_F\ket j=\frac1{\sqrt N}\sum^{N-1}_{k=0}\exp(2\pi ijk/N)\ket k
$$

## Unitary
>[!info]
>The linear transformation given by $U_F$ is unitary

Let $j_1\ne j_2$, and consider $(U_F\ket{j_1})^\dagger U_F\ket{j_2}$. Writing out the product explicitly, we have (up to normalization)

$$
\left(\sum^{N-1}_{k=0}\exp(2\pi ij_1k/N)\ket k\right)^\dagger
\left(\sum^{N-1}_{k=0}\exp(2\pi ij_2k/N)\ket k\right)
=\sum^{N-1}_{k=0}\exp\left(\frac{2\pi i(j_2-j_1)}Nk\right)
=0
$$

We note that $\omega=\exp(2\pi i(j_2-j_1)/N)$ is an $N$th root of unity, so $(\omega-1)\sum_{k=0}^{N-1}\omega^k=\omega^N-1=0$. But $\omega\ne1$ so the summation must be $0$. Trivially $(U_F\ket j)^\dagger U_F\ket j=1$, so $U_F$ is unitary.

## Circuit Construction

Let $N=2^n$ with computational basis $\ket0,\ldots,\ket{2^n-1}$. Write the binary decomposition $j=j_1j_2\cdots j_n$ and $0.j_lj_{l+1}\ldots j_m=j_l/2+j_{l+1}/4+\ldots+j_m/2^{m-l+1}$. Then we can decompose the QFT as
$$
\begin{aligned}
U_F\ket j
&=\frac1{2^{n/2}}\sum^{2^n-1}_{k=0}\exp(2\pi ijk/2^n)\ket k
=\frac1{2^{n/2}}\sum^1_{k_1=0}\cdots\sum^1_{k_n=0}
\exp\left(2\pi ij\sum_{l=1}^kk_l2^{-l}\right)\ket{k_1\ldots k_n}\\
&=\frac1{2^{n/2}}\sum^1_{k_1=0}\cdots\sum^1_{k_n=0}
\bigotimes^n_{l=1}\exp(2\pi ijk_l2^{-l})\ket{k_l}
=\frac1{2^{n/2}}\bigotimes^n_{l=1}\sum^1_{k_l=0}
\exp(2\pi ijk_l2^{-l})\ket{k_l}\\
&=\frac1{2^{n/2}}\bigotimes^n_{l=1}\ket0+\exp(2\pi ij2^{-l})\ket1\\
&=\frac{
\left(\ket 0+\exp(2\pi i0.j_n)\ket 1\right)
\left(\ket 0+\exp(2\pi i0.j_{n-1}j_n)\ket 1\right)
\cdots
\left(\ket 0+\exp(2\pi i0.j_1j_2\cdots j_n)\ket 1\right)
}{2^{n/2}}
\end{aligned}
$$

Define the phase rotation gate with $R_k=\ket0\bra0+\ket1\bra1\exp(2\pi i/2^k)$. Given some input state $\ket{j_1\ldots j_n}$, applying Hadamard takes us to the state $\frac1{2^{1/2}}(\ket 0+\exp(2\pi i0.j_1\ket 1)\ket{j_2\ldots j_n}$. Applying $CR_k$ from qubit $k\to1$ for $k\in[2,n]$, we obtain
$$
\frac1{2^{1/2}}
\bigg(\ket 0+\exp(2\pi i0.j_1j_2\ldots j_n)\ket1\bigg)\ket{j_2\ldots j_n}
$$

Successively performing this operation on $\ket{j_2}\ldots\ket{j_n}$ yields
$$
\frac1{2^{n/2}}
\bigg(\ket 0+\exp(2\pi i0.j_1j_2\ldots j_n\bigg)\ket1)
\bigg(\ket 0+\exp(2\pi i0.j_2\ldots j_n)\ket1\bigg)
\ldots
\bigg(\ket 0+\exp(2\pi i0.j_n)\ket1\bigg)
$$

Finally, applying appropriate swap gates finishes the implementation of $Q_F$.