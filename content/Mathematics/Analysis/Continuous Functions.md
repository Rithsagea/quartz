Source: [[9780070542358|Principles of Mathematical Analysis]]

Let $X$ and $Y$ be metric spaces, $E\subset X$, $p\in E$, and $f:E\to Y$. We say $f$ is <u>continuous</u> at $p$ if for every $\varepsilon>0$, there exists a $\delta>0$ such that $d_Y(f(x),f(p))<\varepsilon$ for all $x\in E$ which $d_X(x,p)<\delta$. If $f$ is continuous at every point of $E$, then $f$ is continuous on $E$.

## Transitivity
>[!info]
>Let $X,Y,Z$ be metric spaces, $E\subset X$, and $f:E\to Y$, $g:f(E)\to Z$. Define the function $h(x)=g(f(x))$. If $f$ is continuous at $p\in E$ and $g$ is continuous at $f(p)$, then $h$ is continuous at $p$.

Let $\varepsilon>0$. By definition, there is $\delta_1>0$ such that for all $y\in f(E)$, $d_Y(y,f(p))<\delta_1$ implies $d_Z(g(y),g(f((p)))<\varepsilon$. Similarly, there is $\delta_2>0$ such that for all $x\in X$, $d_X(x,p)<\delta_2$ implies $d_Y(f(x),f(p))<\delta_1$. Thus $d_X(x,p)<\delta_2$ implies $d_Z(h(x),h(p))<\varepsilon$, and $h$ is continuous at $p$.

## Topological Characterization of Continuity
>[!info]
>Let $X,Y$ be metric spaces. $f:X\to Y$ is continuous if and only if $f^{-1}(V)$ is open in $X$ for every open set $V\subset Y$.

$(\Rightarrow)$ Suppose $f$ is continuous on $X$ and $V\subset Y$ is open. Suppose $p\in X$ and $f(p)\in V$. There is some $\varepsilon$ where $N_\varepsilon(f(p))\subset V$. By continuity, there is some $\delta>0$ where $f(N_\delta(p))\subset N_\varepsilon(f(p))$. Thus for every $x\in N_\delta(p)$, $x\in V$, and $f^{-1}(V)$ is open.

$(\Leftarrow)$ Suppose $f^{-1}(V)$ is open in $X$ for every open $V\subset Y$. For every $p\in X$ and $\varepsilon>0$, $N_\varepsilon(f(p))$ is an open set, so $f^{-1}(N_\varepsilon(f(p)))$ is open by assumption. But $p$ is contained in this set, so there is some $\delta>0$ where $N_\delta(p)\subset f^{-1}(N_\varepsilon(f(p)))$. But $x\in N_\delta(p)$ implies $f(x)\in N_\varepsilon(f(p))$, thus $f$ is continuous.

# Continuity and Compactness

## Preservation of Compactness
>[!info]
>If $f$ is a continuous mapping of a compact metric space $X$ to metric space $Y$, then $f(X)$ is compact.

Let $\{V_\alpha\}$ be an open cover of $f(X)$.
By [[#Topological Characterization of Continuity]], $\{f^{-1}(V_\alpha)\}$ is an open cover of $X$. Since $X$ was originally compact, there is a finite subcover $X\subset f^{-1}(V_{\alpha_1})\cup\ldots\cup f^{-1}(V_{\alpha_n})$. Then $f(X)\subset V_{\alpha_1}\cup\ldots\cup V_{\alpha_n}$ and $f(X)$ is compact.

## Uniform Continuity

Let $f:X\to Y$ be a mapping of metric spaces. We say $f$ is <u>uniformly continuous</u> on $X$ if for every $\varepsilon>0$, there exists $\delta>0$ such that every $p,q\in X$ satisfies $d_X(p,q)<\delta$ implies $d_Y(f(p),f(q))<\varepsilon$.