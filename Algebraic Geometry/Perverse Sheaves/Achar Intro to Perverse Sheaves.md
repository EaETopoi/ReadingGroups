---
date: 2024-05-23T11:19:00
tags:
  - AlgebraicGeometry
  - Sheaves
  - TextbookNotes
  - Derived
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

In this notes we begin introducing the concepts of perverse sheaf theory, following the work of Achar[^1]. We will argue that perverse sheaves form an abelian category, and discuss some of the most important kinds of perverse sheaves, those known as **intersection cohomology complexes**, which can be thought of as the building blocks for the category of perverse sheaves. 

Throughout these notes the term **variety** is used to mean a **quasiprojective complex algebraic variety** (i.e. a locally closed subset of some projective space $\mathbb{P}^n$ in the Zariski topology).

## Perverse $t$-structure

In this section we heavily use the theory of [[Achar t-Structures|t-structures]] in order to construct the category of perverse sheaves. 

>[!def] Perverse $t$-structure
>Let $X$ be a variety. The **perverse $t$-structure** on $X$ is the $t$-structure on the bounded, constructible derived category $D^b_c(X,\mathbb{k})$ given by
>$$\begin{align*}{^pD_c^b(X,\mathbb{k})}^{\leq 0} &:= \{\mathcal{F} \in D_c^b(X,\mathbb{k})\mid \forall i,\dim\text{supp}\,\mathsf{{H}^i(\mathcal{F})\leq -i} \} \\ {^pD_c^b(X,\mathbb{k})}^{\geq 0} &:=  \{\mathcal{F} \in D_c^b(X,\mathbb{k})\mid \forall i,\text{mdsupp}\,\mathsf{{H}^i(\mathbb{D}\mathcal{F})\leq -i} \} \end{align*}$$
>The **heart of the $t$-structure** is denoted
>$$\text{Perv}(X,\mathbb{k}) = {^pD_c^b(X,\mathbb{k})}^{\leq 0}\cap {^pD_c^b(X,\mathbb{k})}^{\geq 0}$$
>and the objects in the heart are called **perverse sheaves**.

The remainder of this subsection is focused on showing that these definitions do indeed provide a $t$-structure. Once we show this we will have **perverse truncation** and **perverse cohomology** functors
$${^p\tau^{\leq n}},{^p\tau^{\geq n}}:D_c^b(X,\mathbb{k})\to D_c^b(X,\mathbb{k}),\;\;{^p\mathsf{{H}^n}}:D_c^b(X,\mathbb{k})\to \text{Perv}(X,\mathbb{k})$$
Further, if $(X_s)_{s \in \mathscr{S}}$ is a **good stratificiation** then we obtain an induced $t$-structure on $D_\mathscr{S}^b(X,\mathbb{k})$.

#### References

[^1]: Achar, P. (2021). Pramod N. Achar: Perverse Sheaves and Applications to Representation Theory. American Mathematical Society. https://www.ams.org/publications/authors/books/postpub/surv-258. Accessed 16 May 2024
