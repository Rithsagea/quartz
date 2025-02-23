# DFAs and NFAs
<u>NFA -> DFA Reduction</u> Construct $\epsilon$-Closures of subsets of nodes, and use subsets as new node

<u>Minimize DFA</u> Partition DFA into final and non-final states. Split partitions if members in the partition have transitions to different partitions for the same input. Fixed state partitions are new nodes.

# Parsing
Given some grammar $G$, define the following

$FIRST(\alpha)$: characters that appear first in string derived from $\alpha$
- For a terminal, $FIRST(x)=\{x\}$

$FOLLOW(\langle\alpha\rangle)$: terminals that appear immediately after $\langle A\rangle$
- Terminal symbols have empty FOLLOW set
- $\epsilon$ does not appear in any FOLLOW set
- the start symbol FOLLOW set should include $EOF$

$PREDICT(\langle A\rangle::=\delta)$: lookahead symbols that are valid for rule $\langle A\rangle::=\delta$

$$FIRST(y_1y_2\cdots)=
\begin{cases}
FIRST(y_1)&\epsilon\not\in FIRST(y_1)\\\{FIRST(y_1)-\epsilon\}\cup FIRST(y_2\cdots)&\epsilon\in FIRST(y_1)
\end{cases}
$$

$$\text{Production Rule: }a\rightarrow b_1b_2\cdots b_i\cdots$$
$$FOLLOW(b_i)=
\begin{cases}
FIRST(b_{i+1}b_{i+2}\cdots)&
\epsilon\not\in FIRST(b_{i+1}b_{i+2}\cdots)\\
(FIRST(b_{i+1}\cdots)-\{\epsilon\})\cup FOLLOW(a)&
\epsilon\in FIRST(b_{i+1}b_{i+2}\cdots)
\end{cases}
$$

$$PREDICT(\langle \alpha\rangle::=\delta)=
\begin{cases}FIRST(\delta)-\{\epsilon\}\cup FOLLOW(\langle A\rangle)&\epsilon\in FIRST(\delta)\\FIRST(\delta)&otherwise\end{cases}
$$

# Scope and Binding
- <u>Lexical Scope</u> non-local variables associated with declarations at *compile time*. Find smallest text block ***syntactically*** enclosing the reference and a declaration of the variable. <u>Access Link</u>
- <u>Dynamic Scope</u> non-local variables are associated with declarations at *run time*. Find the most recent, current active run-time stack frame containing a declaration of the variable. <u>Control Link</u>

![[Call Stack.svg]]

# FP
`car` => first
`cdr` => rest

`[a,b,c]` => `'(a (b (c . null)))`

## Judgement Derivation
![[Judgement Derivation.svg]]

## Lambda Calculus
- Function application is left associative, $(fgz)=((fg)z)$
- Function application precedence over abstraction
	- $(\lambda x.yz)=(\lambda x.(yz))$, $\lambda x.\lambda y.xy=\lambda x.(\lambda y.xy)$
- Multi argument functions $(\lambda xy.z)=(\lambda x.(\lambda y.z))$

Alpha reduction renaming, Beta reduction substitution

True and false 2 parameter functions return first or second param $true\equiv\lambda a.\lambda b.a$, $false\equiv\lambda a.\lambda b.b$