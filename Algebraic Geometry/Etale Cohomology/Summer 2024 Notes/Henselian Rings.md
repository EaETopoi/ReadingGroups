---
date: 2024-05-27T18:52:00
tags:
  - AlgebraicGeometry
  - CommutativeAlgebra
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

These notes are on the structure of Henselian rings in algebraic geometry from a lecture by Levi in the Summer 2024 Etale Cohomology reading group at UIUC. The slogan is that henselian rings are the local rings for the etale topology.

## Henselian Rings

To set the notation, $(R,\mathfrak{m},k)$ will denote a local ring with residue field $k$, and we will use a bar to denote reduction modulo $\mathfrak{m}$. One of the motivation for henselian rings is **Hensel's lemma**.

>[!theorem] Hensel's Lemma
>Let $R$ be a complete local ring, $f \in R[t]$ a monic polynomial, and a factorization $\overline{f} = g_0h_0$ in $k[t]$, for $g_0$ and $h_0$ monic and relatively prime, then there exists $g,h \in R[t]$ such that $f =gh$ and $\overline{g} = g_0$ and $\overline{h} = h_0$.

^32136a


>[!def] Henselian Local Ring
>A **Henselian (local) ring** is a local ring that satisfies the conclusion of Hensel's lemma.

The $g$ and $h$ in [[Henselian Rings#^32136a]] generate the ring $R[t]$ (this follows by Nakayama's lemma and the fact that $g$ and $h$ are relatively prime modulo $\mathfrak{m}$). In particular, this implies that the factorization in Hensel's lemma is unique (one can show that if $f = gh=g'h'$, then $g\mid g'\mid g$, but both are monic, so $g = g'$).

>[!theorem]
>Let $X = \mathsf{Spec}(R)$, and let $x \in X$ be the unique closed point. Then the following are equivalent:
>1. $R$ is a henselian local ring
>2. Every finite $R$-algebra $S$ is a finite product of local rings
>3. If $f:Y\to X$ is quasi-finite and separable, then $Y = \coprod_{i=0}^nY_i$ where $x \notin f(Y_0)$, and $Y_i = \mathsf{Spec}(S_i)$, where $S_i$ is a local ring finitely generated over $R$.
>4. If $f:Y\to X$ is etale, and $y \in Y$ such that $f(y) = x$,  and the map $k(x)\to k(y)$ is an isomorphism, then $f$ has a section $g$ with $g(x) = y$
>5. If $f_1,...,f_n \in R[t_1,...,t_n]$ such that there exists common zeros in $k^n$, $\det(\partial\overline{f}_i/\partial t_j(r))\neq 0$, and there exists $s \in R^n$ with $\overline{s} = r$ and $f_i(s) = 0$.

^614d20

>[!def] Strictly Henselian Rings
>A local ring $R$ is said to be **strictly henselian** if it is henselian and $k$ is separably closed.

Condition (4) in [[Henselian Rings#^614d20]] becomes trivial if $R$ is strictly henselian. This will be the appropriate notion of local ring for the etale topology.

>[!theorem]
>If $R$ is henselian, then the functor $S\mapsto S\otimes_Rk$ gives an equivalence of categories between finite etale $R$-algebras and finite etale $k$-algebras.

In the case when $R$ is Noetherian, $\hat{R}$ is a Noetherian complete local ring with respect to the maximal ideal $\mathfrak{m}$, and we have an inclusion $R\hookrightarrow \hat{R}$, where $\hat{R}$ will be Henselian.

>[!def] Henselization
>If $R$ and $S$ are local rings, with $S$ Henselian, and $f:R\to S$ is a local homomorphisms, then $f$ is a **Henselization** if for any map $g:R\to R'$ which is a local homomorphism to a Henselian ring, then $g$ factors uniquely through $S$. We denote the Henselization of $R$ by $R^h$.

We can construct the Henselization of a local ring $R$ through a colimit of etale neighborhoods. 

>[!def] etale Neighborhoods
>An **etale neighborhood** of a local ring $R$ is a pair $(A,p)$ where $A$ is an etale $R$-algebra and $p\subseteq A$ is a prime ideal lying over $\mathfrak{m}$. Suppose the induced map $k \to k(p)$ is an isomorphism, so $p$ is necessarily maximal. 

A morphism of etale neighborhoods $(A,p)\to (A',p')$ is an $R$-algebra map $A\to A'$ such that $f^{-1}(p') = p$.

>[!lemma]
>If $f,g:Z\to Y$ are morphisms of $X$-schemes, where $Z$ is connected and $Y$ is  etale and separated over $X$, then if there exists a point $z \in Z$ such that $f(z) = g(z) =: y$, such that $f$ and $g$ induce equal maps $k(y)\to k(z)$. Then $f = g$.


>[!theorem]
>Let $R^h = \text{colim}_{(A,p)}A$ be the colimit over etale neighborhoods. Then $R$ is a Henselization of $R$, and the map $R\to R^h$ is faithfully flat and formally etale.

`\begin{proof}`
The indexing category of etale neighborhoods is filtered since we can take pullbacks. Further, we can restrict the category to be small. Then explicitly
$$R^h = \{[(A,p,a)]\mid (A,p)\text{ etale neighborhood}, a\in A\}/\sim$$
where $(A,p,a)\sim (A',p',a')$ if they exists $(B,q,b)$ with maps $(A,p,a)\to (B,q,b)$ and $(A',p',a')\to (B,q,b)$. Then
$$\mathfrak{m}R^h = \{[(A,\mathfrak{m}A,a)]\mid a \in \mathfrak{m}A\}$$
and the map $R^h\to k$ given by $[(A,\mathfrak{m}A,a)]\mapsto a\mod \mathfrak{m}A$ is surjective with kernel $\mathfrak{m}R^h$.
`\end{proof}`

>[!example]
>1. Let $k$ be  a field and $R = k[t_1,...,t_n]_{\langle t_1,...,t_n\rangle}$, then $R^h$ is the algebraic closure of $R$ in $\hat{R}$.
>2. Let $R$ be a **normal domain** (that is still local), let $K = \text{Frac}(R)$, let $G = \text{Gal}(k^{sep}/k)$, and let $S$ be the integral closure of $R$ in $k^{sep}$, and $\mathfrak{n}$ a maximal ideal of $S$ lying over $\mathfrak{m}$. Set $D = \{\sigma \in G\mid \sigma(n) = n\}$. Then
>$$ R^h = S^D_{\mathfrak{n}^D}$$
>

>[!theorem]
>Let $R^{sh} = \text{colim}_{(A,p,\alpha)}A$ where $A$ is etale over $R$, $p$ lies over $\mathfrak{m}$, and $\alpha:k(p)\to k^{sep}$ is a morphism under $k$, then $R^{sh}$ is **strictly henselian, loca, faithfully flat, and formally etale** over $R$. If $f:R\to S$ is a local homomorphism and we fix a map $\varphi:k^{sep}\to k(S)$, where $S$ is a strictly henselian local ring, then $f:R\to S$ uniquely factors through $R\to R^{sh}$ with the factorization inducing $\varphi$ on the residue field.
>

Strict henselianization inherits a number of nice properties from the base ring.

>[!proposition]
>$R$ is noetherian if and only if $R^h$ is noetherian, if and only if $R^{sh}$ is noetherian. In this case, $R$ reduced (resp. normal, regular) if and only if $R^h$ is, if and only if $R^{sh}$ is.


### Henselian Notions for Schemes

>[!def] Etale Neighborhood for schemes
>Let $X$ be a scheme and $x \in X$. We say $(Y,y)$ an etale neighborhood of $x$ over $X$ if $y \mapsto x$ and $k(x) \cong k(y)$.

>[!proposition]
>We have an isomorphism $$\mathcal{O}_{X,x}^h\cong \text{colim}_{(Y,y)}\Gamma(\mathcal{O}_Y,Y)$$

## View Towards Grothendieck Topologies

>[!def] Grothendieck Topology
>A **Grothendieck topology** on a (small) category $\mathcal{C}$ is a collection $J$ such that for each object $C$ of $\mathcal{C}$, $J(C)$ is a set of sieves over $C$, called covering sieves, such that
>1. For any $C$, $y^C$ is a covering sieve for $C$ (i.e. is in $J(C)$)
>2. If $f:B\to C$ is map in $\mathcal{C}$ and $S$ is a covering sieve on $C$, then $f^*S \in J(B)$
>3. If $S$ is a covering sieve on $C$ and $R$ is a sieve on $C$ such that $f^*R$ is a covering sieve for all $f$ in $S$, then $R$ is also a covering sieve.
>   
>A pair of a category $\mathcal{C}$ with an etale topology is called a **site**.

>[!example]
>1. For any topological space, $\mathsf{Top}(X)$ has the usual open cover site.
>2. Let $S$ be a scheme and $\mathcal{C}$ a full-small subcategory of the category of $S$-schemes closed under pullback. The **Big Zariski (etale) site** on $\mathcal{C}$ has as covering sieves those induced by Zariski covers, which are open immersions, and etale covers.

>[!def] Sheaves
>Let $(\mathcal{C},J)$ be a site. A pre-sheaf $\mathscr{F}:\mathcal{C}^{op}\to \mathsf{Set}$ is a $J$-sheaf if and only if for any covering sieve $S$ of $C$ and any morphism of pre-sheaves $\alpha:S\Rightarrow \mathscr{F}$ (thought of as an amalgamation family), there exists a unique lift to the maximal covering sieve $\widetilde{\alpha}:y^C\Rightarrow \mathscr{F}$.

A Grothendieck topos is a category equivalet to $\mathsf{Sh}(\mathcal{C},J)$. A **fiber functor** on a topos $\mathcal{T}$ is a functor $\mathcal{T}\to \mathsf{Set}$ which preserves small colimits and finite limits.

How is this related to Henselian rings?

>[!def] $J$-local
>Let $S$ be a separable Noetherian scheme, and let $\mathsf{Sch}_S$ denote the category of separable finite type $S$-schemes. A functor $\mathsf{Sch}_S\to \mathsf{Set}$ is said to be **$J$-local** if $$\coprod_{i \in I}F(X_i)\to F(X)$$
>is surjective for all covers $\{X_i\to X\}$ of $X$. A scheme $X$ is said to be **$J$-local** if $\mathsf{Hom}_S(X,-)$ is $J$-local.


>[!proposition]
>Let $\mathsf{Sch}_S$ be equipped with the Zariski site. The local affine schemes are given by spectra of local rings. If we replace the Zariski site by the (small) etale site then the local affine schemes are the spectra of strictly henselian local rings.


>[!proposition]
>Let $J$ be a topology on $\mathsf{Sch}_S$ such that all Zariski covers are $J$-covers. Then we have an equivalence of categories between the opposite category of $J$-local affine $S$-schemes and the category of fiber functors on $\mathsf{Sh}_J(\mathsf{Sch}_S)$, with the map corresponding to the strict henselianization of rings.



