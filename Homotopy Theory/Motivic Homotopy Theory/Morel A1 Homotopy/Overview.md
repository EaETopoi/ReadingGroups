---
date: 2024-07-08T07:21:00
tags:
  - AlgebraicGeometry
  - Homotopy
  - MotivicHomotopyTheory
  - TextbookNotes
type: Summary
summary:
---
## Introduction

The set of notes in this folder contain an investigation of F Morel's book, *$\mathbb{A}^1$-Algebraic  Topology over a Field*[^1]. In order to make these notes more coherent, in this brief note we provide suitable conventions and preliminary definitions which will provide helpful references while reading the text.

## Preliminaries and Conventions

### Scheme Preliminaries

We will begin with useful pre-requisite definitions from algebraic geometry which will help in our study. In particular, we now recall the definitions of a number of important properties of morphisms of schemes. Note that, by abuse of notation, one often refers to a scheme $X$ over $S$ as satisfying these properties, by which one means that the structure morphism $X\to S$ satisfies these properties. We use Vakil's *Rising Sea*[^2] for the majority of these definitions.

>[!def] Locally of Finite Type and Finite Type Morphisms
>A morphism of schemes $f:X\to Y$ is **locally of finite type** if for all open affines $V \subseteq Y$, $V \cong \mathsf{Spec}(B)$, and any open affine $U \subseteq f^{-1}(V)$, $U \cong \mathsf{Spec}(A)$, the induced cring map $B\to A$ is finitely generated (i.e. $A\cong B[x_1,...,x_n]/I$).
>
>$f:X\to Y$ is of **finite type** if it is locally of finite type and quasi-compact.

>[!def] Flat
>A morphism of schemes $f:X\to Y$ is **flat** if for all $x \in X$, the morphism on the level of stalks, $f^\#_x:\mathcal{O}_{f(x),Y}\to \mathcal{O}_{x,X}$, is flat (i.e. $\mathcal{O}_{x,X}$ is a flat $\mathcal{O}_{f(x),Y}$-module).

>[!def] Locally of Finite Presentation
>A morphism of schemes $f:X\to Y$ is **locally of finite presentation** if for each open affine $V \subseteq Y$, $V \cong \mathsf{Spec}(B)$, $f^{-1}(V)= \bigcup_{i \in I}U_i$, with $U_i \cong \mathsf{Spec}(A_i)$, where the induced cring maps $B\to A_i$ are finitely presented (i.e. $A_i \cong B[x_1,...,x_n]/(f_1,...,f_r)$).

>[!def] Unramified
>A morphism of schemes $f:X\to Y$ is **unramified** if
>1. $f$ is locally of finite presentation
>2. for each $x \in X$, $\kappa(x)/\kappa(f(x))$ is a separable extension
>3. for each $x \in X$, $f^\#_x(\mathfrak{m}_{Y,f(x)})\mathcal{O}_{X,x} = \mathfrak{m}_{X,x}$.

>[!def] Smooth
>A morphism of schemes $f:X\to Y$ is smooth if it is locally of finite presentation, flat, and for every **geometric point** $\overline{y}\to Y$, the fiber $X_\overline{y} = X\times_Y\overline{y}$, is **regular**. Here a **geometric point** is a morphism $\overline{y}\to Y$ such that $\overline{y} = \mathsf{Spec}(k)$ for some algebraically closed field $k$. Further, a scheme $X$ is regular if for each $x \in X$, the Krull dimension of $\mathcal{O}_{X,x}$ matches the dimension of the Zariski cotangent space, $\mathfrak{m}_{X,x}/\mathfrak{m}_{X,x}^2$, as a vector space over $\kappa(x) = \mathcal{O}_{X,x}/\mathfrak{m}_{X,x}$.

>[!def] Etale
>A morphism of schemes $f:X\to Y$ is **Etale** if
>1. $f$ is unramified
>2. $f$ is flat

Equivalently, a morphism is etale if and only if it is smooth and unramified.

>[!def] Dimension
>The **dimension** of a scheme $X$ (or more generally a topological space) is the supremum of the lengths of chains of closed irreducible subsets of $X$, where indexing starts at $0$.

>[!def] Codimension
>If $Y$ is a subset of a scheme $X$, the **codimension** of $Y$ in $X$ is the supremum of the lengths of chains of closed irreducible subsets of $X$ containing $\overline{Y}$.

