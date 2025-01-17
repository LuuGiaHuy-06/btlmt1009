# Euclidean Shortest Paths in the Presence of Rectilinear Barriers

## Abstract

Euclidean shortest path (ESP) between two specified points (source, destination) in the plane avoids a given set of barriers.

Before: polygonal obstacles with the aid of the visibility graph **$\Omega(n^2)$**

Goal:
-   Path must lie within $n$*-vertex simple polygon*
-   Obstacles are $n$ *disjoint and parallel* line segments.

Greedy: $O(n \log n)$ time algorithms

## Introduction
Graph $G=(V,E)$, source = $s$, destination = $t$

with Dijkstra: $O(|V|^2)$

*Visibility graph*:
-   Nodes are the vertices of the polyhedral obstacles
-   Edges are the segments joining two nodes without intersecting the interior of any obstacle

This paper: two cases in which the obstacles are $n$ line segments:
-   P1. The given line segments form a simple polygon, to which $s$ and $t$ are internal.
-   P2. The given line segments are disjoint and parallel. 

## Shortest paths within a polygon

**Definition 1**: no two nonconsecutive segments intersect.

**Definition 2**: $n$*-vertex simple polygon $P=(q_1, q_2, ..., q_n)$
1. $\bar{q_{i} q_{j}}, j \neq i + 1$ do not cross any edge of P.
2. P is triangulated if its interior has been partitioned into $n - 2$ triangles by $n - 3$ diagonals. (?)

**Definition 3**: The dual tree of a triangulated simple polygon $P$ is a graph $T = (V,E)$
1. each triangle in $P \Leftrightarrow$ one node of $V$ corresponds.
2. two triangles share a segment in $P \Leftrightarrow$ one edge of $E$ connects two nodes of $V$ (The diagonal of $P$ and the corresponding edge in $T$ are said to be *dual*).

Note that the triangulation of $P$ is entirely arbitrary; one suitable triangulation may be obtained-for example-in time $O(n \log n)$ using the algorithm of 5(ref).

### Method
Let $\delta s$ and $\delta t$ be the two triangles in (the triangulated) $P$ which contain $s$ and $t$ , respectively.
In $T$ there is a unique path $\pi$ are the duals of $\delta s$ and $\delta t$. 
Since each diagonal divides $P$ into two parts, which respectively contain $s$ and $t$, the shortest path from $s$ to $t$ *exactly once*.

This observation and a known property 9 of the visibility graph provide the basis for an efficient algorithm. This property is expressed by the following *lemma*.

#### Lemma 1
Let $S$ be the set of endpoints of the rectilinear barriers. The vertices of the shortest path between $s$ and $t$ belong to the set $S \cup${ $s,t$ }.

Indeed, since each path from the root $s$ crosses a diagonal exactly once $\Rightarrow$ “greedy” algorithm.

Addition, $P$ restrict to $P'$ which dualizes to $\pi$ called a "sleeve":

**Definition 4**: A triangulated polygon is called a *sleeve* if its dual tree is a chain.

In what follows we assume that the given polygon $P$ is a sleeve with $n$ vertices, including $s$ and $t$.

Let $v_{i}^{(1)}$, $v_{i}^{(2)}$ be the two extreme points of diagonal $d_i, 1 < i < n - 3$

Let $D(s, v_{i}^{(j)})$ be the shortest path from $s$ to $v_{i}^{(j)}$, $j = 1,2$.

Let $D_i = D(s, v_{i}^{(1)}) \cup (s, v_{i}^{(2)})$

$D_i$ has a unique vertex $v$ which is common to both $D(s, v_{i}^{(1)})$ and $(s, v_{i}^{(2)})$ and is furthest from $s$ on either chain.

*Assume at first that neither of the latter subchains is empty*; then we claim that $D(v, v_{i}^{(j)} ) ( j = 1,2)$ is an *inward-convex* polygonal chain;

Can proves that $D(s, v_{i}^{(j)} ) ( j = 1,2)$ may diverge at most at one vertex $v$.

$D_i$ is a chain branching at some vertex $v$, called a cusp into two inward-convex chains.

Note that either of these two chains could be empty (but not both)
