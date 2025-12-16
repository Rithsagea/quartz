The subset sum problem considers a collection of numbers $x_1,\cdots,x_k$ and a number $t$. We want to find a subcollection that sums to $t$. The corresponding language is given

$$
SUBSET\text-SUM=\left\{\langle S,t\rangle:S=\{x_1,\cdots,x_k\},\exists\{y_1,\ldots,y_l\}\subseteq\{x_1,\ldots,x_k\},\sum y_i=t\right\}
$$

## NP-Complete
>[!info]
>$SUBSET\text-SUM$ is NP-complete

A nondeterministic Turing machine a select an arbitrary subset and test if it sums up correctly in polynomial time. Thus $SUBSET\text-SUM\in NP$.

To show completeness, we reduce from [[3SAT]]. Let $\phi$ be a Boolean formula with variables $x_1,\ldots,x_l$ and clauses $c_1,\ldots,c_k$. For each variable $x_*$ and clause $c_*$, add the following numbers to a collection $S$
$$
\begin{aligned}
&y_*=10^k(10^*)+\sum_{i=1}^k10^{i-1}\mathbb 1_{x_*\in c_i}&
z_*=10^k(10^*)+\sum_{i=1}^k10^{i-1}\mathbb 1_{\bar x_*\in c_i}\\
&g_*=h_*=10^{*-1}
\end{aligned}
$$

Write $t=(10^k\sum_{i=1}^l10^i)+(\sum_{i=1}^k3\cdot10^{i-1})$. Note that when summing these numbers together, the total weight on each digit is at most $5$, thus adjacent digits cannot affect each other through carrying. A satisfying assignment corresponds exactly to choosing one of $y_*$ and $z_*$ for a truth assignment of $x_*$, and padding any clauses with less than three true literals using $g_*$ and $h_*$. This is a polynomial time reduction, thus $SUBSET\text-SUM$ is NP-complete.