---
date: 2024-06-16T12:21:00
tags:
  - AlgebraicGeometry
  - Varieties
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

In this note we cover the basics of varieties, as viewed from the theory of schemes, following Vakil[^1].

## Varieties

>[!def] Variety
>A **variety** over a field $k$ is a reduced (i.e. all sections are reduced), separated scheme (i.e. the structure map $V\to\mathsf{Spec}(k)$ is separated) of finite type over $k$ (i.e. the structure map $V\to \mathsf{Spec}(k)$ is locally of finite type and quasi-compact).

In many other texts  varieties are assumed to be irreducible and $k$ is assumed algebraically closed. Morphisms of $k$-varieties are just morphisms of the underlying $k$-schemes. However, due to the restriction on the structure morphisms of the variety, morphisms of $k$-varieties end up being automatically of finite type and separated.

A **subvariety** of a variety $V$ is a **reduced** locally closed subscheme of $V$. An open subvariety is an open subscheme. A closed subvariety is a reduced closed subscheme.

#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024