>[!def] Nisnevich Topology
>A morphism of schemes $f:X\to Y$ is **Nisnevich** if it is etale and for every point $y \in Y$, there exists $x \in f^{-1}(y)$ such that the induced map of residues $\kappa(y)\to \kappa(x)$ is an isomorphism. 
>
>A family of morphisms $\{u_\alpha:X_\alpha\to X\}$ is a **Nisnevich cover** if each morphism is etale and the family is mutually Nisnevich in the sense that for  all $x \in X$, there exists $\alpha$ and $y \in u_\alpha^{-1}(x)$ such that the induced map $\kappa(x)\to \kappa(y)$ is an isomorphism. These covers give a pre-topology on the category of schemes.

### Algebraic Preliminaries

>[!def] Perfect Field
>A field $k$ is **perfect** if $\text{char}(k) = 0$ or $\text{char}(k) = p > 0$ and $\sigma:x\mapsto x^p$ is an automorphism of $k$.

>[!def] Transcendence
>Let $E/F$ be a field extension and let $F'$ and $F''$ be intermediate field extensions. We define the equivalence relation $F'\sim F''$ be requiring that $F'F''$ is algebraic over both $F'$ and $F''$.
>
>Then a **transcendence basis** of $E/F$ is a set of elements $\{x_i\}_{i \in I} \in E$ that are **algebraically independent** over $F$, and such that $F(\{x_i\}_{i \in I}) \sim E$. The cardinality of a transcendence basis is an invariant of an extension, and is called the **transcendence degree** of $E$ over $F$.

>[!def] Valuation Ring
>An integral domain $D$ is a **valuation ring** if for all $x \in F(D)$, its field of fractions, $x \in D$ or $x^{-1} \in D$. Equivalently, $D$ is a valuation ring if and only if any of the following hold:
>1. $D$ is an local subring of a field $F(D)$ which is maximal with respect to **dominance/refinement**, where a local subring $(A,\mathfrak{m}_A)$ dominates a local subring $(B,\mathfrak{m}_B)$ if and only if $A \supseteq B$ and $\mathfrak{m}_A\cap B = \mathfrak{m}_B$
>2. The ideals of $D$ are **totally ordered** by inclusion
>3. The principal ideals of $D$ are **totally ordered** by inclusion
>4. There exists a **totally ordered abelian group** $\Gamma$ and a **valuation** $\nu:F(D)\to \Gamma\cup\{\infty\}$ such that $D = \{x \in F(D)\,:\,\nu(x) \geq 0\}$
>
>A valuation ring is **discrete** if $\Gamma \cong \mathbb{Z}$. Equivalently a discrete valuation ring is a non-field which is a local principal ideal domain, or a valuation ring which is Noetherian.

In general, the valuation group can be taken to be $F(D)^\times/D^\times$.

## Notation

- $\mathsf{Sm}_k$ will denote the category of smooth finite type $k$-schemes (i.e. smooth + quasi-compact) where $k$ is a perfect field.
- $\mathcal{F}_k$ will denote the category of field extensions of $k$ of finite transcendence degree.
- For a scheme $X$ and an integer $i$, we write $X^{(i)}$ for the set of points of codimension $i$.
- The category $\mathsf{Sm}_k$ is endowed with the **Nisnevich** topology (ala Grothendieck).
- A **space** will refer to a simplicial object in the category of sheaves of sets on $\mathsf{Sm}_k$. 
- $\mathsf{Sm}'_k$ will denote the category of **essentially smooth $k$-schemes**. Here an **essentially smooth $k$-scheme** is a scheme $X\to k$ such that $X$ is Noetherian and the limit of a left filtering system $(X_\alpha)_{\alpha \in A}$ which each transition $X_\beta\to X_\alpha$ being an etale affine morphism between smooth $k$-schemes.
- Given a pre-sheaf of sets on $\mathsf{Sm}_k$, $P:\mathsf{Sm}_k^{op}\to \mathsf{Set}$, and an essentially smooth $k$-scheme $X = \lim_{\alpha}X_\alpha$, we set $$F(X) := \text{colim}_{\alpha}F(X_\alpha)$$

>[!example]
>- For any $F \in \mathcal{F}_k$, the $k$-scheme $\mathsf{Spec}(F)$ is essentially $k$-smooth.
>- For each $x \in X \in \mathsf{Sm}_k$, the local scheme $X_x := \mathsf{Spec}(\mathcal{O}_{X,x})$ of $X$ at $x$, as well as its henselization $X_x^h := \mathsf{Spec}(\mathcal{O}_{X,x}^h)$, are essentially smooth $k$-schemes. The complement of the  closed point in these types of schemes are also essentially smooth over $k$.



#### References

[^1]: Morel, F. (2012). A1-Algebraic Topology over a Field (Vol. 2052). Berlin, Heidelberg: Springer. https://doi.org/10.1007/978-3-642-29514-0
[^2]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024
