---
date: 2024-07-08T21:21:00
tags:
  - AlgebraicGeometry
  - Homotopy
  - MotivicHomotopyTheory
  - KTheory
  - Article
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

These notes follow the exposition of Bachmann in[^1] for the sake of providing a crash-course introduction to $\mathbb{A}^1$-homotopy theory. These notes follow the perspective of $\infty$-categories, via the model of quasi-categories (a model of $(\infty,1)$-categories), which we now explore.

## Infinity Categories and $K$-Theory

In these notes we provide no recollection of definitions of infinity categories, leaving the primary work to notes such as [[Introduction to Quasi-Categories]] and [[Infinity Categories from Scratch]]. When referring to an $\infty$-category $\mathcal{C}$ with objects $X$ and $Y$, a morphism $X\to Y$ will refer to a point of $\mathsf{Map}_\mathcal{C}(X,Y)$ (in the quasi-categorical sense this is a $0$-simplex). 

An important example for our current work is the $\infty$-category $\mathcal{S}pc$ of spaces which has CW complexes (or Kan complexes, up to taste) as objects and function complexes (i.e. sets of continuous maps with compact-open topology, possibly weakly replaced by a weakly equivalent CW complex, or the mapping simplicial set) as mapping spaces. In this case $h\mathcal{S}pc$ is the **homotopy category of spaces**, which topologically has CW complexes as objects and homotopy classes of maps as hom sets, or simplicially has Kan complexes as objects and simplicial homotopy classes of maps as hom sets.

The $\infty$-category of $\infty$-categories, $\mathbb{C}at_\infty$ is also a natural construction. We also have, for any $\infty$-categories $\mathcal{C}$ and $\mathcal{D}$, an $\infty$-category $\mathsf{Fun}(\mathcal{C},\mathcal{D})$, of $(\infty-)$functors. It is in general difficult to write down $\infty$-functors in general, due to the infinite amount of data.

>[!example]
>If $\alpha:F\to G$ is a map of infinity functors, then $\alpha$ is an equivalence if and only if the image of $\alpha$ in $\mathsf{Fun}(h\mathcal{C},h\mathcal{D})$ is. I.e., $\alpha$ is an equivalence if and only if for all $X \in \mathcal{C}$, $\alpha_X:F(X)\to G(X)$ is an equivalence in $\mathcal{D}$.

If $\mathbb{1}$ is the terminal $1$-category, then $\text{Fun}(N_\bullet(\mathbb{1}),\mathcal{C})\simeq \mathcal{C}$ for a $\infty$-category $\mathcal{C}$.

### Limits and Colimits

We now begin interpreting 1-categorical structures in our context. As with limits and colimits in $1$-categories, it is important to first discuss initial and terminal objects of an infinity category.

An object $X\in \mathcal{C}$ is said to be **initial** if for all $Y \in \mathcal{C}$, $\mathsf{Map}_\mathcal{C}(X,Y)\simeq *$, or in other words the mapping space out of object is contractible. Note this implies that $X$ is also initial as an object of the homotopy category, $h\mathcal{C}$.

**Notation:** For $\infty$-categories $\mathcal{C},\mathcal{D}$, we have a functor $\mathcal{D}\to \mathsf{Fun}(\mathcal{C},\mathcal{D})$ which sends $d\in \mathcal{D}$ to the functor $d^*:\mathcal{C}\to *\xrightarrow{d}\mathcal{D}$. 

We can now consider colimits.

>[!def] Colimits in $\infty$-categories
>Given a functor $F:\mathcal{C}\to \mathcal{D}$, a **colimit** of $F$ is an object $d \in \mathcal{D}$ together with a morphism $\alpha:F\to d^*$ in $\mathsf{Fun}(\mathcal{C},\mathcal{D})$ such that for each $X \in \mathcal{D}$, the composite
>$$\mathsf{Map}_\mathcal{D}(d,X)\to \mathsf{Map}_{\mathsf{Fun}(\mathcal{C},\mathcal{D})}(d^*,X^*)\xrightarrow{\alpha\circ -}\mathsf{Map}_{\mathsf{Fun}(\mathcal{C},\mathcal{D})}(F,X^*)$$
>is an equivalence of spaces.

