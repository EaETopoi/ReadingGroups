---
date: 2024-05-22T22:45:00
tags:
  - AlgebraicGeometry
  - Sheaves
  - TextbookNotes
type: Notes
summary:
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

These notes are designed as an introduction to the theory of quasicoherent and coherent sheaves, following Vakil's[^1] book closely, and including solutions to a number of exercises found therein. The theory of quasicoherent and coherent sheaves can be largely motivated as an algebraic generalization of the theory of vector bundles which appear prominently in fields such as manifold theory and K-theory. 

Recall that a vector bundle $V$ on a geometric space $X$, in some geometric category $\mathcal{G}$, is an object of the category together with a morphism $p:V\to X$, the bundle morphism, such that every point $x$ of $X$ has an open neighborhood $U$ witnessing a **local trivialization**. This means that there exists an isomorphism $p^{-1}(U)\cong U\times V_U$ for a vector space object $V_U$ which is compatible with the bundle morphism, where the right bundle morphism is given by projection. Further, at each point of $U$ this isomorphism restricts to an isomorphism of vector spaces.

Historically important examples of vector bundles that come to mind are the tangent bundle $TM$, cotangent bundle $T^*M$, tensor bundles $TM^{\otimes p}\otimes T^*M^{\otimes q}$, and Mobius strip over a circle. All of these bundles so far are very geometric in flavour and structure, so a main question that arises is how we talk about them in the language of sheaf theory? Well any vector bundle has a natural sheaf in terms of the sheaf of sections of the bundle morphisms, which naturally encodes the local triviality condition as a condition of being a **locally free sheaf**. Here a **locally free sheaf** on a ringed space $(X,\mathcal{O}_X)$ is an $\mathcal{O}_X$-module that is locally isomorphic to a free sheaf (i.e. one of the form $\mathcal{O}_X^{\oplus I}$). As we will discuss below this isn't quite the right setting for algebraic geometry, as it doesn't give a convenient abelian category where we can do homological algebra. However, we will construct the theory of quasicoherent sheaves which contains that of locally free sheaves, and hence vector bundles, as a sub-theory while also forming an abelian category.

## Vector Bundles as Sheaves

