---
date: 2024-05-14T09:30:00
tags:
  - 2Segal
  - Homotopy
  - Minicourse
  - Simplicial
type: Notes
summary: Notes on 1-Segal and 2-Segal sets with examples from a mini-course offered by Julie Bergner
---
```table-of-contents
title: 
style: nestedList # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
minLevel: 0 # Include headings from the specified level
maxLevel: 0 # Include headings up to the specified level
includeLinks: true # Make headings clickable
debugInConsole: false # Print debug info in Obsidian console
```
## Introduction 

These notes are from a mini-course offered online by Julie Bergner on 1-Segal and 2-Segal objects and their applications in Homotopy theory. 

1-Segal objects should behave much like categories. Heuristically, 1-Segal sets have a collection of objects and morphisms between objects, and has a unique composition for composable pairs which is associative.

On the other hand, 2-Segal sets has a weaker structure. In particular, composition may not exist, or if it exists may not be unique, but it is still "associative" in a suitable sense.

Goal first day: Introduce and define 1-Segal and 2-Segal sets/[[2-Segal Spaces|spaces]] in a rigorous way, and give several examples

## Simplicial Objects

>[!def] Simplicial Category
>The category $\Delta$, or simplicial category, has as objects finite ordered sets $[n] = \{0 \leq 1 \leq \cdots \leq n\}$ for $n \geq 0$ an integer, with morphisms order-preserving maps. The category $\Delta$ has a strong factorization system in terms of injective and surjective maps. In particular, we can factorize maps uniquely as a composite of face maps and degeneracy maps.

Explicitly, here the face maps are the unique injective maps $d_i^n:[n-1]\to [n]$ for $0 \leq i \leq n$ given by skipping the $i$th term, while the degeneracy maps are the unique surjective maps $s_i^n:[n+1]\to [n]$ for $0 \leq i \leq n$ given by doubling up at $i$.

The simplicial category while useful is most useful when looked at through the perspective of pre-sheaves.

>[!def] Simplicial Sets
>A **simplicial set** is a functor $K:\Delta^{op}\to \mathbf{Sets}$. We write $K_n := K([n])$, and call $K_n$ the set of $n$-simplices. The image of $d_i^n:[n-1]\to [n]$ under $K$ are called **face maps** while the image of $s_i^n:[n+1]\to [n]$ under $K$ are called **degeneracy maps**.

Simplicial sets can be geometrically realized to topological spaces via a functor 

$$
\begin{equation}
|\cdot|:\mathbb{Sets}^{\Delta^{op}}\to\mathbb{Top}
\end{equation}
$$

^ea5da5
which can be realized as the left-Kan extension of the functor from $\Delta\to \mathbb{Top}$ given by sending $[n]$ to the topological $n$-simplex $\Delta^n$.

>[!example]
>Let $G$ be a group. Its **nerve** is the simplicial object $\mathcal{G}:\Delta^{op}\to \mathbb{Sets}$ given by $\mathcal{G}_n = G^n$, where the face maps $\mathcal{G}(d_i^n):\mathcal{G}_n\to \mathcal{G}_{n-1}$ are given by multiplication if $0 < i < n$, and projection onto the ends if $i = 0,n$.  The degeneracy maps $\mathcal{G}(s_i^n):\mathcal{G}_n\to \mathcal{G}_{n+1}$ are given by inserting identity elements. The geometric realization, $|N(G)|$ is a model for $\mathbb{B}G$, the **classifying space** of $G$, a $K(G,1)$.

More generally, we can consider a small category $\mathcal{C}$, its nerve being the simplicial set $N(\mathcal{C})$ with $0$-simplexes objects, $1$-simplexes morphisms, and $n$-simplices lists of composable morphisms, with the same face and degeneracy maps.
## 1-Segal and 2-Segal Sets

>[!def] 1-Segal Set
>A **$1$-Segal set** is a simplicial set $K$ such that $K_n\cong K_1\times_{K_0}\cdots \times_{K_0}K_1$ for all $n \geq 2$, which is an $n$-iterated pullback, thought of as collections of $n$-composable morphisms. Explicitly, the pullback diagram is associated with alternating face maps. 