>[!example] Pushouts
>Let $\mathcal{C}$ be the $1$-category indexing pushout diagrams. Given $X,Y,Z \in \mathcal{D}$ and $Y\xleftarrow{\alpha} X\xrightarrow{\beta}Z$, a pushout is an object $P \in \mathcal{D}$ together with morphisms $f:Y\to P$ and $g:Z\to P$, as well as a homotopy $H:f\alpha\simeq g\beta$ in $\text{Map}_\mathcal{C}(X,P)$.
>
>Additionally, given another object $P'$, the canonical map
>$$\mathsf{Map}_\mathcal{C}(P,P')\to \mathsf{Map}_\mathcal{C}(Y,P')\times_{\mathsf{Map}_\mathcal{C}(X,P')}\mathsf{Map}_\mathcal{C}(Z,P')$$
>is an equivalence, where the right hand side is the homotopy pullback of spaces. As a space, this homotopy pullback is the space of triples $f':Y\to P',g':Z\to P'$, and $H':f'\alpha\simeq g'\beta$.

In other words, the space of maps from $P$ into $P'$ is equivalent to the space of pushout-candidates with vertex $P'$.
### Commutative Monoids

Throughout let $\mathcal{C}$ be an $\infty$-category with finite products.

>[!def] Commutative Monoids
>We write $\mathsf{CMon}(\mathcal{C})\subset \mathsf{Fun}(\text{Fin}_*,\mathcal{C})$ the full subcategory on those functors $M:\text{Fin}_*\to \mathcal{C}$ such that for all $n \geq 0$, the map $M(\underline{n})\to M(\underline{1})^n$, induced by the $n$ pointed maps $\underline{n}=\{*,1,...,n\}\to \underline{1}$ with fiber over $*$ of size $n$, is an equivalence.

As a special case, we have that $M(\underline{0})\simeq M(\underline{1})^0\simeq *$, the terminal object of $\mathcal{C}$.

Given $M \in \mathsf{CMon}(\mathcal{C})$, we have a map $$M(\underline{1})\times M(\underline{1})\simeq M(\underline{2})\to M(\underline{1})$$
which we call addition, and is induced by the map $\{*,1,2\}\to \{*,1\}$ given by sending $1,2$ to $1$ and $*$ to $*$. 

>[!example]
>If $\mathcal{C}$ is a $1$-category, then $\text{Fun}(\text{Fin}_*,\mathcal{C})$ is the $1$-functor category from pointed finite sets into $\mathcal{C}$. Then $\text{CMon}(\mathcal{C})$ has as objects functors $M:\text{Fin}_*\to \mathcal{C}$ such that $M(\underline{n})\cong M(\underline{1})^n$, and using the canonical map we witness $M(\underline{1})$ as an object of $\mathcal{C}$ with a multiplication. We also have the natural map $M(\underline{0})\cong *\to M(\underline{1})$ given by the unique pointed map $\{*\}\to \{*,1\}$. 
>
>This gives $M(\underline{1})$ the data of a commutative monoid object in $\mathcal{C}$. To see this note that the composite $M(\underline{1})\cong M(\underline{1})\times M(\underline{0})\to M(\underline{1})\times M(\underline{1})\to M(\underline{1})$ is represented by the pointed map $\{*,1\}\to \{*,1\}$ given by the identity. The left-unity is similar. Further, associativity is the statement that the composites $\{*,1,2,3\}\to \{*,1,2\}\to \{*,1\}$ that either send $1\mapsto 1\mapsto 1,2\mapsto 2\mapsto 1,$ and $3\mapsto 2\mapsto 1$, or $1\mapsto 1\mapsto 1,2\mapsto 1\mapsto 1, 3\mapsto 2\mapsto 1$ are identical, and so yield identical maps $M(\underline{3})\to M(\underline{1})$.
>
>Finally, commutivity follows from the fact that the composite $\{*,1,2\}\to \{*,1,2\}\to \{*,1\}$ given by $1\mapsto 2\mapsto 1,2\mapsto 1\mapsto 1$ is identical to the definition of the monoid operation.

If $M \in \text{CMon}(\mathcal{S}pc)$, composing with $\pi_0:\mathcal{S}pc\to \mathsf{Set}$ gives a commutative monoid in $\mathsf{Set}$.

>[!def] Grouplike Monoids
>An $M \in \text{CMon}(\mathcal{S}pc)$ is called **grouplike** if $\pi_0M$ is a group. Let $\text{CMon}(\mathcal{S}pc)^{gp}$ denote the full subcategory of grouplike monoids. A **group-completion** of $M$ is a $M^{gp} \in \text{CMon}(\mathcal{S}pc)^{gp}$ together with a map $M\to M^{gp}$ such that for any $Z \in \text{CMon}(\mathcal{S}pc)^{gp}$ we have an equivalence $$\mathsf{Map}_{\text{CMon}(\mathcal{S}pc)}(M,Z)\simeq \mathsf{Map}_{\text{CMon}(\mathcal{S}pc)}(M^{gp},Z)$$

Observe that we have an

$$\mathsf{Map}_{\text{CMon}(\mathcal{S}pc)}(M,Z)\simeq \mathsf{Map}_{\text{CMon}(\mathcal{S}pc)^{gp}}(M^{gp},Z)$$
which becomes an isomorphism
$$\text{CMon}(\pi_0M,\pi_0Z)\cong \text{Grp}(\pi_0(M^{gp}),\pi_0Z)$$
Assuming that all groups can be realized as the $\pi_0$ of a space, we have that $\pi_0(M^{gp})\cong \pi_0(M)^{gp}$.

>[!thm] McDuff-Segal
>Let $M \in \text{CMon}(\mathcal{S}pc)$. Then $M^{gp}$ exists and $$H_*(M^{gp})\simeq H_*(M)[\pi_0(M)^{-1}]$$
>where the right denotes the localization with respect to the Pontryagin ring structure.


### Algebraic $K$-theory of rings

Throughout let $\mathcal{V}$ denote a symmetric monoidal $1$-category. For $X \in \text{Fin}_*$, let $X' = X\backslash\{*\}$. Given a map $\alpha:X\to Y$ in $\text{Fin}_*$, we want a map $$\alpha_\otimes:\mathcal{C}^{X'}\to \mathcal{C}^{Y'}$$
given by $(c_x)_{x \in X'}\mapsto (\otimes_{x \in f^{-1}(y)}c_x)_{y \in Y'}$. However, we must be careful about ordering and associating the tensor product that appears in this definition. We don't have to be too careful, however, because the coherence theorem or symmetric monoidal categories tells us that any choice will give a well-defined object which is equivalent to any other choice by a unique isomorphism.

An issue with this choice approach is that in general we would have $\alpha_\otimes\beta_\otimes \neq (\alpha\beta)_\otimes$, which is desired. Instead, we construct a functor
$$\mathcal{C}^\otimes:\text{Fin}_*\to \mathsf{Cat}_1$$ by specifying $\mathcal{C}^\otimes(X)$ to be the category of objects $(c_x)_{x \in X'} \in \mathcal{C}^{X'}$, together with a choice of $f_\otimes^*((c_x)_{x \in X'}) \in \mathcal{C}^{Y'}$ for all $f:X\to Y$ in $\text{Fin}_*$. The morphisms are just the morphisms in $\mathcal{C}^{X'}$. On maps, $\alpha:X\to Y$ in $\text{Fin}_*$, we define $\alpha_\otimes:\mathcal{C}^\otimes(X)\to \mathcal{C}^\otimes(Y)$ by sending using the data of a choice equipped to each object, together with the data of choices coinciding with the initial object under pullback.

In other words, if $(c_x)_{x \in X'}$ with choices $f_\otimes^*(c_x)_{x \in X'}$ is an object of $\mathcal{C}^\otimes(X)$, then we take the image under $\alpha_\otimes$ to be $\alpha_\otimes^*(c_x)_{x \in X'}$ together with the data for each $g:Y\to Z$ of $(g\alpha)_\otimes^*(c_x)_{x \in X'}$ coming from our original object. In this way functoriality of $\mathcal{C}^\otimes$ is baked into the construction. Additionally, if $F:(c_x)_{x \in X'}\to (d_x)_{x \in X'}$ is a morphism in $\mathcal{C}^\otimes(X)$, then $\alpha_\otimes(F):\alpha_\otimes^*(c_x)_{x \in X'}\to \alpha_\otimes^*(d_x)_{x \in X'}$ is defined by applying $F_x$ to the appropriate components of the tensors, and then applying a (necessarily unique) isomorphism for commuting and associating the tensors if needed. As a composite of natural transformations, $\alpha_\otimes(F)$ is natural, and so a map in $\mathcal{C}^\otimes(X)$. By naturality of the associator and symmetror, as well as functoriality of the monoidal structor, $\alpha_\otimes$ is functorial.

The functor $\mathcal{C}^\otimes$ is in fact an element of $\text{CMon}(\mathsf{Cat}_1)$ (i.e. $\mathcal{C}^\otimes$ represents a strict symmetric monoidal category).

>[!rmk] Feeling (**NEED REF**)
>The above construction shows that given a symmetric monoidal category $\mathcal{C}$, one can produce a commutative monoid object $\mathcal{C}^\otimes$ which represents a *strict* symmetric monoidal category. Heuristically, this strict symmetric monoidal category should be the strictification of the category $\mathcal{C}$.

Moving on, the **classifying space**, or **nerve** construction gives an $\infty$-functor
$$B:\mathsf{Gpd}_1\to \mathcal{S}pc$$
Given a symmetric monoidal category $\mathcal{C}$, as above, we can compose $\mathcal{C}^\otimes$ with the core functor, $\mathsf{Cat}_1\to \mathsf{Gpd}_1,\mathcal{D}\mapsto \mathcal{D}^{\cong}$, obtained by discarding non-isomorphisms, before post-composing with the nerve $B$ to obtain a functor
$$B\mathcal{C}^{\otimes,\cong}:\mathsf{Fin}_*\to \mathcal{S}pc$$
which is a commutative monoid of spaces.

>[!def] $K$-theory space
>Let $R$ be a ring (possibly non-commutative). Let $\text{Proj}(R)$ be the category of finitely generated projective left $R$-modules, viewed as a symmetric monoidal category for the direct sum operation. The **$K$-theory space** of $R$ is
>$$K(R) = (B\text{Proj}(R)^{\otimes,\cong})^{gp} \in \text{CMon}(\mathcal{S}pc)$$
>The **algebraic $K$-theory groups of $R$** are
>$$K_i(R) := \pi_iK(R)$$


>[!example]
>Let $k$ be a field. Then $\text{Proj}(k) = \mathsf{Vect}_k$, since all modules over a field are free, and hence projective. The functor, before groupifying, that defines the $K$-theory space of $k$, sends $\underline{1}$ to the nerve of the category with objects finite dimensional vector spaces with choice of sum ordering and associating for every map in $\text{Fin}_*$, and maps are just $k$-linear isomorphisms. The monoid structure by a functor that pairs of vector spaces, with associated data, to their sum.
>
>$\pi_0$ of the nerve this construction gives a monoid, which as a set, is $\mathbb{N}$, and where the monoid operation gives a monoid isomorphic to $(\mathbb{N},+)$. Groupifying we find that $K_0(k) \cong \mathbb{Z}$.

The same argument as above shows that $K_0(R) \cong \mathbb{Z}$ for any local ring $R$. In this sense, $K_0(R)$, for a ring $R$, is measuring how close the category of finitely generated projective modules over $R$ is to being the category of free $R$-modules.

If $M \in \text{CMon}(\mathcal{S}pc)$ and $m \in M$, we obtain a map
$$\text{colim}(M\xrightarrow{+m}M\xrightarrow{+m}M\xrightarrow{+M}\cdots)\xrightarrow{\text{tel}(m)}M^{gp}$$
induced by taking the map out of the $i$th place to be $M\xrightarrow{-im}M^{gp}$.



## Unstable Motivic Homotopy Theory

<span style="color:rgb(255, 0, 0)">Warning:</span>  In these notes we treat size issues relatively naively, but in general, especially when dealing with presheaf and sheaf categories, it is important to be careful about whether all your data is of the appropriate size for your universe.

### Presheaves

The motivating theorem for much of this section, which has an analogous result in ordinary category theory, is that colimits and limits in functor categories exist if they exist in the codomain, and the evaluation functor preserves them.

>[!thm] Limits In Functor $\infty$-categories
>Let $\mathcal{C},\mathcal{D},\mathcal{E}$ be $\infty$-categories. If $\mathcal{E}$ has colimits (resp. limits) of shape $\mathcal{D}$, then so does $\mathsf{Fun}(\mathcal{C},\mathcal{E})$, and for any $X \in \mathcal{C}$, the evaluation functor $\text{ev}_X:\mathsf{Fun}(\mathcal{C},\mathcal{E})\to \mathcal{E}$ preserves them.

>[!def] 
>If $\mathcal{C}$ is an $\infty$-category, we write $\mathcal{P}(\mathcal{C}) := \mathsf{Fun}(\mathcal{C}^{op},\mathcal{S}pc)$ for the category of (space-valued) presheaves on $\mathcal{C}$.

The category $\mathcal{S}pc$ has all limits and colimits  (of appropriate size), and so $\mathcal{P}(\mathcal{C})$ does as well. These pre-sheaves of spaces will largely take the place of pre-sheaves of sets from ordinary category theory.

Further, as in ordinary category theory, we even have a Yoneda type embedding $\mathcal{C}\to \mathcal{P}(\mathcal{C})$ which satisfies the yoneda lemma, with isomorphism replaced by equivalence.

### Adjoints

Consider a functor of $\infty$-categories $R:\mathcal{D}\to \mathcal{C}$. Consider the $\infty$-category
$$\mathcal{E} = \text{Fun}(\mathcal{C},\mathcal{D})\times_{\text{Fun}(\mathcal{D},\mathcal{D})}\text{Fun}([1],\text{Fun}(\mathcal{D},\mathcal{D}))\times_{\text{Fun}(\mathcal{D},\mathcal{D})}\{id\}$$
with limits formed in $\mathsf{Cat}_\infty$, and where the map $\text{Fun}(\mathcal{C},\mathcal{D})\to \text{Fun}(\mathcal{C},\mathcal{D})$ is pre-composition with $R$, and the maps $\text{Fun}([1],\text{Fun}(\mathcal{D},\mathcal{D}))\to \text{Fun}(\mathcal{D},\mathcal{D})$ are evaluation at $0$ and $1$, respectively. Intuitively, $\mathcal{E}$ be thought of as the space of left adjoint candidates $(L:\mathcal{C}\to \mathcal{D},\alpha:LR\to \text{id}_\mathcal{D})$. Let $\mathcal{E}_0$ be the full subcategory of those pairs $(L,\alpha)$ such that for any $X \in \mathcal{C}$ and $Y \in \mathcal{D}$, the composite
$$\mathsf{Map}_\mathcal{C}(X,RY)\xrightarrow{L}\mathsf{Map}_\mathcal{D}(LX,LRY)\xrightarrow{\alpha_Y\circ-}\mathsf{Map}_\mathcal{D}(LX,Y)$$
is an equivalence.

>[!def] Adjoints
>A **left adjoint** of a functor $R$ is an object of $\mathcal{E}_0$, as defined above.

We have the following homotopical uniqueness result:

>[!proposition]
>The $\infty$-category $\mathcal{E}_0$ is either empty or equivalent to the terminal $\infty$-category. It follows that any two left adjoints are equivalent in an "essentially unique way".

### Presentability

For the construction of $\infty$-functors, a type of **adjoint functor theorem** will be extremely useful. This will rely on the notion of **presentable** $\infty$-categories (i.e. $\infty$-categories with all small colimits which can be realized as the category of $\kappa$-small $\text{Ind}$-objects for some small $\infty$-category and some regular cardinal $\kappa$).

>[!thm] Properties of Presentable $\infty$-categories
>1. Presentable $\infty$-categories have limits and colimits for all diagrams
>2. Let $\mathcal{D}$ be a diagram of presentable $\infty$-categories such that all the functors preserve colimits or all the functors preserve limits. Then the category $\lim\mathcal{D}$ is presentable
>3. Let $\mathcal{C}$ be an $\infty$-category. Then $\mathcal{P}(\mathcal{C})$ is presentable.

>[!example] Equivalences of Spaces
>Let $\mathcal{E} \subset \text{Fun}([1],\mathcal{S}pc) =:\mathcal{D}$ denote the full subcategory of functors corresponding to equivalences in $\mathcal{S}pc$. It turns out that $\mathcal{E}\simeq \mathcal{S}pc$, and so $\mathcal{E}$ is presentable. The inclusion $\mathcal{E}\hookrightarrow \mathcal{D}$ is a functor of presentable categories preserving limits. If $\mathcal{C}$ is a presentable $\infty$-category and $f:X\to Y$ is a morphism in $\mathcal{C}$, then evaluation at $f$ defines a functor $\mathcal{C}\to \text{Fun}([1],\mathcal{S}pc)$ which preserves limits.
>
>The pullback diagram of $\infty$-categories, $\mathcal{C}_f$, associated with these maps is then presentable, and corresponds to the full subcategory of $\mathcal{C}$ on those objects $T$ such that $f^*:\text{Map}_\mathcal{C}(Y,T)\hookrightarrow \text{Map}_\mathcal{C}(X,Y)$ is an equivalence.

**Aside on Size:** Recall that a cardinal can be considered as an equivalence class of bijective sets, or even ordinals. A cardinal can also be considered to be the smallest ordinal in such an equivalence class. We say a cardinal $\kappa$ is **regular** if the category $\mathsf{Set}_{<\kappa}$ of sets of cardinality less than $\kappa$ is closed under colimits of cardinality less than $\kappa$. Recall that in ordinary category theory an object is $\kappa$ small if its representable copresheaf preserves $\kappa$-filtered colimits.

>[!def] $\kappa$-filtered
>Let $\kappa$ be a regular cardinal and $\mathcal{C}$ an $\infty$-category. We call $\mathcal{C}$ $\kappa$-filtered if for every $\kappa$-small $\infty$-category $\mathcal{D}$ and every functor  $F:\mathcal{D}\to \mathcal{C}$, there is an object $c \in \mathcal{C}$ and a morphism $F\to c^* \in \text{Fun}(\mathcal{D},\mathcal{C})$.

We can now state the adjoint functor theorem in the context of $\infty$-categories.

>[!thm] Adjoint Functor Theorem
>Let $R:\mathcal{D}\to \mathcal{C}$ be a functor of presentable categories preserving limits and $\kappa$-filtered colimits for some regular cardinal $\kappa$. Then $R$ admits a left adjoint $L$.

^f7407e

In the category $\mathcal{S}pc$, finite limits commute with $\kappa$-filtered colimits for any $\kappa$, as in $\mathsf{Set}$ in ordinary category theory. This is another reason why the category of spaces is the suitable replacement for the category of sets in higher category theory.

<span style="color:rgb(255, 0, 0)">Warning:</span>  An $\infty$-category being finite is a stricter constraint than an ordinary category being finite. In particular, equalizers are **not** finite limits in this context.

### Motivic Spaces

Throughout let $S$ be a scheme and let $\mathsf{Sm}_S$ denote the category of smooth (i.e. locally of finite presentation, flat, and geometrically regular) schemes of finite type (i.e. locally of finite type and quasi-compact) over $S$. We now can begin discussing $\mathbb{A}^1$-homotopy theory.

>[!def] $\mathbb{A}^1$-invarinats
>We say $F \in \mathcal{P}(\mathsf{Sm}_S)$ is a **$\mathbb{A}^1$-invariant** if for every $X \in \mathsf{Sm}_S$, the canonical map $F(X)\to F(X\times \mathbb{A}^1)$ is an equivalence. We write $L_{\mathbb{A}^1}\mathcal{P}(\mathsf{Sm}_S)$ for the subcategory of $\mathbb{A}^1$-invariant presheaves.

From the previous discussion the inclusion $L_{\mathbb{A}^1}\mathcal{P}(\mathsf{Sm}_S)\hookrightarrow \mathcal{P}(\mathsf{Sm}_S)$ admits a left adjoint, which we denote by $L_{\mathbb{A}^1}$. In other words, the subcategory of $\mathbb{A}^1$-invariants forms a reflexive subcategory of the $\infty$-category of space valued pre-sheaves on smooth finite type schemes over $S$. Heuristically, one should expect a monadicity result that the $\mathbb{A}^1$-invariants for a kind of $\infty$-category of Eilenberg-Moore algebras.

We now induce a kind of topology on our relative scheme category.

>[!def] Nisnevich square.
>Let $X$ be a scheme. A **Nisnevich square** is a pullback square for an open immersion $i:U\to X$ along an etale map $p:V\to X$, such that $V\times_X(X\backslash U)\cong X\backslash U$, where $X\backslash U$ is given the **reduced induced scheme structure**.

>[!def] Nisnevich Local
>We say $F\in \mathcal{P}(\mathsf{Sm}_S)$ is **Nisnevich local** if for all $X,Y \in \mathsf{Sm}_S$, we have $F(X\coprod Y)\simeq F(X)\times F(Y)$, $F(\emptyset)\simeq *$, and for every Nisnevich square, applying $F$ gives a pullback square in spaces. Let $L_{Nis}\mathcal{P}(\mathsf{Sm}_S)$ denote the full subcategory of Nisnevich local presheaves.

Using the commutivity of filtered colimits and pullbacks we can see that the inclusion of this full subcategory admits a left adjoint $L_{Nis}$.

>[!def] Motivic Spaces Category
>We call $\mathcal{S}pc(S) := L_{mot}\mathcal{P}(\mathsf{Sm}_S) := L_{Nis}\mathcal{P}(\mathsf{Sm}_S)\cap L_{\mathbb{A}^1}\mathcal{P}(\mathsf{Sm}_S)$ the category of **motivic spaces**.

<span style="color:rgb(255, 0, 0)">Warning:</span> $L_{mot}$ is not given by the composite $L_{Nis}L_{\mathbb{A}^1}$ or the composite $L_{\mathbb{A}^1}L_{Nis}$, in general, as neither necessarily preserve objects in the subcategory defined by the other. However, it can be shown that $L_{mot}$ can be achieved by alternating composites of these two functors infinitely many times.

#### Localization


>[!def] $\mathbb{A}^1$-equivalence
>A map $f:F\to G \in \mathcal{P}(\mathsf{Sm}_S)$ is called an **$\mathbb{A}^1$-equivalence** if $L_{\mathbb{A}^1}f$ is an equivalence.

Note that by construction, for every $X \in \mathsf{Sm}_S$, the projection $X\times \mathbb{A}^1\to X$ is an $\mathbb{A}^1$-equivalence. Similarly, one can show that for $F \in \mathcal{P}(\mathsf{Sm}_S)$, the map $F\times\mathbb{A}^1\to F$ is an equivalence. **TBD** 

We hope to make the $\mathbb{A}^1$-localization explicit using the analogy with simplicial sets. Let $\mathbb{\Delta}$ denote the simplex category.

>[!def] Standard Cosimplicial Scheme
>The **standard cosimplicial scheme** is the functor:
>$$\mathbb{\Delta}^\bullet:\mathbf{\Delta}\to \mathsf{Sch}_S,\;[n]\mapsto \mathbb{\Delta}^n_S\subseteq \mathbb{A}^{n+1}_S$$
>where $\mathbb{\Delta}^n\subseteq \mathbb{A}^{n+1}$ is determined by the equation $T_0+\cdots +T_n = 1$, and the structure maps are induced by partial projections and face inclusions.

In particular, $\mathbb{\Delta^n}\cong \mathsf{Spec}(\mathbb{Z}[T_0,...,T_n]/\langle T_0+\cdots+T_n-1\rangle)$.  We now have a density type theorem for the $\mathbb{A}^1$-localization.

>[!thm]
>Let $F \in \mathcal{P}(\mathsf{Sm}_S)$ and $X \in \mathsf{Sm}_S$. Then we have an equivalence
>$$L_{\mathbb{A}^1}F(X) \simeq \text{colim}_{[n] \in \mathbb{\Delta}^{op}}F(X\times \mathbb{\Delta}^n)$$



For our other localization, $L_{Nis}\mathcal{P}(\mathsf{Sm}_S)$ is equivalent to a category of sheaves.


### $K$-theory

We briefly return to $K$-theory to discuss the algebraic $K$-theory space of a ring.

>[!thm] Algebraic $K$-theory Space
>Let $S$ be a **regular noetherian scheme** of finite dimension. Then there exists $K \in \mathcal{S}pc(S)$ (in the category of motivic spaces over $S$) such that for each $X \cong \mathsf{Spec}(A) \in \mathsf{Sm}_S$, we have $K(X)\simeq K(A)$, the **algebraic $K$-theory space** of the ring $A$.

^9a27fc

When $X$ is not affine in the above, we call $K(X)$ the **Thomason-Trobaugh K-theory** of $X$.

How do we interpret [[Bachmann K-theory and Motivic Homotopy Theory#^9a27fc]]? This is quite subtle, but heuristically the theorem says that the assignment of affine schemes to algebraic $K$-theory spaces is an $\mathbb{A}^1$-invariant that satisfies some descent condition (specifically **Nisnevich descent**). These interpretations rely crucially on the regularity assumption on $S$, since in general $K$-theory need *not* be an $\mathbb{A}^1$-invariant.

As one might hope from classical algebraic geometry/scheme theory, we have presheaves of groups, such as $\text{GL}_n$, on $\mathsf{Sm}_S$, given by sending $\text{GL}_n(\mathcal{O}_X(X))$. Taking a colimit over $n$, we obtain the pre-sheaf of groups, $\text{GL}$. If we take classifying spaces on each section we obtain $B\text{GL} \in \mathcal{P}(\mathsf{Sm}_S)$.  It turns out that in this context algebraic $K$-theory space functor is equivalent to
$$K\simeq L_{mot}(\mathbb{Z}\times B\text{GL}) \in \mathcal{S}pc(S)$$
in the category of motivic spaces.

Another perspective can be obtained by consider the Grassmannian scheme of $n$-planes in $\mathbb{A}^m$, $\text{Gr}_n(\mathbb{A}^m)$, and taking the colimit over $m$ to obtain $\text{Gr}_n = \text{colim}_m\text{Gr}_n(\mathbb{A}^n)$. For this object we have $L_{mot}B\text{GL}_n\simeq L_{mot}\text{Gr}_n$, and so taking the colimit over $n$ and using the previous observation we have
$$K\simeq L_{mot}(\mathbb{Z}\times \text{Gr}_\infty)$$


## Stable Motivic Homotopy Theory

### Pointed Categories

>[!def] Pointed $\infty$-category
>An $\infty$-category $\mathcal{C}$ is said to be **pointed** if it admits a $0$-object (i.e. an object which is simultaneously initial and final).

Moving forward let $\text{Pr}$ denote the $\infty$-category of presentable $\infty$-categories with colimit preserving functors between them.

>[!proposition]  Initial Pointed Presentable Category
>Let $\mathcal{C}$ be a presentable $\infty$-category with a final object $*$. Then the $\infty$-category
>$$\mathcal{C}_* := \{*\}\times_\mathcal{C}\text{Fun}([1],\mathcal{C})$$
>is the initial, pointed presentable $\infty$-category under $\mathcal{C}$ in $\text{Pr}$, where the functor $\mathcal{C}\to \mathcal{C}_*$ is given by $c\mapsto (*\to c\amalg *)$. 

An object of $\mathcal{C}_*$ consists an object $c \in \mathcal{C}$ and a morphism $*\to c$. 

>[!def] Pointed Motivic Spaces
>Write $\mathcal{S}pc(S)_*$ for the category of **pointed motivic spaces**.

>[!def] Cofiber Sequence 
>A pushout square of the form
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20B%20%5C%5C%0A%09%7B*%7D%20%26%20C%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D180%7D%2C%20draw%3Dnone%2C%20from%3D2-2%2C%20to%3D1-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="begin{tikzcd}[white]	A &amp; B \\	{*} &amp; C	\arrow[from=1-1, to=1-2]	\arrow[from=1-1, to=2-1]	\arrow[from=1-2, to=2-2]	\arrow[from=2-1, to=2-2]	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=180}, draw=none, from=2-2, to=1-1]\end{tikzcd}" /></p>
>
>and denoted $A\to B\to C\simeq B/A$.

### Symmetric Monoidal Categories

We now give a brief introduction to symmetric monoidal $\infty$-categories.

>[!def] Symmetric Monoidal $\infty$-categories
>A **symmetric monoidal $\infty$-category** is an object of $\text{CMon}(\mathsf{Cat}_\infty)$ (note the analogy with strict symmetric monoidal categories as commutative monoid objects in $\mathsf{Cat}$). A **presentably symmetric monoidal $\infty$-category** is a symmetric monoidal $\infty$-category $\mathcal{C}$ such that $\mathcal{C}$ is presentable and the tensor product preserves colimits in each variable separately.
>
>We write $\text{CAlg}(\text{Pr})$ for the category of presentably symmetric monoidal categories and symmetric monoidal, cocontinuous, functors.

We will write $I$ for the unit object of a general symmetric monoidal $\infty$-category.

>[!thm] Cartesian Monoidal $\infty$-category
>Let $\mathcal{C}$ be an $\infty$-category with finite products. Then there exists a canonical symmetric monoidal category $\mathcal{C}^\times \in \text{CMon}(\mathsf{Cat}_\infty)$ with underlying object $\mathcal{C}$ and tensor product given by the cartesian product.

This theorem implies that $\mathcal{S}pc(S)$, the category of motivic spaces over $S$, is a symmetric monoidal $\infty$-category under cartesian products. Additionally, $\mathcal{S}pc(S)$ is cartesian closed, which implies that it is presentably symmetric monoidal.

>[!thm] Smash Product Structure
>Let $\mathcal{C}$ be a presentable $\infty$ category. Write $\mathcal{C}_*^\land$ for the initial object of $\text{CAlg}(\text{Pr})$ under $\mathcal{C}^\times$ such that the underlying category is pointed. Then the underlying category of $\mathcal{C}^\land_*$ is $\mathcal{C}_*$ and the symmetric monoidal operation is given by
>$$X\land Y = X\times Y/X\lor Y$$
>where $X\lor Y = X\amalg_*Y$ is the coproduct in $\mathcal{C}_*$.
>

Again we find that $\mathcal{S}pc(S)_*$, the pointed motivic category, is presentably symmetric monoidal. 

### Stabilization

>[!def] Stabilization
>Let $\mathcal{C} \in \text{CAlg}(\text{Pr})$ and $X \in \mathcal{C}$. Given $\mathcal{D} \in \mathcal{C}/\text{CAlg}(\text{Pr})$ we say that $X$ **acts invertibly** on $\mathcal{D}$ if the functor $\mathcal{D}\to \mathcal{D}$ informally given by $d\mapsto X\otimes d$, is an equivalence. We denote by $\mathcal{C}[X^{-1}]$ the initial object of $\text{CAlg}(\text{Pr})$ under $\mathcal{C}$ on which $X$ acts invertibly, and call it the **stabilization of $\mathcal{C}$ with respect to $X$**.

>[!example]
>Let $\mathcal{C} = \mathcal{S}pc_*$ (the $\infty$-category of pointed spaces) and let $X = S^1$. Then the category $\mathcal{C}[(S^1)^{-1}]$ is called the **stable $\infty$-category**. We denote the stable $\infty$-category by $\mathcal{SH}$. The homotopy category, $h\mathcal{SH}$, is called the **stable homotopy category** (constructed by Boardman). We denote the stabilization functor $\mathcal{S}pc_*\to \mathcal{SH}$ by $\Sigma^\infty$, and the tensor on $\mathcal{SH}$ by $\land$.

>[!def] Stable Motivic $\infty$-category
>Let $\mathbb{P}^1 \in \mathcal{S}pc(S)_*$ denote $\mathbb{P}^1$ pointed at $1$. The category $\mathcal{SH}(S) := \mathcal{S}pc(S)_*[(\mathbb{P}^1)^{-1}]$ is called the **stable motivic $\infty$-category**. We write $\Sigma^\infty:\mathcal{S}pc(S)_*\to \mathcal{SH}(S)$ for the stabilization functor, and $\land$ for the tensor product in $\mathcal{SH}(S)$.

The following result gives a first step at making these abstract stabilizations more tractible, while helping to explain why they are referred to as stabilizations, in analogy with stable homotopy theory in the classical setting.

>[!thm] Stability
>Let $\mathcal{C} \in \text{CAlg}(\text{Pr})$ be a presentably symmetric monoidal category and let $X \in \mathcal{C}$ be an object in the underlying category. Suppose that for some $n \geq 2$, the cyclic permutations on $X^{\otimes n}$ are homotopic to the identity. Then the presentable category underlying the stabilization $\mathcal{C}[X^{-1}]$ is equivalent to the category
>$$Sp^\mathbb{N}(\mathcal{C},X) = \text{eq}\left(\text{Fun}(\mathbb{N},\mathcal{C})\rightrightarrows \text{Fun}(\mathbb{N},\mathcal{C})\right)$$
>where one of the two endomorphisms is the identity, and the other is $\Omega:(X_n)_n\mapsto (\Omega_XX_{n+1})_n$, where $\Omega_X$ is the right adjoint to $(-)\otimes X:\mathcal{C}\to \mathcal{C}$ (which exists by an $\infty$-categorical adjoint functor theorem dual to [[Bachmann K-theory and Motivic Homotopy Theory#^f7407e]]).

Objects of $Sp^\mathbb{N}(\mathcal{C},X)$ are sequences $(c_1,c_2,...)$ of objects $c_i \in \mathcal{C}$ together with "bonding maps" $c_i\simeq \Omega_Xc_{i+1}$, and morphisms the appropriate commutative diagrams.

It can be shown that if $S^1 \in \mathcal{S}pc(S)_*$ denotes the constant presheaf with values the circle $S^1$ and $\mathbb{G}_m$ the image of the representable sheaf $\mathbb{A}^1\backslash 0$ at $1$, then $S^1\land \mathbb{G}_m\simeq \mathbb{P}^1$. This property implies that the operations
$$\Sigma^{1,1} := \Sigma_{\mathbb{G}_m}:=(-) \land \Sigma^\infty \mathbb{G}_m:\mathcal{SH}(S)\to \mathcal{SH}(S)$$
and
$$\Sigma^{1,0} := \Sigma_{S^1}:=(-) \land \Sigma^\infty S^1:\mathcal{SH}(S)\to \mathcal{SH}(S)$$
are invertible. For $p,q \in \mathbb{Z}$, we write $$\Sigma^{q,p} := (\Sigma^{1,1})^{\circ p}(\Sigma^{1,0})^{\circ (q-p)}$$
>[!def] Bigraded Homotopy Groups
>For $E \in \mathcal{SH}(S)$, an object of the stable motivic $\infty$-category, the groups
>$$\pi_{i,j}(E) := [\Sigma^{i,j}I,E]=\pi_0\text{Map}_{\mathcal{SH}(S)}(\Sigma^{i,j}I,E)$$
>are called the **bigraded homotopy groups of $E$**. We also write
>$$\pi_i(E_j) := [\Sigma^iI,\Sigma^{j,j}E] = \pi_{i-j,-j}(E)$$

We refer to $\Sigma^{1,0}$ as **suspension**, in analogy with the classical topological construction. The statement that $\Sigma^{1,0}$ is invertible says that $\mathcal{SH}(S)$ is a **stable $\infty$-category**. Such $\infty$-categories have triangulated homotopy categories. In particular, this means that if $A\to B\to C$ is a cofiber sequence in $\mathcal{SH}(S)$, then for any $q \in \mathbb{Z}$ we obtain a long exact sequence
$$\cdots \to \pi_{*,q}A\to \pi_{*,q}B\to \pi_{*,q}C\to \pi_{*-1,q}A\to \cdots$$
>[!def] Milnor-Witt $K$-theory
>Let $k$ be a field. The graded ring $K_*^{MW}(k)$, called the **Milnor-Witt $K$-theory** of $k$, is given by the quotient of the free non-commutative algebra on generators $[a]$ in degree $1$ for $a \in k^\times$, and a generator $\eta$ in degree $-1$, subject to the relations
>1. $\eta[a] = [a]\eta$
>2. $[a][1-a] = 0$, $\forall a \neq 0,1$
>3. $[ab] = [a]+[b]+\eta[a][b]$,
>4. $\eta(2+\eta[-1])=0$
>The graded ring $K_*^M(k) := K_*^{MW}(k)/\langle \eta\rangle$ is called the **Milnor $K$-theory of $k$**.








#### References

[^1]: Bachmann, T. (n.d.). Algebraic K-theory from the viewpoint of motivic homotopy theory.
