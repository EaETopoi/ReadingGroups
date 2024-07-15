---
date: 2024-07-12T10:28:00
tags:
  - EquivariantHomology
  - StableHomology
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

In these notes we start an introduction to equivariant stable homotopy theory and equivariant homology, as outlined in Bertrand Guillou's notes[^1]. First some motivation and discussion from Anna Marie Bohmann in[^2]. So first, what is equivariant stable homotopy theory about? Well, as the name suggests it is a subfield of algebraic topology, specifically homotopy theory, that studies *equivariant* and *stable* objects. For this pre-amble we consider our group action to be always by a compact Lie group $G$. For stability, we are motivated by the **Freudenthal suspension isomorphism** to consider suspension as an "invertible operation" - suspension corresponds, in many homology/cohomology theories, to shifting in degree, so suspension being an invertible operation corresponds to these homology/cohomologies/homotopy spaces stabilizing as we ascend our chains. This can be realized as requiring that loops and suspension give a self-equivalence of the equivariant stable homotopy category. This procedure involves the language of spectra.

When referring to a $G$-space in this introduction we mean a based $G$-space $*\to X$, where $G$-fixes the basepoint.

### Spectra

In the no-equivariant setting, we can consider a **pre-spectrum** $X$ to be a sequence of space $\{X_n\}$ for $n \geq 0$ with structure maps
$$\sigma:\Sigma X_n\to X_{n+1}$$
If the adjoint of the structure maps, $\widetilde{\sigma}_n:X_n\to \Omega X_{n+1}$, are homeomorphisms, then $X$ is said to be a **spectrum**.

We want to equivariant-ify this definition. However, the naive thing does not capture what we are interested in.  To make this translation we first change perspectives from thinking of the spectra as being indexed by $\mathbb{N}$ to being indexed by sphere, $S^0,S^1,S^2,...$. However, we want to introduce such spheres with $G$-actions, as well as to keep track of how two such spheres with $G$-actions are related. Since these spheres have a fixed $G$-action, we need to make a modification.

To encode these spheres with $G$-actions we can consider $n$-dimensional real representations $\lambda:G\to \mathsf{GL}(V)$ of the group $G$. Taking a compactification of $V$ we obtain, non-equivariantly, the sphere $S^V \cong S^{\dim V}$. We will write $S^\lambda$ for such a sphere with $G$-action induced by a representation of $G$.

A $G$-spectrum should then be a collection of $G$-spaces, as in the non-equivariant context, but now indexed by the real finite dimensional representations $\lambda$ of $G$, with appropriate structure morphisms. This leads us to the following definition.

>[!def] $G$-Universe
>A $G$-universe $\mathscr{U}$ is a countably infinite dimensional representation of $G$ with an inner product such that
>1. $\mathscr{U}$ contains the trivial representation as a subrepresentation (i.e. there is a fixed point of the action, which will act as our basepoint)
>2. $\mathscr{U}$ contains countably many copies of each finite dimensional subrepresentation

We can think of $\mathscr{U}$ as a direct sum $(V_i)^{\infty}$ where $\{V_i\}$ is a set of distinct irreducible representations of $G$. We say a $G$-universe is **complete** if it contains every irreducible representation of $G$, up to isomorphism. We say a $G$-universe is **trivial** if it contains only the trivial representation.

Moving forward we fix a $G$-universe $\mathscr{U}$. Let $V$ be a finite dimensional subrepresentation of $\mathscr{U}$ and let $S^V$ denote its one-point compactification. We will write $\Sigma^V(-) = S^V\land -$ and $\Omega^V(-) = \mathsf{Top}_*(S^V,-)$ for the suspension and loop space functors with respect to one of these enriched spheres.

