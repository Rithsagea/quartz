---
title: Church-Turing Thesis
date: 2025-03-05
---

## Turing Machine
A <u>Turing Machine</u> is a 7 tuple $M=(Q,\Sigma,\Gamma,\delta,q_{start},q_{accept},q_{reject})$
- $Q$ is finite set of states
- $\Sigma$ is finite input alphabet
- $\Sigma\subseteq\Gamma$ is finite tape alphabet
- $\delta:Q\times\Gamma\to Q\times\Gamma\times\{L,R\}$

A configuration consists of (1) content of tape in $\Gamma^*$ (2) state in $Q$ (3) position of head $\mathbb N$. The initial configuration is $q_{start}w\sqcup\sqcup\ldots\sqcup$

If machine reaches $q_{accept}$ or $q_{reject}$, it halts. Define $L(M)$ to be
$$
\{w\in\Sigma^*|M\text{ halts on }w\text{ and accepts it}\}
$$

A Turing machine <u>accepts</u> $w$ if there is a sequence of configurations $C_1,C_2,\ldots,C_k$ where $C_1$ is the start configuration of $M$ to $w$, $C_i$ yields $C_{i+1}$, and $C_k$ is an accepting configuration.

### Turing Recognizable
$L\subseteq\Sigma^*$ is <u>Turing recognizable</u> or <u>recursively enumerable</u> if $\exists M$ such that $L(M)=L$

It is <u>Turing decidable</u> or <u>recursive</u> if $\exists M$ such that $w\in L$ when $M$ halts on accept, and $w\not\in L$ means $M$ halts on reject.

$E_{DFA}=\{\langle D\rangle|D\in DFA,L(D)\ne\varnothing\}$

## Variants
<u>Multitape Turing Machine</u> $\delta:Q\times\Gamma^k\to Q\times\Gamma^K\times\{L,R,S\}^k$

<u>Nondeterministic Turing Machine</u> $\delta:Q\times\Gamma\to\mathcal P(Q\times\Gamma\times\{L,R\})$

These are both equivalent to regular Turing machines

An <u>enumerator</u> is a Turing-machine that has a working tape, along with a printer tape. A language is Turing-recognizable iff some enumerator enumerates it.

## Church-Turing Thesis
Any physically realizable computational device can be simulated by standard Turing machine up to polynomial time loss in efficiency.