For example, we can consider $\mathcal{G}(n)=\Delta[1]\amalg_{\Delta[0]}\cdots \amalg_{\Delta[0]}\Delta[1]$, which naturally includes into $\Delta[n]$. Contravariance gives a natural map
$$
\mathbf{Hom}_{\mathbf{SSets}}(\Delta[n],K)\to \mathbf{Hom}_{{\mathbf{SSets}}}(\mathcal{G}(n),K)
$$
where by Yoneda the left hand-side is $K_n$, and the right is $K_1\times_{K_0}\cdots \times_{K_0}K_1$. We call these **1-Segal maps**, and a 1-Segal set is precisely a simplicial set where all 1-Segal maps are isomorphisms.

Note, 1-Segal sets correspond to nerves of categories. Indeed all nerves of categories are 1-Segal sets, and we can define a category using $K_1\times_{K_0}K_1\xrightarrow{\cong} K_2 \xrightarrow{d_{1}} K_1$, which can be checked to be associative.


Next, we move to 2-Segal Sets, as introduced by Dyckerhoff and Kapranov. Another perspective is given by discrete decomposition spaces, which were formulated Galvez, Carrillo, Kock, and Tonks.

To begin, we can think of $G(n)$ as "triangulating" a line segment $\bullet\to\bullet\to\cdots\to\bullet$. Now, for 2-Segal sets we are going to move up a dimension and triangulate regular polygons, with **cyclically labeled vertices**. 

>[!example]
>Consider a cyclically labeled square, with edges directed from lower to higher vertices. We can triangulate the square in two ways --- One is by taking an edge from $0$ to $2$ along the diagonal, while the other is given by taking the edge from $1$ to $3$. <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%093%20%26%202%20%26%203%20%26%202%20%5C%5C%200%20%26%201%20%26%200%20%26%201%20%5Carrow%5Bfrom%3D1-2%2C%20to%3D1-1%5D%20%5Carrow%5Bfrom%3D1-4%2C%20to%3D1-3%5D%20%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-1%5D%20%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-2%5D%20%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%20%5Carrow%5Bfrom%3D2-2%2C%20to%3D1-2%5D%20%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-3%5D%20%5Carrow%5Bfrom%3D2-3%2C%20to%3D2-4%5D%20%5Carrow%5Bfrom%3D2-4%2C%20to%3D1-3%5D%20%5Carrow%5Bfrom%3D2-4%2C%20to%3D1-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white] 3 &amp; 2 &amp; 3 &amp; 2 \\ 0 &amp; 1 &amp; 0 &amp; 1 \arrow[from=1-2, to=1-1] \arrow[from=1-4, to=1-3] \arrow[from=2-1, to=1-1] \arrow[from=2-1, to=1-2] \arrow[from=2-1, to=2-2] \arrow[from=2-2, to=1-2] \arrow[from=2-3, to=1-3] \arrow[from=2-3, to=2-4] \arrow[from=2-4, to=1-3] \arrow[from=2-4, to=1-4]\end{tikzcd}" /></p>
>We can think of these triangulations, say $\mathcal{J}_1$ and $\mathcal{J}_2$, as collections of faces on the simplicial set $\Delta[3]$. For a simplicial set $K$, we will obtain maps <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%26%203%20%5C%5C%0A%09%26%26%26%26%202%20%5C%5C%0A%090%20%26%26%26%201%0A%09%5Carrow%5Bfrom%3D2-5%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D2-5%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bfrom%3D3-4%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D3-4%2C%20to%3D2-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]&amp;&amp; 3 \\ &amp;&amp;&amp;&amp; 2 \\0 &amp;&amp;&amp; 1\arrow[from=2-5, to=1-3]\arrow[from=3-1, to=1-3]\arrow[dashed, from=3-1, to=2-5]\arrow[from=3-1, to=3-4]\arrow[from=3-4, to=1-3]\arrow[from=3-4, to=2-5]\end{tikzcd}" /></p>
$$K_2\times_{K_1}K_{2}\cong\mathbf{Hom}(\mathcal{J}_{1},K)\xleftarrow{(d_{1},d_{3})}\mathbf{Hom}(\Delta[3],K)\xrightarrow{(d_{0},d_{2})}\mathbf{Hom}(J_{2},K)\cong K_{2}\times_{K_{1}}K_{2}$$

