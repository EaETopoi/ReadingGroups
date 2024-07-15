---
date: 2024-06-07T18:57:00
tags:
  - AlgebraicGeometry
  - Sheaves
  - EtaleCohomology
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

In these notes Dinglong Wang covers an introduction to the category of etale sheaves by introducing the general theory of Grothendieck topoi. Throughout $\mathcal{C}$ will be a small category. 

## Preliminary Notions

>[!def] Grothendieck Topos
>A **Grothendieck topos** is a category which is equivalent to the category of sheaves on some site $(\mathcal{C},J)$. 

In general it can be difficult to see whether a given category can be represented by some site. The primary tool that answers this question is **Girard's Theorem**. Before recalling this result we recall some categorical notions.

>[!def] Compact Objects
>Given a locally small category $\mathcal{C}$ that admits filtered colimits, an object $C \in \mathcal{C}$ is said to be **compact** or **finitely presentable** if the co-representable functor $\mathcal{C}(C,-):\mathcal{C}\to \mathsf{Set}$ preserves these filtered colimits.

>[!example]
>- Compact objects in any category of algebras (e.g. groups, rings, modules, algebras, etc.) are finitely presented algebras (i.e. finitely generated with finitely many relations).
>- Compact objects in $\mathsf{Top}$ are finite discrete spaces.

Note that coproducts can be expressed as filtered colimits, and so are preserved.

>[!def] Accessible
>A category $\mathcal{C}$ is **accessible** if
>1. $\mathcal{C}$ has filtered colimits
>2. There is a set of compact objects that generate $\mathcal{C}$ under filtered colimits.

>[!remark]
>The category $\mathsf{Top}$ is **not** accessible since a filtered colimit of discrete spaces is discrete since the inclusion of $\mathsf{Set}$ into $\mathsf{Top}$ is left-adjoint to the forgetful functor.

>[!def] Presentable
>A category $\mathcal{C}$ is **presentable** if 
>1. $\mathcal{C}$ is accessible
>2. $\mathcal{C}$ is cocomplete

When dealing with presentable categories we have a simpler version of the adjoint functor theorem.

>[!theorem] Adjoint Functor Theorem for Presentable Categories
>Let $F:\mathcal{C}\to \mathcal{D}$ be a functor between presentable categories. Then 
>1. $F$ has a right adjoint if and only if it preserves all small colimits
>2. $F$ has a left adjoint if and only if it preserves all limits and is accessible (i.e. also preserves filtered colimits)


>[!def]
>Let $\mathcal{E}$ be a category with pullbacks and colimits of some shape $I$. We say that colimits of shape $I$ are **universal** if they are stable under pullback. I.e. for arbitrary $f:X\to Y$, the pullback functor $$f^*:\mathcal{E}/Y\to \mathcal{E} / X$$
>preserves $I$-colimits.

>[!def] Disjoint Coproducts
>A binary coproduct $A\amalg B$ in a category $\mathcal{C}$ is said to be **disjoint** if 
>1. the inclusions $A\to A\amalg B$ and $B\to A\amalg B$ are monic
>2. the pullback of the inclusions exist and is an initial object

>[!def] Congruence
>In a category $\mathcal{C}$ with pullbacks, a **congruence** on an object $X$ is a monomorphism $i:R\xrightarrow{(p_1,p_2)} X\times X$ such that there exists a common section $r:X\to R$ of $p_1$ and $p_1$ (representing **reflexivity**), an internal **symmetry** $s:R\to R$ such that $p_1\circ s = p_2$ and $p_2\circ s = p_1$, and an **internal transitivity** map $t:R\times_X R\to R$ which $(p_1q_1,p_2q_2):R\times_XR\to X\times X$ factors through, where $q_1,q_2$ are the projections of the pullback.
>$$\begin{CD}R\times_X R @>q_2>> R \\ @Vq_1VV @VVp_1V \\ R @>>p_2> X\end{CD}$$
>If $R$ is the kernel pair for some morphism then the congruence is said to be **effective**

A congruence on an object $X$ can be equivalently thought of as an internal category object whose $(source,target)$-map is a monomorphism, and such that if we have a map $x_1\to x_2$ (internally), we also have a map $x_2\to x_1$ (internally).

