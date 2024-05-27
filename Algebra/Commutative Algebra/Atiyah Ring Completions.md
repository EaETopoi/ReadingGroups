---
date: 2024-05-20T20:48:00
tags:
  - CommutativeAlgebra
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

In these notes we introduce and collect results on ring completions with respect to ideals, commenting on their application to Algebraic Geometry. We primarily follow the text by Atiyah[^1]. Before embarking on this task why do we care about completions of rings? Well in complex algebraic geometry we can pass to the complex topology and expand rational functions as power series about a given point. However, in abstract algebraic geometry more generally we do not have the complex topology to fall back on, so instead we have to take the approach of considering formal power series. We also see completions as important concepts in number theory, such as in the formulation of the $p$-adic numbers. This section clarifies the general procedure of **adic completion**. 

Completions provide another method for concentrating attention near a point of a scheme, though in a coarser fashion than localization (non-singular points in a variety of dimension $n$ all have completions being formal power series in $n$ variables but these local rings for two such points cannot be isomorphic in general unless the varieties they lie on are birationally equivalent).

Two of the important properties we will see is that completion, like localization, preserves exactness and the Noetherian property when restricted to finitely-generated modules. An important tool in the study of completions are graded rings (with $k[x_1,..,x_n]$ with grading given by degree being a prototypical example), which are also foundational for the study of projective algebraic geometry.

If $A$ is a local ring of a point $P$ on a variety $V$ with maximal ideal $\mathfrak{m}$, its associated graded ring $G_\mathfrak{m}(A)$ will correspond to the projective tangent cone at $P$ (i.e. all lines through $P$ which are tangent to $V$ at $P$). 


## Topologies and Completions

Let $G$ be a topological abelian group, not necessarily Hausdorff. If $\{0\}$ is closed in $G$, then the diagonal is closed in $G\times G$ (being the kernel of the difference mapping) and so $G$ is Hausdorff. If $a$ is a fixed element of $G$, translation by $a$ is a homeomorphism, so $G$ is Hausdorff if and only if it has a closed point. Further, this implies we can translate neighborhoods to and from $0$, so the topology of $G$ is uniquely determined by its neighborhood system about $0$.

>[!lemma]
>Let $H$ be the intersection of all neighborhoods of $0$ in $G$. Then
>- $H$ is a subgroup of $G$
>- $H$ is the closure of $\{0\}$
>- $G/H$ is Hausdorff
>- $G$ is hausdorff $\iff$ $H = 0$.

^8d5482

`\begin{proof}`
The first bullet follows immediately from the continuity of the group operations. For the second bullet note that $x \in H$ if and only if $0 \in x-U$ for all neighborhoods $U$ of $0$ (and hence all neighborhoods of $x$), which holds if and only if $x$ is in the closure of $\{0\}$.

The third bullet is a general fact about coset spaces of closed subgroups. Namely, if $N \leq G$ is a closed subgroup, then $G/N$ is Hausdorff. To show this let $xN,yN \in G/N$ such that $xN \neq yN$, or in other words $e \notin xNy^{-1}$. Note that $xNy^{-1}$ is closed since elements of $G$ act by homeomorphisms, so there exists an open neighborhood $U$ of $e$ not intersecting $xNy^{-1}$. Taking the pre-image of $U\cap U^{-1}$ under $(x,y)\mapsto xy^{-1}$ we obtain a basic open $A\times A$ since for any $(x,y)$, $xy^{-1} \in U\cap U^{-1}$ if and only if $yx^{-1} \in U\cap U^{-1}$ since $U\cap U^{-1}$ is symmetric. Next, setting $V = A\cap A^{-1}$ we find that $V$ is a symmetric open neighborhood of $e$ satisfying $VV \subseteq U$. Then $V,VV\cap xNy^{-1} = \emptyset$. As $V$ is symmetric this implies that $e \notin VxNy^{-1}V^{-1} = (Vx)N(Vy)^{-1}$. Further, since $NN = N$ and $N^{-1} = N$, as it is a group, $e \notin (VxN)(VyN)^{-1}$. Now $VxN$ and $VyN$ are open neighborhoods of $xN,yN$ in $G/N$, respectively, and since $e \notin (VxN)(VyN)^{-1}$, they cannot intersect. This concludes the proof that $G/N$ is Hausdorff.

The last bullet is immediate from the discussion prior to the lemma.
`\end{proof}`

Suppose we are in a case where $0 \in G$ has a countable basis for its neighborhood system. Then we can define the completion $\hat{G}$ of $G$ by means of Cauchy sequences, where a **Cauchy sequence** in $G$ is a sequence of elements $(x_\nu)$ of $G$ such that for any neighborhood $U$ of $0$, there exists a sufficiently large integer $s(U)$ with the property that if $\mu,\nu\geq s(U)$, then $x_\mu-x_\nu \in U$. We say that two Cauchy sequences $(x_\nu)$ and $(y_\nu)$ are equivalent if $x_\nu-y_\nu\to 0$ in $G$. Then we can define $\hat{G}$ to be the set of equivalence classes of Cauchy sequences, which then becomes an abelian group via pointwise operations. The natural map $\phi:G\to \hat{G}$ is then a homomorphism of topological abelian groups, which is in general not injective as its kernel is the intersection of all open neighborhoods of $0$ in $G$ (i.e. the subgroup $H$ given previously). Thus, $\phi$ is injective if and only if $G$ is Hausdorff.

This entire construction can be generalized to the non-countable case using nets.

Note that for a continuous map $f:G\to H$ of abelian topological groups, $f$ preserves Cauchy sequences (**note** this is not generally true if $f$ is not a group homomorphism). Then $f$ induces a homomorphism $\hat{f}:\hat{G}\to \hat{H}$ on completions, which is continuous. In particular, $\hat{-}$ defines a functor $\mathsf{TopAb} \to \mathsf{CpTopAb}$.

### Topological Groups in Commutative Algebra

