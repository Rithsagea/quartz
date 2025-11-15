---
date: 2024-12-09
---

## Basic Math
### Order Notation
Let $f,g:\mathbb Z_{>0}\rightarrow\mathbb R_{>0}$. We define the following relations
- $f=O(g)\Leftrightarrow(\exists c>0)\ f(n)\le c\cdot g(n)$
- $f=\Omega(g)\Leftrightarrow g=O(f)$
- $f=\Theta(g)\Leftrightarrow (f=O(g))\land(f=\Omega(g))$

Furthermore, we can define stronger relations
- $f=o(g)\Leftrightarrow(\forall c>0)(\exists n_0\ge 0)(\forall n\ge n_0)\ f(n)\le c\cdot g(n)$
- $f=\omega(g)\Leftrightarrow\ g=o(f)$

### Big-O Identities
- $kf=\Theta(f)$
- $a>b\Rightarrow n^a=\Omega(n^b)$
- $x^n=\Omega(n^k)$
- $n^k=\Omega((\log n)^k)$

### Master Theorem
Given a recurrence relation $T(n)=aT(\lceil n/b\rceil))+O(n^d)$ with constants $a>0$, $b>1$, and $d\ge 0$
$$
T(n)=\cases{
O(n^d\log n)&\text{if }d=\log_ba\\
O(n^{\log_ba})&\text{if }d<\log_ba
}
$$

## Arithmetic Algorithms
### Modular Exponentiation
Input: Two $n$-bit integers $x$ and $N$, an integer exponent $y$
Output: $x^y\mod N$
Runtime: $O(n)$
```py
def modexp(x, y, N):
	if y == 0: return 1
	z = modexp(x, y // 2, N)
	if y % 2 == 0:
		return (z ** 2) % N
	else:
		return (x * (z ** 2)) % N
```

### Extended Euclid
Input: Two positive integers $a$ and $b$ with $a\ge b\ge 0$
Output: Integers $x,y,d$ such that $d=\gcd(a,b)$ and $ax+by=d$
Runtime: $O(n)$. There are $n$ iterations, each with cost $O(n^2)$ (division)
```py
def extended_euclid(a, b):
	if b == 0: return (1, 0, a)
	(xp, yp, d) = extended_euclid(b, a % b)
	return (yp, xp - floor(a / b) * yp, d)
```

For integers $a,N$, if $\gcd(a,N)=1$, then we can compute $a^{-1}\pmod N$ by running the extended gcd algorithm. Equivalently $a\cdot a^{-1}+k\cdot N=1$

### Fermat's Little Theorem
If $p$ is prime, then for every $1\le a<p$, $a^{p-1}\equiv 1\pmod p$

### RSA
Pick primes $p$ and $q$, then let $N=pq$. For any $e$ relatively prime to $(p-1)(q-1)$,
1. $x\mapsto x^e\pmod N$ is a bijection on $\{0,1,\ldots,N-1\}$
2. Let $d\equiv e^{-1}\pmod{(p-1)(q-1)}$. Then $(x^e)^d\equiv x\pmod N$

### Fast Fourier Transform
Input: An array $a=(a_0,a_1,\ldots,a_{n-1})$, for $n$ a power of $2$. A primitive $n$th root of unity, $\omega$
Output: $M_n(\omega)a$
Runtime: $O(n\log n)$

```py
def fft(a, omega):
	if omega == 1: return a
	(s[0],s[1],...,s[n/2-1]) = FFT((a[0], a[2],..., a[n-2]), omega ** 2)
	(t[0],t[1],...,t[n/2-1]) = FFT((a[1], a[3],..., a[n-1]), omega ** 2)
	for j in range(0, n/2):
		r[j] = s[j] + omega ** j * t[j]
		r[j + n/2] = s[j] - omega ** j * t[j]
	return r
```

## Divide and Conquer
### Multiplication
Input: Positive integers $x$ and $y$, in binary
Output: Their product
Runtime: $T(n)=3T(n/2)+O(n)$; $O(n^{\log_2 3})$