>[!def] Quotients
>If $R$ is a congruence on an object $X$ in a category $\mathcal{C}$, the **quotient object** for the congruence is the coequalizer $Q$ of the induced pair of morphisms $R\rightrightarrows X$. If $R$ is an effective congruence than the quotient $Q$ is said to be an **effective quotient**.

We can now state Giraud's theorem.

>[!theorem] Giraud's Theorem
>A locally small category $\mathcal{E}$ is a **Grothendieck topos** if and only if it satisfies the following conditions:
>1. $\mathcal{E}$ is presentable
>2. all colimits in $\mathcal{E}$ are **universal**
>3. it has **disjoint coproducts**
>4. it has **effective quotients**


>[!example]
>1. Let $\mathcal{C}$ be a small category. Then $\mathsf{Ps}(\mathcal{C})$ is the category of sheaves on the site $(\mathcal{C},J)$ where $J$ is the trivial topology, i.e. the only covering sieves are maximal sieves.
>2. As a consequence of (1), $\mathsf{Set},\mathsf{Set}^{N}, \mathsf{SSet},$ and $\mathsf{SPr}(\mathcal{C})$, are all Grothendieck topoi, and hence satisfy their nice properties.
>3. Let $\mathcal{G}$ be a topological group. Let $B\mathcal{G}$ be the category with objects discrete topological spaces (i.e. sets) with continuous $\mathcal{G}$-action, and morphisms $\mathcal{G}$-equivariant morphisms of $\mathcal{G}$-sets.
>4. Given a scheme $X$, $\mathcal{E}_{et} := \mathsf{Sh}((\mathsf{Sch}/X),et)$, the **big etale topos**, and $\mathsf{Sh}(X_{et})$, the **small etale topos**.


Note that every Grothendieck topos is an example of an elementary topos, which we now briefly investigate.

### Elementary Topoi

>[!def] Subobject Functor
>Given a category $\mathcal{C}$, let $\mathsf{Sub}_\mathcal{C}(-):\mathcal{C}^{op}\to \mathsf{Set}$ be the functor that assigns each object $C \in \mathcal{C}$ the set of isomorphism classes of monomorphisms into $C$ in the slice category $\mathcal{C}/C$, and each morphism $f:C\to D$, a map $\mathsf{Sub}_\mathcal{C}(D)\to \mathsf{Sub}_\mathcal{C}(C)$ given by pullback.


>[!def] Subobject Classifier
>In a category $\mathcal{C}$ with finite limits, a **subobject classifier** is a monic morphism $\mathsf{true}:1\to \Omega$, where $1$ is the terminal object in $\mathcal{C}$, such that for any monomorphism $f:S\hookrightarrow C$, there exists a unique $\phi_f:C\to \Omega$ such that the following is a pullback diagram
>$$\begin{CD} S @>!>> 1 \\ @VfVV @VVtrueV \\ C @>>\phi> \Omega \end{CD}$$


>[!exercise]
>A category $\mathcal{C}$ with finite limits has a subobject classifier if and only if $\mathsf{Sub}_\mathcal{C}(-)$ is representable.

`\begin{proof}`

`\end{proof}`


>[!def] Elementary Topos
>An **elementary topos** $E$ is a category which satisfies the following properties:
>1. $E$ has all finite limits and finite colimits
>2. $E$ has exponential objects (i.e. is cartesian closed)
>3. $E$ has a subobject classifier

>[!claim]
>All Grothendieck topoi are elementary topoi.

`\begin{proof}`
As has been shown in [[Sheaves on Sites]], all Grothendieck topoi are (co)complete, and so in particular finitely (co)complete. Further, every Grothendieck topoi is cartesian closed, so we need only provide a sub-object classifier.

**TBC**
`\end{proof}`

### Basic Constructions in Elementary Topoi

Consider a topological space $X$ and a collection of open subsets $\mathcal{U}$. Let $j(\mathcal{U})$ denote the collection of open sets covered by $\mathcal{U}$. If we view a sieve in $\mathsf{Top}(X)$ as a family of open sets, $j(y^X) = y^X$, $j(j(\mathcal{U})) = j(\mathcal{U})$, and $j(\mathcal{U}_1\cap \mathcal{U}_2) \subseteq j(\mathcal{U}_1)\cap j(\mathcal{U}_2)$, which is an equality if both $\mathcal{U}_1$ and $\mathcal{U}_2$ are sieves.