Moving forward we assume that a topological group $G$ has a countable basis for the neighborhood system about $0$ given by subgroups of $G$. In other words, we have a sequence of subgroups
$$G = G_0 \supseteq G_1 \supseteq \cdots \supseteq G_n \supseteq \cdots$$
such that for any subset $U \subseteq G$, $U$ is a neighborhood of $0$ if and only if there exists $n \geq 0$ such that $U \supseteq G_n$. We generate a topology on $G$ by completing this neighborhood basis at $0$ to a filter and then taking all translates to get the neighborhood systems of all other points in $G$. A set is then open if and only if it is a neighborhood of all of its points, and by construction this topology turns $G$ into a topological abelian group. Additionally, by construction each of the $G_n$ are open in $G$.

Recall that an open subgroup of a topological group is closed since it is the complement of the union of all non-trivial cosets, where cosets are homeomorphic to the group and hence open, so the complement is open, being a union of open sets.

>[!example] p-adic Topology
>Consider the abelian group $\mathbb{Z}$. We define a topology on $\mathbb{Z}$ by specifying the basis for a neighborhood system about $0$ in $\mathbb{Z}$ given by $\mathbb{Z} \supseteq p\mathbb{Z}\supseteq p^2\mathbb{Z} \supseteq \cdots$. 

In the current case of topologies given by sequences of subgroups of a group we can provide a purely algebraic definition of the completion procedure. Suppose $(x_\nu)$ is a Cauchy sequence in the group $g$. Then the image of the sequence in $G/G_n$ for any $n$ will ultimately become constant. Denote this eventual value by $\xi_n$. Passing from $n+1$ to $n$ we observe that $\xi_{n+1}\mapsto \xi_n$ under the quotient $$G/G_{n+1}\xrightarrow{p_{n+1}}G/G_n$$
Thus, we obtain a **coherent sequence** $(\xi_n)$ with respect to the sequence of maps 
$$\cdots\to  G/G_{n+1}\to G/G_n\to \cdots \to G/G_0 \cong 0$$
which is an element of the limit. On the other hand, such a coherent sequence $(\xi_n)$ can be used to construct a Cauchy sequence $x_n$ given rise to it by taking $x_0$ to be any element of the coset $\xi_n$. Thus, in this context we can define $\hat{G}$ equally as the inverse limit
$$\hat{G}\cong \lim\limits_{\leftarrow}G/G_n$$
with connecting maps given by quotients $p:G/G_{n+1}\to G/G_n$. 

>[!def] Inverse System
>An **inverse system** in a category $\mathcal{C}$ is a functor $F:I^{op}\to \mathcal{C}$ where $I$ is a directed set viewed as a category. Explicitly, an inverse system consists of a family of objects $\{A_\nu\}_{\nu \in I}$ together with a map $f_{\nu\mu}:A_\mu\to A_\nu$ for every $\nu \leq \mu$ such that $f_{\nu\nu} = 1_{A_\nu}$ and the maps satisfy the cocycle condition $f_{\nu\omega} = f_{\nu\mu}\circ f_{\mu\omega}$ for $\nu \leq \mu\leq \omega$.
>
>The **inverse limit** of an inverse system $A_\bullet$ is the categorical limit
>$$A = \lim\limits_{\xleftarrow[\nu \in I]{}}A_i$$

Note that the observations preceding the definition imply that if we have a different sequence of subgroups which generates the same topology, the resulting inverse limits are isomorphic. An additional nice property of our inverse systems of interest here is that all connecting morphisms $G/G_{n+1}\to G/G_n$ are surjective. In such a case we say that it is a **surjective system**. These satisfy nice properties with respect to preservation of exact sequences.

>[!proposition] Inverse Limit Exact Sequence
>Let $0\to A_\bullet \to B_\bullet \to C_\bullet \to 0$ be an exact sequence of inverse limit diagrams over a common directed set $I$ in an abelian category with $I$ shaped limits. Then 
>$$0\to \lim\limits_{\leftarrow}A_\nu \to \lim\limits_{\leftarrow}B_\nu\to \lim\limits_{\leftarrow}C_\nu$$
>is exact. If the system $A_\bullet$ is also surjective, $I = \mathbb{N}$, the abelian category is complete, and products commute with epimorphisms, then $$0\to \lim\limits_{\leftarrow}A_\nu \to \lim\limits_{\leftarrow}B_\nu\to \lim\limits_{\leftarrow}C_\nu\to 0$$
>is exact.

^22285c

`\begin{proof}`
Since limits commute the first exact sequence is immediate as taking $\lim\limits_{\leftarrow}$ preserves kernels. Next, suppose $A_\bullet$ is surjective and the hypotheses on $I$ hold, and let $A,B,C$ denote products over the directed systems. We can define a map $d^A:A\to A$ given via projections as $\pi_\nu\circ d^A = \pi_\nu - p_{\nu+1}\circ \pi_{\nu+1}$, and similarly for $B$ and $C$. Then $\ker d^A$ is exactly the inverse limit of our system. Note that since products commute with epimorphisms in our category we obtain a commutative diagram of exact sequences
$$\begin{CD}0 @>>> A @>>> B @>>> C @>>> 0 \\ @. @Vd^AVV @Vd^BVV @Vd^CVV @. \\ 0 @>>> A @>>> B @>>> C @>>> 0 \end{CD}$$
which by the snake lemma gives an exact sequence
$$0\to \ker d^A\to \ker d^B\to \ker d^C\to \text{coker}\,d^A\to \text{coker}\,d^B\to \text{coker}\, d^C\to 0$$
For the last step we argue by embedding into a category of $R$-modules so we can work element wise. We wish to show $d^A$ is surjective provided $A_\bullet$ is a surjective system. Let $(a_n)_{n \in \mathbb{N}} \in A$. Set $x_0 = 0$ and choose $x_1$ such that $p_1(x_1) = -a_0$. Now, suppose that the equations hold for all $m\leq n$. Then we have $x_0,x_1,...,x_n,x_{n+1}$ such that $x_n-p_{n+1}(x_{n+1}) = a_n$. Now, since $p_{n+2}$ is surjective there exists $x_{n+2}$ such that $p_{n+2}(x_{n+2}) = x_{n+1}-a_{n+1}$. By induction we obtain an element $(x_n)_{n \in \mathbb{N}} \in A$ such that $d^A((x_n)_{n \in \mathbb{N}})) = (a_n)_{n \in \mathbb{N}}$. Thus, $\text{coker}\,d^A = 0$, so the above exact sequence gives the SES
$$0\to \lim\limits_{\leftarrow}A_\nu \to \lim\limits_{\leftarrow}B_\nu \to \lim\limits_{\leftarrow}C_\nu \to 0$$
`\end{proof}`

