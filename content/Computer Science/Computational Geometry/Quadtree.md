Source: [[10.5555 2031416|Geometric Approximation Algorithms]]

A <u>quadtree</u> is a decomposition of some bounded region of $\mathbb R^d$ into hypercubes.

## Construction

Let $P\subseteq\mathbb [0,1]^d$, and let the root node correspond to the hypercube $[0,1]^d$. The children of this node are defined to be $2^d$ partitioning hypercubes with half edge length. To actually construct the tree, start with the root node, and continuously expand into child nodes until the leaf nodes are empty or only contain $1$ point.

## Path Compression

If two points are very close to each other, the naive construction can have arbitrarily long empty paths. This can be alleviated by "compressing" these empty levels into a single node. <u>It is possible to compute this in $O(n\log n)$ time</u>