>[!def] $G$-spectrum
>A **$G$-prespectrum** indexed on $\mathcal{U}$ is a collection of $G$-spaces, $\{EV\}$, for each finite dimensional subrepresentation of $\mathscr{U}$, together with $G$-maps
>$$\sigma_{V,W}:\Sigma^{W-V}EV\to EW$$
>whenever $V \subseteq W$, and $W-V$ denotes the **orthogonal complement** of $V$ in $W$. Further, when $V \subseteq W \subseteq X$, we require that the transitivity diagram
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CSigma%5E%7BX-V%7DEV%7D%20%26%26%26%20EX%20%5C%5C%0A%09%7B%5CSigma%5E%7BX-W%7D%5CSigma%5E%7BW-V%7DEV%7D%20%26%26%26%20%7B%5CSigma%5E%7BX-W%7DEW%7D%0A%09%5Carrow%5B%22%7B%5Csigma_%7BV%2CX%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%5Ccong%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7B%5CSigma%5E%7BX-W%7D%5Csigma_%7BV%2CW%7D%7D%22'%2C%20from%3D2-1%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7B%5Csigma_%7BW%2CX%7D%7D%22'%2C%20from%3D2-4%2C%20to%3D1-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\Sigma^{X-V}EV} &amp;&amp;&amp; EX \\	{\Sigma^{X-W}\Sigma^{W-V}EV} &amp;&amp;&amp; {\Sigma^{X-W}EW}	\arrow[&quot;{\sigma_{V,X}}&quot;, from=1-1, to=1-4]	\arrow[&quot;\cong&quot;', from=1-1, to=2-1]	\arrow[&quot;{\Sigma^{X-W}\sigma_{V,W}}&quot;', from=2-1, to=2-4]	\arrow[&quot;{\sigma_{W,X}}&quot;', from=2-4, to=1-4]\end{tikzcd}" /></p>
>
>where $S^{X-V} \cong S^{X-W}\land S^{W-V}$ induces the left hand isomorphism.
>
>A **$G$-spectrum** indexed on $\mathscr{U}$ is then a $G$-prespectrum such that the adjoint structure maps
>$$\widetilde{\sigma}_{V,W}:EV\to \Omega^{W-V}EW$$
>are homeomorphisms.

Let us now consider some examples to get a feel for this definition.

>[!example]
>If $\mathscr{U} = \mathbb{R}^\infty = \bigcup_{n\geq 0}\mathbb{R}^n$ and $G$ is the trivial group, we effectively recover the definition of non-equivariant spectra, with some multiplicity.

>[!example]
>If $X$ is a $G$-space, we can define $EV = S^V\land X$ to get the suspension prespectrum of $X$. Once we know how to turn prespectra into spectra, this will become the suspension spectrum of $X$.

We say that a $G$-spectrum indexed by a complete universe (i.e. contains all irreducible representations) is **genuine**, while a $G$-spectrum indexed on a trivial universe is called **naive**.

>[!def] Category of $G$-Spectra
>We write $G\mathcal{S}\mathscr{U}$ for the category of $G$-spectra indexed by the universe $\mathscr{U}$, given by defining a morphism $D\to E$ of $G$-spectra as a collection of maps $DV\to EV$ that commute with the structure maps.

We now list some important properties of this category of $G$-spectra.

>[!Properties/Facts] Properties of the category of $G$-spectra
>1. There is a functor $\mathcal{S}$ that turns a pre-spectra indexed on $\mathscr{U}$ into a spectra indexed on $\mathscr{U}$, which comes with an adjoint and is analogous to sheafification in the theory of pre-sheaves.
>2. Naive $G$-pre-spectra are equivalent to sequences $E_n$ of $G$-spaces with structure maps $\Sigma E_n\to E_{n+1}$, that are $G$-maps.
>3. A map of spectra $D\to E$ is said to be a **weak equivalence** if every $DV\to EV$ is an equivariant weak equivalence. (<span style="color:rgb(255, 0, 0)">Warning</span>: This does **not** work in general for pre-spectra) With this definition a map of $G$-spaces $X\to Y$ is an equivariant weak equivalence if it induces an isomorphism $\pi_*(X^H)\to \pi_*(Y^H)$ for each closed subgroup $H \leq G$.
>4. There is a symmetric monoidal smash product on the category of $G$-spectra over a universe $\mathscr{U}$. The homotopy category of $G$-spectra (given by localizing at weak equivalences) is triangulated. When $\mathscr{U}$ is complete this homotopy category is what we call the **stable equivariant homotopy category**.
>5. We can suspend by any representation sphere $S^V$, and these functors, with desuspension, give inverse equivalences of categories. The suspension spectrum functor $\Sigma^\infty:G\mathsf{Top}\to G\mathcal{S}\mathscr{U}$ has an adjoint $\Omega^\infty$ that sends a spectrum to its zeroth space $E\{0\} = E_0$.
>6. If $\mathscr{U}$ is a complete $G$-universe, we can take its $G$ fixed points to get a trivial universe $\mathscr{U}^G$ with an inclusion $\mathscr{U}^G\hookrightarrow \mathscr{U}$. This inclusion gives a pair of adjoint functors
>   $$G\mathcal{S}\mathscr{U}(i_*E,E')\cong G\mathcal{S}\mathscr{U}^G(E,i^*(E'))$$
>   for $E$ a naive $\mathscr{U}^G$ spectrum and $E'$ a genuine $\mathscr{U}$ spectrum. If $V \subseteq \mathscr{U}^G$, then $i^*(E')$ has $V$th space $(i^*E')V = E'(iV)$, and if $V' \subseteq \mathscr{U}$, then $i_*E$ has $V'$th space $(i_*E)V' = EV\land S^{V'-iV}$, where $V = i^{-1}(V'\cap i(\mathscr{U}^G))$.


### Equivariant Homotopy Groups

We now move to looking at higher homotopy groups equivariantly. Throughout let $X$ be a pointed $G$-space. Again, we want to replace the spheres that normally appear in the homotopy groups, $[S^n,X]$, by spheres with $G$-action. We do this by using smash products with $G$-orbits. Specifically, we look at $G$-cosets, as these represent all possible transitive $G$-actions. Explicitly, suppose $G\to \mathsf{Top}(X)$ is a continuous transitive action of $G$ on $X$. Then for $x \in X$, let $H := \text{Stab}_G(x) = \{g \in G\,\vert\,g\cdot x = x\}$, which is the fiber of the map $\varphi :G\to G\times X\to X$ given by $g\mapsto (g,x)\mapsto g\cdot x$ above $\{x\}$, and so is closed.  Then, by the universal property of the quotient we have a unique bijective map $\widetilde{\varphi}:G/H\to X$. Since $G$ is compact, and closed subset is compact, and hence their image in $H$ is compact. If $X$ is Hausdorff this is closed, and so $\widetilde{\varphi}$ is a closed mapping, and hence a homeomorphism, so this context is sufficient for our work.

>[!def] Equivariant Homotopy Groups
>Let $H$ be a closed subgroup of $G$. Then we have an **equivariant homotopy group** of $X$ given by
>$$\pi_n^H(X) := [S^n\land (G / H)_+,X]^G$$

Since $S^n$ is fixed by $G$, a map $S^n\land (G/H)_+\to X$ must land in $H$-fixed points of $X$.

Now, how do we pass to the stable perspective? Here we want $\underline{S}^n := \Sigma^\infty S^n$, which is a (genuine) $G$-spectra indexed by some (complete) universe $\mathscr{U}$. Consider $\underline{S}^n_H := (G/H)_+\land \underline{S}^n$ for all closed subgroups $H \leq G$.

>[!def] Homotopy Groups of $G$-Spectra
>Let $E$ be a $G$-spectrum. Then its $n$th homotopy group relative to the closed subgroup $H \leq G$ is
>$$\pi_n^H(E) := [\underline{S}_H^n,E]^G$$
>where this hom is in the homotopy category of $G$-spectra.

These homotopy groups, when collected together, form what is called a **Mackey functor**, a contravariant functor from $\mathcal{B}_G\mathscr{U}$, the full subcategory of the homotopy category on $\underline{S}_H^n$'s, to abelian groups.

>[!theorem] Weak Equivalences vs. Isomorphisms
>If $f:E\to E'$ is a map of $G$-spectra, then each component map $fV:EV\to E'V$ is a weak equivalence of $G$-spaces if and only if $f_*:\pi_n^H(E)\to \pi_n^H(E')$ is an isomorphism for all closed $H \leq G$ and all $n$.

^98740a

[[Bertrand Guillou Notes#^98740a]] shows that our previous definition of weak equivalences of spectra is sensible. This implies that the $G$-spheres obtained from smashing with orbits are suitable for detecting weak equivalences. 

### Fixed Points

Now, given any $G$-spectrum $E$ we want to find a non-equivariant spectrum that will behave as the fixed points for $E$. However, $E$ isn't a single $G$-space, so how do we formalize this?

First, let us consider $X$ a non-equivariant space and $Y$ a $G$-space with fixed point space $Y^G$. Then we have an adjunction
$$G\mathsf{Top}(X,Y)\cong \mathsf{Top}(X,Y^G)$$
where we give $X$ the trivial $G$-action on the left. When we extend this construction to spectra we should obtain a similar adjunction.

Let $\mathscr{U}$ be a $G$-universe with fixed points $\mathscr{U}^G$. For a naive $G$-spectrum $D$ indexed on $\mathscr{U}^G$, define a nonequivariant spectrum $D^G$ indexed by $\mathscr{U}^G$ by $(D^G)V = (DV)^G$ for $V \subseteq \mathscr{U}^G$. If $C$ is a non-equivariant spectrum indexed on $\mathscr{U}^G$, we then have an adjunction
$$G\mathcal{S}\mathscr{U}^G(C,D)\cong \mathcal{S}\mathscr{U}^G(C,D^G)$$
as we hoped, where on the left we regard $C$ as a naive $G$-spectrum with trivial action.

We need one more step to get to $G$-spectra in general. Let $E$ be a $G$-spectra indexed by $\mathscr{U}$. Now, from the inclusion $i:\mathscr{U}^G\to \mathscr{U}$ of representations we get a pullback functor $i^*:G\mathcal{S}\mathscr{U}\to G\mathcal{S}\mathscr{U}^G$, effectively forgetting representations outside of $\mathscr{U}^G$, and define $E^G := (i^*E)^G$. We call $i^*E$ the underlying naive spectrum for $E$. We can now compose our adjunctions to obtain our desired result. Recall that $i_*\dashv i^*$ where $i_*:G\mathcal{S}\mathscr{U}^G\to G\mathcal{S}\mathscr{U}$ is given on $E$ by $(i_*E)V' = EV\land S^{V'-iV}$, for $V = i^{-1}(V'\cap i(\mathscr{U}^G))$, which can be thought of as extending the spectrum along the restriction of the sphere to a fixed point representation by taking its orthogonal complement in the original representation. It follows that
$$G\mathcal{S}\mathscr{U}(i_*(C),E)\cong \mathcal{S}\mathscr{U}^G(C,(i^*E)^G)= \mathcal{S}\mathscr{U}^G(C,E^G)$$
where $C$ is a non-equivariant spectrum indexed on $\mathscr{U}^G$.

>[!rmk]
>For genuine $G$-spectra we have a map
>$$E^G\land (E')^G\to (E\land E')^G$$
>but this is generally *not* an equivalence. Further, for a $G$-space $X$, in general $(\Sigma^\infty X)^G\cancel{\cong}\Sigma^\infty(X^G)$.

Due to these issues we also consider other kinds of fixed points, such as **geometric fixed points**, given by a functor $\Phi^G:G\mathcal{S}\mathscr{U}\to \mathcal{S}\mathscr{U}^G$ with the properties that
1. $\Sigma^\infty(X^G)\simeq \Phi^G(\Sigma^\infty X)$ and
2. $\Phi^G(E)\land \Phi^G(E')\simeq \Phi^G(E\land E')$


### Universal Spaces and Splitting Isotropy Types

Universal spaces in the theory of classification of mathematical objects are of incredible importance. For example, one can think of universal bundles which classify $G$-bundles for a suitably nice group $G$, as well as a prolific amount of other similar type of universal constructions in mathematics. In this section we proceed with such a construction, beginning with the notion of a family of subgroups.

>[!def] Family of Subgroups
>A **family** $\mathscr{F}$ of subgroups of a group $G$ is a set of subgroups that is closed under conjugacy and taking subgroups, which can be summarized in the condition that it is closed under subconjugacy: If $H \in \mathscr{F}$ and $g^{-1}Kg \subseteq H$ for some $g \in G$ and $K \leq G$, then $K \in \mathscr{F}$.

>[!def] $\mathscr{F}$-space
>Let $\mathscr{F}$ be a family of subgroups of $G$. A **$\mathscr{F}$-space** is a $G$-space all of whose isotropy groups are in $\mathscr{F}$. Recall that for a $G$-space $X$, an isotropy subgroup in $G$ is exactly the stabilizer, $\mathsf{Stab}_G(x)$, of some point $x \in X$.

Given a family of subgroups $\mathscr{F}$, we can construct a **universal $\mathscr{F}$-space**, which we denote by $E\mathscr{F}$, which up to homotopy type we define as having $H$-fixed points
$$(E\mathscr{F})^H \simeq \left\{\begin{array}{cc}
* & H \in \mathscr{F}  \\
\emptyset & H\notin \mathscr{F}
\end{array}\right.$$
where by $*$ we mean that $(E\mathscr{F})^H$ is a (weakly) contractible space. Such a equivariant homotopy type satisfies a universal property in the sense that if $X$ is a $\mathscr{F}$-space with the homotopy type of a CW-complex, then there is a unique homotopy class of $G$-maps $X\to E\mathscr{F}$.

>[!example]
>Let $\mathscr{F} = \{(1)\}$. Then $E\{1\}^H$ is the homotopy type of a free $G$-space that is non-equivariantly contractible. In this case we write $E\{1\} = EG$, and $EG/G\cong BG$ is a model for the classifying space for $G$.


>[!example]
>If $\mathscr{F}$ consists of all subgroups, then $E\mathscr{F}$ is contractible, with all spaces of fixed points also contractible.

Let $\mathscr{F}$ be a family of subgroups. We construct a "**isotropy splitting cofibration**", namely
$$E\mathscr{F}_+\to S^0\to \widetilde{E}\mathscr{F}$$
where the first map is just the map $E\mathscr{F}\to *$ with a disjoint basepoint added. This cofibration implies
$$(\widetilde{E}\mathscr{F})^H \simeq \left\{\begin{array}{cc}
* & H \in \mathscr{F} \\
S^0 & H \notin \mathscr{F}
\end{array}\right.$$
If we take the smash of this cofibration with a $G$-space $X$, or more generally a $G$-spectrum $E$, its splits $X$ into an $\mathscr{F}$-space $E\mathscr{F}_+\land X$ and an $\mathscr{F}$-contractible space $\widetilde{E}\mathscr{F}\land X$, which is to say $\widetilde{E}\mathscr{F}\land X$ is $H$-contractible for all $H \in \mathscr{F}$ (here **$H$-contractible** means that the space contracts via a homotopy which at every stage is a $H$-map, to a map with values in a single orbit). The reason for the  name, isotropy splitting cofibration, or sometimes, isotropy separation cofibration, is due to the fact that when smashing it with a $G$-space $X$, it splits the $G$-space into an $\mathscr{F}$-space, $E\mathscr{F}_+\land X$, and an $\mathscr{F}$-contractible space, $\widetilde{E}\mathscr{F}\land X$.
 
This cofiber sequence also lets us provide a definition of the geometric fixed points functor.

>[!def] Geometric Fixed Points
>Let $\mathscr{P}$ be the family of all proper subgroups of $G$. Then
>$$\Phi^G(E) = (E\land \widetilde{E}\mathscr{P})^G$$

Note that $E\land \widetilde{E}\mathscr{P}$ has contractible space of $H$-fixed points for all proper subgroups $H$ of $G$, so up to homotopy type only the $G$-fixed points of $E$ remain.

>[!def] Free $G$-Spectrum
>We say a $G$-spectrum $E$ is **free** if the canonical map $EG_+\land E\to E$ obtained by smashing $E$ with the isotropy splitting cofibration is a $G$-equivalence.


### The Tom Dieck Splitting Theorem

Recall that in general for a $G$-space $X$, $(\Sigma^\infty X)^G\neq \Sigma^\infty(X^G)$ when working with our first notion of fixed points of spectra. However, we do have a formula describing the left hand side in terms of fixed points of the $G$-space due to Tom Dieck:

>[!thm] Tom Dieck Splitting Theorem
>For a based $G$-CW complex $X$, there is a natural equivalence
>$$(\Sigma^\infty X)^G\simeq \bigvee_{\text{conj. class }H\leq G}\Sigma^\infty(EWH_+\land_{WH}\Sigma^{\text{Ad}(WH)}X^H)$$
>where $WH = NH/H$ is the Weyl group of $H$ in $G$ and $\text{Ad}(WH)$ is the adjoint representation.

To understand this result a bit more concretely, let $X$ be a two sphere $S^2$ with an action of $C_2$ by rotation by $\pi$ around a central axis. Then
$$
\begin{align}
(\Sigma^\infty X)^{C_2} &\simeq \Sigma^\infty(E1_+\land X^{C_2})\lor \Sigma^\infty(E{C_2}_+\land_{C_2}X) \\
&= \Sigma^\infty(X^{C_2})\lor \Sigma^\infty
(E{C_2}_+\land_{C_2}X) \\
&= \Sigma^\infty(S^1)\lor \Sigma^\infty(E{C_2}_+\land_{C_2}X)  
\end{align}
$$
where the right term gives the **Borel construction** on $X$. It follows that the fixed point spectrum of $X$ in this case is the suspension spectrum of the fixed points of $X$ together with this Borel construction term.

### $RO(G)$-Graded Homology and Cohomology

Using our construction of equivariant spectra via representations of the group $G$, we can now define homology and cohomology theories that are not just integer graded, but are instead graded on the real representation ring $RO(G)$ of $G$. For any virtual representation $\nu = W-V$ (i.e. a formal difference of ordinary representations with respect to direct sum), we form a genuine $G$-spectrum $S^\nu = \Sigma^WS^{-V}$ (**How to construct this?**). Once $S^\nu$ is constructed, we can define the homology and cohomology groups represented by a genuine $G$-spectrum $E$ by 
$$E_\nu^G(X) = [S^\nu,E\land X]^G$$
and
$$E^\nu_G(X) = [S^{-\nu}\land X,E]^G$$


## Equivariance in Topology

Throughout we denote the category of $G$-spaces and $G$-equivariant maps by $G\mathsf{Top}$. Most often we will be interested in free actions, $\varphi:G\to \mathsf{Top}(X)$ for a topological space $X$, where $\varphi(g)(x) = x$ if and only if $g = e$. Equivalently, this means that for any $H \leq G$,
$$X^H := \{x \in X\,\vert\,h\cdot x = x,\forall h \in H\} = \emptyset$$
>[!example]
>Let $V$ be a finite dimensional vector space over $F$, where $F$ is either $\mathbb{C}$ or $\mathbb{R}$. Recall that a representation of $G$, on $V$, is a group homomorphism $\varphi:G\to \mathsf{GL}(V)$, where linear automorphisms for finite dimensional vector spaces are necessarily continuous for the unique topology on $V$ induced by any linear isomorphism $V \cong F^{\dim V}$. 
>
>Note that under this isomorphism $V$ is a locally compact, path-connected, convex, Hausdorff space. We let $S^V$ denote the one-point compactification of $V$, which for $F = \mathbb{R}$ is homeomorphic to $S^n$, the $n$-dimensional sphere. Note that if $\varphi:V\to V$ is an automorphism, then it extends uniquely, since $S^V$ is dense in $V$, to a map $\widetilde{\varphi}:S^V\to S^V$, where I claim $\widetilde{\varphi}(\infty) = \infty$. To see that this is continuous let $U \subseteq S^V$ be an open neighborhood of $\infty$. Then the complement $S^V\backslash U\subseteq V$ is compact. It follows that $\widetilde{\varphi}^{-1}(S^V\backslash U)$ is compact, being the continuous image of a compact set under the map $\widetilde{\varphi}^{-1}$. Therefore, $\widetilde{\varphi}^{-1}(U)$ is open in the one-point compactification.

^fce3b1

The argument used in [[Bertrand Guillou Notes#^fce3b1]] holds more generally for any proper map $\varphi:V\to W$, where in the case of vector spaces, such a linear map is proper if and only if it is injective. This implies that these representation spheres fit into a functor
$$S^{(-)}:\mathsf{Mod}^{inj}_{\mathbb{R}[G]}\to G\mathsf{Top}$$

As in homotopy theory more generally, it is often most convenient to work with based spaces.

>[!def] Based $G$-space
>A **based $G$-space** is a $G$-space $X$, equipped with an equivariant map $*\to X$ (i.e. we are choosing a $G$-fixed point in $X$). A morphism of $G$-spaces is a basepoint preserving $G$-equivariant map. Let $G\mathsf{Top}_*$ denote the resulting category of based $G$-spaces.

By choosing $\infty$ as our basepoint, we can regard $S^{(-)}$ as a functor into $G\mathsf{Top}_*$. As with other representation categories, we obtain a triple adjunction when given a subgroup $H \leq G$:

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BG%5Cmathsf%7BTop%7D_*%7D%20%26%26%26%20%7BH%5Cmathsf%7BTop%7D_*%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cdownarrow_H%5EG%7D%22'%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bco%5Cuparrow_H%5EG%7D%22%2C%20bend%20left%20%3D%2050%2C%20from%3D1-4%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cuparrow%5EG_H%7D%22'%2C%20%20bend%20right%20%3D%2050%2C%20from%3D1-4%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-89%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-91%7D%2C%20draw%3Dnone%2C%20from%3D2%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{G\mathsf{Top}_*} &amp;&amp;&amp; {H\mathsf{Top}_*}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\downarrow_H^G}&quot;', from=1-1, to=1-4]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{co\uparrow_H^G}&quot;, bend left = 50, from=1-4, to=1-1]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{\uparrow^G_H}&quot;',  bend right = 50, from=1-4, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-89}, draw=none, from=0, to=1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-91}, draw=none, from=2, to=0]
\end{tikzcd}
" /></p>

where $\downarrow_H^G$ is the restriction functor, which is simply pre-composition of the action by the inclusion $H\hookrightarrow G$, while $\uparrow_H^G$ and $\text{co}\uparrow_H^G$ are the induction and co-induction functors, respectively, corresponding to left and right Kan extensions of $H$-spaces along $H\hookrightarrow G$, respectively. Explicitly we can describe the induction functor as follows:

>[!def] (co)Induction
>Let $H \leq G$, and let $X \in H\mathsf{Top}$. Then $\uparrow_H^G(X)$ is the quotient of $G\times X$ by the relation $(g\cdot h,x)\sim (g,h\cdot x)$ for all $h \in H$, $g \in G$ and $x \in X$.
>
>On the other hand, $co\uparrow_H^G(X)$ can be modeled by the space $H\mathsf{Top}(G,X)$ where $G$ is given $H$ action $h\cdot g = gh^{-1}$ and the space is given action $(g\cdot \varphi)(x) := \varphi(g^{-1}x)$.

We wish to show that these definitions of induction and co-induction fit into the appropriate Kan extensions. Write $\mathcal{H}$ and $\mathcal{G}$ for the one-object categories corresponding to the groups $H$ and $G$. Then consider the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BH%7D%7D%20%26%26%20%7B%5Cmathsf%7BTop%7D%7D%20%5C%5C%0A%09%26%20%7B%5Cmathcal%7BG%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%5Crho%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Cuparrow_H%5EG%5Crho%7D%22'%2C%20dashed%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Ceta_H%5EG%7D%22%2C%20shorten%20%3C%3D3pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{H}} &amp;&amp; {\mathsf{Top}} \\
	&amp; {\mathcal{G}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;\rho&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=2-2]
	\arrow[&quot;{\uparrow_H^G\rho}&quot;', dashed, from=2-2, to=1-3]
	\arrow[&quot;{\eta_H^G}&quot;, shorten &lt;=3pt, Rightarrow, from=0, to=2-2]
\end{tikzcd}
" /></p>


where $\eta_H^G:\rho(*)\to G\times_H\rho(*)$ is the map of $H$-spaces given by including $x\mapsto [(e,x)]$, which is naturally $H$-equivariant. The map is also continuous, being the composite of continuous maps. Finally, to see that this pair is universal with this property let $\varphi:\mathcal{G}\to \mathsf{Top}$ be a $G$-space and let $\alpha:\rho\Rightarrow \varphi\circ \iota$ by a map of $G$-spaces, and hence a continuous map $\alpha:\rho(*)\to \varphi(*)$ such that $\alpha(g\cdot x) = g\cdot\alpha(x)$. We define a map $\beta:G\times_H\rho(*)\to \varphi(*)$ by $\beta([(g,x)]) = g\cdot \alpha(x)$, which is well-defined and a map of $G$-spaces, being the unique map out of the quotient induced by the composite
$$G\times \rho(*)\xrightarrow{1\times \alpha}G\times \varphi(*)\to \varphi(*)$$
Further, we have that $\alpha$ factors as $\beta\circ \eta_H^G$. Further, $\beta$ is uniquely specified by this condition by $G$-equivariance. Therefore, the induction is the appropriate left Kan extension.

Let us consider the co-induction now:

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BH%7D%7D%20%26%26%20%7B%5Cmathsf%7BTop%7D%7D%20%5C%5C%0A%09%26%20%7B%5Cmathcal%7BG%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%5Crho%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Bco%5Cuparrow_H%5EG%5Crho%7D%22'%2C%20dashed%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon_H%5EG%7D%22%2C%20shorten%20%3C%3D3pt%2C%20Rightarrow%2C%20from%3D2-2%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{H}} &amp;&amp; {\mathsf{Top}} \\
	&amp; {\mathcal{G}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;\rho&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=2-2]
	\arrow[&quot;{co\uparrow_H^G\rho}&quot;', dashed, from=2-2, to=1-3]
	\arrow[&quot;{\epsilon_H^G}&quot;, shorten &lt;=3pt, Rightarrow, from=2-2, to=0]
\end{tikzcd}
" /></p>

where $\epsilon_H^G:H\mathsf{Top}(G,\rho(*))\to \rho(*)$ given by the continuous map $(\varphi:G\to \rho(*))\mapsto \varphi(e)$. Observe that for $h \in H$, $(h\cdot\varphi) \mapsto \varphi(h^{-1}) = \varphi(h\cdot e) = h\cdot \varphi(e)$. Further, if $\sigma:\mathcal{G}\to \mathsf{Top}$ is another $G$-set with map $\alpha:\sigma\circ \iota\to \rho$, we can define $\beta:\sigma(*)\to H\mathsf{Top}(G,\rho(*))$ by $\beta(x)(g) := \alpha(g^{-1}\cdot x)$, which is a map of $H$-spaces, while $$\beta(g\cdot x)(g') = \alpha({g'}^{-1}g\cdot x) = \alpha((g^{-1}g')^{-1}\cdot x) = \beta(x)(g^{-1}g') = (g\cdot \beta(x))(g')$$
so $\beta$ gives a $G$-space map which $\alpha$ factors through using $\epsilon_H^G$. This factorization condition also uniquely specifies $\beta$. Thus, $co\uparrow_H^G\rho$ gives the desired right Kan extension.

>[!example]
>1. If $H = \{e\}$, the induced $G$-space $\uparrow_e^G(X)$ is just the free $G$-space $G\times X$.
>2. If $H \leq G$, $\uparrow_H^G(*)\cong G\times_H *\cong G/H$. More generally, if $X$ is a $H$-space with trivial action, $\uparrow_H^G(X) \cong G/H\times X$, where $G$ acts only on the $G/H$ piece.
>3. If $C_2\leq C_4$ is the cyclic group of order $2$ in the cyclic group of order $4$. and $S^\sigma$ is the compactification of the sign representation of $C_2$, $\uparrow_{C_2}^{C_4}(S^\sigma)$ is a pair of circles, one which acts by the identity while the other performs a reflection while going between the two circles.

This third example shows that the sphere functor $S^{(-)}$ is not natural with respect to the induction functor between modules and spaces. Indeed, if it were, this last space would be a single sphere, not a pair of spheres.

Let us now introduce the based version of induction:

>[!def] Based (co)Induction
>Let $H \leq G$, and let $X$ be a based $H$-space. The **induced based $G$-space** of $X$ is $G_+\land_HX$, which is the quotient of $G_+\land X$ by the relation $(g\cdot h,x)\sim (g,h\cdot x)$ for all $g \in G$, $h \in H$, and $x \in X$.
>
>The **coinduced based $G$-space** of $X$ is $H\mathsf{Top}_*(G_+,X)$, with same actions as in the unbased setting.

As in the unbased setting we obtain a triple adjunction, now of based $H$ and $G$-space categories. Note that in general if $X$ and $Y$ are spaces, with $X$ based, $X\land Y_+ \cong (X\times Y)/(\{x_0\}\times Y)$.

Note that if $X$ is a based $H$-space with trivial action, $G_+\land_H X \cong (G/H)_+\land X$. We also refer to $G_+\land X$ as the free pointed $G$-space on a space $X$.

>[!def] Fixed Points
>Let $X$ be a $G$-space. The subspace of **fixed points** of $X$ is defined to be 
>$$X^G := \{x \in X\,\mid\,g\cdot x = x,\forall g \in G\}$$

This procedure gives another useful adjunction, namely the trivial-fixed point adjunction

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BG%5Cmathsf%7BTop%7D%7D%20%26%26%26%20%7B%5Cmathsf%7BTop%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B(-)%5EG%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22triv%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-4%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-88%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{G\mathsf{Top}} &amp;&amp;&amp; {\mathsf{Top}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{(-)^G}&quot;', bend right = 30, from=1-1, to=1-4]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;triv&quot;', bend right = 30, from=1-4, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-88}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

For a subgroup $H\leq G$, we define the $H$-fixed points functor on $G$-spaces to be the composite of the restriction functor, $\downarrow_H^G$, and the $H$-fixed points functor $(-)^H$ on $H$-spaces.

Together with our previous induction-restriction adjunction, we obtain the composite adjunction

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BTop%7D%7D%20%26%26%20%7BH%5Cmathsf%7BTop%7D%7D%20%26%26%20%7BG%5Cmathsf%7BTop%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22triv%22%2C%20bend%20left%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B(G%2FH)%5Ctimes-%7D%22%2C%20bend%20left%20%3D%2060%2C%20from%3D1-1%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B(-)%5EH%7D%22%2C%20bend%20left%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cuparrow_H%5EG%7D%22%2C%20bend%20left%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%7B(-)%5EH%7D%22%2C%20bend%20left%20%3D%2060%2C%20from%3D1-5%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cdownarrow_H%5EG%7D%22%2C%20bend%20left%20%3D%2030%2C%20from%3D1-5%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D2%2C%20to%3D3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Top}} &amp;&amp; {H\mathsf{Top}} &amp;&amp; {G\mathsf{Top}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;triv&quot;, bend left = 30, from=1-1, to=1-3]
	\arrow[&quot;{(G/H)\times-}&quot;, bend left = 60, from=1-1, to=1-5]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{(-)^H}&quot;, bend left = 30, from=1-3, to=1-1]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{\uparrow_H^G}&quot;, bend left = 30, from=1-3, to=1-5]
	\arrow[&quot;{(-)^H}&quot;, bend left = 60, from=1-5, to=1-1]
	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, &quot;{\downarrow_H^G}&quot;, bend left = 30, from=1-5, to=1-3]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=2, to=3]
\end{tikzcd}
" /></p>

This is in fact an enriched adjunction, viewing all categories as enriched over $\mathsf{Top}$, which in particular means that we have a homeomorphism  $G\mathsf{Top}(G/H\times X,Y)\cong \mathsf{Top}(X,Y^H)$, which as a special case gives that $Y^H\cong G\mathsf{Top}(G/H,Y)$.

### Equivariant Homotopy Theory

We begin slowly introducing homotopy theory, starting with the notion of equivariant homotopies.

>[!def] Equivariant Homotopies
>Let $f,g:X\to Y$ be maps of $G$-spaces. Endowing $I$ with the trivial action, an equivariant homotopy from $f$ to $g$ is a homotopy $h:X\times I\to Y$ which is also a map of $G$-spaces.

Equivalently, an equivariant homotopy is a homotopy through equivariant maps.

>[!example]
>Let $S^\sigma$ be the compactification of the $C_2$-sign representation. Let $\infty,0:*\to S^\sigma$ be the inclusions of the basepoint at $\infty$ and $0$, i.e. the two fixed points. Note that forgetting equivariance these two points are in the same path component, since the sphere is path connected. However, with equivariance they are not in the same path component since $(S^\sigma)^G \cong S^0$ is **not** path connected.

Note that with our current definition of equivariant homotopies, we can consider the equivariant homotopy groups $[S^n,X]_G \cong \pi_n(X^G)$, since $S^n$ has the trivial action. However, we want to consider $\pi_n(X^H)$ as $H$ varies over all subgroups of $G$, and in this case we have natural inclusion reversing maps
$$\pi_n(X^K)\to \pi_n(X^H),\;\forall H\leq K \leq G$$
giving a diagram of fundamental groups. We refer to the data assembling such a diagram as a **coefficient system for $G$**, and we write $\underline{\pi}_n(X)$ for this data when $X$ is a (based) $G$-space.

>[!def] Weak $G$-Homotopy Equivalence
>A map of $G$-spaces $f:X\to Y$ is said to be a **weak $G$-homotopy equivalence** if it induces an isomorphism on $\underline{\pi}_n$ for all $n\geq 0$ (where we choose a basepoint $x_0 \in X^G)$ as a common basepoint for the system).

