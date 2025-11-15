---
title: Topology
date: 2024-11-27
---

## Topological Space

Let $X$ be a nonempty set and $\tau\subseteq\mathscr P(X)$ be a family of subsets of $X$. $\tau$ is a <u>topology on</u> $X$ if it satisfies the following properties:
(a) $\varnothing\in\tau$ and $X\in\tau$
(b) Any union of elements in $\tau$ is also an element of $\tau$
(c) Any intersection of <u>finitely many</u> elements of $\tau$ is an element of $\tau$

$(X,\tau)$ is a <u>topological space</u>, and the members of $\tau$ are <u>open sets</u> in $X$

$F\subseteq X$ is closed if $X\setminus F$ is open.

Function $f:A\rightarrow B$ respects boolean operations.

$$f^{-1}(\overline V)=\overline{f^{-1}(V)}\quad f^{-1}(B-V)=A-f^{-1}(V)$$

## Relative Topology

Let $(X,\tau)$ be a topological space, and $S\subseteq X$ a nonempty subset of $X$. Define the <u>relative topology</u>, $\tau_S:=\{S\cap G|G\in\tau\}$. Then we can we define open, closed, and compactness <u>relative</u> to $S$. A <u>neighborhood</u> of $a$ is any open set containing $a$. $(S,\tau_S)$ is a topology.

$(\mathbb Z,\tau_{\mathbb Z})$ is the discrete topology. All subsets of $\mathbb Z$ are closed and open