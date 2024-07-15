---
date: 2024-06-09T11:29:00
tags:
  - AlgebraicGeometry
  - Topoi
  - CategoryTheory
  - Sheaves
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

In these notes we provide an introduction to the theory of geometric morphisms between topoi, following the work of Mac Lane and Moerdijk[^1]. Geometric morphisms can be motivated by the direct and inverse image functors appearing for sheaves on spaces. In fact, these give a host of examples of such functors, and when considering morphisms within topoi we also obtain a host of examples of geometric morphisms between slice categories of the topos (which are themselves topoi). This is briefly discussed in the note [[Sheaves on Sites]].

## Basics of Geometric Morphisms

As motivated by our familiarity with direct and inverse image functors, and their adjunction, we define a geometric morphism as follows.

>[!def] Geometric Morphism
>A **geometric morphism** between topoi, $f:\mathcal{E}\to \mathcal{D}$, is a pair of functors $f_*:\mathcal{E}\to \mathcal{D}$ and $f^*:\mathcal{D}\to \mathcal{E}$ such that $f^*\dashv f_*$ and $f^*$ is left exact (i.e. it preserves finite limits).

All geometric morphisms between sheaf categories on spaces arise from morphisms of the spaces themselves, assuming the codomain is suitably separated (e.g. Hausdorff).


>[!exercise]
>Given topological spaces $X$ and $Y$, with $Y$ Hausdorff, and a geometric morphism $p:\mathsf{Sh}(X)\to \mathsf{Sh}(Y)$, prove that there exists a unique map $f:X\to Y$ which induces the geometric morphism. (Hint: first construct $f^{-1}:\mathsf{Top}(Y)\to \mathsf{Top}(X)$, and then obtain $f:X\to Y$)

`\begin{proof}`
By definition $p$ is  pair of functor $p_*:\mathsf{Sh}(X)\to \mathsf{Sh}(Y)$ and $p^*:\mathsf{Sh}(Y)\to \mathsf{Sh}(X)$ such that $p^* \dashv p_*$ and $p^*$ is left-exact (i.e. preserves finite limits). Recall that the terminal object in $\mathsf{Sh}(Y)$ is the constant one-object pre-sheaf $1$. Note that a sub-object of $1$ is a sheaf $\mathscr{F}$ which is either empty or $1$ on each open set. Further, since it is a sheaf $\mathscr{F}$ must in fact be $j_!(1\vert_U)$, the skyscraper sheaf for $1$ associated with some open set $U$, given by the union of all open sets on which $\mathscr{F}$ is $1$.

Since $p^*$ is left exact it sends $1$ to $1$, and sub-objects of $1$ to sub-objects of $1$. Thus, $p^*$ restricts to a map of open subsets $\mathsf{Top}(Y)\to \mathsf{Top}(X)$ which preserves finite limits and all colimits. We define $f:X\to Y$ by $f(x) = y$ if and only if $x \in f^*(V)$ for all neighborhoods $V$ of $y$. Since $Y$ is assumed Hausdorff, this is well-defined. Further, $f^{-1}(V) = p^*(V)$ for any open set $V$, so $f$ is continuous. Further, for any sheaf $\mathscr{F}$ on $X$ and any open set $V \subseteq Y$,
$$f_*(\mathscr{F})(V) = \mathscr{F}(f^{-1}(V))\cong \mathsf{Sh}(X)(f^{-1}(V),\mathscr{F}) = \mathsf{Sh}(X)(p^*V,\mathscr{F})$$
Using the adjunction and yoneda again this is isomorphic to $p_*(\mathscr{F})(V)$. Thus $f_*\cong p_*$, and by uniqueness of adjoints $f^*\cong p^*$.
`\end{proof}`

Another important example comes from the inclusion $\mathsf{Sh}_j\mathcal{E}\to \mathcal{E}$ of sheaves on a topos with a Lawvere-Tierney topology and its left exact left adjoint, the associated sheaf functor. More about this example can be found in [[Lawvere-Tierney Topologies]].

