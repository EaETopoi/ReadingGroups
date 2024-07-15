---
date: 2024-05-27T18:53:00
tags:
  - CommutativeAlgebra
  - AlgebraicGeometry
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

In these notes we discuss henselian rings and the henselianization of a ring, as done in Fu[^1].


## Henselian Rings

We say that a local ring $(R,\mathfrak{m})$ is **henselian** if it satisfies any of the equivalent conditions in the following proposition.

>[!proposition] Henselian Rings
>Let $(R,\mathfrak{m})$ be a local ring, $k = R/\mathfrak{m}$ its residue field, $S = \mathsf{Spec}(R)$, and $s$ the closed point of $S$ (i.e. corresponding to $\mathfrak{m}$). Then the following conditions are equivalent:
>1. Every finite $R$-algebra $A$ is a direct product of local rings
>2. Condition (1) holds for $A = R[t]/(f(t))$ for any monic polynomial $f(t) \in R[t]$ 
>3. For any finite $R$-algebra $A$, the canonical homomorphism $A\to A/\mathfrak{m}A$ induces a one-to-one correspondence between the set of idempotent elements in $A$ and the set of idempotent elements  in $A/\mathfrak{m}A$.
>4. The condition (3) holds for $A = R[t]/(f(t))$ for any monic polynomial $f(t) \in R[t]$.
>5. For any monic polynomial $f(t) \in R[t]$ and any factorization $\overline{f}(t) = \overline{g}(t)\overline{h}(t)$, where $\overline{f}(t)$ is the image of $f(t)$ in $k[t]$, and $\overline{g}(t)$ and $\overline{h}(t)$ are relatively prime monic polynomials in $k[t]$, there exists uniquely determined polynomials $g(t),h(t) \in R[t]$ such that $f(t) = g(t)h(t)$ 


#### References

[^1]: Fu, L. (2015). Etale Cohomology Theory: Revised Edition (Vol. 14). WORLD SCIENTIFIC. https://doi.org/10.1142/9569