---
date: 2024-06-14T18:53:00
tags:
  - AlgebraicGeometry
  - EtaleCohomology
  - Schemes
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

These notes follow a lecture by Jiantong on etale cohomology as part of a summer 2024 reading group on etale cohomology at UIUC.

The general idea with etale cohomology is that we want to create something that works like homological algebra over the etale topology.

Throughout we will fix a scheme $X$, and we will be considering a full sub-category $\mathcal{C}/X$ which is closed under pullbacks, and the structure morphisms for this subcategory $E$ is closed under composition and has isomorphisms. With these assumptions we obtain a site $(\mathcal{C}/X)_E$. The main cases of interest are as follows:
1. The small Zariski site ($E$ = open immersions)
2. The small etale site ($E =$ finite etale morphisms)
3. Big flat site ($LFin/X$ with $E =$ flat morphisms)

Generally we will write $X_E$ for $(\mathcal{C}/X)_E$ and we will write $X_{et}$ in the case of the small etale site.

## Homological Algebra Perspective

An important question will be what are the derived functors in our theory? (this should be some type of Kan extension) Then if we have enough "injectives", or at least computable objects for the cohomology theory/derived functors, we can define our etale cohomology in terms of these derived functors.

>[!thm] Category of Sheaves on a Site has Enough Injectives
>The category $\mathsf{Sh}(\mathcal{C},J)_\mathsf{Ab}$ of abelian sheaves on a site has enough injectives.

>[!def] Family of Generators
>A **family of generators** of a category $\mathcal{C}$ is a collection $\mathcal{G} \subseteq \mathcal{C}_0$ of objects such that for any two distinct morphisms $f,g:X\to Y$ in $\mathcal{C}$, there exists $G \in \mathcal{G}$ and some $h:G\to X$ such that $f\circ h \neq g \circ h$.

>[!lem]
>Any abelian category with AB3$^*$ (arbitrary products), AB5, such that it has a **family of generators**, then it has enough injectives.

Really this lemma is mimicking Baer's criterion. We can show that $\mathsf{Sh}(\mathcal{C},J)$ has a family of generators by sheafifying the generators on pre-sheaves.

>[!lem] Preservation of Injectives
>A functor between abelian categories with exact left adjoint preserves injectives.

We now can use the fact that we have enough injectives to define our sheaf cohomology.

>[!def] Sheaf Cohomology
>For the site $X_E$, the $n$th sheaf cohomology is given by the right derived functor
>$$H^n(X_E,-) := R^n\Gamma(X_E,-)$$
>which we can evaluate on a sheaf on $X_E$.

In general, if $f_*$ is the right adjoint (and hence left exact) functor associated with direct image functor for a geometric morphism, we obtain a cohomology by taking the right derived functor $R^nf_*$.

### Galois Cohomology

If $X = \mathsf{Spec}(k)$, then we have a correspondence between $\mathsf{Sh}(X_{et})$ and discrete $G$-modules, where $G = \text{Gal}(k^{sep}/k)$. Under this correspondence the global sections $\Gamma(X,-)$ corresponds with the fixed point functor $(-)^G$.



### Flasque Sheaves

Recall that a sheaf $\mathcal{F}$ on a topological space $X$ is said to be **flasque** (or **flabby**) if all restriction homomorphisms are surjective. In the classical theory of sheaf cohomology we can compute derived functors using flabby resolutions since they are acyclic with respect to the global sections functor.

We would like to mimic this characterization in the etale site.

>[!def] Flasque Sheaves


>[!thm]
>Let $\mathcal{F}$ be a sheaf on $X_{et}$. Then the following are equivalent
>1. $\mathcal{F}$ is flasque
>2. $\check{H}^n(U,\mathcal{F}) = 0$ for all $U \in X_E$, $n > 0$
>3. For any etale covering $\mathcal{U}$ of $U$, $\check{H}^1(\mathcal{U},\mathcal{F}) = 0$
>4. For any etale covering $\mathcal{U}$ of $U$, $\check{H}^n(\mathcal{U},\mathcal{F}) = 0$ for all $n > 0$.

>[!rmk]
>In general this is not the case for an arbitrary site.

>[!thm]
>Let $T$ be the collection of all flasque sheaves on $X_E$, and let $f$ be either $\Gamma(X,-)$, $H^0(\mathcal{U},-)$, or $\pi_*$, the


#### References

