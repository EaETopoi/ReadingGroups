---
date: 
tags:
  - CategoryTheory
  - EnrichedCatTheory
  - Homotopy
  - TextbookNotes
type: Notes
summary: 
category:
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

In this note we explore the basics of weighted (co)limits, with a focus on the enriched setting and the homotopical perspective found in Riehl[^1]. As we will soon see weighted (co)limits can be encapsulated by normal (co)limits in the case of un-enriched categories. However, in enriched categories weighted (co)limits are essential for providing a complete view of the theory of (co)limits.

## Unenriched Setting

First let us recollect on normal (co)limits in a category $\mathcal{C}$. Recall that the limit of a diagram $D:\mathcal{I}\to \mathcal{C}$ consists of an object $c \in \mathcal{C}$ which represents the functor $\mathcal{C}^{op}\to \mathsf{Set}$ that sends an object $c' \in \mathcal{C}$ to the set of cones over $D$ with peak $c'$. We can represent this functor by $\mathcal{C}^\mathcal{I}(\Delta_{-},D):\mathcal{C}^{op}\to \mathsf{Set}$. This is equivalent to the statement that $c$ comes equipped with a natural transformation $\alpha:\Delta_c\Rightarrow D$ which is final in the comma category $\Delta_{-}/D$.

Alternatively, note that a natural transformation $\alpha:\Delta_d\Rightarrow D$ is equivalent to a natural transformation $\widetilde{\alpha}:\Delta_*\Rightarrow \mathcal{C}(d,D):\mathcal{I}\to \mathsf{Set}$, which are related by $\widetilde{\alpha}_{c'}(*) = \alpha_{c'}$. Thus, our cone functor can be equivalently described by
$$\mathsf{Set}^\mathcal{I}(\Delta_*,\mathcal{C}(-,D)):\mathcal{C}^{op}\to \mathsf{Set}$$
In this context it is a bit more clear what would be our weight. Namely, we can think of the functor $\Delta_*:\mathcal{I}\to \mathsf{Set}$ as a weight for the limit. On the other hand, a colimit is a representation of the functor
$$\mathsf{Set}^{\mathcal{I}^{op}}(\Delta_*,\mathcal{C}(D,-)):\mathcal{C}\to \mathsf{Set}$$
or in other words an object $c \in \mathcal{C}$ together with a natural transformation $\alpha:D\Rightarrow \Delta_c$ which is initial in the comma category $D/\Delta_-$.

We can generalize this construction by replacing $\Delta_*:\mathcal{I}\to \mathsf{Set}$ (resp. $\Delta_*:\mathcal{I}^{op}\to \mathsf{Set}$) with an arbitrary functor $W:\mathcal{I}\to \mathsf{Set}$ (resp. $W:\mathcal{I}^{op}\to \mathsf{Set}$). In this case a representation of $\mathsf{Set}^\mathcal{I}(W,\mathcal{C}(-,D))$ is an object $c \in \mathcal{C}$ together with a natural transformation $\alpha:W\Rightarrow \mathcal{C}(c,D)$ which consists of a collection of morphisms $c\to Di$ for each element of $Wi$ and each $i \in \mathcal{I}$ such that if $f:i\to i'$ in $\mathcal{I}$ such that $Wf:Wi\to Wi'$ maps $x\in Wi$ to $x' \in Wi'$, then the corresponding triangle under $c$ commutes, so $\alpha$ can be thought of as a family of compatible cones under $c$ indexed by $W$. Further, for any other object $c' \in \mathcal{C}$ and natural transformation $\beta:W\Rightarrow \mathcal{C}(c',D)$, there exists a unique $f:c'\to c$ such that $\beta = \mathcal{C}(f,D)\circ\alpha$.

>[!def] Weighted Limit
>A **limit of $D$ weighted by $W:\mathcal{I}\to \mathsf{Set}$** is an object $\lim^WD \in \mathcal{C}$ together with a representation
>$$\mathcal{C}(-,\lim^WD)\cong \mathsf{Set}^\mathcal{I}(W,\mathcal{C}(-,D))$$
>A **colimit of $D$ weighted by $W$** is an object $\text{colim}^WD \in \mathcal{C}$ together with a representation
>$$\mathcal{C}(\text{colim}^WD,-)\cong \mathsf{Set}^{\mathcal{I}^{op}}(W,\mathcal{C}(D,-))$$