Recall that an $H$-equivariant map $S^n\to \downarrow_H^G(X)$ is equivalent to a $G$-equivariant map $(G/H)_+\land S^n\to X$, since $S^n$ has trivial action, and this equivalence preserves homotopies. We can also view $S^n\to \downarrow_H^G(X)$ as a continuous map $S^n\to X^H$. From the non-equivariant setting we observe that $G$-homotopy equivalences induce weak $G$-homotopy equivalences. Further, as with the Whitehead theorem for the non-equivariant setting, these notions coincide when dealing with equivariant versions of CW-complexes.

>[!def] $G$-CW complex
>A **$G$-CW complex** is a space $X$ built as a colimit of $G$-spaces $X_n$, where $X_0$ is a discrete $G$-set and $X_n$ is obtained from $X_{n-1}$ by attaching cells of type $(G/H)\times  D^n$ through pushouts in $G$-spaces, where $H$ varies over the subgroups of $G$.

Note that all non-equivariant CW-complexes are $G$-CW complexes with trivial action since $G/G\cong \{e\}$.

>[!thm] Equivariant Whitehead Theorem
>If $f:X\to Y$ is a weak $G$-homotopy equivalence between $G$-CW complexes, then $f$ is a $G$-homotopy equivalence.


### Equivariant Cohomology a la Borel