With geometric morphisms we obtain a 2-category of topoi, with 0-cells topoi, 1-cells geometric morphisms, and 2-cells natural transformations either $\alpha:f^*\Rightarrow g^*$ or equivalently $\beta:g_*\Rightarrow f_*$, which correspond to each-other under the commutative diagram
$$\begin{CD}\mathcal{E}(g^*\mathscr{F},\mathscr{G}) @>\cong >> \mathcal{D}(\mathscr{F},g_*\mathscr{G}) \\ @V-\circ \alpha_\mathscr{F}VV @VV\beta_\mathscr{G}\circ -V \\ \mathcal{E}(f^*\mathscr{F},\mathscr{G}) @>>\cong > \mathcal{D}(\mathscr{F},f_*\mathscr{G}) \end{CD}$$
### Tensor Product

We recall some notions from [[Kan Extensions]]. Namely, if $\mathcal{C}$ is a small category and $\mathcal{E}$ is a cocomplete category, then a functor $A:\mathcal{C}\to \mathcal{E}$ has a pointwise left Kan extension along the yoneda embedding $y:\mathcal{C}\to \mathsf{Set}^{\mathcal{C}^{op}}$, $L_A:\mathsf{Set}^{\mathcal{C}^{op}}\to \mathcal{E}$, which is defined in terms of colimits/co-ends, and so commutes with colimits. Since a pre-sheaf category on a small category is cocomplete, locally small, well-powered, and has a small generating set, if $\mathcal{E}$ is locally small we have that $L_A$ has a right adjoint $R:\mathcal{E}\to \mathsf{Set}^{\mathcal{C}^{op}}$, which by yoneda must be given by
$$R(E)(C) = \mathcal{E}(A(C),E)$$
Further, by [[Kan Extensions#^42a123]], and the observation that $(y\downarrow P)$ for a pre-sheaf $P$ on $\mathcal{C}$ is exactly the category of elements of $P$, and so
$$L_A(P) = \text{colim}\left(\int_\mathcal{C}P\xrightarrow{\pi_0}\mathcal{C}\xrightarrow{A}\mathcal{E}\right)$$

On the other hand, since $\mathcal{E}$ is cocomplete and locally small it is tensored over $\mathsf{Set}$ (with tensor given by disjoint union), so we can take the tensor of two functors $P:\mathcal{C}^{op}\to \mathsf{Set}$ and $A:\mathcal{C}\to \mathcal{E}$, which is
$$P\otimes_\mathcal{C} A = \int^{C:\mathcal{C}}P(C)\cdot A(C) \cong L_A(P)$$
Expanding this co-end we can realize the tensor as the co-equalizer
$$\coprod_{C\to C':\mathcal{C}}P(C')\cdot A(C)\rightrightarrows \coprod_{C:\mathcal{C}}P(C) \cdot A(C)\to P\otimes_\mathcal{C}A$$
More on ends and co-ends can be found in [[Ends and coEnds]]. 

In general, if we are given a functor $\phi:\mathcal{C}\to \mathcal{D}$ between small categories, it induces a geometric morphism $\mathsf{Set}^{\mathcal{C}^{op}}\to \mathsf{Set}^{\mathcal{D}^{op}}$ by applying the above construction after post-composing with the yoneda embedding. The fact that $\phi^*$ is left-exact follows from the observation that it has a left adjoint.

>[!def] Essential Geometric Morphism
>A geometric morphism between topoi is called **essential** if its inverse image part has a left adjoint.

In all of this work we can replace $\mathsf{Set}$ by a topos, possibly cocomplete, and $\mathcal{C}$ and $\mathcal{D}$ can be replaced by internal categories in $\mathcal{E}$.

## Embeddings and Surjections

>[!def] Surjections and Embeddings
>A geometric morphism $f:\mathcal{E}\to \mathcal{D}$ is said to be a **surjection** if its inverse image $f^*$ is **faithful** (or equivalently when the unit $\eta:1\Rightarrow f_*f^*$ is monic). $f$ is said to be an **embedding** when its direct image functor $f_*$ is fully faithful (or equivalently when the co-unit $\epsilon:f^*f_*\Rightarrow 1$ is an isomorphism).

A typical example of an embedding is the geometric morphism $i:\mathsf{Sh}_j\mathcal{E}\to \mathcal{E}$ for a Lawvere-Tierney topology $j$ on a topos $\mathcal{E}$.

If $G$ is a left-exact comonad on a topos $\mathcal{E}$, then the category of $\mathcal{E}_G$ of Eilenberg-Moore co-algebras is a topos, and we have a geometric morphism $p:\mathcal{E}\to \mathcal{E}_G$. Further, this is a classical example of a surjection.

It turns out that these examples characterize, up to equivalence of topoi, all embeddings and surjections, and that embeddings and surjections give a factorization system on the category of topoi. **TBC**


## Points

>[!def] Points in Topoi
>A **point** of a topos $\mathcal{E}$ is a geometric morphism $p:\mathsf{Set}\to \mathcal{E}$.

Note that $\mathsf{Set} \cong \mathsf{Sh}(1)$, so a point of a topological space, which can be considered to be a map $1\to X$, exactly corresponds to a geometric morphism $x:\mathsf{Set}\cong \mathsf{Sh}(1)\to \mathsf{Sh}(X)$. In this case $x^*$ is the stalk functor and $x_*$ is the skyscraper sheaf functor at $x$.

Note that we can also think of $\mathsf{Set} \cong \mathsf{Sh}(\mathbb{1})$ as the sheaves on the free-arrow category with trivial topology. Then a point of a topos $\mathcal{E}$ is a geometric morphism $p:\mathsf{Sh}(\mathbb{1})\to \mathcal{E}$, which we will later interpret in a special way for Grothendieck topoi.

In general topoi need not have points. Of particular importance for us is the consideration of points of Grothendieck topoi $\mathcal{E}\cong \mathsf{Sh}(\mathcal{C},J)$ for some site $(\mathcal{C},J)$.

### Points in Grothendieck Topoi

A point in a Grothendieck topoi $\mathsf{Sh}(\mathcal{C},J)$ is, as for an elementary topoi, a geometric morphism $p:\mathsf{Sh}(\mathbb{1})\to \mathsf{Sh}(\mathcal{C},J)$, which corresponds, as we will see more on below, to a functor $p:\mathcal{C}\to \mathsf{Sh}(\mathbb{1})$ which is filtering and continuous. 

>[!def] Continuous
>A functor $A:\mathcal{C}\to \mathcal{E}$, for $\mathcal{E}$ an elementary topos, is said to be **continuous** with respect to a Grothendieck topology $J$ on $\mathcal{C}$ if for any covering sieve $S \in J(C)$, viewed as a family of arrows with codomain $C$ and closed under pre-composition, $A(S)$ is a co-cone witnessing $A(C)$ as a colimit. Equivalently, $A(S)$ is an epimorphic family on $C$.

Explicitly $p$ being filtering means that the category of elements $\int_\mathcal{C}p$ is filtered, which is to say 
1. for any $(C,a),(D,b) \in \int_\mathcal{C}p$ there exists $(E,c) \in \int_\mathcal{C}p$ together with maps $k:E\to C$ and $h:E\to D$ such that $p(k)(c) = a$ and $p(h)(c) = b$, 
2. and for any pair of maps $f,g:C\to D$ in $\mathcal{C}$, and any $a \in p(C)$ such that $p(f)(a) = p(g)(a)$, there exists $k:B\to C$ in $\mathcal{C}$ and $b \in p(B)$ such that $p(k)(b) = a$ and $f\circ k = g \circ k$. 

Further, $p$ being continuous means that for any covering sieve $S \in J(C)$,
$$p(C)\cong \lim\limits_{\to (u:D\to C)\in S}p(D)$$
As with sheaves on spaces, we can define stalks of sheaves on sites at points of the Grothendieck topos.

>[!def] Stalks
>Let $p:\mathcal{C}\to \mathsf{Set}$ be a **point** of the Grothendieck topos $\mathsf{Sh}(\mathcal{C},J)$ and let $\mathscr{F}$ be a sheaf on the site. Then the stalk of $\mathscr{F}$ at $p$ is the colimit
>$$\mathscr{F}_p := \text{colim}\left(\left(\int_\mathcal{C}p\right)^{op}\xrightarrow{\pi_0^{op}}\mathcal{C}^{op}\xrightarrow{\mathscr{F}}\mathsf{Set}\right)$$




## Filtering Functors

Points in Grothendieck topoi are special examples of geometric morphisms into Grothendieck topoi. More generally these types of geometric morphisms lend themselves to an interesting description in terms of filtering functors. In this section we explore this perspective.

>[!def] Filtering Category
>A small category $I$ is **filtering** or **filtered** if
>1. $I$ is non-empty
>2. for any $i,j \in I$, there exists an object $k$ such that $k$ admits morphisms $k\to j$ and $k\to i$
>3. for any parallel maps $i\rightrightarrows j$ in $I$, there exists an object $k$ which forks the maps, i.e. $k\to i\rightrightarrows j$ commutes.

Recall that limits over a filtered category are called **filtered limits**, and satisfy a number of interesting properties. A similar argument to that which shows all limits can be recovered from products and equalizers allows us to give an equivalent characterization of filtered categories.

>[!proposition] Filtered Categories Via Cones
>A small category $I$ is filtered if and only if any finite diagram in $I$ has a cone.

Note that all small categories with an initial object are filtered (limits over such categories are given by evaluating at the initial object).

>[!def] Filtering Functors
>A functor $A:\mathcal{C}\to \mathsf{Set}$ is said to be **filtering** if its category of elements $\int_\mathcal{C}A$ is a filtered category.

Explicitly, $A:\mathcal{C}\to \mathsf{Set}$ is filtering if for any $a \in A(C)$ and $b \in A(D)$, there exists $c \in A(E)$ with maps $f:E\to C$ and $g:E\to D$ such that $A(f)(c) = a$ and $A(g)(c) = b$, and for any pair of arrows $h,k:C\to D$ and an $a \in A(C)$ such that $A(h)(a) = A(k)(a)$, there exists $c \in A(E)$ together with a map $f:E\to C$ such that $A(f)(c) = a$ and $h\circ f = k\circ f$.

>[!thm] Filtering vs. Flatness
>A functor $A:\mathcal{C}\to \mathsf{Set}$ is filtering if and only if the functor $-\otimes_\mathcal{C}A:\mathsf{Set}^{\mathcal{C}^{op}}\to \mathsf{Set}$ is left exact.

The only if side of this claim comes from the fact that filtered colimits commute with finite limits. **TBC PROOF**.


>[!corollary]
>If $\mathcal{C}$ is a small category with finite limits, a functor $A:\mathcal{C}\to \mathsf{Set}$ is lat if and only if $A$ is left-exact.

>[!corollary] Filtering Commuting with Finite Limits
>If $\mathcal{D}$ is a small category, then the colimit functor $\lim\limits_{\to}:\mathsf{Set}^\mathcal{D}\to \mathsf{Set}$ commutes with finite limits if and only if $\mathcal{D}^{op}$ is filtered.


### Morphisms into Grothendieck Topoi

Throughout let $\mathcal{E}$ be a topos and let $(\mathcal{C},J)$ be a site. Let $\mathcal{D} = \mathsf{Sh}(C,J)$ denote the Grothendieck topois of sheaves on the site.

To begin, suppose $f:\mathcal{E}\to \mathsf{Set}^{\mathcal{C}^{op}}$ is a geometric morphism. Recall that its inverse image functor $f^*$, being a left adjoint, preserves colimits. Since every pre-sheaf $R$ on $\mathcal{C}$ is a colimit of representable presheaves, the functor $f^*$ is completely determined by what it does to representables, up to natural isomorphism. In particular, recall that a pre-sheaf $R$ can be written as the co-equalizer
$$\coprod_{u:C'\to C,r \in R(C)}y^{C'}\rightrightarrows \coprod_{C \in \mathcal{C},r \in R(C)}y^C\to R$$
or, since (co)limits in a pre-sheaf category are computed term-wise, $R(C'')$ is the colimit
$$\coprod_{u:C'\to C,r \in R(C)}\mathcal{C}(C'',C')\rightrightarrows \coprod_{C \in \mathcal{C},r \in R(C)}\mathcal{C}(C'',C)\to R(C'')$$
where the maps on the left send $u:C'\to C,r \in R(C), f:C''\to C'$ to either $u\circ f:C''\to C,r \in R(C)$, or $f:C''\to C', R(u)(r) \in R(C')$. Since $f^*$ preserves colimits we obtain the co-equalizer
$$\coprod_{u:C'\to C,r \in R(C)}f^*y^{C'}\rightrightarrows \coprod_{C \in \mathcal{C},r \in R(C)}f^*y^C\to f^*R$$
in $\mathcal{C}$.

>[!def] Flat Functor into Topos
>A functor $A:\mathcal{C}\to \mathcal{E}$ is said to be **flat** if the corresponding tensor product functor $-\otimes_\mathcal{C}A:\mathsf{Set}^{\mathcal{C}^{op}}\to \mathsf{Set}$ is left-exact.

From this definition, a flat functor $A:\mathcal{C}\to \mathcal{E}$ induces a geometric morphism $\tau(A):\mathcal{E}\to \mathsf{Set}^{\mathcal{C}^{op}}$ with direct image the functor tensor and inverse image its right adjoint. **TBC**


### Filtering Functors into a Topos



### Geometric Morphisms as Filtering Functors



## Morphisms Between Sites

In this section we restrict to considering geometric morphisms between Grothendieck topoi. From our previous work a geometric morphism $f:\mathcal{E}\to \mathsf{Sh}(\mathcal{C},J)$ from a topos into a Grothendieck topos of sheaves can be identified with a continuous filtering functor $\mathcal{C}\to \mathcal{E}$. If $\mathcal{E} = \mathsf{Sh}(\mathcal{D},K)$ is a Grothendieck topos, we obtain an even simpler description.

>[!thm] Geometric Morphisms Between Grothendieck Topoi
>There is an equivalence between geometric morphisms $\mathsf{Sh}(\mathcal{D},K)\to \mathsf{Sh}(\mathcal{C},J)$, and functors $A:\mathcal{C}\to \mathsf{Sh}(\mathcal{D},K)$ having the four properties
>1. For any object $D$ of $\mathcal{D}$, $D$ is covered by a sieve described by $\{g:D'\to D\mid \exists C\in \mathcal{C},A(C)(D')\neq \emptyset\}$
>2. For $C,C' \in \mathcal{C}$ and $D \in \mathcal{D}$, and for elements $a\in A(C)(D), a' \in A(C')(D)$, the object $D$ is covered by the set of those arrows $g:D'\to D$ such that there are $u:B\to C,u':B\to C'$ and $b \in A(B)(D')$ such that $$A(u)_{D'}(b) = A(D)(g)(a)\;\;\;\;A(u')_{D'}(b) = A(D)(g)(a')$$
>3. For $u,v:C\to C'$ in $\mathcal{C}$ and $D \in \mathcal{D}$, for each $a \in A(C)(D)$ with $A(u)_D(a) = A(v)_D(a)$, the object $D$ is covered by those arrows $g:D'\to D$ for which there exist $w:B\to C$ in $\mathcal{C}$ and $b \in A(B)(D')$ such that $$u\circ w = v\circ w\;\;\;\;A(w)_{D'}(b) = A(C)(g)(a)$$
>4. Given a cover $S \in J(C)$, an object $D \in \mathcal{D}$, and an element $a \in A(C)(D)$, the object $D$ is covered by those arrows $g:D'\to D$ for which there are $u:C'\to C$ in $S$ and $b \in A(C')(D')$ such that $$A(u)_{D'}(b) = A(C)(g)(a)$$

We now move on to consider special types of functors between sites and the geometric morphisms which they induce. Moving forward let $(\mathcal{C},J)$ and $(\mathcal{D},K)$ be sites closed under finite limits. Since all Grothendieck topoi can be represented by such sites, this is not a great loss in generality.

>[!def] Morphism of Sites
>A functor $\phi:\mathcal{C}\to \mathcal{D}$ is called a **morphism of sites** if $\phi$ preserves finite limits and covers, where $\phi$ **preserves covers** if for a covering sieve $S \in J(C)$, the sieve $(\phi(S))$ generated by $\{\phi(u)\mid u:C'\to C\in S(C')\}$ is a covering sieve of $\phi(C)$ in $\mathcal{D}$.

>[!thm] Morphism of Sites Inducing Geometric Morphism
>Any morphism of sites $\phi:\mathcal{C}\to \mathcal{D}$ induces a geometric morphism $f:\mathsf{Sh}(\mathcal{D},K)\to \mathsf{Sh}(\mathcal{C},J)$ where the direct image functor is given by pre-composition by $\phi$ and the inverse image functor sends a sheaf $\mathscr{G}$ on $\mathcal{C}$ to the tensor product $\mathscr{G}\otimes_\mathcal{C}A_\phi$, where $A_\phi$ is the composite
>$$\mathcal{C}\xrightarrow{\phi}\mathcal{D}\xrightarrow{y}\mathsf{Set}^{\mathcal{D}^{op}}\xrightarrow{\mathfrak{a}}\mathsf{Sh}(\mathcal{D},K)$$

`\begin{proof}`
**TBC**
`\end{proof}`

>[!def] Covering Lifting Property
>A functor $\pi:\mathcal{D}\to \mathcal{C}$ has the **covering lifting property** if for any object $D$ of $\mathcal{D}$ and any $J$-cover $S$ of $\pi(D)$, there exists a $K$-cover $R$ of $D$ such that $\pi(R) \subseteq S$. (one also says that $\pi$ is **cocontinuous**)

When are categories are not closed under finite limits we can use the following lemma.

>[!lem]
>Let $(\mathcal{C},J)$ and $(\mathcal{D},K)$ be sites, and suppose we are given two functors $\pi:\mathcal{D}\to \mathcal{C}$ and $\phi:\mathcal{C}\to \mathcal{D}$ with $\pi\dashv \phi$. Then
>1. $y\circ \phi$ is flat (and a fortiori so is $\mathfrak{a}\circ y \circ \phi$)
>2. $\phi$ preserves covers if and only if $\pi$ has the covering lifting property.

`\begin{proof}`
**TBC**
`\end{proof}`


>[!thm] Induced Geometric Morphism
>If $\pi:\mathcal{D}\to \mathcal{C}$ and $\phi:\mathcal{C}\to \mathcal{D}$ are functors between sites such that $\pi\dashv \phi$ and $\pi$ has the clp (or equivalently $\phi$ preserves covers), then there is an induced geometric morphism $f:\mathsf{Sh}(\mathcal{D},K)\to \mathsf{Sh}(\mathcal{C},J)$, with inverse and direct image functors given by
>$$f^*(\mathscr{F}) = \mathfrak{a}(\mathscr{F}\circ \pi)\;\;\;\;f_*(\mathscr{G}) = \mathscr{G}\circ \phi$$

`\begin{proof}`
**TBC**
`\end{proof}`




#### References

[^1]: Sheaves in Geometry and Logic: A First Introduction to Topos Theory | SpringerLink. (n.d.). https://link.springer.com/book/10.1007/978-1-4612-0927-0. Accessed 23 May 2024
