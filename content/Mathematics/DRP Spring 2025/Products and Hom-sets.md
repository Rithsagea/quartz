---
title: Products and Hom-sets
date: 2025-02-27
---

>[!info] Product
>Given a category $\mathscr C$ and collection of objects $(X_i)_{i\in I}\in\mathscr C$ the product is an object $X:=\prod_{i\in I}X_i$ with morphisms $\pi_i:X\to X_i$ such that for all $Y\in\mathscr C$ and collection of morphisms $f_i:Y\to X_i$, there exists a unique morphism $f$ such that the following diagram commutes
>
>```tikz
>\usepackage{tikz-cd}
>\begin{document}
>\begin{tikzcd}
>& X \dar["\pi_i"]
>\\ Y \rar["f_i", swap] \urar["f", dashed]
>& X_i
>\end{tikzcd}
>\end{document}
>```

>[!info] Coproduct
>Given a category $\mathscr C$ and collection of objects $(X_j)_{j\in J}\in\mathscr C$ the coproduct is an object $X:=\coprod_{j\in J}X_j$ with morphisms $\iota_j$ such that for all $Y\in\mathscr C$ and colection of morphisms $f_j:X\to Y$, there exists a unique morphism $f$ such that $f_j=\iota_j\circ f$ and the following diagram commutes
>
>```tikz
>\usepackage{tikz-cd}
>\begin{document}
>\begin{tikzcd}
>X \drar[dashed, "f"]
>\\ X_j \uar["\iota_j"] \rar["f_j", swap]
>& Y
>\end{tikzcd}
>\end{document}
>```

>[!info] Hom-functor
>Let $\mathscr C$ be a category and $a\in\mathscr C$. Define the <u>covariant hom-functor</u> $\hom(a,-):C\to\mathbf{Set}$ which sends $b\in\mathscr C$ to $\hom(a,b)$ and $k:b\to b'$ to $k_*:\hom(a,b)\to\hom(a,b')$, $f\mapsto k\circ f$.
>
>Letting $b\in\mathscr C$, the <u>contravariant hom-functor</u> $\hom_{\mathscr C}(-,b):C^{op}\to\mathbf{Set}$ sends $a\in\mathscr C$ to $\hom(a,b)$ and each arrow $g:a\to a'$ to the function $g^*:\hom(a',b)\to\hom(a,b)$, $f\mapsto f\circ g$


>[!example] Show duality of product and coproduct in homset
>Let $\mathscr C$ be a category. Denote $C$ as the coproduct of $\mathscr C$ and $P$ the product of $\mathscr C$. Show that the following hom-functors are isomorphic
>$$
>\hom(\coprod_{j\in J}A_j,-)\cong\prod_{j\in J}\hom(A_j,-)
>$$
>$$
>\hom(-,\prod_{i\in I}B_i)\cong\prod_{i\in I}\hom(-,B_i)
>$$

We will prove the equivalence by showing there is a natural isomorphism. For convenience, denote $C:=\coprod_{j\in J}A_j$ and $P:=\prod_{i\in I}B_i$.

(1) Let $k:X\to Y$ be an arrow in $\mathscr C$. For the coproduct $C$, we have inclusion maps $\iota_j:X_j\to C$. Given a product $\prod_{j\in J}\hom(A_j,X)$, we have morphisms $\pi_j:\prod_{j\in J}\hom(A_j,X)\to \hom(A_j,X)$. For all $f\in\hom(C,X)$, we can generate a collection of arrows $f_j=\iota_j\circ f$. By the universal property of product, there exists unique $\eta_X$ such that $f_j=\eta_X\circ\pi_j$. We construct $\eta_Y$ similarly. Taking the product $\hom(A_j,k)_{j\in J}$, we have the following commutative diagram.

```tikz
\usepackage{tikz-cd}
\usepackage{amsmath}
\begin{document}
\begin{tikzcd}
\hom(C\text,X) \rar["\eta_X"] \dar["\hom(C\text{,}k)"] &
\prod_{j\in J}\hom(A_j\text,X) \dar["\hom(A_j\text{,}k)_{j\in J}"] \\
\hom(C\text,Y) \rar["\eta_Y"] &
\prod_{j\in J}\hom(A_j\text,Y)
\end{tikzcd}
\end{document}
```

By universal property of coproduct, for all $(f_j)_{j\in J}\in\prod_{j\in J}\hom(A_j,X)$ there is a unique $f:C\to X$ such that $f_j=f\circ\iota_j$. Thus our natural transformation is isomorphic and $\hom(C,-)\cong\prod_{j\in J}\hom(A_j,-)$.

(2) Given an arrow $f:X\to\prod_{i\in I}B_i$, there is a corresponding collection of arrows $f_i:X\to B_i$. There is a unique $\eta_X:\hom(X,P)\to\prod_{i\in I}\hom(X,B_i)$ such that $f_i=\eta_X\circ\pi_i$, where $\pi_i$ is the morphism for $\prod_{i\in I}\hom(X,B_i)$. The collection of arrows $(f_i)_{i\in I}$ is in bijection with $f$, thus $\eta$ is a natural isomorphism and $\hom(-,P)\cong\prod_{i\in I}\hom(-,B_i)$.

![[MikuQed.png | center | 100]]

>[!example] Show ring homomorphism induces homomorphism between $GL_n$
>There are functors $GL_n$ and $(-)_\times$ from $\mathbf{CRing}$ to $\mathbf{Ab}$. Show that there is a natural transformation from $GL_n$ to $(-)_\times$.

For a commutative ring $R$, $GL_n(R)=\{n\times n\text{ non-singular matrices}\}$ and $(R)_\times=\{r\in R|r\text{ is a unit}\}$

Consider the natural transformation $\det:GL_n\to(-)_\times$. Let $\varphi:X\to Y$ be an arrow of $\mathbf{CRing}$, so we have the following diagram

```tikz
\usepackage{tikz-cd}
\usepackage{amssymb}
\begin{document}
\begin{tikzcd}
X \dar["\varphi"] &
GL_n(X) \rar["\det X"] \dar["GL_n\varphi"] &
(X)_\times \dar["(\varphi)_\times"] \\
Y &
GL_n(Y) \rar["\det Y"] &
(Y)_\times
\end{tikzcd}
\end{document}
```

$GL_n\varphi$ is an arrow taking a matrix of $X$ to a matrix of $Y$ component wise. $(\varphi)_\times$ takes the units of $X$ to the units of $Y$. $\det X$ gives the determinant of matrices in $GL_n(X)$, and likewise for $\det Y$. This diagram commutes, thus $\det$ is a natural transformation.

![[MikuQed.png | center | 100]]