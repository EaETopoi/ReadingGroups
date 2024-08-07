---
date: 2024-07-08T14:00:00
tags:
  - GaloisCohomology
  - AlgebraicGeometry
  - NumberTheory
  - SummerSchool
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

These notes are from a talk by Alexander Merkurjev which are part of a larger mini-course on Massey products as they appear in Galois cohomology. This is one of the many mini-courses occurring at the 2024 PCMI.

## Galois Fundamental Group

Throughout let $F$ be a field, and let $\Gamma_F := \text{Gal}(F_{sep}/F)$ be its absolute Galois group, where $F_{sep} = \bigcup_{K/F,\;finGalois}K$, so we have a natural inclusion
$$\Gamma_F\hookrightarrow \prod_{K/F,fin}\text{Gal}(K/F)$$
The group $\Gamma_F$ is pro-finite, which is to say it is a cofiltered limit (indexed by a directed poset) of finite discrete topological groups. Explicitly, we have that
$$\Gamma_F\cong \text{colim}_{F\subseteq K}\text{Gal}(K/F)$$

>[!question]
>What profinite groups $\Gamma$ are isomorphic to $\Gamma_F$ for some field $F$?

In these notes we will investigate this motivating question by determining a number of interesting properties of profinite groups of the form $\Gamma_F$, which do not hold in general, and hence begin to give a classification of the profinite groups resulting from absolute Galois groups.

Consider $p$ a prime and $\Gamma$ profinite. We have a natural cochain complex $C^\bullet(\Gamma,\mathbb{Z}/p\mathbb{Z})$, resulting as a Moore complex of some simplicial set, where
$$C^n(\Gamma,\mathbb{Z}/p\mathbb{Z}) = \mathsf{Top}(\Gamma^n,\mathbb{Z}/p\mathbb{Z})$$
It isn't hard to show that for these cochain complexes,
$$H^1(\Gamma,\mathbb{Z}/p\mathbb{Z}) \cong \mathsf{TopGrp}(\Gamma,\mathbb{Z}/p\mathbb{Z})$$
and the ring structure on the cohomology ring $H^*(\Gamma,\mathbb{Z}/p\mathbb{Z})$ is given by the cup product, which on $1$-cocycles is given by
$$(\alpha\smile\beta)(x,y) = \alpha(x)\cdot \beta(y)$$
If $\Gamma = \Gamma_F$ for some field $F$, we will write
$$H^*(F,\mathbb{Z}/p\mathbb{Z}) := H^*(\Gamma_F,\mathbb{Z}/p\mathbb{Z})$$

>[!thm] Voevodsky-Rost
>If $\xi_p \in F$ (i.e. $F$ has a primitive $p$th root of unity), then $H^*(F,\mathbb{Z}/p\mathbb{Z})$ is generated by $H^1(F,\mathbb{Z}/p\mathbb{Z})$ with relations in degree $2$.

This is a very strong constraint on the group cohomology of $\Gamma_F$, indicating that absolute Galois groups are somewhat special among profinite groups.

### Motivation for the Massey Product

Let $\Gamma$ be a profinite group and let $p$ be a prime, and $n\geq 2$ an integer. In 1975 Dwyer considered the subgroup $U_{n+1}$ of $GL_{n+1}(\mathbb{Z}/p\mathbb{Z})$ given by matrices of the form
$$\begin{pmatrix}
1 & & & * \\
& 1 & & \\
& & \ddots & \\
0 & & & 1
\end{pmatrix}$$
while the centre, $Z_{n+1}$, is given by matrices of the form
$$\begin{pmatrix}
1 & & & * \\
& 1 & 0 & \\
& & \ddots & \\
0 & & & 1
\end{pmatrix}$$
with non-zero entry above the diagonal only in the upper right corner.

Let $\overline{U}_{n+1} = U_{n+1}/Z_{n+1}$, which can be thought of as letting the top right corner be indeterminate. We define
$$U_{n+1}\twoheadrightarrow \overline{U}_{n+1}\twoheadrightarrow (\mathbb{Z}/p\mathbb{Z})^n$$
where the second map is given by $u\mapsto (u_{12},u_{23},...,u_{n(n+1)})$.

Now, let us consider characters, $\chi_1,...,\chi_n \in H^1(\Gamma,\mathbb{Z}/p\mathbb{Z})$, and the associated lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%26%26%26%20%5CGamma%20%5C%5C%0A%09%5C%5C%0A%09%7BU_%7Bn%2B1%7D%7D%20%26%26%20%7B%5Coverline%7BU%7D_%7Bn%2B1%7D%7D%20%26%26%20%7B(%5Cmathbb%7BZ%7D%2Fp%5Cmathbb%7BZ%7D)%5En%7D%0A%09%5Carrow%5B%22%5Crho%22%2C%20dashed%2C%20from%3D1-5%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Coverline%7B%5Crho%7D%7D%22%2C%20dashed%2C%20from%3D1-5%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Cchi%22%2C%20from%3D1-5%2C%20to%3D3-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D3-3%2C%20to%3D3-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp;&amp;&amp;&amp; \Gamma \\
	\\
	{U_{n+1}} &amp;&amp; {\overline{U}_{n+1}} &amp;&amp; {(\mathbb{Z}/p\mathbb{Z})^n}
	\arrow[&quot;\rho&quot;, dashed, from=1-5, to=3-1]
	\arrow[&quot;{\overline{\rho}}&quot;, dashed, from=1-5, to=3-3]
	\arrow[&quot;\chi&quot;, from=1-5, to=3-5]
	\arrow[two heads, from=3-1, to=3-3]
	\arrow[two heads, from=3-3, to=3-5]
\end{tikzcd}
" /></p>

Note that the first lift of the diagram is a collection of characters $\overline{\rho}_{ij}$ for $i < j$ with $(i,j)\neq (1,n+1)$. The $\overline{\rho}_{ij}$ are the upper triangular entries of our matrix. Given such a collection of characters, the lifting condition is exactly
$$\overline{\rho}\text{ lifts }\chi\iff \overline{\rho}_{i(i+1)} = \chi_i$$
where we must also satisfy the addition condition $\overline{\rho}(xy) = \overline{\rho}(x)\overline{\rho}(y)$.

A lift $\rho$ then extends $\overline{\rho}$ if and only if $\rho_{ij} = \overline{\rho}_{ij}$ for all $i < j$, $(i,j)\neq (1,n+1)$. So really, we just need to insert a character $\eta$ into $\overline{\rho}$ at the top left entry such that the group law is satisfied, which becomes
$$\eta(xy) = \eta(y) + \sum_{i=2}^n\overline{\rho}_{1,i}(x)\overline{\rho}_{i,n+1}(y)+\eta(x)$$
where the centre term, which we denote by $\Delta(\overline{\rho})(x,y)$ is a $2$-cocycle. This can be seen by looking at a sequence of the form


#### References