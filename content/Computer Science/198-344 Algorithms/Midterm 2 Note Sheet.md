---
date: 2024-11-09
---

A graph is a set of <u>vertices</u> and <u>edges</u>. A graph is <u>connected</u> if there are paths between each node.

<u>DFS</u> Traverse a graph starting from given node. When visiting a node, set the previsit to the counter. When leaving a node (all children have been exhausted) set postvisit to the counter.

These numberings create different types of edges $u\rightarrow v$
- <u>tree</u> an edge used in the dfs forest
- <u>forward</u> $[_u\quad[_v\quad]_v\quad]_u$
- <u>back</u> $\ \ \ \quad [_v\quad[_u\quad]_u\quad]_v$
- <u>cross</u> $\quad [_v\quad]_v\quad[_u\quad]_u$

Ordering the nodes by decreasing post-visit time gives you a topological sorted array of vertices.

A set of nodes in a DAG is <u>strongly-connected</u> if every node has a path to the other nodes.

<u>Kosaraju's Algorithm</u> Run DFS on the reverse graph and record postvisit. Then run DFS on original graph with decreasing postvisit order nodes. Each collection of visitable nodes is an SCC.

<u>BFS</u>
```python
for all u in V
	dist(u) = infinity

dist(s) = 0
Q = [s] (queue containing just s)
while Q is not empty:
	u = eject(Q)
	for all edges (u,v) in E
		if dist(v) = infinity:
			inject(Q, v)
			dist(v) = dist(u) + 1
```

<u>Djikstras</u>
Operations:
- *Insert* Add element to set
- *Decrease-key* Accommodate the decrease in key value of a particular element
- *Delete-min* Return element with least key and remove from set
- *Make-queue* Build pqueue out of given elements, with given key values.
```python
for all u in V:
	dist(u) = infinity
	prev(u) = null
dist(s) = 0

H = makequeue(V) (using dist-values as keys)
while H is not empty:
	u = deletemin(H)
	for all edges (u,v) in E:
		if dist(v) > dist(u) + l(u,v):
			dist(v) = dist(u) + l(u,v)
			prev(v) = u
			decreasekey(H, v)
```

alternate
```python
R = {}
while R != V
	pick node v not in R with smallest dist
	add v to R
	for all edges (v,z) in E:
		if dist(z) > dist(v) + l(v,z):
			dist(z) = dist(v) + l(v,z)
```

When implemented with Fibonacci heap, gives $O(|V|\log|V|+|E|)$ time complexity

<u>Bellman-Ford</u>
```python
for all u in V:
	dist(u) = infinity
	prev(u) = null

dist(s) = 0
repeat |V|-1 times:
	for all e in E
		update(e)
```

Kruskal - UF
```python
for all u in V:
	makeset(u)

X = {}
Sort the edges E by weight
for all edges {u,v} in E, in increasing order of weight:
	if find(u) != find(v):
		add edge {u,v} to X
		union(u,v)
```

Prim - BFS
```python
for all u in V:
	cost(u) = infinity
	prev(u) = null
pick any initial node u_0
cost(u_0) = 0

H = makequeue(V)    (priority queue, using cost-values as keys)
while H is not empty:
	v = deletemin(H)
	for each {v,z} in E:
		if cost(z) > w(v,z):
			cost(z) = w(v,z)
			prev(z) = v
			decreasekey(H,z)
```