If $\mathcal{U}$ is a sieve, $j(\mathcal{U})$ is also a sieve. We can view $j:\Omega\to \Omega$.

>[!def] (Lawvere-Tierney Topologies)
>Let $\Lambda:\Omega\times \Omega\to \Omega$ be the map classifying the intersection of subobjects. A **LT topology** on an elementary topos $\mathcal{E}$ with subobject classifier $\Omega$ is a map $j:\Omega\to \Omega$ such that
>1. $\mathsf{true} = j\circ \mathsf{true}$
>2. $j = j\circ j$
>3. $j\circ \Lambda = \Lambda \circ j\times j$


>[!def] (Closure Operation)
>A **closure operator** is a natural transformation $\overline{(-)}:\mathsf{Sub}_\mathcal{E}(-)\to \mathsf{Sub}_\mathcal{E}(-)$ such that $A \subseteq \overline{A}$, $\overline{\overline{A}} = \overline{A}$, and $\overline{A\cap B} = \overline{A}\cap \overline{B}$.


>[!exercise]
>Lawevere-Tierney topologies are equivalent to closure operators.


>[!def]
>Given an elementary topos $\mathcal{E}$ with LT topology $j$, a monomorphism $A\hookrightarrow E$ is called **dense** if $\overline{A} = E$, where $\overline{(-)}$ comes from the closure operator associated with $j$.


>[!def]
>An object $F$ of an elementary topos $\mathcal{E}$ is called a **$j$-sheaf** if for all dense monomorphisms $i:A\hookrightarrow E$, the pullback
>$$i^*:\mathcal{E}(E,F)\to \mathcal{E}(A,F)$$
>is an isomorphism.

>[!theorem]
>Grothendieck topologies on $\mathcal{C}$ are equivalent to LT topologies on $\mathsf{Pr}(\mathcal{C})$.

`\begin{proof}[Proof Idea.]`
If $J$ is a Grothendieck topology on $\mathcal{C}$, we define ...
`\end{proof}`

>[!theorem]
>A presheaf is a $j$-sheaf if and only if it is a $J$-sheaf.

### Sheafification

>[!theorem] Little Giraud's Theorem
>There is an equivalence between equivalence classes of left exact subcategories $\mathcal{E}$ of $\mathsf{Pr}(\mathcal{C})$ and Grothendieck topologies $J$ on $\mathcal{C}$ such that $\mathcal{E}\cong \mathsf{Sh}(\mathcal{C},J)$.


## Grothendieck Construction

Let $\mathsf{Set}_*$ be the category of pointed sets. Let $U:\mathsf{Set}_*\to \mathsf{Set}$ be the forgetful functor, which is sometimes called the **Universal $\mathsf{Set}$-bundle**.

>[!def]
>Given a functor $P:\mathcal{C}\to \mathsf{Set}$, the pullback in $\mathsf{Cat}$
>$$\begin{CD}\int_\mathcal{C}P @>>> \mathsf{Set}_* \\ @V\pi_0VV @VVUV \\ \mathcal{C} @>>P> \mathsf{Set}\end{CD}$$
>is called the category of elements of $P$, which is a special case of the Grothendieck construction.


>[!theorem] Restricted Yoneda has a Left Adjoint
>If $A:\mathcal{C}\to \mathcal{E}$ is a functor into a cocomplete category, then the restricted yoneda embedding $RA:\mathcal{E}\to \mathsf{Pr}(\mathcal{C})$ $$\mathcal{E}\xrightarrow{y}\mathsf{Pr}(\mathcal{E})\xrightarrow{A^*}\mathsf{Pr}(\mathcal{C})$$
>has a left adjoint $L_A:\mathsf{Pr}(\mathcal{C})\to \mathcal{E}$, given by the left-Kan extension.



## Geometric Morphisms

How can we have a site independent notion of morphisms of topoi which respects their structure? This comes in the form of geometric morphisms.

>[!def] Geometric Morphisms
>Let $\mathcal{E}$ and $\mathcal{F}$ be topoi. A **geometric morphism** is a pair of functor $f_*:\mathcal{E}\to \mathcal{F}$ and $f^*:\mathcal{F}\to \mathcal{E}$ such that $f^*\dashv f_*$ and $f^*$ is left-exact (i.e. preserves finite-limits).

