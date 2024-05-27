---
date: 2024-05-24T18:26:00
tags:
  - AlgebraicGeometry
  - EtaleCohomology
  - ReadingGroup
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

These notes are from the second lecture for the Summer 2024 Etale Cohomology Reading group at UIUC, offered by Haoran who discussed the Etale topology and Etale morphisms. The focus will be on definitions, properties, and examples of Etale morphisms of schemes.

Recall that a flat morphism are the algebraic analogue of a map with uniform dimension of their fibers (this is the case in the complex topology for complex varieties).

## Etale Morphisms

>[!def] Etale Morphisms
>A morphism of schemes $f:X\to Y$ is said to be **etale** if it is flat and unramified.

Intuitively, the statement that a morphism $f:X\to Y$ is etale is the statement that $Y$ can be defined locally by an equation of the form
$$T^m+a_1T^{m-1}+\cdots + a_m = 0$$
for functions $a_1,...,a_m$ on an open subset $U$ of $X$, and all roots over a the $a_i$ are simple. We begin by recalling the notion of unramified morphisms.

>[!def] Unramified Morphisms
>Let $f:X\to Y$ be a morphism of schemes. $f$ is said to be unramified if
>1. $f$ is locally of finite type
>2. Maps of residue fields yield finite separable extensions
>3. If $x \in X$, then the induced map on stalks $f_x^\#:\mathcal{O}_{Y,f(x)}\to \mathcal{O}_{X,x}$ sends the maximal ideal $\mathfrak{m}_{Y,f(x)}$ to $$f_x^\#(\mathfrak{m}_{Y,f(x)})\mathcal{O}_{X,x} = \mathfrak{m}_{X,x}$$

For our current work it would be useful to recall the notion of a closed immersion as well.

>[!def] Closed Immersion
>Let $\mathcal{I} \leq \mathcal{O}_X$ be a **coherent ideal sheaf** in the structure sheaf of a scheme $X$ corresponding to a map $i:Y\to X$. $i$ is called a **nilpotent immersion** if $i$ is a homeomorphism.
>
>We call $i$ a **thickening** if $\mathcal{I}$ is **locally nilpotent** (i.e. there exists an open covering of $X$, $\{U_i\}_{i \in I}$, such that for all $i$, there exists an $n_0 \in \N$ such that $(\mathcal{I}\vert_{U_i})^{n_0} = 0$). The order of $\mathcal{I}$ is the least $n \in \mathbb{N}$ such that $\mathcal{I}^{n+1} = 0$.
>

>[!def] Formally Unramified
>A map **TBD**


If $R$ is a ring, and $A$ is an $R$-algebra, we say $A$ is formally unramified if the map of affine schemes $\mathsf{Spec}(A)\to \mathsf{Spec}(R)$ is.


>[!def] Unramified Map of Local Rings
>A map of local rings $f:A\to B$ is **unramified** if $f(\mathfrak{m}_A)B = \mathfrak{m}_B$ and $\kappa(B)$ is a finite separable extension of $\kappa(A)$.

>[!def] Unramified 2
>A map of schemes $f:X\to S$ is **unramified** if and only if it is formally unramified and locally of finite type. We say $f$ is formally unramified if and only if for every $x \in X$, their exists an open affine neighborhood $U$ of $x$ such that the restriction $f\vert_U$ is formally unramified.


>[!example]
>Let $L/K$ be an extension of number fields with ring of integers $\mathcal{O}_L$ and $\mathcal{O}_K$. To check that $\mathcal{O}_K\hookrightarrow \mathcal{O}_L$ is unramified we must check two things. 
>- First, for every $\mathfrak{q} \in \mathsf{Spec}(\mathcal{O}_L)$ we must check that for $\mathfrak{p} = \mathfrak{q}\cap \mathcal{O}_K$, the extension $\kappa(\mathfrak{q})/\kappa(\mathfrak{p})$ is finite and separable.
>- The second thing we must check is that $\mathfrak{p}\mathcal{O}_L = \mathfrak{q}$.


>[!remark]
>The notions "formally unramified" and locally of finite type implies that 
>1. Every immersion is unramified
>2. Unramified is stable under base-change


>[!proposition]
>Let $k$ be a field and let $f:X\to \mathsf{Spec}(k)$ be a map of finite type. Then the following are equivalent
>- $f$ is unramified
>- The $k$-scheme $X$ is isomorphic to $\coprod_{i \in I}\mathsf{Spec}(k_i)$ for some finite separable field extension $k_i$ of $k$
>- There exists an algebraically close extension $K$ of $k$ such that the $K$ scheme $X\otimes_kK$ is isomorphic to $\coprod_{j \in J}\mathsf{Spec}(K)$ 
>- $X$ is a geometrically reduced $k$-scheme and $\dim(X) = 0$


>[!proposition]
>A map of schemes $f:X\to S$, locally of finite type, such that for $x \in X$ and $s \in f(x)$, we have that derived sheaves -- Read book


## To Review for Next Time

The following are a list of items in order of importance which require further reading and investigation before the next meeting:
- [ ] Standard Etale Algebra
- [ ] Differentials Sheaf/Kahler Differentials
- [ ] Formally Etale
- [ ] Formally Unramified
- [ ] Formally Smooth
- [ ] Relative dimension
- [ ] Smooth

#### References