We begin our exploration of equivariant cohomology by starting with the perspective of Borel. A motivating example will come from the theory of classifying groups for the space $G$.

Note that we have a model of the classifying space of $G$ where we take the total space $EG$ to be a $G$-CW complex which has contractible underlying space and a free $G$-action. Then the classifying space of $G$ can be modeled by the orbit space $BG := EG/G$.

>[!example]
>1. $G = C_2$, $EC_2\simeq S^\infty$ with the antipodal action of $C^2$. In this way, $BC_2 = EC_2/C_2 \simeq S^\infty/C^2 \cong \mathbb{R}\mathbb{P}^\infty$.
>2. For $G = C_p$, for $p$ an odd prime, $EC_p \simeq S^\infty$ as the unit sphere in $\mathbb{C}^\infty$, where $C_p$ acts on each complex coordinate via multiplication by a $p$th rot of unity. Then $BC_p = EC_p/C_p\simeq S^\infty/C_p$, which is known as an **infinite-dimensional lens space**.
>3. Example **(2)** can be done generally for any cyclic group, so $BC_n\simeq S^\infty/C_n$.
>4. $EG\times EH\simeq E(G\times H)$, for any groups $G$ and $H$, so $B(G\times H)\simeq BG\times BH$.
>5. For $G = \mathbb{Z}$, $E\mathbb{Z} \simeq \mathbb{R}$ and $B\mathbb{Z} = E\mathbb{Z}/\mathbb{Z} \simeq S^1$.
>6. For $G = U(1)$ ($S^1\subseteq \mathbb{C}$ as a group under multiplication), $EU(1) \simeq S^\infty$ viewed as the unit sphere in $\mathbb{C}^\infty$, with free action given by phase multiplication. Then $BU(1) = EU(1)/U(1)\simeq \mathbb{C}P^\infty$

