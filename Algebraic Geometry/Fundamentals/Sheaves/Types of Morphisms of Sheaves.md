---
date: 2024-05-24T07:39:00
tags:
  - AlgebraicGeometry
  - Sheaves
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

In this note we collect a variety of basic information with respect to types of morphisms of sheaves and their properties. The majority of results and points follow those in Vakil[^1]. We will begin by recalling the structure of monomorphisms and epimorphisms in $\mathsf{Sh}(X)$ and how stalks can be used to determine them.

## Sheaves 

### Epis and Monos of Sheaves

First, recall that we have the adjunction
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D(X)%7D%20%26%20%7B%5Cmathsf%7BPs%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-2%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ciota%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Sh}(X)} &amp; {\mathsf{Ps}(X)}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathfrak{a}}&quot;', bend right = 30, from=1-2, to=1-1]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\iota}&quot;', bend right = 30, from=1-1, to=1-2]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]
\end{tikzcd}
" /></p>
so in particular limits in $\mathsf{Sh}(X)$ are computed termwise, and hence monomorphisms are exactly those maps of sheaves which are monomorphisms on all open sets (i.e. **monomorphisms are determined open-set by open-set**). On the other hand, a map of sheaves $f:\mathcal{F}\to \mathcal{G}$ being epi implies that for every point of $x$ the map on stalks $\mathcal{F}_x\to \mathcal{G}_x$ is epi using the adjunction
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSet%7D%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bx_*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B(-)_x%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Set}} &amp;&amp; {\mathsf{Sh}(X)}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{x_*}&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{(-)_x}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>
On the other hand, suppose that all of the stalks are epi and let $h,k:\mathcal{G}\to \mathcal{H}$ be maps of sheaves such that $h\circ f = k\circ f$. Then it follows that $h_x\circ f_x = k_x\circ f_x$ and so $h_x = k_x$ for every point $x \in X$. But $\mathcal{H}$ is a sheaf, so a map into $\mathcal{H}$ is completely determined by its action on stalks. Thus, $h = k$. Therefore, although epimorphisms of sheaves need not be epimorphisms of pre-sheaves, we can **detect epimorphisms stalk by stalk**.

>[!def] Quotient Sheaf
>If $\mathcal{F}\to \mathcal{G}$ is an epimorphism of sheaves we say that $\mathcal{G}$ is a **quotient sheaf** of $\mathcal{F}$.






#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024
