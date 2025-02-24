---
title: DRP Notes, Week 3
date: 2025-02-23
---

## Tensor Product of Abelian Groups
Let $A,B\in\mathfrak{Ab}$. Then the <u>tensor product</u> $A\otimes B$ is defined as the quotient of the free abelian group on $A\times B$ with the following relations
$$
(a_1,b)+(a_2,b)\sim(a_1+a_2,b)\qquad
(a,b_1)+(a,b_2)\sim(a,b_1+b_2)
$$

>[!example] Identity in the monoid $(\mathfrak{Ab},\otimes,\mathbf Z)$
>Let $X\in\mathfrak{Ab}$ and define a map $\varphi:X\otimes\mathbf Z\to X$ with $\varphi(x,a)\mapsto ax$
>
>Let $(x,a)$ be any representative of $X\times\mathbf Z$ in $X\otimes\mathbf Z$. If $a<0$, then $(x,a)=(-x,|a|)$, so WMA $a\ge 0$. For all $\sum_{i}(x_i,a_i)\in X\oplus\mathbf Z$, we have
>$$
>\varphi\left(\sum_i(x_i,a_i)\right)
>=\varphi\left(\sum_i\sum_{j=1}^{a_i}(x_i,1)\right)
>=\varphi\left(\sum_i(a_ix_i,1)\right)
>=\varphi\left(\sum_i a_ix_i,1\right)
>=\sum_ia_ix_i
>$$
>
>To show this a homomorphism, let $(x_1,a_1),(x_2,a_2)\in X\oplus\mathbf Z$. We have $\varphi((x_1,a_1)+(x_2,a_2))=a_1x_1+a_2x_2=\varphi((x_1,a_1))+\varphi((x_2,a_2))$.
>A moment's thought shows the inverse $\varphi^{-1}(x)\mapsto(x,1)$ is a homomorphism, and both $\varphi\circ\varphi^{-1}$ and $\varphi^{-1}\circ\varphi$ are identities. Thus $\varphi$ is an isomorphism and $X\oplus\mathbf Z\cong X$
>
>![[MikuQed.png|center|100]]

>[!example] Tensor product of abelian group and $\mathbf Z^2$
>Let $X$ be an abelian group. For $(x,(a,b))\in X\otimes\mathbf Z^2$, we can write
>$$
>(x,(a,b))
>=(x,(a,0)+(0,b))
>=(x,(a,0))+(x,(0,b))
>=(ax,(1,0)+(bx,(0,1))
>$$
>Using bilinearity in the second component, any element in the tensor product can be written in the form $(x_1,(1,0))+(x_2,(0,1))$. Mapping this to $(x_1,x_2)\in X^2$, we see that $X\oplus\mathbf Z^2\cong X^2$
>
>![[MikuQed.png|center|100]]