We now are ready for the definition.

>[!def] 2-Segal Sets
>A **2-Segal set** $K$ is a simplicial set such that for $n \geq 3$ and every triangulation of a cyclically labelled regular $(n+1)$-gon by vertices, then the induced **2-Segal maps** $$K_n\to K_2\times_{K_1}\cdots\times_{K_1}K_2$$ (where there are $n-1$ copies of $K_2$) is an isomorphism. 

What kind of structure does this give? Well, we still have objects $K_0$ and morphisms $K_1$, but we can't do composition $K_1\times_{K_0}K_1\xleftarrow{(d_0,d_2)}K_2\xrightarrow{d_1}K_1$ since we don't immediately have a map $K_1\times_{K_0}K_1\to K_{2}$, as before. Instead we can look at the pre-image of $(d_0,d_2)$, and then take $d_1$ from there. Naturally, this type of definition does not give uniqueness or existence of composites. But, the composite is still associative, as can be seen from the square example, where associativity comes from the unique gluing of the 2-squares into a 3-simplex.

However, so far we have not talked about identity elements. The idea of identity elements is that they should be **degenerate 1-simplices**. The fact that these provide identities was not immediately obvious, so originally Dyckerhoff-Kapranov imposed a "unitality" conditions so identities composed as expected. But, as shown later by Feller, Garner, Kock, Underhill, Proulx, and Weber, All 2-Segal sets are (strictly) unital.

>[!example] Partial Monoids
>Recall a partial monoid $M$ is a set together with $M_2 \subseteq M\times M$, the "domain of multiplication", with a binary operation $\bullet:M_2\to M$ satisfying $(m\bullet m')\bullet m''$ being defined if and only if $m\bullet (m'\bullet m'')$, and they are equal, as well as a unit $1 \in M$, such that $(1,m),(m,1) \in M_2$ for all $m \in M$, and $m\bullet 1 = 1\bullet m = m$.
>
>We can interpret $M$ as a simplicial set, $M$: 
>- $M_0 = \{1\}$
>- $M_1 = M$
>- $M_k \subseteq M^k$, where $(m_1,...,m_k) \in M^k$ if and only if for all $1 \leq i < k$, $(m_1\bullet \cdots \bullet m_i,m_{i+1}) \in M_2$.
>The face maps are given by multiplying adjacent terms, or dropping terms for the outer face maps, and degeneracy maps insert $1$.
>
>We can check whether this is indeed **2-Segal**. Note that for the three simplex $\Delta[3]$, $d_0$ gives the $2$-simplex $[1,2,3]$ while $d_2$ gives $[0,1,3]$, which has the common edge $[1,3]$ given by applying $d_1$ in the first case and $d_0$ in the second. The **2-Segal** condition is that these maps determine the $3$-simplex. (this is just one of the 2-Segal conditions)

^59fe58

>[!example]
>We can consider Cobordism as a 1-Segal set $\mathbb{2Cob}$. We define the simplicial set structure as follows:
>- $(\mathbf{2Cob})_0 = \{\text{closed 1-dimensional manifolds}\}$
>- $(\mathbf{2Cob})_1 = \{\text{Diffeomorphisms classes of 2-dimensional cobordisms } \Sigma\}$
>- $(\mathbf{2Cob})_k = \{$Diffeomorphism classes $\Sigma$, decomposed as a composite of $k$ cobordisms, $\Sigma_1,...,\Sigma_k\}$.
>
>Here composition is always defined. If we impose a genus constraint, say $\leq g$, and get a $2$-Segal set $\mathbf{2Cob}^{\leq g}$. That is, we can not compose cobordisms which would create genus above $g$.