Combining examples **(3)**, **(4)**, and **(5)** given any finitely generated abelian group $G$ we have an isomorphism $G \cong \mathbb{Z}^r\times \mathbb{Z}/a_1\times \cdots \times \mathbb{Z}/a_n$, where $r \in \mathbb{Z}_{\geq 0}$ and the $a_i \in \mathbb{Z}_{>0}$ are unique. Then the total space for $G$ is given by
$$EG\simeq (E\mathbb{Z})^r\times EC_{a_1}\times\cdots \times EC_{a_n}\simeq \mathbb{R}^r\times \prod_{i=1}^nS^\infty$$
where the $i$th copy of $S^\infty$ has action by $\mathbb{Z}/a_i$. The classifying space for $G$ can also be made explicit, as the product
$$BG\simeq (S^1)^r\times \prod_{i=1}^nS^\infty/C_{a_i}$$

>[!proposition] $K(G,1)$
>The space $BG$ is a $K(G,1)$ space, so $\pi_1(BG)\cong G$ and $\pi_n(BG)\cong (0)$ for all $n > 1$.

^46f3ce

`\begin{proof}`
Note that the universal bundle $EG\to BG$ is in particular a universal covering space map coming from a covering space action, so $\pi_1(BG)\cong G$ by the theory of covering space actions. Note that $G\to EG\to BG$ is a fibration sequence, so we obtain a long exact sequence of homotopy groups
$$\cdots \to \pi_{n+1}(BG)\to \pi_n(G)\to \pi_n(EG)\to \pi_n(BG)\to \cdots $$
It follows that $\pi_{n+1}(BG)\cong \pi_n(G)$ for all $n \geq 0$. If $G$ is a discrete space, then $\pi_n(G) \cong 0$ for $n\geq 1$, and $\pi_0(G)\cong G$, so we obtain the desired isomorphisms.
`\end{proof}`

