---
date: 2025-03-08
---

## Inner Products
Given a vector space $V$, an <u>inner product</u> is bilinear mapping $\Omega:V\times V\to\mathbb R$ with the following properties
- <u>symmetric</u> $\forall x,y\in V$, $\Omega(x,y)=\Omega(y,x)$
- <u>positive definite</u> $\forall x\in V\setminus\{0\}$, $\Omega(x,x)>0$, $\Omega(0,0)=0$

Given an inner product over a vector space $V$ with basis $B=\{b_1,\ldots,b_n\}$, we can write $x=\sum^n_{i=1}\psi_ib_i$ and $y=\sum^n_{i=1}\lambda_i b_i$, so $\langle x,y\rangle=\sum^n_{i=1}\sum^n_{j=1}\psi_i\langle b_i,b_j\rangle\lambda_j$. Taking $\hat x=(\psi_1,\ldots,\psi_n)$, $\hat y=(\lambda_1,\ldots,\lambda_n)$, and $A_{ij}=\langle b_i,b_j\rangle$, $\langle x,y\rangle=\hat x^TA\hat y$

## Orthogonal Projection
Given a lower dimensional subspace $U\subseteq\mathbb R^n$ with $\dim(U)=m\ge 1$ and basis $B=[b_1,\ldots,b_m]$, we can project $x\in\mathbb R^n$ to $U$ with $\pi_U(x)$, with coordinates $\lambda=[\lambda_1,\ldots,\lambda_m]$ for $B$. That is, $\pi_U(x)=B\lambda$. We require $\langle b_i,x-\pi_U(x)\rangle=0$, so $B^T(x-B\lambda)=0$, or $\lambda=(B^TB)^{-1}B^Tx$. Explicitly, the projection is given

$$
\pi_U(x)=B(B^TB)^{-1}B^Tx
$$

## Singular Value Decomposition
For all $A\in M_{m\times n}$ with, we can write $A=U\Sigma V^T$, where $U\in M_{m\times m}$, $V\in M_{n\times n}$ are bases and $\Sigma\in M_{m\times n}$. The diagonals of $\Sigma$ are the $r=\mathrm{rank}(A)$ singular values, $\sigma_1,\ldots,\sigma_r$.

Using the <u>spectral theorem</u>, we know any symmetric matrix has an orthonormal basis of eigenvectors. Then we can compute basis for $U$ and $V$ as follows

$$
AA^T
=U\Sigma V^TV\Sigma^TU^T
=U\pmatrix{\sigma^2_1&0&0\\0&\ddots&0\\0&0&\sigma_n^2}U^T
$$

$$
A^TA
=V\Sigma^TU^TU\Sigma V^T
=V\pmatrix{\sigma^2_1&0&0\\0&\ddots&0\\0&0&\sigma_m^2}V^T
$$

To actually compute these values, we can find the right singular vectors by diagonalizing $A^TA$ and computing eigenvectors / eigenvalues (the square of the singular values). Given $V=[v_1,\ldots,v_n]$, with with singular values $\sigma_1\ldots,\sigma_n$, we can compute the left singular vectors with $u_i=\frac1{\sigma_i}Av_i$, and $U=(u_1,\ldots,u_m)$.

Alternatively, given $U$ and $V$, we can compute singular values directly with $U^TAV=\Sigma$.

## Differentiation
Given a function $f:\mathbb R^n\to\mathbb R$, $x\mapsto f(x)$, the partial is given with $\frac{\partial f}{\partial x_i}$, and gradient $\nabla_x f=\left[\frac{\partial f}{\partial x_1},\ldots,\frac{\partial f}{\partial x_n}\right]$. This can be generalized to a mulitvariate function $f:\mathbb R^n\to\mathbb R^m$, where $f(x)=\pmatrix{f_1(x)\\\vdots\\f_m(x)}$ and $f_i:\mathbb R^n\to\mathbb R$ with the Jacobian

$$
J_f=\frac{df}{dx}=
\pmatrix{
\frac{\partial f}{\partial x_1}&
\cdots&
\frac{\partial f}{\partial x_n}}
=
\pmatrix{
\frac{\partial f_1}{\partial x_1} &
\cdots &
\frac{\partial f_1}{\partial x_n} \\
\vdots & & \vdots \\
\frac{\partial f_m}{\partial x_1} &
\cdots &
\frac{\partial f_m}{\partial x_n}
}
$$

## Neural Networks
The $i$th layer of a neural network is represented with a function, where $x$ is the previous layer's inputs, $A$ is the weight matrix, and $b$ is the bias vector.
$$
f_i(x_{i-1})=\sigma(A_{i-1}x_{i-1}+b_{i-1})\qquad
f_0=x
$$

Given $K$ layers, and an expected output $y$, define a loss function
$$
L(\theta)=\|y-f_K(\theta,x)\|^2\qquad
\theta=(A_0,b_0,\ldots,A_{K-1},b_{K-1})
$$