To see that weighted (co)limits are encapsulated by normal (co)limits in unenriched categories suppose $\mathcal{C}$ is (co)complete (or at least the (co)limits below exist). Then $\mathcal{C}$ is cotensored (and tensored) over $\mathsf{Set}$ we can compute
$$\mathsf{Set}^\mathcal{I}(W,\mathcal{C}(-,D)) \cong \int_{i:\mathcal{I}}\mathsf{Set}(Wi,\mathcal{C}(-,Di)) \cong \int_{i:\mathcal{I}}\mathcal{C}(-,Di^{Wi}) \cong \mathcal{C}\left(-,\int_{i:\mathcal{I}}Di^{Wi}\right)$$
where the end in the right hand hom is the functor cotensor product $\{W,D\}$ of $W:\mathcal{I}\to \mathsf{Set}$ and $D:\mathcal{I}\to \mathcal{C}$. It follows that
$$\lim^WD \cong \int_{i :\mathcal{I}}Di^{Wi}$$
Similarly, we have that
$$\text{colim}^WD \cong \int^{i:\mathcal{I}}Wi\cdot Di$$

An important aspect of these weighted constructions is that they assemble into bifunctors, when such weighted (co)limits exist:
$$\lim^--:(\mathsf{Set}^\mathcal{I})^{op}\times \mathcal{C}^\mathcal{I}\to \mathcal{C}$$
and $$\text{colim}^--:\mathsf{Set}^{\mathcal{I}^{op}}\times \mathcal{C}^{\mathcal{I}}\to \mathcal{C}$$

### Yoneda and Category of Elements

Note that by the Yoneda lemma we have that
$$Di\cong \lim^{\mathcal{I}(i,-)}D\cong \int_{i':\mathcal{I}}Di'^{\mathcal{I}(i,i')}\cong \text{eq}\left(\prod_{i':\mathcal{I},f:i\to i'}Di'\rightrightarrows\prod_{g:i'\to i'',f:i\to i'}Di''\right)$$
and similarly
$$Di\cong \text{colim}^{\mathcal{I}(-,i)}D\cong \int^{i':\mathcal{I}}{\mathcal{I}(i,i')}\cdot Di'\cong \text{coeq}\left(\coprod_{g:i'\to i'',f:i\to i'}Di''\rightrightarrows\coprod_{i':\mathcal{I},f:i\to i'}Di'\right)$$

Recall that all (co)limits can be written in terms of (co)equalizers and (co)products in a canonical way. Taking this viewpoint, the (co)equalizer appearing for the (co)end which realizes the weighted (co)limit can be viewed as a limit over the category of elements for $W$. Namely,
$$\lim^WD \cong \int_{i:\mathcal{I}}Di^{Wi}\cong \lim_{\int_{\mathcal{I}}W}(D\circ \pi_0)$$
and
$$\text{colim}^WD\cong \int^{i:\mathcal{I}}Wi\cdot Di \cong \text{colim}_{\int_{\mathcal{I}}W}(D\circ \pi_0)$$
where $\pi_0:\int_\mathcal{I}W\to \mathcal{I}$ is the natural projection. 

In this context the representable isomorphisms we obtained above correspond to the (co)yoneda lemmas, and represent them dually
$$W\cong \lim_{\int_\mathcal{I}W}\mathcal{I}(-,i)\;\;\;\text{ and }\;\;\;W\cong \text{colim}_{\int_\mathcal{I}W}\mathcal{I}(i,-)$$

The Grothendieck construction, and associated category of elements of a functor, play a crucial role in determining if that functor is representable.

>[!proposition] Characterization of Representable Functors
>A functor $W:\mathcal{I}\to \mathsf{Set}$ is representable if and only if $\int_\mathcal{I}W$ has an initial object \left( dually $W:\mathcal{I}^{op}\to \mathsf{Set}$ is representable if and only if $\int_\mathcal{I}W$ has a terminal object \right).

### Kan Extensions

If $\mathcal{I}$ is also small, then for any $K:\mathcal{I}\to \mathcal{J}$, from [[Kan Extensions]] we have a pointwise right Kan extension of $D$ along $K$ given by
$$\text{Ran}_KD(j) = \int_{i:\mathcal{I}}Di^{\mathcal{J}(j,Ki)}\cong \lim^{\mathcal{J}(j,K)}D$$
and similarly for a pointwise left Kan extension
$$\text{Lan}_KD(j) = \int^{i:\mathcal{I}}\mathcal{J}(Ki,j)\cdot Di \cong \text{colim}^{\mathcal{J}(K,j)}D$$

