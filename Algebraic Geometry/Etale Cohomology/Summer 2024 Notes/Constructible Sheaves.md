---
date: 2024-06-28T19:01:00
tags:
  - AlgebraicGeometry
  - EtaleCohomology
  - Sheaves
  - Schemes
type: Notes
summary:
---
## Introduction

These notes provide an introduction and motivation for constructible sheaves, as provided in lecture by Levi Poon during the Etale Cohomology summer reading group at UIUC.

Why do we care about constructible things? Often we care about locally constant things (i.e. locally constant sheaves). However, in non-constructible contexts a lot of the nice properties we want for computations are not available.

## Constructible Sheaves

Throughout we will write $X$ for a Noetherian scheme and $A$ for a Noetherian ring. Note there exists a theory without these Noetherian hypotheses, but they will help simplify our discussion, and will be important in giving us the ability to perform **Noetherian induction**.

>[!def] Locally Constant sheaves on a site
>Let $\mathcal{F}$ be a sheaf (of sets, abelian groups, $A$-modules, etc.) on the etale site $X_{et}$. $\mathcal{F}$ is said to be **locally constant** if there exists an etale cover, $\{X_i\to X\}$, such that $\mathcal{F}\vert_{X_i}$ is isomorphic to a constant sheaf.

>[!def] Constructible Sheaves
>Let $\mathcal{F}$ be a sheaf on $X_{et}$. Then $\mathcal{F}$ is said to be **constructible** if there exists a decomposition $X = \bigcup_{i=1}^nX_i$, where the $X_i$ are locally closed subschemes, such that $\mathcal{F}\vert_{X_i}$ is locally constant with finite stalk (abelian groups, sets)/finitely generated stalkes/$A$ ($A$-modules).

We now move onto some basic properties of constructible sheaves.

>[!lem] Locally Constant with Finite Stalk
>Let $\mathcal{F}$ be a sheaf of sets on $X_{et}$. Then the following are equivalent:
>1. $\mathcal{F}$ is locally constant with finite stalk
>2. $\mathcal{F}$ is representable, i.e. $\mathcal{F}\cong y^Y$, such that $Y\to X$ is finite etale
>3. There exists a finite surjective etale map $\pi:Y\to X$ such that $\pi^*\mathcal{F}$ is constant on connected components.

>[!lem] Characterization of Constructability
>If $\mathcal{F}$ is a sheaf of sets (resp. $A$-modules), $\mathcal{F}$ is constructible if and only if for all irreducible closed subschemes $Y \subseteq X$, there exists $V \neq \emptyset$ open such that $\mathcal{F}\vert_V$ is locally constant with finite (resp. finitely generated) stalks.


>[!proposition]
>If $f:U\to X$ is of finite type and etale, then $y^U$ is constructible and $f_!A$ is constructible.

The idea is that all constructible things are of this form, as long as we allow "more general things" for $U$.

We can think of constructability as a kind Noetherian condition. We try to make this more precise in the following.

>[!proposition] Constructible Classification
>Let $\mathcal{F}$ be a sheaf of $A$-modules. Then the following are equivalent:
>1. $\mathcal{F}$ is constructible
>2. $\mathcal{F}$ is Noetherian (in the sense of chains of subsheaves)
>3. There exists an exact sequence $A_V\to A_U\to \mathcal{F}\to 0$ such that $f:U\to X$ and $g:V\to X$ are finite type and etale, and $A_U = f_!A, A_V = g_!A$.

The main idea for the proof is to use the fact we're dealing with a Noetherian scheme and ring, and so can do Noetherian induction.

>[!corollary] Constructible Classification for Abelian Group valued Sheaves
>Let $\mathcal{F}$ be a sheaf of abelian groups. Then the following are equivalent:
>1. $\mathcal{F}$ is constructible as a sheaf of abelian groups
>2. $\mathcal{F}$ is constructible as a sheaf of $\mathbb{Z}/n$-modules for some $n \neq 0$
>3. $\mathcal{F}$ is Noetherian and torsion.

>[!corollary] Constructible Sheaves is an Abelian Category
>The full subcategory of constructible sheaves of $A$-modules is an abelian subcategory closed under extensions.

>[!thm]
>Let $f:X\to Y$ be finite and $\mathcal{F}$ a sheaf of $A$-modules on $X_{et}$. Then $\mathcal{F}$ is constructible if and only if $f_*\mathcal{F}$ is constructible.

This theorem is true more generally for proper morphisms.

## Algebraic Spaces
\
>[!def] Etale Equivalence Relation
>Let $X$ be a scheme and let $Y\to X$ be a scheme over $X$. An **etale equivalence relation** on $Y$ is a monomorphism $(i_1,i_2):R\hookrightarrow Y\times_XY$ of $X$-schemes such that 
>1. $i_1,i_2$ are etale
>2. for all $T \in \mathsf{Sch}_X$, $R(T)$ (the $T$-points of $R$) is an equivalence relation on $Y(T)$ (by the induced map $R(T)\hookrightarrow Y(T)\times_{X(T)}Y(T)$)


>[!def] Algebraic Spaces
>A sheaf of sets $\mathcal{A}$ on $(\mathsf{Sch}/X)_{et}$ is an **algebraic space** if $\mathcal{A}\cong Y/R$ for some $Y$ and $R$ an etale equivalence relation on $Y$.


>[!example]
>1. Every $X$-scheme is an algebraic space over $X$ using the trivial relation on itself (the diagonal) viewed as a sheaf by the Yoneda embedding.
>2. If $\mathcal{G}$ is a discrete group acting on $X$, such that $\mathcal{G}\times X\to X\times X$, $(g,x)\mapsto (x,gx)$, is a monomorphism, then $X\times X/\mathcal{G}\times X \cong X/\mathcal{G}$ is an algebraic space over $\mathbb{Z}$.


>[!def] Representable morphism of algebraic spaces
>Let $f:\mathcal{A}\to \mathcal{B}$ be a morphism of algebraic spaces (i.e. a morphism of sheaves). Then $f$ is **representable** if for all $Y\to X$, and morphism $y^Y\to \mathcal{B}$, then the pullback $\mathcal{A}\times_\mathcal{B}y^Y$ is representable (i.e. represents a scheme).

If we have a property $P$ which is "nice" and $f$ is representable, then $f$ is $P$ if and only if for all $y^Y\to \mathcal{B}$, the map $\mathcal{A}\times_\mathcal{B}y^Y\to y^Y$ in the context of the above definition is $P$.

If $\mathcal{A}$ is an algebraic space of the form $Y/R$, then we say $\mathcal{A}\to y^X$ is etale if $Y$ is of finite type over $X$ (**Note**: This isn't the full level of generality).

>[!thm]
>$\mathcal{A}$ is an algebraic space if and only if the diagonal $\mathcal{A}\to \mathcal{A}\times \mathcal{A}$ is representable and there exists an etale surjective morphism $Y\to \mathcal{A}$.


>[!thm]
>Let $X$ be a scheme, $\mathcal{F}$ a sheaf of sets on $X_{et}$ (the small etale site), then there exists a unique algebraic space (up to isomorphism) etale over $X$, $\widetilde{\mathcal{F}}$, such that $\widetilde{\mathcal{F}}\vert_{X_{et}} \cong \mathcal{F}$.



