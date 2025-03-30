---
title: Decidability
date: 2025-03-30
---

## Decidable Languages

The following are also decidable by simulation and equivalence of DFA, NFA, and regular expressions.

$$
\begin{array}{c}
A_{DFA}=\{\langle B,w\rangle|B\text{ is a DFA that accepts input string }w\}\\
A_{NFA}=\{\langle B,w\rangle|B\text{ is a NFA that accepts input string }w\}\\
A_{REX}=\{\langle R,w\rangle|R\text{ is a regular expression that accepts input string }w\}\\
\end{array}
$$

$E_{DFA}=\{\langle D\rangle|D\in DFA,L(D)\ne\varnothing\}$ is decidable performing a tree search for accept state from start state.

$EQ_{DFA}=\{\langle A,B\rangle|A,B\in DFA, L(A)=L(B)\}$ is decidable by constructing $C$ such that $L(C)=(L(A)\cap\overline{L(B)})\cup(\overline{L(A)}\cap L(B))$, and testing if $C\in E_{DFA}$.

$A_{CFG}=\{\langle G,w\rangle|G\text{ is a CFG that generates string }w\}$ is decidable by converting $G$ to Chomsky normal form, and finding all derivations of length $|w|$. Any derivation of this length will take at most $2|w|-1$ steps.

$E_{CFG}=\{\langle G\rangle|G\in CFG,L(G)=\varnothing\}$ is decidable by marking all terminal symbols, and then marking all variables that have marked children. If the start symbol is marked, then there is some string in $G$. There are only $|V|$ variables, so this algorithm will terminate.

## Undecidable Languages

The set of Turing-recognizable languages are countable, but the set of all languages is uncountable since $\mathcal P(\Sigma^*)\approx\mathcal P(\mathbb N)$ is not

---

$A_{TM}=\{\langle M,w\rangle|M\text{ is a TM and M accepts }w\}$ is undecidable, but recognizable. The second property can be seen by simply running $M$ on $w$. The first property requires additional construction. Assume $A_{TM}$ is decidable with decider $H$ and construct $D$.

$$
H(\langle M,w\rangle)=\begin{cases}
accept & \text{if }M\text{ accepts }w\\
reject & \text{if }M\text{ does not accept }w
\end{cases}
$$
$$
D(\langle M\rangle)
=\lnot H(\langle M,\langle M\rangle\rangle
=\begin{cases}
accept & \text{ if }M\text{ does not accept }\langle M\rangle\\
reject & \text{ if }M\text{ accepts }\langle M\rangle
\end{cases}
$$

Running $D(\langle D\rangle)$, we get a contradiction, since both $accept$ and $reject$ fail to satisfy the condition on $D$. Thus $H$ cannot exist and $A_{TM}$ is undecidable.

---

A language is <u>co-Turing recognizable</u> if it is the complement of a Turing recognizable language. A language is decidable iff it is Turing recognizable and co-Turing recognizable. This can be seen by running both deciders simultaneously.

As a result, $\overline{A_{TM}}$ is not Turing-recognizable.

## Halting Problem
$HALT_{TM}=\{\langle M,w\rangle|M\text{ is a TM and }M\text{ halts on input }w\}$ is undecidable by reduction to $A_{TM}$. Given $\langle M,w\rangle$, we can run $HALT_{TM}$ and $M$ on $w$ simultaneously, returning appropriate results to create a decider for $A_{TM}$.

## Examples

$E_{TM}=\{\langle M\rangle|M\text{ is a TM and }L(M)=\varnothing\}$ is undecidable also by reduction to $A_{TM}$. Given $\langle M,w\rangle$, modify $M$ such that $M'$ accepts $w'$ iff $M$ accepts $w$ and $w=w'$. Then, running $E_{TM}$ on $M'$ decides if $A_{TM}$ accepts $\langle M,w\rangle$.

$REGULAR_{TM}=\{\langle M\rangle|M\text{ is a TM and }L(M)\text{ is a regular language}\}$ is undecidable. Given some $\langle M,w\rangle$, construct $M'$ that accepts $0^n1^n$ by default, and all strings iff $M$ accepts $w$. Then $REGULAR_{TM}(M')$ is a decider for $A_{TM}$.

$EQ_{TM}=\{\langle M_1,M_2\rangle|M_1\text{ and }M_2\text{ are TMs and }L(M_1)=L(M_2)\}$ is undecidable, by reduction to $E_{TM}$. Let $M'$ be a TM that rejects all inputs, and compare input $\langle M\rangle$ to $M'$.

---

A <u>linear bounded automaton</u> is a Turing machine where the tape head cannot move off the portion containing the input. This means the set of possible configurations is finite.

An $LBA$ with $q$ states, $g$ symbols, has $qng^n$ configurations given a tape of length $n$. Thus $A_{LBA}$ is decidable, since we can simulate this many steps and before accepting or determining looping.