```py
def multiply(x, y):
	n = max(len(x), len(y))
	if n == 1: return x * y
	xl, xr = x[:len(x)//2], x[len(x)//2:]
	yl, yr = y[:len(y)//2], y[len(y)//2:]
	p1 = multiply(xl, yl)
	p2 = multiply(xr, yr)
	p3 = multiply(xl + xr, yl + yr)
	return p1*(2**n) + (p3-p1-p2) * (2**(n//2)) + p2
```

### Mergesort
Input: Array of numbers $a[1\ldots n]$
Output: A sorted version of the array
Runtime: $T(n)=2T(n/2)+O(n)$; $O(n\log n)$

```py
def mergesort(a):
	if len(a) > 1:
		return merge(
			mergesort(a[:n//2]),
			mergesort(a[n//2:]))
	else:
		return a
		
def merge(x, y):
	if len(x) == 0: return y
	if len(y) == 0: return x
	if x[0] <= y[0]:
		return [x[0]] + merge(x[1:], y)
	else:
		return [y[0]] + merge(x, y[1:])
```

### Selection
Input: A list of numbers $S$; an integer $k$
Output: The $k$th smallest element of $S$

For some $v\in S$, define $S_L$, $S_v$, $S_R$ to be elements of $S$ less than, equal to, or greater than $v$.

$$\text{selection}(S,k)=\left\{\array{\text{selection}(S_L,k)&\text{if }k\le|S_L|\\v&\text{if }|S_L|<k\le|S_L|+|S_v|\\\text{selection}(S_R,k-|S_L|-|S_v|)&\text{if }k>|S_L|+|S_v|}\right.
$$

With some expectations, we have $T(n)\le T(3n/4)+O(N)$, so $O(n)$ runtime

## Graphs
### DFS
Input: $G=(V,E)$ is a graph; $v\in V$
Output: $\text{visited}(u)$ is true if $u$ reachable from $v$
Runtime: $O(|V|+|E|)$

```py
def explore(V, E, v):
	visited(v) = true
	previsit(v)
	for (v,u) in E:
		if not visited[u]: dfs(G, u)
	postvisit(v)

def dfs(V, E)
	for v in V:
		visited v = false
	for v in V:
		if not visited(v):
			explore(v)
```

We can identify connected components with the following previsit

```py
def explore(V, E, v):
	...
	id += 1
	
def previsit(v):
	component_id[v] = id

def dfs(V, E):
	id = 0
	...
```

### Topological Ordering
```py
def previsit(v):
	pre[v] = clock
	clock += 1

def postvisit(v):
	post[v] = clock
	clock += 1
```
For a DAG, vertices with descending postvisit orderings will be sorted in topological order. We have the following types of edges $(u,v)$

- *tree edge* - an edge used in the DFS forest
- *forward edge* - node to nonchild descendant $\underset{u}{[}\ \underset{v}{[}\ \underset{v}{]}\ \underset{u}{]}$
- *back edge* - lead to ancestor node $\underset{v}{[}\ \underset{u}{[}\ \underset{u}{]}\ \underset{v}{]}$
- *cross edge* - lead to postvisited node $\underset{v}{[}\ \underset{v}{]}\ \underset{u}{[}\ \underset{u}{]}$

### Strongly Connected Components (Kosaraju's)
Let $G=(V,E)$ be a DAG, and define a relation where $u\sim v$ if there is a path from $u$ to $v$ and vice versa. This relation partitions $V$ into <u>strongly connected components</u>. To compute the strongly connected components of a graph, we can run <u>Kosaraju's algorithm</u>. This algorithm runs in linear time; $O(|V|+|E|)$

1. Run DFS on $G^R$ (the reverse graph)
2. Run the connected components algorithm, exploring vertices in topological order from the previous DFS.

### BFS
Input: Graph $G=(V,E)$; vertex $s\in V$
Output: For $u$ reachable from $s$, $\text{dist}(u)$ is the distance $s\rightarrow u$
Runtime: $O(|V|+|E|)$

```py
def bfs(V, E, s):
	for u in V:
		dist(u) = inf
	dist(s) = 0
	q = [s]
	while not len(q) == 0:
		u = q.pop()
		for edges (u,v) in E:
			if dist(v) = inf:
				q.append(v)
				dist(v) = dist(u) + 1
```

### Dijkstra's Algorithm
Input: Graph $G=(V,E)$, directed or undirected; positive edge lengths $\{l_e:e\in E\}$; vertex $s\in V$
Output: For all vertices $u$ reachable from $s$, $\text{dist}(u)$ is shortest distance $s\rightarrow u$
Runtime:

| impl           | deletemin                             | io key                                | runtime                                                                |
| -------------- | ------------------------------------- | ------------------------------------- | ---------------------------------------------------------------------- |
| Array          | $O(\vert V\vert)$                     | $O(1)$                                | $O(\vert V\vert^2)$                                                    |
| Binary Heap    | $O(\log\vert V\vert)$                 | $O(\log\vert V\vert)$                 | $O((\vert V\vert+\vert E\vert)\log\vert V\vert)$                       |
| $d$-ary Heap   | $O(\frac{d\log\vert V\vert}{\log d})$ | $O(\frac{\log\vert V\vert)}{\log d})$ | $O((\vert V\vert\cdot d+\vert E\vert)\frac{\log\vert V\vert}{\log d})$ |
| Fibonacci Heap | $O(\log\vert V\vert)$                 | $O(1)$ amortized                      | $O(\vert V\vert\log\vert V\vert+\vert E\vert)$                         |