## Enriched Setting

Throughout let $\mathcal{V}$ denote a closed symmetric monoidal category with suitable (co)limits appearing below. Note that this implies that $\mathcal{V}$ is naturally enriched over itself. Let $\underline{\mathcal{C}}$ be a category enriched over $\mathcal{V}$.

>[!def] Weighted (co)Limit
>Given a $\mathcal{V}$-functor $F:\underline{\mathcal{D}}\to \underline{\mathcal{C}}$ and $\mathcal{V}$-functor $W:\underline{\mathcal{D}}\to \underline{\mathcal{V}}$, the **weighted limit** of $F$ by $W$, if it exists, is an object $\lim^WF$ of $\mathcal{C}$ with a $\mathcal{V}$-natural isomorphism
>$$\underline{\mathcal{C}}(c,\lim^WF)\cong \underline{\mathcal{V}}^{\underline{\mathcal{D}}}(W,\underline{\mathcal{C}}(c,F))$$
>Dually, if $W:\underline{\mathcal{D}}^{op}\to \underline{\mathcal{V}}$ is a $\mathcal{V}$-functor, the **weighted colimit** of $F$ by $W$, if it exists, is an object $\text{colim}^WF$ of $\mathcal{C}$ together with a $\mathcal{V}$-natural isomorphism
>$$\underline{\mathcal{C}}(\text{colim}^WF,c) \cong \underline{\mathcal{V}}^{\underline{\mathcal{D}}^{op}}(W,\underline{\mathcal{C}}(F,c))$$

We will write $W\star F$ for  $\text{colim}^WF$ and $\{W,F\}$ for $\lim^WF$ moving forward.

Let us consider a collection of examples.

>[!example] (co)tensoring
>Let $\mathbb{1}$ denote the free $\mathcal{V}$-category on the terminal category (i.e. the $\mathcal{V}$-category with a single object and with hom-object the monoidal unit $*$, and composition the left/right unitor). A $\mathcal{V}$-functor $\mathbb{1}\to \underline{\mathcal{C}}$ consists of an object $c$ of $\mathcal{C}$ together with the map $*\to \underline{\mathcal{C}}(c,c)$ which is the identity map for $c$ in $\mathcal{C}$. A $\mathcal{V}$-natural transformation between such functors is a map $*\to \underline{\mathcal{C}}(c,d)$ with no other conditions.
>
>The $\mathcal{V}$-category $\underline{\mathcal{V}}^{\mathbb{1}}$ of $\mathcal{V}$-functors and $\mathcal{V}$-natural transformations is then just $\underline{\mathcal{V}}$. It follows that the limit of $n:\mathbb{1}\to \underline{\mathcal{C}}$ weighted by $\nu:\mathbb{1}\to \underline{\mathcal{V}}$ is defined by the universal property
>$$\underline{\mathcal{C}}(c,\lim^\nu n)\cong \underline{\mathcal{V}}(\nu,\underline{\mathcal{C}}(c,n))$$
>which exactly characterizes the **cotensor** of $n$ with $\nu$, $n^\nu$.
>
>Dually, the colimit of $c:\mathbb{1}\to \underline{\mathcal{C}}$ weighted by $\nu:\mathbb{1}^{op}\to \underline{\mathbb{V}}$ is defined by the universal property
>$$\underline{\mathcal{C}}(\text{colim}^\nu c,n)\cong \underline{\mathcal{V}}(\nu,\underline{\mathcal{C}}(c,n))$$
>which is exactly the universal property of the **tensor** of $\nu$ with $c$, $\nu\otimes c$.

Thus, the statement that an enriched category is (co)tensored over $\mathcal{V}$ is exactly the statement of the existence of certain weighted (co)limits.

>[!example] Weighted Yoneda
>By the enriched yoneda lemma **REF**, limits and colimits weighted by representable $\mathcal{V}$-functors are computed by evaluating the diagram at the representing object: i.e., the isomorphisms
>$$\underline{\mathcal{C}}(c,\lim^{\underline{\mathcal{D}(d,-)}}F)\cong \underline{\mathcal{V}}^{\underline{\mathcal{D}}}(\underline{\mathcal{D}}(d,-),\underline{\mathcal{C}}(c,F))\cong \underline{\mathcal{C}}(c,Fd)$$
>implies that $\lim^{\underline{\mathcal{D}(d,-)}}F\cong Fd$.

