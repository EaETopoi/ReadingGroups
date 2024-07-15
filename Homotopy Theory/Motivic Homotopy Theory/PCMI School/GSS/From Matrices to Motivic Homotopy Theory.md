---
date: 2024-07-08T11:06:00
tags:
  - MotivicHomotopyTheory
  - Homotopy
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

In these notes we record a talk by Dr. Aravind Asok, from USC, on matrices and their connection to motivic homotopy theory.

## Splitting problems.

Throughout let $M$ be a *nice* space, such as a manifold or CW complex, of dimension $d$. Let $\mathscr{V}_r(M)$ denote the set of isomorphism classes of rank $r$ (real) vector bundles on $M$. 

The statement that the map $\mathscr{V}_r(M)\to \mathscr{V}_r(M\times I)$ is a bijection is homotopy invariance of vector bundles. Let $\text{Gr}_r^{top}$ denote the Grassmannian of $r$-dimensional subspaces of an infinite dimensional vector space, which has a nice vector bundle. Maps $M\to \text{Gr}_r^{top}$ yield rank $r$ vector bundles

>[!thm]
>Pulling back along the tautological bundle induces a homotopy equivalence
>$$[M,\text{Gr}_r^{top}]\to \mathscr{V}_r(M)$$

Now, consider the splitting problem associated with a map $s_r:\text{Gr}_{r-1}^{top}\to \text{Gr}_r^{top}$ classifying the sum of the tautological bundle of rank $r-1$ and a trivial rank $1$ bundle. When then does a rank $r$ bundle have a nowhere vanishing $r-1$ given by extension along $s_r$.

>[!example]
>Consider a closed manifold $M$ of dimension $d$ and fix $\xi:M\to \text{Gr}_r^{top}$


>[!example]
>Take $M$ a closed manifold of dimension $d$ and fix $\xi:M\to \text{Gr}_d^{top}$. When does this have a nowhere vanishing section?
>
>The **obstruction** to existence of such a section is that the cohomology class which is Poincare dual to the vanishing locus of a generic section, i.e. **(twisted) Euler class**.
>
>Note $\pi_1(\text{Gr}_r^{top}) \cong \mathbb{Z}/2$ via the determinant, and $\xi$ yields an orientation character $\omega_\xi:\pi_1(M)\to \mathbb{Z}/2$ if and only if there exists an orientation local system on $M$.


In these types of problems we would like to measure the failure of $s_r$ to be a weak homotopy equivalence, as this describes the failure of existence of extensions. This failure is measured by the fiber sequence
$$S^{r-1}\to \text{Gr}_{r-1}^{top}\xrightarrow{s_r}\text{Gr}_r^{top}$$
The idea of **obstruction theory** is that there is an inductive procedure to decide whether lifts exists using **unstable** homotopies of $S^{r-1}$.

In this setting, our **Euler class** arises from the degree map
$$\text{deg}:\pi_{r-1}(S^{r-1})\cong \mathbb{Z}$$
when $r \geq 2$. Since the group is **stable**, the answer to our question will be independent of $r$. 

### Corank 1

>[!thm] S.D. Liao '54
>Let $M$ be a manifold of dim $d+1,d\geq 4$. If $\xi$ is an oriented rank $d$ vector bundle on $X$, then $\xi$ splits off a trivial rank $1$ summand iff $0 = e(\xi) \in H^d(M,\mathbb{Z})$ and $$0 = o_2(\xi) \in H^{d+1}(M,\mathbb{Z}/2)/(Sq^2+\omega_2(\xi))\cup H^{d-1}(M,\mathbb{Z}/2)$$
>(this represents a pair of null-homotopies and their relation)