Operations:
- *Insert* Add element to set
- *Decrease-key* Accommodate the decrease in key value of a particular element
- *Delete-min* Return element with least key and remove from set
- *Make-queue* Build pqueue out of given elements, with given key values.

```py
def dijkstra(V, E, l, s):
	for u in V:
		dist(u) = inf
		prev(u) = None
	dist(s) = 0
	H = makequeue(V)
	while H is not empty:
		u = deletemin(H)
		for all edges (u,v) in E:
			if dist(v) > dist(u) + l(u,v):
				dist(v) = dist(u) + l(u,v)
				prev(v) = u
				decreasekey(H, v)
```

Alternate Implementation
```py
R = {}
while R != V
	pick node v not in R with smallest dist
	add v to R
	for all edges (v,z) in E:
		if dist(z) > dist(v) + l(v,z):
			dist(z) = dist(v) + l(v,z)
```

### Bellman-Ford
Input: Directed graph $G=(V,E)$; edge lengths $\{l_e:e\in E\}$ with no negative cycles; vertex $s\in V$
Output: For all $u$ reachable from $s$, $\text{dist}(u)$ is minimum distance from $s\rightarrow u$
Runtime: $O(|V|\cdot|E|)$

If another iteration yields updates to the distances, there is a negative cycle.

```py
def bellman_ford(V, E, l, s):
	for u in V:
		dist(u) = inf
		prev(u) = None
	dist(s) = 0

	for i in range(0, |V| - 1):
		for (u,v) in E:
			dist(v) = min(dist(v), dist(u), l(u,v))	
```

### Cut Property
Suppose edges $X$ are part of a minimum spanning tree of $G=(V,E)$. For any subset of nodes $S$ where $X$ does not cross $S$ and $V-S$, let $e$ be the lightest edge across the partition. Then $X\cap\{e\}$ is part of some MST.

### Kruskal's Algorithm
Input: A connected undirected graph $G=(V,E)$ with edge weights $w_e$
Output: A minimum spanning tree defined by edges $X$
Runtime: $O(|E|\log|V|)$

```py
def makeset(x)
	p[x] = x
	rank[x] = 0

def find(x)
	while x != p[x]:
		x = p[x]

def union(x, y):
	rx = find(x)
	ry = find(y)
	if rx == ry: return
	if rank[rx] > rank[ry]:
		p[ry] = p[rx]
	else:
		p[rx] = p[ry]
		if rank[rx] == rank[ry]:
			rank[ry] = rank[ry] + 1

def kruskal(V, E, w):
	for u in V:
		makeset(u)
	X = {}
	sort E by weight
	for (u,v) in E:
		if find(u) != find (v):
			add edge (u,v) to X
			union(u,v)
```

### Prim's Algorithm
Input: A connected undirected graph $G=(V,E)$ with edge weights $w_e$
Output: A minimum spanning tree defined by the array prev
Runtime: $O(|E|\log|V|)$