We have a 2-category $\mathsf{Topoi}$ with objects topoi, morphisms geometric morphisms, and 2-cells natural transformations between $f_*$ (note that this is equivalent to natural transformations between $f^*$ as they are adjoint). 

Due to their deep connection with geometry, we would like to think of topoi as being geometric in some way. This begins by introducing points of topoi.

>[!def]
>A **point of a topos** $\mathcal{E}$ is a geometric morphism $p:\mathsf{Set}\to \mathcal{E}$ (i.e. a pair of functors $p_*:\mathsf{Set}\to \mathcal{E}$ and $p^*:\mathcal{E}\to \mathsf{Set}$ with $p^* \dashv p_*$, with $p^*$ left-exact).


>[!exercise]
>Given topological spaces $X$ and $Y$, with $Y$ Hausdorff, and a geometric morphism $p:\mathsf{Sh}(X)\to \mathsf{Sh}(Y)$, prove that there exists a unique map $f:X\to Y$ which induces the geometric morphism. (Hint: first construct $f^{-1}:\mathsf{Open}(Y)\to \mathsf{Open}(X)$, and then obtain $f:X\to Y$)

`\begin{proof}`
By definition $p$ is  pair of functor $p_*:\mathsf{Sh}(X)\to \mathsf{Sh}(Y)$ and $p^*:\mathsf{Sh}(Y)\to \mathsf{Sh}(X)$ such that $p^* \dashv p_*$ and $p^*$ is left-exact (i.e. preserves finite limits). Recall that the terminal object in $\mathsf{Sh}(Y)$ is the constant one-object pre-sheaf $1$. Note that a sub-object of $1$ is a sheaf $\mathscr{F}$ which is either empty or $1$ on each open set. Further, since it is a sheaf $\mathscr{F}$ must in fact be $j_!(1\vert_U)$, the skyscraper sheaf for $1$ associated with some open set $U$, given by the union of all open sets on which $\mathscr{F}$ is $1$.

Since $p^*$ is left exact it sends $1$ to $1$, and sub-objects of $1$ to sub-objects of $1$. Thus, $p^*$ restricts to a map of open subsets $\mathsf{Top}(Y)\to \mathsf{Top}(X)$ which preserves finite limits and all colimits. We define $f:X\to Y$ by $f(x) = y$ if and only if $x \in f^*(V)$ for all neighborhoods $V$ of $y$. Since $Y$ is assumed Hausdorff, this is well-defined. Further, $f^{-1}(V) = p^*(V)$ for any open set $V$, so $f$ is continuous. Further, for any sheaf $\mathscr{F}$ on $X$ and any open set $V \subseteq Y$,
$$f_*(\mathscr{F})(V) = \mathscr{F}(f^{-1}(V))\cong \mathsf{Sh}(X)(f^{-1}(V),\mathscr{F}) = \mathsf{Sh}(X)(p^*V,\mathscr{F})$$
Using the adjunction and yoneda again this is isomorphic to $p_*(\mathscr{F})(V)$. Thus $f_*\cong p_*$, and by uniqueness of adjoints $f^*\cong p^*$.
`\end{proof}`

>[!def]
>A functor $A:\mathcal{C}\to \mathsf{Set}$ is called **flat** if the functor tensor product $-\otimes_\mathcal{C}A$ is (left) exact. Let $\mathsf{Flat}(\mathcal{C})$ be the full subcategory of $\mathsf{Fun}(\mathcal{C},\mathsf{Set})$ consisting of flat functors.

>[!theorem]
>We have an equivalence of categories from $\mathsf{Flat}(\mathcal{C})$ to $\mathsf{Topos}(\mathsf{Set},\mathsf{Pr}(\mathcal{C}))$.

>[!def] Continuous Functor
>A functor $A:\mathcal{C}\to \mathsf{Set}$ is said to be **continuous** if $A$ sends covering sieves to colimit diagrams.


If $A$ is a flat functor, then $A$ is continuous if and only if it sends covering sieves to epimorphic families. 

>[!corollary]
>There is an equivalence of categories between continuous flat functors

#### References


