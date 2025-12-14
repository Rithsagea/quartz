Source: [[10.5555 524279|Introduction to the Theory of Computation]]

A <u>literal</u> is a (negated) boolean variable, while a <u>clause</u> is disjunction $(\lor)$ of literals. A formula is in <u>conjunctive normal form</u> if it is a conjunction ($\land$) of clauses. A subset of these are called <u>3cnf-formula</u> if all the clauses have three literals. Define the following language
$$
3SAT=\{\langle\phi\rangle:\phi\text{ is a satisfiable 3cnf-formula}\}
$$

## NP-Complete
>[!info]
>$3SAT$ is $NP$-complete

It is known that [[Boolean Satisfiability#NP-Complete|SAT]] is $NP$-complete. Furthermore $3SAT\subseteq SAT$, thus $3SAT\in NP$. Given some boolean formula $\phi$, this can be rewritten as a conjunction of disjunctions, by distributing $x\land(y\lor z)=(x\land y)\lor(x\land z)$ and applying DeMorgan's Law. Finally, a string of disjunctions can be decomposed into 3-length disjunctions by adding helper variables $z_1,z_2,\ldots$
$$
(a_1\lor a_2\lor\ldots\lor a_l)
=
(a_1\lor a_2\lor z_1)
\land(\overline{z_2}\lor a_3\lor z_3)
\land\ldots
\land(\overline{z_{l-3}}\lor a_{l-1}\lor a_l)
$$

Then $a_1\ldots a_l$ is satisfied iff some choice of $a_1\ldots a_l$ and $z_1\ldots z_{l-3}$ satisfies the right. At most a constant factor of variables are introduced with this substitution. Thus $\phi$ can be made into a 3cnf-formula and $SAT$ is reduced to $3SAT$.