```py
def prim(V, E, w):
	for u in V:
		cost[u] = inf
		prev[u] = None
	cost[V[0]] = 0
	
	H = makequeue(V)
	while not H is empty:
		v = deletemin(H)
		for {v,z} in E:
			if cost[z] > w(v,z):
				cost[z] = w(v,z)
				prev(z) = v
				decreasekey(H, z)
```

## Greedy
### Huffman Encoding
Input: An array $f[1\cdots n]$ of frequencies
Output: An encoding tree with $n$ leaves
Runtime: $O(n\log n)$

Intuitively, this algorithm merges the smallest 2 nodes at each step, so that the largest nodes are at the top of the tree. This means that the most common occurrences are assigned the shortest character.

```py
def huffman(f):
	H = pqueue of integers, ordered by f
	for i in range(0, n): insert(H, i)
	for k in range(n, 2n):
		i = deletemin(H), j = deletemin(H)
		create node k with children i, j
		f[k] = f[i] + f[j]
		insert(H, k)
```

### Horn Formula
A Horn Formula is comprised of the two types of components
- *implications* conjunction of positive literals implying positive literal $(v\land w)\Rightarrow u$
- *negative clause* disjunction of negative literals $(\bar u\lor\bar v\lor\bar y)$

Input: Horn Formula
Output: a satisfying assignment, if one exists

```
set all variables false
while there is unsatisfied implication:
	set RHS variable to be true
	
if all pure negative clauses satisfied: return assignment
else: return 'formula unsatisfiable'
```

### Set Cover
Input: A set of elements $B$; sets $S_1,\ldots,S_m\subseteq B$
Output: A selection of $S_i$ whose union is $B$
Cost: Number of sets picked

A greedy algorithm would continuously pick the set containing the largest amount of uncovered elements. This will always perform at most $\ln n$ times as worse as the optimal solution, where $|B|=n$.

## Dynamic Programming
### Longest Increasing Subsequence
<u>Problem</u> We have an array of numbers $(a_1,\ldots a_n)$. We want to find the longest increasing subsequence $(a_{n_1},\ldots,a_{n_k})$ such that $a_{n_i}<a_{n_{i+1}}$.

<u>Solution</u> Compute the following recursive relation. Runs in $O(n^2)$

$$
f(n)=\text{max length LIS of }(a_1,\ldots,a_n)
$$
$$
f(n)=\max\{f(a_k)+1\big|k<n,a_k<a_n\}
$$

### Edit Distance
<u>Problem</u> Given two strings $x[1\cdots n]$ and $y[1\cdots m]$, what are the minimum number of substitutions, deletions, and insertions needed to turn $x$ to $y$.

<u>Solution</u> Define $E(i,j)$ as the edit distance of $x[1\cdots i]$ to $y[1\cdots j]$. We want to compute $E(n,m)$. Runs in $O(mn)$

$$
E(i,j)=\min\cases{1+E(i-1,j)\\1+E(i,j-1)\\\mathrm{diff}(i,j)+E(i-1,j-1)}
$$
$$
\mathrm{diff}(i,j)=\cases{0&x[i]=y[j]\\1&x[i]\ne y[j]}
$$

### Knapsack
<u>Problem</u> Given a set of items $K=((w_0,v_0)\ldots,w(w_n,v_n))\subseteq\wp(\mathbb R\times\mathbb R)$, we want to pick up items $(w_i,v_i)\in K$, where $w$ is the weight of the item and $v$ is the value of the item. We can only carry $W$ weight, and we want to maximize the value of the items we pick up.

<u>Solution</u> Compute the following recursive relation. Runs in $O(W\times |K|)$

$$K(w)=\text{max value with knapsack of capacity }w$$
$$K(w)=\max\{K(w-w_i)+v_i\big|w_i\le w\}$$

#### Without Repetition
Now we only allow at most 1 copy of each item in the knapsack. Let $0\le j\le n$. Compute the following recursive relation.

$$
K(w,j)=\cases{
K(w,j-1)&\mathrm{if}\ w_j>w\\
\max\{K(w,j-1),K(w-w_j,j-1)+v_j&\mathrm{otherwise}}
$$