>[!example] Pullback Weight
>Let $\mathcal{V} = \mathsf{Cat}$ with its usual symmetric monoidal structure. Let $\mathcal{D}$ be the unenriched category indexing pullback diagrams (i.e. a cospan). Let $W:\mathcal{D}\to \mathsf{Cat}$ be determined by $\mathbb{1}\xrightarrow{0}\mathbb{2}\xleftarrow{1}\mathbb{1}$ and let $F:\mathcal{D}\to \mathsf{Cat}$ be determined by $\mathcal{A}\xrightarrow{H}\mathcal{C}\xleftarrow{K}\mathcal{B}$, where $\mathbb{2}$ is the walking arrow category with $0,1:\mathbb{1}\to\mathbb{2}$ the natural endpoint inclusions.
>
>Applying the universal property of the $W$-weighted limit of $F$ to the unit object $\mathbb{1} \in \mathsf{Cat}$ we obtain the isomorphisms
>$$\lim^WF\cong \underline{\mathsf{Cat}}(\mathbb{1},\lim^WF) \cong \underline{\mathsf{Cat}}^{\mathcal{D}}(W,\underline{\mathsf{Cat}}(\mathbb{1},F))\cong \underline{\mathsf{Cat}}^{\mathcal{D}}(W,F)$$
>Recall that 
>$$\underline{\mathsf{Cat}}^\mathcal{D}(W,F)\cong \text{eq}\left(\prod_{d:\mathcal{D}}\underline{\mathsf{Cat}}(Wd,Fd)\rightrightarrows\prod_{d,d':\mathcal{D}}\underline{\mathsf{Cat}}(\mathcal{D}(d,d'),\underline{\mathsf{Cat}}(Wd,Fd'))\right)$$
>Thus, an object of this category is a triple $a \in \mathcal{A},b\in\mathcal{B}$ and $g:c\to c'$ in $\mathcal{C}$ such that $c = Ha$ and $c' = Kb$. In other words, an object is a natural transformation $W\Rightarrow F$. An arrow between $Ha\to Kb$ and $Ha'\to Kb'$ is then a pair of morphisms $a\to a'$ in $\mathcal{A}$ and $b\to b'$ in $\mathcal{B}$ making the associated square commute. In other words, $\lim^WF$ is exactly the **comma category** $H/K$.

In general, if $W,F:\underline{\mathcal{D}} \to \underline{\mathcal{V}}$, we can use the trick above to determine
$$\lim^WF\cong \underline{\mathcal{V}}(*,\lim^WF)\cong \underline{\mathcal{V}}^{\underline{\mathcal{D}}}(W,\underline{\mathcal{V}}(*,F))\cong \underline{\mathcal{V}}^{\underline{\mathcal{D}}}(W,F)$$
so the weighted limit of $\mathcal{V}$-valued $\mathcal{V}$-functors is the object of $\mathcal{V}$-natural transformations from the weight to the diagram.

It follows that we obtain the following sequence of natural isomorphism, which matches that found in the unenriched setting:
$$\underline{\mathcal{C}}(c,\lim^WF)\cong \underline{\mathcal{V}}^{\underline{\mathcal{D}}}(W,\underline{\mathcal{C}}(c,F))\cong \lim^W \underline{\mathcal{C}}(c,F)$$
and
$$\underline{\mathcal{C}}(\text{colim}^WF,c)\cong \underline{\mathcal{V}}^{\underline{\mathcal{D}}^{op}}(W,\underline{\mathcal{C}}(F,c))\cong \lim^W \underline{\mathcal{C}}(F,c)$$
which expresses a kind of (co)continuity of the enriched representable functors with respect to weighted (co)limits. However, this is relatively immediate from our definitions since we defined weighted (co)limits in $\underline{\mathcal{C}}$ representably as weighted limits in $\underline{\mathcal{V}}$, and so in terems of normal limits in $\mathcal{V}$, which are hence ordinary limits in $\mathsf{Set}$.


### Conical (co)limits

Throughout let $\mathcal{V}$ be a closed symmetric monoidal category with suitable (co)limits (e.g. (co)complete). Recall that we have an adjunction

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BV%7D-%5Cmathsf%7BCat%7D%7D%20%26%26%20%7B%5Cmathsf%7BCat%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22U%22'%2C%20bend%20right%20%3D%2040%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22F%22'%2C%20bend%20right%20%3D%2040%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{V}-\mathsf{Cat}} &amp;&amp; {\mathsf{Cat}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;U&quot;', bend right = 40, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;F&quot;', bend right = 40, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

where $F$ sends a category $\mathcal{C}$ to the **free $\mathcal{V}$-category** with objects those of $\mathcal{C}$ and with hom-object the copower $\sqcup_{\mathcal{C}(a,b)}*$, with identity morphisms given by the appropriate inclusion and composition given by the composition in $\mathcal{C}$ along with the isomorphisms
$$\left(\sqcup_{\mathcal{C}(b,c)}*\right)\otimes \left(\sqcup_{\mathcal{C}(a,b)}*\right)\cong \sqcup_{\mathcal{C}(b,c)}\left(*\otimes\left(\sqcup_{\mathcal{C}(a,b)}*\right)\right)\cong \sqcup_{\mathcal{C}(b,c)\times\mathcal{C}(a,b)}*$$
assuming that the monoidal product commutes with copowers. On the other hand $U$ sends an enriched category $\underline{\mathcal{C}}$ to the **underlying category** with the same objects and hom sets $\mathcal{V}(*,\underline{\mathcal{C}}(a,b))$, and composition given by using the composition of $\underline{\mathcal{C}}$ and appropriate transpositions.

From this adjunction we have that a $\mathcal{V}$-functor $F:\mathcal{D}\to \underline{\mathcal{C}}$ out of a free $\mathcal{V}$-category corresponds to an unenriched functor $F:\mathcal{D}\to \mathcal{C}$ landing in the underlying category. In this case, where the domain of our diagram is a free $\mathcal{V}$-category, we can take our weight to be the functor $*:\mathcal{D}\to \mathcal{V}$ that is constant at the monoidal unit. The weighted (co)limits that result are called **conical (co)limits**. 

The conical colimit $\lim^*F$ has the defining universal property
$$\underline{\mathcal{C}}(c,\lim^*F)\cong \underline{\mathcal{V}}^{\mathcal{D}}(*,\underline{\mathcal{C}}(c,F))\cong \lim^*\underline{\mathcal{C}}(c,F)$$
**TBC**

### Enriched (co)completeness


### Homotopy (co)limits in terms of weighted (co)limits

We now interpret homotopy (co)limits as weighted (co)limits, which will allow us to more easily describe their local universal property that we would expect of them. For a treatment of homotopy (co)limits using derived functors see [[Homotopy (co)Limits via Riehl]].

Suppose $\mathcal{M}$ is a simplicial model category with all objects cofibrant and let $F:\mathcal{D}\to \mathcal{M}$. By **REF** we can model the homotopy colimit of $F$ as the colimit of $F$ weighted by $N(-/\mathcal{D}):\mathcal{D}^{op}\to \mathsf{SSet}$. From the defining universal property of the weighted colimit we have that
$$\underline{\mathcal{M}}(\text{hocolim}_\mathcal{D}F,m)\cong \underline{\mathsf{SSet}}^{\mathcal{D}^{op}}(N(-/\mathcal{D}),\underline{\mathcal{C}}(F,m))$$
so the homotopy colimit is an object of $\mathcal{M}$ equipped with a universal simplicial natural transformation $N(d/\mathcal{D})\Rightarrow \underline{\mathcal{C}}(Fd,\text{hocolim}_{\mathcal{D}}F)$. 

>[!example] Topological Spaces
>Let $\mathcal{D}$ be the category indexing pushout diagrams, $b\leftarrow a\rightarrow c$, (i.e. the free span) and let $\mathcal{M} = \mathsf{Top}$ with its standard enrichement. The slice categories $b/\mathcal{D}$ and $c/\mathcal{D}$ are isomorphic to the terminal. This implies that the corresponding components of the simplicial natural transformation pick out points in the space $\underline{\mathcal{M}}(Fb,\text{hocolim}_\mathcal{D}F)$ and $\underline{\mathcal{M}}(Fc,\text{hocolim}_\mathcal{D}F)$. On the other hand, the space $N(a/\mathcal{D})$ is the wedge of two intervals, picking out a path in $\underline{\mathcal{M}}(Fa,\text{hocolim}_\mathcal{D}F)$.
>
>Naturality implies that the path picked out defines a homotopy between the maps $Fb\to \text{hocolim}_\mathcal{D}F$ and $Fc\to \text{hocolim}_\mathcal{D}F$.

**TBC**

#### References

[^1]: Riehl, E. (2014). Categorical Homotopy Theory. Cambridge: Cambridge University Press. https://doi.org/10.1017/CBO9781107261457