>[!proposition] $K(G,n)$
>If $X$ is a $K(G,n)$ space, then $\Omega X$ is a $K(G,n-1)$ space.

`\begin{proof}`
Observe that using the adjunction $\Sigma \dashv \Omega$ and the homeomorphism $\Sigma S^n \cong S^{n+1}$, we have that $\pi_k(\Omega X) \cong \pi_{k+1}(X)$, and so $\pi_k(\Omega X) \cong 0$ if $k \neq n-1$ and is $G$ when $k  = n-1$.
`\end{proof}`

We connect these concepts to cohomology now.

>[!proposition] Free Resolution from Universal Bundle
>The chain complex of cellular chain $C_*(EG)$ form a free resolution of $\mathbb{Z}$ over $\mathbb{Z}[G]$.

^0d1700

`\begin{proof}`
Recall $G$ acts freely on $EG$. This implies that in any cellular construction of $EG$, only $G$-free cells can appear (i.e. $G\times D^{k}$). Each such free cell constributes a copy of $\mathbb{Z}[G]$ when considering $C_*(EG)$ as a chain complex of $\mathbb{Z}[G]$-modules. Since $EG$ is contractible, it has homology $\mathbb{Z}$ in degree $0$, so we can augment $EG$ to give the desired free resolution $EG\to \mathbb{Z}$.
`\end{proof}`

