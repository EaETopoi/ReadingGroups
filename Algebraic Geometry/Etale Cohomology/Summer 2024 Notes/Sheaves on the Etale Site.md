---
date: 2024-06-03T18:40:00
tags:
  - AlgebraicGeometry
  - Sheaves
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

These notes are from a lecture given by Juhan on sheaves on the Etale site during the 2024 summer reading group on etale cohomology at UIUC.

## Sheaves

Recall that we can consider sheaves on a site, as discussed at length in [[Sheaves on Sites]]. The focus of this talk will be three sites with underlying category a full subcategory of the slice category $\mathsf{Sch}/S$, for $S$ a fixed scheme. All three examples will fall in the following class:

>[!scenario] 
>Let $E$ be a class of morphism in the category of schemes, $\mathsf{Sch}$, satisfying the following properties:
>1. $E$ contains all isomorphisms
>2. $E$ is closed under composition
>3. $E$ is closed under base-change
>   
>Then if $S$ is a fixed scheme, the slice category $\mathsf{Sch}/S$ and the full-subcategory $E/S$ (where an object $U\to S$ lives in $E$) have natural Grothendieck topologies given by saying that a sieve $R$ over $U\to S$ is a covering sieve if there exists $\{(U_i\to S)\to (U\to S)\}_{i \in I}$ in $R$ such that each $U_i\to S$ is in $E$ and the image of the $U_i$ cover $U$.

^f8b0cb

We will write $\mathsf{FEt}/S$ to denote the site $E/S$ where $E$ is the class of finite type etale morphisms.

To begin we show that it suffices to check on affine covers for the sheaf condition in the case of many examples.

>[!proposition]
>Let $E$ be a class of morphisms, as in [[Sheaves on the Etale Site#^f8b0cb]], with the added property that open immersions are in $E$. Then if $P:(E/S)^{op}\to \mathsf{Set}$ is a pre-sheaf on the site, it is a sheaf if and only if it satisfies the sheaf condition with respect to affine covers.

`\begin{proof}`
Let $g:U\to S$ be an object in $E/S$ and let $\{h_i:U_i\to S\}_{i \in I}$ be a family in $E/S$ together with maps $g_i:U_i\to U$ in the slice category, so $g\circ g_i = h_i$ and $U = \bigcup_{i \in I}g_i(U_i)$. Since each $U_i$ is a scheme, we can take a cover $U_i = \bigcup_{j \in J}V_{ij}$ for open affines $V_{ij}$ in $U_i$, and the maps $V_{ij}\to U_i\to S$ are in $E$ since $E$ contains open immersions and is closed under composition.

For each $i \in I$ let $s_i \in P(U_i)$ be a section such that for any $i,i' \in I$, $s_i\vert_{U_i\times_SU_{i'}} = s_{i'}\vert_{U_i\times_SU_{i'}}$. Then we have associated sections $t_{ij} \in P(V_{ij})$ for every $i \in I$ and $j \in J$, and further $t_{ij}\vert_{V_{ij}\times_SV_{i'j'}} = t_{i'j'}\vert_{V_{ij}\times_SV_{i'j'}}$. Since $P$ satisfies the sheaf condition with respect to affines it follows that there exists a unique $t \in P(U)$ which agrees on restrictions to the affines. Further, applying the uniqueness on affines at each case we also have that $t\vert_{U_i} = s_i$ for each $i \in I$. Further, any other such amalgamation must agree on restriction to the affines, and hence must equal $t$ by uniqueness.
`\end{proof}`

## Representable Schemes

For $Y \in \mathsf{Sch}/X$ we will write $y^Y := \mathsf{Sch}/X(-,Y)$. We will show that are the site $\mathsf{Sch}/X$ and $E/X$ described previously is sub-canonical, so $y^Y$ is always a sheaf.

>[!proposition]
>Let $Y \in \mathsf{Sch}/X$. Then $y^Y$ is a sheaf on the $E$-site for $\mathsf{Sch}/X$.

`\begin{proof}`
**TBD**
`\end{proof}`


## Inheriting Sheaves and Sheaf Properties

If $X$ is a scheme and $\mathscr{M}$ is a quasi-coherent sheaf over $X$, then we can obtain a sheaf on $\mathsf{Zar}/X$ and $\mathsf{FEt}/X$ given by the pre-sheaf that maps $\pi:U\to X$ to $\Gamma(U,\pi^*\mathscr{M})$. In particular, when $\mathscr{M} = \mathcal{O}_X$ is the structure sheaf for $X$, then this construction gives what we call the structure sheaf on the etale site, $\mathcal{O}_{X_{et}}$.


When dealing with a topological space we can think about stalks for points. However, our space has been replaced with a category, so what do we mean by a point? Well, we will say that a morphism $\gamma:s\to X$ is a **geometric point** if $s = \mathsf{Spec}(k)$ for a field $k$ such that $k^{sep} = k$. Then if $\mathscr{F}$ is a sheaf on the small etale site $\mathsf{FEt}/X$, the stalk of $\mathscr{F}$ at the geometric point $s$ is given by
$$\mathscr{F}_s = \Gamma(s,\gamma^*\mathscr{F}) = \lim\limits_{\to (s\to U)}\mathscr{F}(U)$$
Further, as one would hope, when dealing with pre-sheaves this definition of stalk is preserved by sheafification, which is to say if $\mathscr{G}$ is a pre-sheaf on the small etale site, then
$$(\mathscr{G}^+)_s \cong \mathscr{G}_s$$
Further, as in the topological setting exactness for sequences can be checked at the level of stalks for all geometric points.


## Galois Coverings

Let $f:Y\to X$ be a faithfully flat map of schemes and let $G$ be a finite group with a group homomorphism
$$G^{op}\to \text{Aut}_X(Y)$$
(i.e. a right action by $G$ on $f:Y\to X$). We say that $f$ is a **Galois covering** of $X$ if the map
$$Y\times G = \coprod_{g \in G}Y\to Y\times_XY$$
which on the level of sets is given by $(g,y)\mapsto (y,gy)$, is an isomorphism. This will imply that $f$ is finite, surjective, and etale. Explicitly this map is given by the universal property of the coproduct, where for $g \in G$ we have the map $Y\to Y\times_XY$ induced by the identity and the image of $g$ in $\text{Aut}_X(Y)$.

>[!example]
>Let $K = k[y]/(f)$ where $f$ is a monic irreducible polynomial. Then $$K\otimes_kK \cong K[T]/(f) \cong \prod_{}$$


>[!proposition]
>Let $f:Y\to X$ be a galois covering and let $\mathscr{F}$ be a pre-sheaf on the small etale site over $X$ such that $\mathscr{F}$ preserves products (i.e. sends coproducts to products by contravariance). Then the sequence $$\mathscr{F}(X)\to \mathscr{F}(Y)\rightrightarrows \mathscr{F}(Y\times_XY)\cong \prod_{g \in G}\mathscr{F}(Y)$$
>is exact if and only if $\mathscr{F}(X) \cong \mathscr{F}(Y)^G\hookrightarrow \mathscr{F}(Y)$ is the restriction map.

### To Read

- [ ] Cech-Cohomology and its use in determining the sheaf condition for separated presheaves.

#### References