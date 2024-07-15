---
date: 2024-06-09T00:11:00
tags:
  - AlgebraicGeometry
  - Schemes
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

In this section we cover the basic definitions and results required to introduce and study the notion of dimension for schemes, following the work of Vakil[^1].

## Dimension and Codimension

In algebraic geometry the notion of dimension can be quite subtle, but the goal is for it to match our geometric intuition. 

>[!def] Dimension
>The **dimension** of a topological space $X$, denoted $\dim X$, is the supremum of lengths of chains of closed irreducible sets (with enumeration starting at $0$). The **dimension** of a ring $R$ is the supremum of the lengths of chains of nested prime ideals (with enumeration starting at $0$).

Since we have a bijection between irreducible closed subsets of $\mathsf{Spec}(A)$ and prime ideals of $A$ (in an inclusion-reversing fashion), these two concepts of dimension coincide. 


#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024
