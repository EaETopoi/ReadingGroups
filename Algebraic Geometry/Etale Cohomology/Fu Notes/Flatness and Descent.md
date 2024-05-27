---
date: 2024-05-20T15:25:00
tags:
  - AlgebraicGeometry
  - EtaleCohomology
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

In these notes we investigate the notions of flatness and descent as worked out in Fu[^1]. In order to set notation we $\mathbb{A}^n$ for the affine scheme $\mathsf{Spec}(\mathbb{Z}[t_1,...,t_n])$ and we write $\mathbb{P}^n$ for the projective scheme $\mathsf{Proj}(\mathbb{Z}[t_0,t_1,...,t_n])$.  In general, for a scheme $S$ we write $\mathbb{A}_S^n$ to denote the affine scheme obtained by pullback
$$\begin{CD} \mathbb{A}^n_S @>>> \mathbb{A}^n \\ @VVV @VVV \\ S @>>> \mathsf{Spec}(\mathbb{Z}) \end{CD}\;\;\begin{CD} \mathbb{P}^n_S @>>> \mathbb{P}^n \\ @VVV @VVV \\ S @>>> \mathsf{Spec}(\mathbb{Z}) \end{CD}$$
Note that via the natural inclusion of $\mathbb{A}^n$ into $\mathbb{P}^n$ as $\mathsf{Spec}(\mathbb{Z}[t_1/t_0,...,t_n/t_0])$ induces, by the universal property of the pullback, a similar identification of $\mathbb{A}_S^n$ in $\mathbb{P}^n_S$. For results on flat modules we refer to [[Fu Flat Modules]].  

#### References

[^1]: Fu, L. (2015). Etale Cohomology Theory: Revised Edition (Vol. 14). WORLD SCIENTIFIC. https://doi.org/10.1142/9569