[[Bertrand Guillou Notes#^0d1700]] implies that we can compute the (co)homology of classifying spaces in terms of group (co)homology. 

>[!corollary] Classifying Space (co)homology vs Group (co)homology
>Let $A$ be an abelian group viewed as a trivial $G$-module. Then we have isomorphisms
>$$H_*(BG;A)\cong H_*(G;A)\;\;\text{ and }\;\; H^*(BG;A)\cong H^*(G)$$

We now turn to the Borel construction of equivariant (co)homology.

>[!def] Borel Construction
>Let $X$ be a $G$-space. The **Borel construction** on $X$ is the orbit space of the diagonal $G$-action on $EG\times X$, which we write as $EG\times_GX$. The **Borel-equivariant homology and cohomology** of $X$ is defined to be
>$$H_*^{Borel}(X):= H_*(EG\times_GX)\;\;\;\;H_{Borel}^*(X):= H^*(EG\times_GX)$$

This is an example of an equivariant (co)homology theory. However, soon we will study more important such theories such as the **Bredon cohomology theories**. We also write $X_{hG} := EG\times_GX$, and refer to it as the homotopy orbit space of $X$. This can be thought of as replacing $*$ in $X/G\cong *\times_GX$ by $EG$ under the "free resolution" $EG\to *$. In this way if $X^G\cong G\mathsf{Top}(*,X)$ is the set of $G$-fixed points of $X$, resolving with respect to $EG$ first we get the **homotopy fixed point space**, $X^{hG} := G\mathsf{Top}(EG,X)$. Note that Borel cohomology cannot distinguish $EG$ and $*$. This is an example of a more general phenomenon known as underlying equivalence.

>[!def] Underlying Equivalence
>A map of $G$-spaces $f:X\to Y$ is an **underlying equivalence** if it induces an equivalence on underlying spaces.

>[!proposition] Underlying Equivalences to $G$-equivalences
>The functor $EG\times -:G\mathsf{Top}\to G\mathsf{Top}$ sends underlying equivalences to $G$-equivalences.

This implies that the homotopy orbit and homotopy fixed points constructions take underlying equivalences to equivalences of $G$-spaces. Further, it also follows that Borel cohomology takes underlying equivalences to isomorphisms.

In order to keep developing the theory of Borel cohomology, and equivariant cohomology more generally, we take a brief digression into the theory of **Mackey Functors**.

First, for a subgroup $H \leq G$, note that as a universal cover $EG/H\simeq BH$, so $EG$ is a model for $EH$ and we obtain a quotient map
$$EG / H\twoheadrightarrow EG / G$$
that models $BH\to BG$, and this is an intermediate covering map of degree $|G:H|$ (recall that the degree of a covering map is the cardinality of any of its fibers, if it is path connected). Further, this gives an induced map on Borel constructions
$$p_H^G:EH\times_HX\to EG\times_GX$$
again of degree $|G:H|$ for any $G$-space $X$. Indeed, note that since the action of $G$ on $EG$ is free, the resulting diagonal action on $EG\times X$ is also free, and in fact a covering space action, and so the claim follows from the same Galois correspondence for covering space actions. The pullbacks $(p_H^G)^*$ will form our restrictions.

When these indexes are finite, our induction or transfer maps are induced by the fact that if $p:E\to B$ is a covering space map, we obtain maps on the level of homology and cohomology, $p^!:H_*(B)\to H_*(E)$ and $p_!:H^*(E)\to H^*(B)$ which are induced, at least on the level of chains, by sending an $n$-chain on $B$ to the sum of its lifts, which is equal in number to the degree of the cover. This implies that the composites
$$H_*(B)\xrightarrow{p^!}H_*(E)\xrightarrow{p_*}H_*(B)\;\;\text{ and }\;\;H^*(B)\xrightarrow{p^*}H^*(E)\xrightarrow{p_!}H^*(B)$$
are multiplication by the degree. With this data it follows that for a $G$-space $X$ and an abelian group $A$, the groups $H_{Borel}^*(EH\times_H X;A)$ as $H$ ranges over subgroups of $G$ form a $G$-Mackey functor, where $(p_H^G)_!$ forms our induction maps. The conjugation maps can be constructed by using a functorial description of the total space construction, $E$.

The property that the composite $(p_H^G)_!\circ (p_H^G)^*$ being multiplication by the subgroup index is a property of special Mackey functors known as **cohomological Mackey functors**. For example group cohomology satisfies this property.

### Bredon (co)Homology

We begin introducing another equivariant (co)homology theory.

>[!def] Orbit Category
>Let $\mathcal{O}_G$ denote the **orbit category** of $G$ whose objects are the $G$-orbits $G/H$ and whose morphisms are $G$-equivariant maps.

Note that since we are considering finite index subgroups, $\mathcal{O}_G$ is a full subcategory of the category $\mathsf{FinSet}_G$ of finite $G$-sets. We have a natural bijection
$$\mathsf{Hom}_{\mathcal{O}_G}(G / H, G / K) \cong \{gK \in G/K\,\mid\,g^{-1}Hg \subseteq K\}$$
and so in particular $\mathsf{Aut}_{\mathcal{O}_G}(G/H,G/H) = N_G(H)/H = W_G(H)$.

>[!def] Coefficient System
>A **coefficient system** for $G$ is a functor $M:\mathcal{O}_G^{op}\to \mathsf{Ab}$.

A Mackey functor is then just a pair of coefficient systems (one contravariant, $M^*:\mathcal{O}_G^{op}\to \mathsf{Ab}$, and one covariant, $M_*:\mathcal{O}_G\to \mathsf{Ab}$) such that the covariant functor preserves coproduct and together the two coefficient systems satisfy a coherency condition with respect to pullback diagrams. Explicitly, for every pullback diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BX%5Ctimes_YZ%7D%20%26%26%20Z%20%5C%5C%0A%09%5C%5C%0A%09X%20%26%26%20Y%0A%09%5Carrow%5B%22%7Bp_2%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bp_1%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Cbeta%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Calpha%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{X\times_YZ} &amp;&amp; Z \\
	\\
	X &amp;&amp; Y
	\arrow[&quot;{p_2}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{p_1}&quot;', from=1-1, to=3-1]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=3-3]
	\arrow[&quot;\beta&quot;, from=1-3, to=3-3]
	\arrow[&quot;\alpha&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

of $G$-sets, $M_*(\beta)\circ M^*(\alpha) = M^*(p_2)\circ M_*(p_1)$. To relate this to the axiomatic definition of Mackey functors we use the maps $\pi_H^K:G / H \to G / K$, when $H \leq K$, given by mapping $xH\mapsto xK$, as well as $c_g:G/H\to G/\mathsf{Ad}_g(H)$ given by $xH\mapsto xg^{-1}H$. Then the restriction $R_H^K := M^*(\pi^K_H)$ while the induction is $I^K_H := M_*(\pi_H^K)$, and the conjugation is $M_*(c_g) = M^*(c_{g^{-1}})$. The coset formula is a result of the pullback condition and the preservation of disjoint unions.

For example, if $X$ is a $G$-space, $\underline{\pi}_n(X)(G/H) := \pi_n(X^H)$ defines a coefficient system. Similarly, $\underline{H}_n(X;A)(G/K) := H_n(X^K;A)$ defines a coefficient system. Both of these are examples of coefficient system obtained from a **coefficient system of spaces** by post composing with an invariant landing in abelian groups.

If $X$ is a $G$-CW complex the assignment $\underline{C}_n(X)(G/K) := C_n^{cell}(X^K)$ defines a coefficient system, using the fact that fixed points of a $G$-CW complex form a CW complex. Further, fixing $K \leq G$ and letting $n$ vary we obtain a chain complex $\underline{C}_*(X)(G/K) := C_*^{cell}(X^K)$ where all the boundary maps induce maps of coefficient systems, so that $\underline{C}_*(X)$ is a **chain complex of coefficient systems**.

>[!def] Bredon Cohomology
>Let $X$ be a $G$-space and $\underline{M}:\mathcal{O}_G^{op}\to \mathsf{Ab}$ a $G$-coefficient system. Then $\mathsf{Hom}_{Coeff}(\underline{C}_*(X),\underline{M})$ is a cochain complex of abelian groups, which we write as $C_{Coeff}^*(X;M)$. The **Bredon cohomology of $X$ with coefficients in $\underline{M}$** 
>$$H^n_{Bredon}(X;\underline{M}) := H^n(C_{Coeff}^*(X;\underline{M}))$$
>which we write as $H^*_G(X;\underline{M})$.

Let us consider the case when $\underline{M}$ is the constant $G$-coefficient system associated with an abelian group $A$, denoted $\underline{A}$. A map of coefficient systems $\alpha:\underline{C}\to \underline{A}$ corresponds to a cone under $\underline{C}$ at $A$. Note that for any $G/H \in \mathcal{O}_G$ we have $\mathsf{Hom}_{\mathcal{O}_G}(G/e,G/H) \cong G/H$, and in particular we have a commuting triangle

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cunderline%7BC%7D(G%2FH)%7D%20%26%26%20%7B%5Cunderline%7BC%7D(G%2Fe)%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%20A%0A%09%5Carrow%5B%22%7B%5Cunderline%7BC%7D(eH)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7BG%2FH%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7BG%2Fe%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\underline{C}(G/H)} &amp;&amp; {\underline{C}(G/e)} \\
	\\
	&amp; A
	\arrow[&quot;{\underline{C}(eH)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\alpha_{G/H}}&quot;', from=1-1, to=3-2]
	\arrow[&quot;{\alpha_{G/e}}&quot;, from=1-3, to=3-2]
\end{tikzcd}
" /></p>

so the map of coefficient systems is determined by $\alpha_{G/e}$ uniquely. Further, recall that $\mathsf{Hom}_{\mathcal{O}_G}(G/e,G/e) \cong G$, and $\underline{C}(G/e)$ obtains a canonical $G$-action from this isomorphism. Therefore, since

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cunderline%7BC%7D(G%2Fe)%7D%20%26%26%20%7B%5Cunderline%7BC%7D(G%2Fe)%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%20A%0A%09%5Carrow%5B%22%7B%5Cunderline%7BC%7D(g)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7BG%2Fe%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7BG%2Fe%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\underline{C}(G/e)} &amp;&amp; {\underline{C}(G/e)} \\
	\\
	&amp; A
	\arrow[&quot;{\underline{C}(g)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\alpha_{G/e}}&quot;', from=1-1, to=3-2]
	\arrow[&quot;{\alpha_{G/e}}&quot;, from=1-3, to=3-2]
\end{tikzcd}
" /></p>

must commute for all $g \in G$, we have that
$$\mathsf{Hom}_{Coeff}(\underline{C},\underline{A})\cong \mathsf{Hom}_{\mathsf{Ab}}(\underline{C}(G/e) / G,A)$$
describing an adjunction between coefficient systems and abelian groups.



## Mackey Functors

The central importance of Mackey functors in equivariant stable homotopy theory is analogous to the importance of abelian groups in non-equivariant stable homotopy theory.

>[!def] Mackey Functor
>A **Mackey functor** $\underline{M}$ for a group $G$ is a pair of functors $R:\mathsf{Sub}(G)^{op}\to \mathsf{Ab}$, $I:\mathsf{Sub}(G)\to \mathsf{Ab}$, restriction and induction, that agree on objects, with image of $H$ denoted by $\underline{M}(H)$, together with a collection of maps $c^g_H:\underline{M}(H)\to \underline{M}(\text{Ad}_g(H))$ for all $H\leq G$ and $g\in G$, where $\text{Ad}_g:\mathsf{Sub}(G)\to \mathsf{Sub}(G)$ is an endoorphism on the category given by conjugation by $g$, such that for each $g \in G$, the collection of maps $c^g_H$ form a natural transformation from $R$ and $I$ to $R\circ \mathsf{Ad}_g$ and $I\circ \mathsf{Ad}_g$, respectively, and such that $c^g_H\circ c^{g'}_H = c^{gg'}_H$, and $c_H^h = 1_{\underline{M}(H)}$ when $h \in H$.
>
>Finally, the functors must satisfy the **double coset formula**
>$$R_L^H\circ I_K^H = \sum_{KhL \in K\backslash H / L}I^L_{\mathsf{Ad}_{h^{-1}}(K)\cap L}\circ c^{h^{-1}}_{K\cap \mathsf{Ad}_h(L)}\circ R_{K\cap \mathsf{Ad}_h(L)}^K$$
>for all $L,K \leq H \leq G$.

We can expand this to a slightly more general definition. Explicitly we can describe a Mackey functor $\underline{M}$ as a pair of functors $R,I$ from the category of finite $G$-sets to $\mathsf{Ab}$ such that finite disjoint unions of $G$-sets are sent to direct sums and for every pullback diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BX%5Ctimes_YZ%7D%20%26%26%20Z%20%5C%5C%0A%09%5C%5C%0A%09X%20%26%26%20Y%0A%09%5Carrow%5B%22%7Bp_2%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bp_1%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Cbeta%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Calpha%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{X\times_YZ} &amp;&amp; Z \\
	\\
	X &amp;&amp; Y
	\arrow[&quot;{p_2}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{p_1}&quot;', from=1-1, to=3-1]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=3-3]
	\arrow[&quot;\beta&quot;, from=1-3, to=3-3]
	\arrow[&quot;\alpha&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

$R(\beta)\circ I(\alpha) = I(p_2)\circ R(p_1)$. In this context the $c^g_H$ correspond to certain pullbacks for the isomorphism $H\to \mathsf{Ad}_g(H)$.

When $g$ normalizes $H$, $c^g_H:\underline{M}(H)\to \underline{M}(H)$ is an endomorphism of the group $\underline{M}(H)$, and since $H$ acts trivially we have a natural group action of the **Weyl group** of $H$, $W_G(H) := N_G(H)/H$, on $\underline{M}(H)$. In particular, this means that $\underline{M}(e)$ is equipped with a $G$-action.

Let us begin by defining a standard Mackey functor.

>[!def] Fixed Point Mackey Functor
>Let $M$ be an $R[G]$-module. The **fixed points Mackey functor** on $M$ is given by $\underline{F(M)}(H) := M^H$, the $H$-fixed points of $M$, on objects, with restriction $R_H^K:M^K\to M^H$ the inclusion of fixed points, and the induction map $I_H^K:M^H\to M^K$ given by
>$$I_H^K(m) := \sum_{kH \in K/H}k\cdot m$$
>and $c_g:M^H\to M^{gHg^{-1}}$ is given by acting by $g$.





#### References

[^1]: Guillou, B. (n.d.). CLASS NOTES EQUIVARIANT HOMOTOPY AND COHOMOLOGY MATH 751 (FALL 2020).
[^2]: Bohmann, A. M. (n.d.). BASIC NOTIONS OF EQUIVARIANT STABLE HOMOTOPY THEORY.