Here $e(\xi)$ is the Euler class. As with the last result, the dimension hypotheses allow us to conclude that two obstructions are needed to be analyzed, the primary one being the Euler class obstruction and the other, if the first vanishes, being the obstruction arising from
$$\pi_d(S^{d-1}) \cong \left\{\begin{array}{cc} \mathbb{Z} & d=3 \\ \mathbb{Z}/2 & d\geq 4 \end{array}\right.$$

>[!Takeaway]
>Because of the form of the homotopy of the sphere, when studying these splitting problems we find different situations where things are either stable or unstable.

## Splitting Algebraic Vector Bundles

Let $R$ be a commutative ring throughout. Recall that a module $P$ is projective iff any of the following hold:
1. $P$ satisfies a lifting property (**Fill in**)
2. If $P$ is finitely generated, then there exists an $n$ and $\epsilon \in \text{End}_r(R^{\oplus n})$ such that $\epsilon^2 = \epsilon$ and $P = \text{im}(\epsilon)$ (i.e. $P$ is the image of a projective operator)

**Slogan:** Projective modules "are" vector bundle

We can make this explicit by observing that if $P$ is a finitely generated $R$-module, then $f_1,...,f_n \in R$ such that $P\vert_{D(f_i)}$ is a free $R[1/f_i]$-module. In other words $P$ gives a locally trivial vector bundle over the Zariski topology on $\mathsf{Spec}(R)$.

On the other hand, if $M$ is a compact manifold, a vector bundle $\pi:E\to M$ is equivalent to a finitely generated projective $C(M)$-module, given by continuous sections of $\pi$.


>[!def]
>Suppose $R$ is a Noetherian ring of Krull dimension $d$ and $P$ is a projective $R$-module of rank $r$:
>1. $\mathscr{V}_r(\mathsf{Spec}(R)) \cong$ classes of rank $r$ projective $R$-modules (i.e. rank $r$ algebraic vector bundles)
>2. corank $P = d-r$.

The assignment $P\mapsto P\oplus R$ determines a **stabilization function**
$$s_r:\mathscr{V}_{r-1}(\mathsf{Spec}(R))\to \mathscr{V}_r(\mathsf{Spec}(R))$$
The algebraic equivalent to our previous considerations is the following:

>[!thm]
>The function $s_r$ is surjective for $r > d$ (i.e. **negative corank**).



### Corank $0$: Complications

Assume $k$ is a field and $R$ is a **smooth** $k$-algebra of dimension $d$ and $P$ a projective $R$-module of rank $d$. The **obstruction**, "the vanishing locus of a generic section", is the $d$-th **Chern class**, $c_d(P)$ (this is an **algebraic subvariety**). The obstruction lies in the Chow group of codimension $d$ algebraic cycles modulo rational equivalence, $CH^d(\mathsf{Spec}(R))$. 

However, in the algebraic case, unlike the topological one, the consideration of this obstruction is **not sufficient in general** to solve our splitting problem. For example, the tangent bundle to the real $2$-sphere has $c_2$ trivial, but does not split off a free rank $1$ summand.

>[!question]
>When, if ever, is the obstruction in algebraic problems sufficient?

### Euler Class in Alg Geometry

>[!thm]
>If $k$ is algebraically closed, and $X$ is a smooth affine $d$-fold over $k$, then the image of $s_{d-1,X}$ consists of those $\mathcal{E}$ of rank $d$ such that $0 = c_d(\mathcal{E}) \in CH^d(X)$

This theorem gives a sufficient condition for the obstruction to determine splitting. This theorem expanded by cases at first over a number of years, starting in '76 by R.Swan-M.P. Murthy with $d=2$, N. Mohan Kumar and M.P. Murthy with $d=3$ in '82, and the general case in '92 by M.P. Murphy.


## Classification of Vector Bundles

The grassmannian, $\mathsf{Gr}_r$, which is essential to the study of vector bundles in topology is an infinite dimensional algebraic variety, and hence difficult to deal with in algebraic geometry.

A map $\mathsf{Spec}(R)\to \mathsf{Gr}_r$ corresponds to a vector bundle on $R$ and a collection of generating sections. When considering **naive homotopies** between such maps, i.e. maps $H:\mathsf{Spec}(R[t])\to \mathsf{Gr}_r$, what can we say?

>[!thm]
>If $k$ is a field and $R$ is a **regular** $k$-algebra, then
>$$[\mathsf{Spec}(R),\mathsf{Gr}_r]_{naive}\xrightarrow{\cong}\mathscr{V}_r(\mathsf{Spec}(R))$$

This theorem is an incredibly hard problem, with even the $R = k[t_1,...,t_n]$ being equivalent to the statement that all projective modules over a polynomial ring are free. This difficulty comes from the fact that naive homotopy is generally badly behaved (e.g. it is not an equivalence relation in general), although it is in this case due to special properties of the grassmannian.

Further, the restriction to **regular** rings in the theorem (i.e. a smoothness condition) is necessary in order to give an analog of homotopy invariance.

## Motivic Perspective

Take the notation in [[Reading Notes/Homotopy Theory/Motivic Homotopy Theory/Morel A1 Homotopy/Overview|Overview]]. The category $\mathsf{Sm}_k$ is in general not big enough to do homotopy theory, as, for example, $\text{Gr}_r$ is not in this category, and quotients do not in general exist.

Let $P(\mathsf{Sm}_k)$ denote the space-valued presheaves on $\mathsf{Sm}_k$. We force two kinds of maps to be equivalences:
1. Nisnevich local equivalences: 
2. $\mathbb{A}^1$-equivalences: $X\times \mathbb{A}^1\to X$
The resulting category $\mathsf{Spc}_k$ is the category of **motivic spaces** (which is technically an $\infty$-category).

If $k$ is regular, one may show $[X,\mathbb{P}^\infty]_{\mathbb{A}^1} = \text{Pic}(X)$ represents line bundles for any smooth $k$-scheme $X$. However, this fails for $\text{Gr}_r$ with $r \geq 2$. If we restrict ourselves, however, the set of naive homotopy classes of maps is well behaved.

>[!thm] (Affine Representability)
>If $k$ is a field or $\mathbb{Z}$, then for any smooth affine $k$-scheme, $X = \mathsf{Spec}(R)$, then
>$$[\mathsf{Spec}(R),\mathsf{Gr}_r]_{naive}\xrightarrow{\cong}\mathscr{V}_r(\mathsf{Spec}(R))$$

The main essence is the Bass-Quillen conjecture for all smooth algebras over $k$.

### Lifting Problem Perspective.

>[!thm]
>If $k$ is either a field of a Dedekind ring with perfect residue fields, then there is an $\mathbb{A}^1$-fiber sequence of the form
>$$\mathbb{A}^r\backslash 0\to \mathsf{Gr}_{r-1}\to \mathsf{Gr}_r$$

One can heuristically think of gluing cells, from the topological context. With this result we can build a version of obstruction theory in $\mathbb{A}^1$-homotopy theory.

### Spheres in Motivic Homotopy Theory

We view $S^1$ and $\mathbb{G}_m$ as circles in $\mathbb{A}^1$-homotopy theory. In $\mathsf{Spc}_k$ we have equivalences of the form $\mathbb{P}^1\sim S^1\land \mathbb{G}_m$ and $\mathbb{A}^n\backslash 0\sim S^{n-1}\land \mathbb{G}_m^{\land n}$, and $\mathbb{A}^{n+1}\backslash 0\sim \mathbb{P}^1\land \mathbb{A}^n\backslash 0$.

Define
$$S^{p,q}:= S^{p-q}\land \mathbb{G}_m^{\land q}$$

In this theory we must consider **homotopy sheaves** rather than **homotopy groups** in order to obtain the right Whitehead theorem.

>[!thm] F. Morel
> For any $n \geq 2$, the sphere $\mathbb{A}^n\backslash 0$ is $(n-2)$-$\mathbb{A}^1$-**connected**.

The intuition behind $\mathbb{A}^1$-connectedness is that any two points can be connected by a chain of affine lines over any extension of the base field.

>[!thm] F. Morel
>For any $n\geq 2$, there is an isomorphism $\pi_{n-1}^{\mathbb{A}^1}(\mathbb{A}^n\backslash0)\cong \mathbf{K}_n^{MW}$ (which is a **sheaf**)

The idea of the proof is the **Hurewicz theorem**, which tells us that this is the first non-vanishing homotopy coinciding with homology. The suspension isomorphism in this context tells us that homology is a "free sheaf of abelian groups" on $\mathbb{G}_m^{\land n}$. 

### Euler Class

>[!thm] F. Morel
>Suppose $k$ is a field, $X$ is a smooth affine $k$-variety of dimension $d$, and $\xi:E\to X$ is a rank $d$ algebraic vector bundle on $X$. There exists a canonically defined "Euler class"
>$$e(\xi) \in H^d(X,\mathbf{K}_n^{MW}(\det\xi))=\widetilde{CH}^d(X,\det\xi)$$
>whose vanishing is sufficient to guarantee $E$ splits off a free rank $1$ summand.

This theorem describes an Euler class like obstruction condition for the splitting of algebraic vector bundles over $X$. 

## Homotopy Theory of $\mathbb{A}^1$

The notion of "stable range" in classical homotopy theory and topology comes from the following:

>[!thm] (Freudenthal)
>For any $n \geq 0$, the unit map $$S^n\to \Omega\Sigma S^n$$
>is **$(2n-1)$-connected**

Because $\mathbb{A}^{n+1}\backslash0\sim \mathbb{P}^1\land \mathbb{A}^n\backslash0$, we want to understand homotopy sheaves with respect to $\mathbb{P}^1$-suspension. However, this result is **false** in this case.


## Look-into


#### References