We will write $\lim\limits_{\leftarrow}^1A_\nu$ for $\text{coker}\,d^A$ moving forward. 

>[!corollary]
>Let $0\to G'\xrightarrow{i} G\xrightarrow{p} G''\to 0$ be a SES of groups. Let $G$ have a topology defined by a sequence $\{G_n\}$ of subgroups, and give $G'$ and $G''$ the subspace and quotient topologies, respectively (in this case the subspace topology is given by $\{i^{-1}(G_n)\}$ and $\{p(G_n)\}$). Then 
>$$0\to \hat{G}'\to \hat{G}\to \hat{G}''\to 0$$
>is a SES.
>

^9706e0

`\begin{proof}`
We can apply [[Atiyah Ring Completions#^22285c]] to the exact sequences
$$0\to G'/i^{-1}(G_n)\to G/G_n\to G''/p(G_n)\to 0$$
which fit in an exact sequence of directed systems.
`\end{proof}`

If we apply [[Atiyah Ring Completions#^9706e0]] with $G' = G_n$, then $G'' = G/G_n$ has the discrete topology, so $\hat{G}'' = G''$, which allows us to deduce that 
$$\hat{G}/\hat{G}_n \cong G/G_n \tag{1}$$
Upon taking inverse limits it follows that 
$$\hat{\hat{G}} \cong \hat{G}$$
so taking completions is an idempotent procedure. In general, if $\phi:G\to \hat{G}$ is an isomorphism we say that $G$ is **complete**, so in particular all completions are complete. Note that with the topology inherited from $\hat{G} = \hat{G}_0 \supseteq \hat{G}_1 \supseteq \cdots \supseteq \hat{G}_n\supseteq \cdots$$ our map $\phi$ is injective and $\bigcap_{n=0}^{\infty}\hat{G}_n = \{0\}$, so $\hat{G}$ is Hausdorff as well. ^0c5e37

>[!example] Ring Completion
>Take $G = A$, a ring, and $G_n = I^n$ for $I$ and ideal in $A$. The topology so defined by $A \supseteq I \supseteq I^2 \supseteq \cdots$ is called the **$I$-adic topology** on $A$. Since the $I^n$ are ideals, with this topology $A$ becomes a **topological ring**. By [[Atiyah Ring Completions#^8d5482]] $A$ is a Hausdorff topological ring if and only if $\bigcap_{n=0}^{\infty}I^n = (0)$. The **completion** $\hat{A}$ of $A$ is again a topological ring with topology induced by $\hat{A} \supseteq \hat{I}\supseteq \hat{I}^2 \supseteq \cdots$, and $\phi:A\to \hat{A}$ is a continuous ring homomorphism whose kernel is $\bigcap_{n=0}^{\infty}I^n$ (indeed $\ker \phi\to \hat{A}$ is the zero map means $\ker\phi\to A/I^n$ is zero for all $n$, so $\ker\phi \subseteq I^n$ for each $n$).

>[!example] Module Completion
>Take $G = M$ an $A$-module and $G_n = I^nM$ where $I \subseteq A$ is an ideal. This defines the **$I$-adic topology** on $M$, and the completion $\hat{M}$ is a topological $\hat{A}$-module. 
>
>If $f:M\to N$ is an $A$-module homomorphism, then $f(I^nM) \subseteq I^nF(M) \subseteq I^nM$, and so $f$ is continuous with respect to the $I$-adic topologies on both modules. Further, $f$ defines a topological $\hat{A}$-module homomorphism $\hat{f}:\hat{M}\to \hat{N}$.

>[!example]
>1. For $A = k[x]$, $k$ a field and $x$ an indeterminate, setting $I = \langle x\rangle$ gives the completion $\hat{A} = k[[x]]$, the ring of formal power series, with $\hat{I}$-adic topology.
>2. For $A = \mathbb{Z}$, $I = p\mathbb{Z}$, $p$ and prime, we have $\hat{A}$ is the ring of **$p$-adic integers**. Its elements can be realized as infinite series $\sum_{n=0}^{\infty}a_np^n$, for $0 \leq a_n \leq p-1$, where in the topology $p^n\to 0$ as $n\to \infty$.


### Filtrations 

Throughout let $A$ denote a ring and $I$ an ideal in $A$. For an $A$-module $M$, we can define the $I$-topology in a few ways. To see this we will take an aside on filtrations.

>[!def] Filtrations
>An infinite chain $M = M_0 \supseteq M_1 \supseteq \cdots \supseteq M_n \supseteq \cdots$, where $M_n$ are submodules of $M$, is called a **filtration** of $M$, and denoted by $(M_n)_{n\geq 0}$. We say that it is an **$I$-filtration** if $IM_n \subseteq M_{n+1}$ for all $n \geq 0$, and a **stable $I$-filtration** if $IM_n = M_{n+ 1}$ for all sufficiently large $n$. 

It follows that $(I^nM)_{n\geq 0}$ is always a stable $I$-filtration. 

>[!lemma] Bounded Difference
>If $(M_n)_{n\geq 0}$ and $(M_n')_{n\geq 0}$ are stable $I$-filtrations of$M$, then they have a **bounded difference** (i.e. there exists an integer $n_0$ such that $M_{n+n_0}\subseteq M_n'$ and $M_{n+n_0}'\subseteq M_n$ for all $n \geq 0$). Hence, all stable $I$-filtrations determine the same topology on $M$, named the $I$-topology.

^6107f9

`\begin{proof}`
It suffices to take $M_n' = I^nM$ the standard stable $I$-filtration. Since $M_n$ is a stable $I$-filtration we have that $IM_n\subseteq M_{n+1}$ for all $n \geq 0$, and there exists $n_0 \in \mathbb{N}$ such that for $n \geq n_0$, $IM_n = M_{n+1}$. Then for all $n\geq 0$ we have $I^nM \subseteq I^{n-1}M_1 \subseteq \cdots \subseteq M_n$ and for all $n \geq 0$, $M_{n+n_0} = I^nM_{n_0} \subseteq I^nM$, as desired.
`\end{proof}`

## Graded Rings and Modules

The theory of graded rings provides the necessary algebraic structure for considering projective geometry. In this section we introduce the notion of graded rings and modules and consider some of the basic properties.

>[!def] Graded Rings
>A **graded ring** graded by a monoid $M$ is a ring $A$ together with a family $(A_m)_{m \in M}$ of additive subgroups of $A$ such that $A = \bigoplus_{m \in M}A_m$ such that $A_mA_n \subseteq A_{mn}$ for all $m,n \in M$. In particular $A_e$ is a subring of $A$, where $e$ is the identity of the monoid $M$ and each $A_m$ is an $A_e$-module.

>[!def] Graded Module
>If $A$ is a graded ring, a **graded $A$-module** is an $A$-module $K$ together with a family $(K_m)_{m \in M}$ of additive subgroups of $M$ such that $K = \bigoplus_{m \in M}K_m$ and $A_mK_n \subseteq K_{mn}$ for all $m,n \in M$. So each $K_m$ is an $A_e$-module.
>
>An element $x$ of $K$ is said to be **homogeneous** if $x \in K_m$ for some $m \in M$, in which case we say $x$ is of degree $m$. 

Since any element of a graded $A$-module can be written uniquely as a finite sum of homogeneous elements, $y = \sum_{m \in M}y_m$,we say that the non-zero $y_m$ are the **homogeneous components of $y$**.

In most cases we consider $M$ is either the abelian group $\mathbb{Z}$ or the submonoid $\mathbb{N}$, with operation given by addition.

>[!example]
>$A = R[x_1,...,x_n]$, for $R$ a cring, is a ring graded in $\mathbb{N}$ with $A_n =$ the set of all homogeneous polynomials of degree $n$.
>

If $K$ and $N$ are graded $A$-modules, a **homomorphism of graded $A$-modules** is an $A$-module homomorphism $f:K\to N$ such that $f(K_m) \subseteq N_m$ for all $m \in M$. This gives us a category $(A,M)\mathsf{GrMod}$ of graded modules associated with a graded ring $A$.

>[!def] Ideal of non-constant terms
>If $A$ is a ring graded over $\mathbb{Z}$ (or $\mathbb{N}$), let $A_+ = \bigoplus_{n>0}A_n$, which for $\mathbb{N}$ is an ideal in $A$.

>[!proposition] Graded Noetherian Ring
>The following are equivalent for a ring $A$ graded over $\mathbb{N}$:
>1. $A$ is Noetherian as a ring
>2. $A_0$ is Noetherian as a ring and $A$ is finitely generated as an $A_0$-algebra.

`\begin{proof}`
Suppose first that $A$ is Noetherian. Then $A_0 \cong A/A_+$ is Noetherian, since the quotient of Noetherian ring is Noetherian. Since $A$ is Noetherian and $A_+$ is an ideal it is finitely generated, so there exists $x_1,...,x_s \in A_+$ which we can take to be homogeneous elements of degrees $k_1,\dots,k_s$ (all $> 0$). Let $A'$ be the subring of $A$ generated by $x_1,...,x_s$ over $A_0$. We wish to show $A_n \subseteq A'$ for all $n \geq 0$, by induction on $n$. This is vacuously true for $n = 0$. Inductively suppose the claim holds for some $n-1$, $n > 0$. Let $y \in A_n$. Since $y \in A_+$ $y$ is a linear combination of $x_i$, say $y = \sum_{i=1}^sa_ix_i$, where $a_i \in A_{n-k_i}$ (where $A_m = 0$ for $m < 0$). Since each $k_i > 0$, our inductive hypothesis implies that each $a_i$ is a polynomial in the $x_i$'s with coefficients in $A_0$, $a_i = a_i(x_1,\dots,x_s) \in A_0[x_1,\dots,x_s]$. Thus, we have that 
$$y = \sum_{i=1}^sa_i(x_1,\dots,x_s)x_i \in A_0[x_1,\dots,x_s]$$
so $A_n \subseteq A_0[x_1,...,x_s] = A'$. As this holds for all $n \geq 0$ we have that $A = A'$, and so is a finitely generated $A_0$-algebra.

The implication $(2)\implies (1)$ follows from Hilbert's basis theorem.
`\end{proof}`
Given a non-graded ring $A$, we can construct a ring graded over $\mathbb{N}$ in a number of ways. If $I$ is an ideal of $A$ we can form the graded ring $A_I = \bigoplus_{n=0}^{\infty}I^n$. Similarly, if $M$ is an $A$ module and $M_n$ is an $I$-filtration of $M$, then $M_I = \bigoplus_{n=0}^{\infty}M_n$ is a graded $A_I$-module, as $I^mM_n\subseteq M_{m+n}$. Stability will tell us valuable information about when these graded $A_I$-module is finitely generated.

When $A$ is Noetherian and $I$ is finitely generated, $A_I = A[x_1,...,x_n]$ is a finitely generated $A$-algebra, and Noetherian by Hilbert's Basis Theorem. 

>[!lemma] F.g. iff Stable
>If $A$ is Noetherian, $M$ is a finitely generated $A$-module, and $(M_n)_{n\geq 0}$ is an $I$-filtration of $M$ for  an ideal $I$ of $A$, then the following are equivalent:
>1. $M_I$ is a finitely generated $A_I$-module
>2. The filtration $(M_n)_{n\geq 0}$ is stable.

^2cb666

`\begin{proof}`
Since $M$ is finitely generated as an $A$-module, each $M_n$ is also finitely generated as an $A$-module. Thus, each $Q_n = \bigoplus_{r=0}^nM_r$ is finitely generated as an $A$-module. We can extend $Q_n$ to an $A_I$-submodule of $M_I$ by defining
$$M_{I,n} := Q_n\oplus \bigoplus_{m\geq 1}I^mM_n$$
Since $Q_n$ is finitely generated as an $A$-module, $M_{I,n}$ is finitely generated as an $A_I$-module. The $M_{I,n}$ form an ascending chain whose union is $M_I$. 

From the remark above the Lemma we have that $A_I$ is  Noetherian, so $M_I$ is finitely generated as an $A_I$-module if and only if the chain of $M_{I,n}$ stabilizes, i.e. there exists $n_0 \geq 0$ such that $M_I = M_{I,n_0}$, which holds if and only if $M_{n_0+r} = I^rM_{n_0}$ for all $r \geq 0$, which is exactly the stability condition for a filtration.
`\end{proof}`

We now move to prove the **Artin-Rees lemma** which will be important for a number of properties of graded modules.

>[!proposition] Artin-Rees lemma
>Let $A$ be a Noetherian ring, $I$ an ideal in $A$, $M$ a finitely-generated $A$-module, and $(M_n)_{n\geq 0}$ a stable $I$-filtration of $M$. If $M'$ is a submodule of $M$, then $(M'\cap M_n)$ is a stable $I$-filtration of $M'$.

^64e590

`\begin{proof}`
By assumption we have $I(M'\cap M_n) \subseteq IM'\cap IM_n \subseteq M'\cap M_{n+1}$, so $(M'\cap M_n)_{n \geq 0}$ is indeed an $I$-filtration. Thus, it defines a graded $A_I$-module which is a submodule of $M_I$. Since $M_I$ is finitely generated, and hence Noetherian as $A_I$ is Noetherian, by [[Atiyah Ring Completions#^2cb666]], it follows that the submodule $M_I'$ is also finitely generated. Applying  [[Atiyah Ring Completions#^2cb666]] again we find that the filtration $(M'\cap M_n)_{n\geq 0}$ is stable.
`\end{proof}`

If we take the standard example of a stable $I$-filtration on a module, $M_n = I^nM$, then we can obtain the usual Artin-Rees lemma:

>[!corollary] Classical Artin-Rees lemma
>Let $A$ be a Noetherian ring, $I$ an ideal in $A$, and $M$ a finitely-generated $A$-module. If $M'$ is a submodule of $M$, then there exists an integer $k$ such that $$(I^nM)\cap M' = I^{n-k}((I^kM)\cap M')$$
>for all $n \geq k$.

On the other hand, combining [[Atiyah Ring Completions#^64e590]] with [[Atiyah Ring Completions#^6107f9]] we obtain the following significant version.

>[!theorem]
>Let $A$ be a Noetherian ring, $I$ an ideal, $M$ a finitely-generated $A$-module and $M'$ a submodule of $M$. Then the filtrations $I^nM'$and $(I^nM)\cap M'$ have **bounded difference**. In particular, the $I$-topology of $M'$ coincides with the topology induced by the $I$-topology of $M$.

^0426e3

If we combine [[Atiyah Ring Completions#^0426e3]] with [[Atiyah Ring Completions#^22285c]] we obtain the following exactness property of completions:

>[!proposition] Exactness of Completions
>If $0\to M'\to M\to M''\to 0$ is an exact sequence of finitely-generated modules over a Noetherian ring $A$. Let $I$ be an ideal of $A$, then the sequence of $I$-adic completions $$0\to \hat{M}' \to \hat{M}\to \hat{M}''\to 0$$
>is exact.

^01cdb5

Note that as we have a natural map $\phi:A\to \hat{A}$, we can always regard the completion $\hat{A}$ as an $A$-algebra, and so any $A$-module $M$ can form a $\hat{A}$-module under change of scalars, $\hat{A}\otimes_AM$. We can compare this to the $\hat{A}$-module $\hat{M}$. The natural $A$-module homomorphism $M\to \hat{M}$ allows us to define a $\hat{A}$-module homomorphism
$$\hat{A}\otimes_AM\to \hat{A}\otimes_A\hat{M}\to \hat{A}\otimes_{\hat{A}}\hat{M} \cong \hat{M}$$
where the second arrow is from the universal property of the $\otimes_A$ tensor. This map is not only in general not an isomorphism, but is often not even injective or surjective. However, assuming certain finiteness conditions we do obtain such a result.

>[!proposition] Tensor with Completion
>For any ring $A$, if $M$ is finitely-generated then the map $\hat{A}\otimes_AM\to \hat{M}$ is surjective. If, futher, $A$ is Noetherian, then $\hat{A}\otimes_AM\to \hat{M}$ is an isomorphism of $\hat{A}$-modules.

^e90ab1

`\begin{proof}`
By [[Atiyah Ring Completions#^01cdb5]] we have that the $I$-adic completion preserves finite direct sums. Thus, if $F \cong A^{\oplus n}$ then $\hat{A}\otimes_AF\cong \hat{A}^{\oplus n}\cong \hat{F}$. Now, suppose $M$ is finitely generated and write down its associated short exact sequence
$$0\to N\to F\to M\to 0$$
Using the fact that tensoring is right exact and  [[Atiyah Ring Completions#^01cdb5]] we obtain the commutative diagram
$$\begin{CD} @. \hat{A}\otimes_AN @>>> \hat{A}\otimes_AF @>>> \hat{A}\otimes_AM @>>> 0 \\ @. @V\gamma VV @V\beta VV @V\alpha VV @. \\ 0 @>>> \hat{N} @>>> \hat{F} @>>\delta> \hat{M} @>>> 0 \end{CD}$$
Since $\beta$ is an isomorphism and $\delta$ is surjective, we must have that $\alpha$ is also surjective. Now, assume $A$ is Noetherian. Then $N$ is also finitely generated, so from the first argument $\gamma$ is also surjective. Since $\beta$ is an isomorphism, and so in particular a monomorphism, it follows by the **4-lemma** that $\alpha$ is also a monomorphism. Then as maps which are both monic and epic are isomorphisms in abelian categories we are done.
`\end{proof}`
It follows that when $A$ is Noetherian, tensoring with $\hat{A}$ is exact when restricted to the category of finitely-generated $A$-modules. This proves the following by part $(5)$ of [[Fu Flat Modules#^79d8e7]].

>[!proposition]
>If $A$ is a Noetherian ring, $I$ an ideal, and $\hat{A}$ the $I$-adic completion of $A$, then $\hat{A}$ is a flat $A$-algebra.

Thus, although the completion functor is not generally exact for non-finitely-generated modules, the functor $\hat{A}\otimes_A-$ is exact, and the two functors coincide on finitely-generated modules.

We finish this section by analyzing the ring $\hat{A}$ in more depth.

>[!proposition] Properties of Ring Completion
>Let $A$ be a Noetherian ring and $I$ an ideal of $A$. If $\hat{A}$ denotes its $I$-adic completion then
>1. $\hat{I} = I\hat{A} \cong \hat{A}\otimes_AI$ 
>2. $\widehat{(I^n)} = (\hat{I})^n$ 
>3. $I^n/I^{n+1}\cong \hat{I}^n/\hat{I}^{n+1}$ 
>4. $\hat{I}$ is contained in the Jacobson radical of $\hat{A}$

^515897

`\begin{proof}`
Note that as $A$ is Noetherian $I$ is finitely generated. Then [[Atiyah Ring Completions#^e90ab1]] implies that $\hat{A}\otimes_AI \cong \hat{I} = I\hat{A}$, proving $(1)$. Next, Applying $(1)$ to $I^n$ we can deduce that $$\widehat{(I)^n} \cong I^n\hat{A} = (I\hat{A})^n \cong (\hat{I})^n$$
Next, applying Equation [[Atiyah Ring Completions#^0c5e37|(1)]] we obtain $A/I^n\cong \hat{A}/\hat{I}^n$, which gives $(3)$ once quotients are taken. Since $\hat{A}$ is complete for its $\hat{I}$-topology, if $x \in \hat{I}$ then the sequence $\sum_{n=0}^\infty x^n$ converges in $\hat{A}$ in the $\hat{I}$-topology. But $(1-x)\cdot \sum_{n=0}^{\infty}x^n = 1$, so $1-x$ is a unit in $\hat{A}$. Recall that the Jacobson radical $\mathfrak{R}$ of a ring $A$ is characterized by the fact that $x \in \mathfrak{R}$ if and only if $1-xy$ is a unit in $A$ for all $y \in A$. Thus, we must have that every element of $\hat{I}$ is an element of the Jacobson radical of $\hat{A}$, or in other words $\hat{I} \subseteq \mathfrak{R}$.
`\end{proof}`

Often we will be considering adic completions of local rings with respect to maximal ideals (closed points) in algebro-geometric settings. When this is the case, and we add a finiteness condition, we find that the local ring structure is preserved.

>[!proposition]
>Let $A$ be a Noetherian local ring with maximal ideal $\mathfrak{m}$. Then the $\mathfrak{m}$-adic completion $\hat{A}$ of $A$ is a local ring with maximal ideal $\hat{\mathfrak{m}}$.

`\begin{proof}`
By part $(3)$ of [[Atiyah Ring Completions#^515897]] we have $\hat{A}/\hat{\mathfrak{m}}\cong A/\mathfrak{m}$. Since $A/\mathfrak{m}$ is a field so is $\hat{A}/\hat{\mathfrak{m}}$, and so $\hat{\mathfrak{m}}$ is maximal in $\hat{A}$. By part $(4)$ we also have that $\hat{\mathfrak{m}}$ is contained in the Jacobson radical of $\hat{A}$, which is only possible if $\hat{\mathfrak{m}}$ is the unique maximal ideal of $\hat{A}$. It follows that $\hat{A}$ is a local ring.
`\end{proof}`

As we discussed at the start of the section taking the completion of a ring loses a significant amount of information in favour of certain key pieces. However, how do we know how much is actually lost upon taking completions? Krull's Theorem provides a partial answer to this question.

>[!theorem] Krull's Theorem
>Let $A$ be a Noetherian ring, $I$ an ideal of $A$, $M$ a finitely-generated $A$-module, and $\hat{M}$ the $I$-completion of $M$. Then the kernel $\ker\,\phi = \bigcap_{n=1}^{\infty}I^nM$ of $\phi:M\to \hat{M}$ consists of exactly those $x \in M$ which are annihilated by some element of the coset $1+I$.

^3d8ed9

`\begin{proof}`
Since $\ker\phi$ is an intersection of all neighborhoods of $0$ in $M$, it is closed in the $I$-topology and the topology induced on it is trivial. By [[Atiyah Ring Completions#^0426e3]] the induced topology on $\ker\phi$ is coincides with its $I$-topology. Since $I\ker\phi$ is a neighborhood in the $I$-topology it follows that $I\ker\phi = \ker \phi$. As $M$ is finitely-generated as an $A$-module and $A$ is Noetherian, $M$ is Noetherian and so $\ker\phi$ is also finitely-generated. As $I\ker\phi = \ker\phi$ and $\ker\phi$ is finitely generated, [[Atiyah Localization#^3db31f]] implies that there exists $\alpha \in I$ such that $(1-\alpha)\ker\phi = 0$. On the other hand, if $(1-\alpha)x = 0$ for some $\alpha \in I$, then $x = \alpha^nx$ for all $n \geq 0$, so $x \in \bigcap_{n=0}^{\infty}I^nM = \ker \phi$ .
`\end{proof}`
>[!remark]
>If $S$ is a multiplicatively closed set of the form $1+I$ for an ideal $I$ of $A$, then [[Atiyah Ring Completions#^3d8ed9]] says that $A\to \hat{A}$ and $A\to S^{-1}A$ have the same kernel. Further, for $\alpha \in \hat{I}$, $$(1-\alpha)^{-1} = 1+\alpha+\alpha^2+\cdots$$
>converges in $\hat{A}$ so that every element of $S$ becomes a unit in $\hat{A}$. Hence, by the universal property of the localization we obtain a unique injective map $S^{-1}A\to \hat{A}$ making the triangle 
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20%7B%5Chat%7BA%7D%7D%20%5C%5C%0A%09A%20%26%20%7BS%5E%7B-1%7DA%7D%0A%09%5Carrow%5B%22%5Cphi%22%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-2%2C%20to%3D1-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	&amp; {\hat{A}} \\	A &amp; {S^{-1}A}	\arrow[&quot;\phi&quot;, from=2-1, to=1-2]	\arrow[from=2-1, to=2-2]	\arrow[dashed, from=2-2, to=1-2]\end{tikzcd}" /></p>
>commute.

In this way we can identify $S^{-1}A$ with a subring of $\hat{A}$ when $S = 1+I$.

>[!example] Warning
>[[Atiyah Ring Completions#^3d8ed9]] can fail when $A$ is not Noetherian. Take as an example $A$ to be the ring of all $C^{\infty}$ functors on $\mathbb{R}$ and let $I$ be the ideal of those $f$ which vanish at $0$ (note $I$ is maximal since $A/I\cong \mathbb{R}$). Then $I$ is generated by the identity function $x$, and $\bigcap_{n=0}^{\infty}I^n$ is the set of all $f \in A$, all of whose derivatives vanish at the origin. Indeed, all elements of $\bigcap_{n=0}^{\infty}I^n$ have all derivatives vanishing at the origin by the product rule. On the other hand, if $g:\mathbb{R}\to \mathbb{R}$ is a $C^{\infty}$ function which is zero and has all derivatives equal to zero at $0$. Then we can write $g$ as the product $g = x^n\frac{g}{x^n}$ for any $n \in \mathbb{N}$. where $g/x^n$ is defined piecewise to be $0$ at $0$ and equal to $g/x^n$ elsewhere. This defines a $C^{\infty}$ function since all derivatives of $g$ are zero (this can be shown by an inductive argument on $n$ using the definition of the derivative and l'Hopital's rule).
>
>On the other hand, $f$ is annihilated by some element $1+\alpha$, for $\alpha \in I$, if and only if $f$ vanishes identically in some neighborhood of $0$. However, the well known $C^{\infty}$ function given by $e^{-1/x^2}$ for $x > 0$ and $0$ for $x \leq 0$, is not identically zero in any neighborhood of $0$ but has vanishing derivatives at $0$. This shows that the kernels of 
>$$A\to \hat{A} \text{ and } A\to S^{-1}A$$
>for $S = 1+I$ do not coincide, so $A$ cannot be Noetherian.

Krull's theorem has a number of important corollaries, a few of which we collect here.

>[!corollary] 
>Let $A$ be a Noetherian domain with $I \neq (1)$ a proper ideal of $A$. Then $\bigcap_{n=0}^{\infty}I^n = (0)$.

`\begin{proof}`
Since $1+I$ contains no zero-divisors, as $A$ is a domain and $0 \notin 1+I$, the kernel of $A\to \hat{A}$ must be trivial by [[Atiyah Ring Completions#^3d8ed9]].
`\end{proof}`

>[!corollary]
>Let $A$ be a Noetherian ring, $I$ an ideal of $A$ contained in the Jacobson radical and let $M$ be a finitely generated $A$-module. Then the $I$-topology of $M$ is Hausdorff (i.e. $\bigcap_{n=0}^{\infty}I^nM = 0$).

^a7cd93

`\begin{proof}`
Since $I$ is contained in the Jacobson radical every element of $1+I$ is a unit (recall $x \in \mathfrak{R}$ if and only if $1-xy$ is a unit in $A$ for all $y \in A$, as otherwise $1$ would live in a maximal ideal, which is impossible). Then the result follows by [[Atiyah Ring Completions#^3d8ed9]].
`\end{proof}`

>[!corollary]
>Let $A$ be a Noetherian local ring with maximal ideal $\mathfrak{m}$, and let $M$ be a finitely-generated $A$-module. Then the $\mathfrak{m}$-topology of $M$ is Hausdorff.

`\begin{proof}`
Since $A$ is a local ring $\mathfrak{m}$ equals $A$'s Jacobson radical, and so we can apply [[Atiyah Ring Completions#^a7cd93]]. 
`\end{proof}`
**COMMENT ON P-PRIMARY IDEALS ONCE THAT SECTION IS WRITTEN**


### The Associated Graded Ring

We end these notes by investigating a special graded ring associated with a ring and an ideal.

>[!def] Associated Graded Ring
>Let $A$ be a ring with $I$ an ideal of $A$. The **associated graded ring** of $A$ is the graded ring
>$$G_I(A) := \bigoplus_{n=0}^{\infty}I^n/I^{n+1}$$
>where multiplication is defined as follows: for each $x_n \in I^n$, let $\overline{x}_n$ denote the image of $x_n$ in $I^n/I^{n+1}$; define $\overline{x}_m\overline{x}_n$ to be $\overline{x_mx_n}$, i.e. the image of $x_mx_n$ in $I^{m+n}/I^{m+n+1}$.

If $M$ is an $A$-module and $(M_n)_{n \geq 0}$ an $I$-filtration of $M$ (recall this means $IM_n \subseteq M_{n+1}$), then define 
$$G_I(M) := \bigoplus_{n=0}^{\infty}M_n/M_{n+1}$$
which is a graded $G_I(A)$-module.

>[!proposition]
>Let $A$ be a Noetherian ring and $I$ an ideal of $A$. Then
>1. $G_I(A)$ is Noetherian
>2. $G_I(A)$ and $G_{\hat{I}}(\hat{A})$ are isomorphic as graded rings
>3. if $M$ is a finitely-generated $A$-module and $(M_n)_{n\geq 0}$ is a stable $I$-filtration of $M$ (i.e. $IM_n \subseteq M_{n+1}$ and there exists $n_0$ such that $n \geq n_0$ implies $IM_n = M_{n+1}$), then $G_I(M)$ is a finitely-generated graded $G_I(A)$-module.

^e7fee4

`\begin{proof}`
First for $(1)$ since $A$ is Noetherian $I$ is finitely generated by say $x_1,...,x_s$. Let $\overline{x}_i$ be the image of $x_i$ in $I/I^2$. Then $G_I(A) = (A/I)[\overline{x}_1,...,\overline{x}_s]$ is a finitely generated $A/I$ algebra, where $A/I$ is Noetherian being the quotient of a Noetherian ring, so $G_I(A)$ is Noetherian by the Hilbert basis theorem.

Next, by [[Atiyah Ring Completions#^515897]] property $(3)$ we have that $I^n/I^{n+1}\cong \hat{I}^n/\hat{I}^{n+1}$ for all $n$, so we obtain the desired isomorphism of associated graded rings.

Finally let $M$ be a finitely generated $A$-module with $(M_n)_{n\geq 0}$ a stable $I$-filtration of $M$. Let $x_1,...,x_s$ be generators of $M$ over $A$. and let $\overline{x}_i$ denote the image of $x_i$ in $M_1/M_2$. Since the filtration is stable there exists $n_0$ such that $M_{n_0+r} = I^rM_{n_0}$ for all $r \geq 0$, and hence $G_I(M)$ is generated by $\bigoplus_{n\leq n_0}M_n/M_{n+1}$. Since each $M_n/M_{n+1}$ is Noetherian, being the quotient of a Noetherian module (by induction), and being annihilated by $I$, it is a finitely generated $A/I$-module. Thus, $\bigoplus_{n\leq n_0}M_n/M_{n+1}$ is generated by a finite number of elements as an $A/I$-module, so $G_I(M)$ is finitely generated as a $G_I(A)$-module.
`\end{proof}`

We can connect the completion of a filtered group to its associated graded group as in the following lemma.

>[!lemma]
>Let $\phi:A\to B$ be a homomorphism of filtered groups (i.e. $\phi(A_n) \subseteq B_n$ for all $n\geq 0$), and let $G_I(\phi):G_I(A)\to G_I(B)$ and $\hat{\phi}:\hat{A}\to \hat{B}$ be the induced homomorphisms of the graded and completed groups. Then we have that if $G_I(\phi)$ is injective (resp. surjective), then $\hat{\phi}$ is injective (resp. surjective).

^141e7d

`\begin{proof}`
Consider the diagram of exact sequences
$$\begin{CD}0 @>>> A_n/A_{n+1} @>>> A/A_{n+1} @>>> A/A_n @>>> 0 \\ @. @VVG_n(\phi)V @VV\alpha_{n+1}V @VV\alpha_nV @. \\ 0 @>>> B_n/B_{n+1} @>>> B/B_{n+1} @>>> B/B_n @>>> 0  \end{CD}$$
By the snake lemma we have an exact sequence of kernels and cokernels. If $G_I(\phi)$ is injective (resp. surjective) then using the 4-Lemma and induction on $n$ we have that $\ker \alpha_n = 0$ (resp. $\text{coker}\,\alpha_n = 0$). Moreover, in the surjectivity case $\ker\alpha_{n+1}\to \ker\alpha_n$ is surjective for all $n$. Using [[Atiyah Ring Completions#^22285c]] and the fact that $\hat{\phi}$ is given by taking the inverse limit over the $\alpha_n$ we obtain the desired result. **NEED TO DOUBLE CHECK**
`\end{proof}`

Our final goal for this section is to show that $\hat{A}$ is Noetherian. This requires some preliminary results.

>[!proposition]
>Let $A$ be a ring, $I$ an ideal of $A$, $M$ an $A$-module, and $(M_n)_{n\geq 0}$ an $I$-filtration of $M$. Suppose $A$ is complete in the $I$-topology and that $M$ is Hausdorff in its filtration topology. Suppose also that $G_I(M)$ is a finitely-generated $G_I(A)$-module. Then $M$ is a finitely-generated $A$-module.

^3631ee

`\begin{proof}`
Let $\overline{x}_1,...,\overline{x}_s$ be a finite set of generators of $G_I(M)$ such that they are all homogeneous, and $x_i$ is of degree $n(i)$, and so is the image of some $x_i \in M_{n(i)}$. Let $F^i$ be the $A$-module with stable $I$-filtration given by $F^i_k = I^{k+n(i)}$ and put $F = \bigoplus_{i=1}^rF^i$. Then the mapping that sends the generator of $F^i$ to $x_i$ defines a homomorphism $$\phi:F\to M$$
of filtered groups, and $G_I(\phi):G_I(F)\to G_I(M)$ is a homomorphism of $G_I(A)$-modules which by construction is surjective. By [[Atiyah Ring Completions#^141e7d]] $\hat{\phi}$ is surjective. Note that since $F$ is free, $I$-completion is exact, and $A \cong \hat{A}$, it follows that $F\cong \hat{F}$. Further, since $M$ is Hausdorff $M\to \hat{M}$ is injective. Since $\hat{\phi}$ is surjective it follows that $\phi$ must be surjective, and so $x_1,...,x_s$ generate $M$ as an $A$-module.
`\end{proof}`

>[!corollary]
>Let $A$ be a ring, $I$ an ideal of $A$, $M$ an $A$-module, and $(M_n)_{n\geq 0}$ an $I$-filtration of $M$. Suppose $A$ is complete in the $I$-topology and that $M$ is Hausdorff in its filtration topology. Suppose also that $G_I(M)$ is a finitely-generated $G_I(A)$-module. If $G_I(M)$ is a Noetherian $G_I(A)$-module, then $M$ is a Noetherian $A$-module.

^adb9ac

`\begin{proof}`
It suffices to show every submodule of $M$ is finitely generated. Let $M'$ be a submodule of $M$. Then $M_n' = M'\cap M_n$ gives an $I$-filtration of $M'$, and the embedding $M'_n\to M_n$ gives rise to an embedding of the associated graded $G_I(A)$-module $G_I(M')$ in $G_I(M)$. Since $G_I(M)$ is Noetherian it follows that $G_I(M')$ is finitely generated, so by [[Atiyah Ring Completions#^3631ee]] we have that $M'$ is a finitely generated $A$-module, as desired.
`\end{proof}`

>[!theorem] Noetherian Completion
>If $A$ is a Noetherian ring and $I$ is an ideal of $A$, then the $I$-completion $\hat{A}$ of $A$ is Noetherian.

^360133

`\begin{proof}`
By [[Atiyah Ring Completions#^e7fee4]] bullet $(2)$ we have that $G_I(A)\cong G_{\hat{I}}(\hat{A})$, and so $G_{\hat{I}}(\hat{A})$ is Noetherian. Applying [[Atiyah Ring Completions#^adb9ac]] to the complete ring $\hat{A}$ and taking $M = \hat{A}$ filtered by $\hat{I}^n$, and so being Hausdorff, then implies that $\hat{A}$ is Noetherian.
`\end{proof}`

>[!corollary]
>If $A$ is a Noetherian ring, then the power series ring $B = A[[x_1,...,x_n]]$ in $n$ variables is Noetherian. In particular, $k[[x_1,...,x_n]]$ for $k$ a filed is Noetherian.

`\begin{proof}`
Recall that $A[x_1,...,x_n]$ is Noetherian by Hilbert's basis theorem. Then since $B$ is its completion for the $(x_1,...,x_n)$-adic topology the result follows by [[Atiyah Ring Completions#^360133]].
`\end{proof}`



#### References

[^1]:  Introduction to Commutative Algebra | Mathematical Association of America. (n.d.). https://maa.org/press/maa-reviews/introduction-to-commutative-algebra. Accessed 20 May 2024