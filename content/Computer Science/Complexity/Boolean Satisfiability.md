Source: [[10.5555 524279|Introduction to the Theory of Computation]]

A <u>Boolean formula</u> is an expression written with $\mathsf{AND}\ (\land)$, $\mathsf{OR}\ (\lor)$, and $\mathsf{NOT}\ (\lnot)$. For example, $\phi=(\bar x\land y)\lor(x\land \bar z)$. Write the language of satisfiable expressions

$$
SAT=\{\langle\phi\rangle:\phi\text{ is a satisfiable Boolean formula}\}
$$

# NP-Complete
>[!info]
>$SAT$ is $NP$-complete.

Clearly $SAT\subseteq NP$, as a nondeterministic Turing machine can guess an assignment to check for satisfiability. Now let $A\in NP$ with polytime verifier [[Turing Machine]] $N$ that terminates in $O(n^k)$. A <u>tableau</u> for $N$ with input $w=w_1w_2\ldots w_n$ is an $n^k\times n^k$ table, where rows represent configurations. Furthermore, assume each configuration is wrapped with $\#$.

![[Boolean Satisfiability Tableau.png| center | 400]]

Let $Q$, $\Gamma$ be the state and tape alphabet of $N$, and $(i,j)\in[n^k]^2$. We write the value at $i,j$ in the tableau as $cell[i,j]$. For each $s\in C=Q\cup\Gamma\cup\{\#\}$, set a variable $x_{i,j,s}$ to $1$ if $cell[i,j]=s$.

## Cell Constraint
We require that each cell has exactly one assignment from our variables. This is represented as follows.
$$
\phi_{cell}=\bigwedge_{(i,j)\in[n^k]^2}\left[
\left(\bigvee_{s\in C}x_{i,j,s}\right)\land
\left(\bigvee_{s\ne t\in C}
(\overline{x_{i,j,s}}\lor\overline{x_{i,j,t}}\right)
\right]
$$

## Start / End Constraint
We want the first configuration to correspond to the input $w$. This explicitly specifies start state, input, trailing spaces, and boundary character $\#$.
$$
\phi_{start}=x_{1,1,\#}\land x_{1,2,q_0}
\land\bigwedge_{i\in[n]}x_{1,i+2,w_i}
\land\bigwedge_{j\in[n+3,n^k-1]}x_{1,j,\textvisiblespace}
\land x_{1,n^k,\#}
$$

Additionally, we require that the automata eventually hits an accept state.
$$
\phi_{accept}=\bigvee_{(i,j)\in[n^k]^2}x_{i,j,q_{accept}}
$$

## Move Constraint
Within each configuration, there is only a single cell containing a state. The cell to its right represents the tape location of the Turing machine at that step. Suppose $\delta(q,\sigma)=\{(q_L,\sigma_L,L),(q_R,\sigma_R,R)\}$. For $\sigma',\sigma''\in\Gamma\cup\{\#\}$, the following are valid $2\times3$ windows.
$$
\begin{aligned}
&\begin{array}{|ccc|}
q & \sigma & \sigma'\\
\sigma_R & q_R &  \sigma'\\
\end{array}
&\begin{array}{|ccc|}
\sigma' & q & \sigma \\
\sigma' & \sigma_R & q_R \\
\end{array}
\qquad
&\begin{array}{|ccc|}
\sigma' & \sigma'' & q \\
\sigma' & \sigma'' & \sigma_R \\
\end{array}
\\
\hline
&\begin{array}{|ccc|}
q & \sigma & \sigma'\\
\sigma'' & \sigma_L &  \sigma'\\
\end{array}
&\begin{array}{|ccc|}
\sigma' & q & \sigma \\
q_L & \sigma' & \sigma_L\\
\end{array}
\qquad
&\begin{array}{|ccc|}
\sigma' & \sigma'' & q \\
\sigma' & q_L & \sigma''\\
\end{array}
\end{aligned}
$$

The $(i,j)$ window refers to a $2\times 3$ region where $(i,j)$ is the upper central cell. Write $\mathcal W\subseteq C^{2\times 3}$ as the set of valid windows.
To enforce these transitions, we write the following rule

$$
\phi_{move}=\bigwedge_{\substack{i\in[1,n^k-1]\\j\in[2,n^k-1]}}
\bigvee_{W\in\mathcal W}
\bigwedge_{\substack{di\in [2]\\dj\in [3]}}
x_{i+di-1,j+dj-2,W[di,dj]}
$$

## Analysis
The final boolean formula is given by $\phi=\phi_{cell}\land\phi_{start}\land\phi_{move}\land\phi_{accept}$. There are $O(n^{2k}|C|)$ variables and $O(|C|^6n^{2k})$ components in $\phi$, thus this gives polynomial reduction of any $NP$ problem to some boolean satisfiability instance.