Recall that for a manifold $M$, a **rank $n$ vector bundle** on $M$ is a manifold $V$ together with a bundle map $\pi:V\to M$ such that $\pi^{-1}(\{x\})$ has the structure of an $n$-dimensional real vector space for each $x \in M$, and for each $x \in M$ we have an open neighborhood and an isomorphism $\phi:U\times \mathbb{R}^n\to \pi^{-1}(U)$ in the slice category over $U$ (i.e. the triangle below commutes):
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cpi%5E%7B-1%7D(U)%7D%20%26%26%20%7BU%5Ctimes%20%5Cmathbb%7BR%7D%5En%7D%20%5C%5C%0A%09%26%20U%0A%09%5Carrow%5B%22%5Ccong%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%5Cpi%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Cpi_1%7D%22%2C%20from%3D1-3%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\pi^{-1}(U)} &amp;&amp; {U\times \mathbb{R}^n} \\
	&amp; U
	\arrow[&quot;\cong&quot;, from=1-1, to=1-3]
	\arrow[&quot;\pi&quot;', from=1-1, to=2-2]
	\arrow[&quot;{\pi_1}&quot;, from=1-3, to=2-2]
\end{tikzcd}
" /></p>
where when restricted to fibers $\phi$ gives an linear isomorphism of $\mathbb{R}$-vector spaces. When $n = 1$ we say that the vector bundle is a **line bundle**. In some cases vector bundles are allowed to have non-uniform ranks on different connected components of the space, and also have infinite-rank.

Note that if $(V,\pi)$ is a vector bundle over a manifold $M$, then for trivializations $(U_1,\phi_1)$ and $(U_2,\phi_2)$, the map $$\phi_2\vert_{\pi^{-1}(U_1\cap U_2)}\circ \phi_1^{-1}\vert_{\phi_1(\pi^{-1}(U_1\cap U_2))}:U\times \mathbb{R}^n \to U\times \mathbb{R}^n$$
induces a family of invertible transformation $T_{12}:U_1\cap U_2\to \text{GL}(n,\mathbb{R})$ in the category. In general, if $\{U_i\}_{i \in I}$ is a cover of $M$ by trivializations, the induced $\{T_{ij}\}_{i,j \in I}$ satisfy what we call a **1-cocycle condition**
$$T_{ik}\vert_{U_i\cap U_j\cap U_k} = T_{jk}\vert_{U_i\cap U_j\cap U_k}\circ T_{ij}\vert_{U_i\cap U_j\cap U_k}$$
Indeed, recall that in singular chains on a space $X$, our boundary map $\partial_n:\text{Sing}_n(X)\to \text{Sing}_{n-1}(X)$ is given on a generator $\sigma:\Delta^n\to X$ by
$$\partial_n(\sigma) = \sum_{i=0}^n(-1)^i\sigma\vert_{[v_0,\dots,\hat{v}_i, \dots,v_n]}$$
Dualizing to the perspective of singular cochains, $d^n:\text{Sing}^{n-1}(X;G)\to \text{Sing}^n(X;G)$ is given at $\tau:\text{Sing}_{n-1}(X)\to G$ and $\sigma :\Delta^n\to G$ by
$$d^n(\tau)(\sigma) = \sum_{i=0}^n(-1)^i\tau(\sigma\vert_{[v_0,\dots,\hat{v}_i, \dots,v_n]})$$
and in the case of $n = 2$ this gives 
$$d^2(\tau)(\sigma) = \tau(\sigma\vert_{[v_1,v_2]})-\tau(\sigma\vert_{[v_0,v_2]})+\tau(\sigma\vert_{[v_0,v_1]})$$
which is $0$ (i.e. $\tau$ is a 1-cocycle) if and only if $\tau$ satisfies the $1$-cocycle condition


### Sheaf of Sections

We now move to interpreting our above definition in the context of sheaves. If $(V,\pi)$ is a rank $n$-vector bundle over a manifold $M$, we naturally have the sheaf of sections $\mathscr{F}$ of $V$ which is in fact an $\mathcal{O}_M$-module using the $\mathbb{R}$-vector space structure of each fiber.

Further, if $(U,\phi)$ is a trivialization of the vector bundle, note that the sheaf of sections for the bundle $U\times \mathbb{R}^n\to U$ consists of $n$-tuples of smooth functions $f:U\to \mathbb{R}$, which are sections of the $\mathcal{O}_M$ sheaf at $U$. In particular, its sheaf of sections is isomorphic to the free sheaf $\mathcal{O}_M\vert_U^{\oplus n}$. Thus, since the trivialization gives an isomorphism of $\mathscr{F}\vert_U$ with the sheaf of sections for this bundle we have that the trivializations correspond to the statement that the sheaf of sections is a **locally free sheaf of rank $n$**. 

Now, if $(U_1,\phi_1)$ and $(U_2,\phi_2)$ are two trivializations of the bundle, with transition function $T_{12}$, then we have the chain of isomorphisms $\mathcal{O}_M\vert_{U_1\cap U_2}^{\oplus n}\cong \mathcal{F}\vert_{U_1\cap U_2}\cong \mathcal{O}_M\vert_{U_1\cap U_2}^{\oplus n}$, where on a section $s$ of $\mathcal{F}\vert_{U_1\cap U_2}$ at $V \subseteq U_1\cap U_2$, with images $\vec{s}^1:U\to \mathbb{R}^n$ and $\vec{s}^2:U\to \mathbb{R}^n$, respectively, the sequence of isomorphisms takes
$$\vec{s}^1\mapsto \phi_1^{-1}\circ \vec{s}^1=s\mapsto \phi_2\circ \phi_1^{-1}\circ \vec{s}^1=\vec{s}^2$$
where the left-hand side of the last equality is exactly $T_{12}\vec{s}^1$.


**Note:** In the literature rank 1 locally free sheaves, or in other words line bundles, are often called **invertible sheaves**. This comes from the fact that if $X$ is a locally ringed space and $\mathcal{F}$ and $\mathcal{G}$ are $\mathcal{O}_X$-modules with $\mathcal{F}\otimes_{\mathcal{O}_X}\mathcal{G}\cong \mathcal{O}_X$, then we say $\mathcal{F}$ and $\mathcal{G}$ are invertible sheaves.


The above discussion can be carried wholesale to the context of ringed spaces and locally free sheaves on them. Again sometimes we allow the rank of a locally free sheaf to vary across connected components or even be infinite.
#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024
