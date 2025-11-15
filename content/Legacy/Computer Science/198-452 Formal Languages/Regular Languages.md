---
title: Regular Languages
date: 2025-02-19
---

## Deterministic Finite Automata

A <u>deterministic finite automaton</u> is a 5-tuple $M=(Q,\Sigma,\delta,q_0,F)$ 
- $Q$, a finite set of states
- $\Sigma$, a finite alphabet
- $\delta:Q\times\Sigma\to Q$, the transition function
- $q_0\in Q$, the start state
- $F\subset Q$, the accept states

$L(M)\subset\Sigma^*$ is the set of strings <u>recognized</u> / <u>accepted</u> by $M$.
$w=w_1w_2\cdots w_n$ is in $L(M)$ iff there is a sequence of states $r_0,r_1,\ldots,r_n$ such that $r_0=q_0$, $\delta(r_i,w_{i+1})=r_{i+1}$ for $0\le i\le n-1$ and $r_n\in F$

## Nondeterministic Finite Automata
Define $\Sigma_\varepsilon=\Sigma\cup\{\varepsilon\}$, where $\epsilon$ represents an empty string

A <u>nondeterminstic finite automaton</u> is a 5-tuple $M=(Q,\Sigma,\delta,q_0,F)$
- $Q$, a finite set of states
- $\Sigma$, a finite alphabet
- $\delta:Q\times\Sigma_\varepsilon\to\mathcal P(Q)$, the transition function
- $q_0\in Q$ the start state
- $F\subset Q$ the accept states

Given a string $w\in\Sigma^*$, we can write $w=y_1y_2\cdots y_m$ where $y_i\in\Sigma_\epsilon$. This string is accepted by $M$ iff there exists a sequence of states $r_0,r_1,\ldots,r_m$ such that $r_0=q_0$, $r_{i+1}\in\delta(r_i,y_{i+1})$ for $0\le i\le m-1$, and $r_m\in F$

Every NFA has an equivalent DFA over the states $\mathcal P(Q)$ and appropriately constructed transitions.


## Regular Expressions

A language is <u>regular</u> if it is recognized by some DFA

Given languages $A$ and $B$, the regular operations are as follows
- <u>union</u> $A\cup B=\{x|x\in A\cup B\}$
- <u>concatenation</u> $A\circ B=\{xy|x\in A,y\in B\}$
- <u>star</u> $A^*=\{x_1x_2\ldots x_k|k\ge 0,x_i\in A\}$

Regular languages are closed under these operations.

A <u>regular expression</u> $R$ over $\Sigma$ is an object of the following type

$$
\operatorname{type}\text{ Regex}=
\begin{cases}
a\in\Sigma\\
\varepsilon\\
\varnothing\\
\text{Regex}\cup\text{Regex}\\
\text{Regex}\circ\text{Regex}\\
\text{Regex}^*
\end{cases}
$$

A language is regular if it can be expressed by a regular expression.

## Generalized Nondeterministic Finite Automata
A <u>generalized nondeterministic finite automata</u> is a 5-tuple $(Q,\Sigma,\delta,q_{\text{start}},q_{\text{accept}})$, where
- $Q$ is a finite set of states
- $\Sigma$ is a finite alphabet
- $\delta(Q-\{q_{\text{accept}}\})\times(Q-\{q_{\text{start}}\})\to\mathcal R$ is a transition function, and $\mathcal R$ is the set of all regular expressions over $\Sigma$
- $q_{\text{start}}$ is the start state
- $q_{\text{accept}}$ is the accept state

A GNFA accepts a string $w\in\Sigma^*$ if $w=w_1w_2\cdots w_k$ where $w_i\in\Sigma^*$ and there is a sequence of states $q_0,q_1,\ldots,q_k$ such that $q_0=q_{\text{start}}$ is the start state, $q_k=q_{\text{accept}}$ is the accept state, and $w_i\in L(\delta(q_{i-1},q_i))$

Define a procedure $\text{CONVERT}(G)$ to reduce the number of states in a GNFA $G$
1. Let $k$ be the number of states of $G$
2. If $k=2$, then there is a start and end state connected by an arrow. Return the regex of this arrow
3. If $k>2$, pick any $q_{\text{rip}}\in Q$ such that $q_{\text{rip}}\ne q_{\text{start}},q_{\text{accept}}$ and let $G'$ be a GNFA $(Q',\Sigma,\delta',q_{\text{start}},q_{\text{end}})$ where $Q'=Q-\{q_{\text{rip}}\}$, and for all $q_i\in Q'-\{q_{\text{accept}}\}$, $q_j\in Q'-\{q_{\text{accept}}\}$, $\delta'(q_i,q_j)=\delta(q_i,q_{\text{rip}})\delta(q_{\text{rip}},q_{\text{rip}})^*\delta(q_{\text{rip}},q_j)\cup\delta(q_i,q_j)$
4. Compute and return $\text{CONVERT}(G')$

## Pumping Lemma

If $A$ is a regular language, then there is a number $p$ (the pumping length) where if $s\in A$ with $|s|\ge p$, then $s$ can be divided into 3 pieces $s=xyz$ where
1. for $i\ge 0$, $xy^iz\in A$
2. $|y|>0$
3. $|xy|\le p$

The proof for this uses the pidgeon hole principle to show that for a DFA with $p$ states, a string with length greater than $p$ must repeat one of these states, and thus yields the string $y$.

This tool is used to show that languages are not regular.