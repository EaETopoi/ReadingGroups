---
date: 2024-06-25T11:47:00
tags:
  - CategoryTheory
  - InfinityCategories
  - Homotopy
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

In these notes we describe the connection between categories and simplicial sets through the nerve construction, following the work in  [Kerodon](https://kerodon.net/)[^1].

As seen in [[Topological Spaces to Simplicial Sets]] topological spaces simplicially are Kan complexes. In this note we will realize categories in our simplicial context as simplicial sets satisfying another kind of lifting condition. We will also briefly discuss the notion of the homotopy category of a simplicial set, which will correspond to a left adjoint of our nerve construction, following a similar pattern to the geometric realization-singular simplices adjunction.

## Nerve of a Category

We have a natural fully faithful functor $h:\mathbb{\Delta}\to \mathsf{Cat}$ which sends the linearly ordered set $[n]$ to its associated category. Given a non-decreasing map $f:[m]\to [n]$, the functor $h(f)$ is given by acting on the objects as $f$, which induces a functor since $f$ is non-decreasing. Since $\mathsf{Cat}$ is cocomplete and $\mathbb{\Delta}$ is small we can use [[Kan Extensions#^79496e]] to realize the left Kan extension of $h$ along the yoneda embedding, which is given by
$$hX = \int^{n:\mathbb{\Delta}}\mathsf{sSet}(y^n,X)\cdot h([n])\cong \int^{n:\mathbb{\Delta}}h([n])\cdot X_n$$
We can realize the category $hX$ also as the coequalizer
$$hX\cong \text{coeq}\left(\coprod_{n\to m:\mathbb{\Delta},\sigma \in X_m}h([n])\rightrightarrows \coprod_{n:\mathbb{\Delta},\sigma\in X_n}h([n]) \right)$$
so an object in $hX$ is a $0$-simplex $x \in X_0$, while a morphism from $x$ to $y$ is a $1$-simplex $\sigma \in X_1$ such that $d_1^1\sigma = x$ and $d_0^1\sigma = y$. Composition is a bit more delicate.

As usual the right adjoint to the homotopy functor $h$ is simpler to describe, being given by $N_n(\mathcal{C}) = \mathsf{Cat}(h(\mathbb{\Delta}^n),\mathcal{C})$, which is a chain of $n$-composable arrows in $\mathcal{C}$. The face map $\delta_n^i:[n-1]\to [n]$ sends a chain $x_0\to x_1\to\cdots \to x_n$ (i.e. a functor $h([n])\to \mathcal{C}$) to the chain given by composing $x_{i-1}\to x_i\to x_{i+1}$ if $0 < i < n$, and removing the ends if $i = 0,n$. The degeneracy map $\eta_n^i:[n+1]\to [n]$ sends a chain $x_0\to x_1\to \cdots \to x_n$ to the chain given by inserting an identity for $x_i$. 

From this description it is very easy to **detect degenerate simplices** in $N_\bullet(\mathcal{C})$. Namely, a degenerate simplex is exactly a chain of morphisms, where at least one of the morphisms in the chain is an identity.

We refer to $N_\bullet(\mathcal{C})$ as the **nerve** of the category $\mathcal{C}$. If we compose with the geometric realization functor, we say that $|N_\bullet(\mathcal{C})|$ is the **classifying space** of the category $\mathcal{C}$. Note that $N_\bullet$ is a fully faithful functor, with maps of nerves being uniquely determined by the data on the level $0$-simplices and $1$-simplices.

Note that the restriction map
$$\mathsf{sSet}(\Delta^n,N_\bullet(\mathcal{C}))\to \mathsf{sSet}(\partial\Delta^n,N_\bullet(\mathcal{C}))$$
is an injection for $n = 2$, since the composite of two maps is unique, and a bijection for $n > 2$, since if the faces of a diagram of maps commutes, the whole diagram commutes.

### Monoid of a category

Note that a monoid is identical in axiomatization to a 1-object category. Namely, this equivalence corresponds to an equivalence of categories between the category of monoids, $\mathsf{Mon}$, and the full subcategory of $\mathsf{Cat}$ consisting of one-object categories. We will write $BM$ for the category associated to a monoid. (i.e. $\text{Ob}(BM) = \{*\}$, and $BM(*,*) = M$).

Let $B_\bullet M := N_\bullet(BM)$ be the nerve associated with the category for the monoid $M$. We call $B_\bullet M$ the **classifying simplicial set of the monoid $M$**. Note that an $n$-simplex of $B_\bullet M$ is exactly an $n$-tuple of elements of $M$, so really we have an isomorphism
$$B_\bullet M \cong M^\bullet$$
where $M^\bullet$ is the simplicial set with set of $n$-simplices $M^n$, with face and degeneracy operators given by composition and inserting identities, respectively. We have the following abstract characterization of these types of simplicial sets.

>[!proposition] Simplicial Description of Monoids
>The functor $B_\bullet:\mathsf{Mon}\to \mathsf{sSet}$ is a fully faithful embedding with essential image those simplicial sets $S_\bullet$ such that for each $n \geq 0$ the following condition holds:
>- For $1 \leq i \leq n$, let $\rho_i:S_n\to S_1$ be the map associated to the inclusion $[1]\cong \{i-1,i\}\hookrightarrow [n]$. Then the maps $\{\rho_i\}_{1\leq i \leq n}$ determine a bijection $S_n\to \prod_{1\leq i\leq n}S_1$

^344163

Note that this condition is very similar to that of 1-Segality in [[2-Segal Sets]]. Indeed, as was repeatedly mentioned in those notes, monoids serve as an excellent example of one Segal sets. [[Categories and Simplicial Sets#^344163]] says that 1-Segal sets $S_\bullet$ with $S_0 = \{*\}$ are exactly those equivalent to simplicial sets induced by monoids.

Before proving this result we recall some interesting points. First, recall that we have a natural inclusion $\mathsf{Mon}\hookrightarrow \mathsf{SemiGrp}$ of monoids into semigroups which has left adjoint $(-)^+:\mathsf{SemiGrp}\to \mathsf{Mon}$ that formally appends an identity.

**Proof of [[Categories and Simplicial Sets#^344163]] needed**


### Characterizing Nerves

In this subsection we characterize what simplicial sets are in the essential image of the nerve functor. This work will be important for our later generalization to quasi-categories and their connection to normal categories.

>[!proposition] Essential Image of Nerve Functor
>The essential image of the nerve $N_\bullet$ consists of simplicial sets $S_\bullet$ satisfying the following condition:
>- Every inner horn map $\sigma_0:\Lambda_i^n\to S_\bullet$ (i.e. $0 < i < n$) extends uniquely to an $n$-simplex $\sigma:\Delta^n\to S_\bullet$.

^50e2ab

We will prove [[Categories and Simplicial Sets#^50e2ab]] through a series of lemmas. First let us show that the image of any category satisfies the inner horn condition.

>[!lemma] Image of Nerve
>Every inner horn $\sigma_0:\Lambda_i^n\to N_\bullet(\mathcal{C})$, for $\mathcal{C}$ a category, extends uniquely to an $n$-simplex $\sigma:\Delta^n\to N_\bullet(\mathcal{C})$.

^1e6087

`\begin{proof}`
Let $\sigma_0:\Lambda_i^n\to N_\bullet(\mathcal{C})$ be an inner horn in the nerve of $\mathcal{C}$. For $0 \leq j \leq n$ let $C_j := \sigma_0([0]\xrightarrow{j}[n])$. Splitting into cases first suppose $n \geq 3$. Then $\Lambda_i^n$ and $\Delta^n$ have the same set of $1$-simplices. For $0 \leq j\leq k \leq n$, let $f_{k,j}:C_j\to C_k$ denote the $1$-simplex of $N_\bullet(\mathcal{C})$ given by $\sigma_0([1]\xrightarrow{j\leq k}[n])$. Note that $f_{j,j} = \sigma_0([1]\xrightarrow{j=j} [n]) = \sigma_0([1]\to [0]\xrightarrow{j}[n]) = s_0^0(C_j) = 1_{C_j}$ so it remains to show that the 1-cocycle condition $f_{\ell,k}\circ f_{k,j}=f_{\ell,j}$ holds.

Note that the triple $j\leq k\leq \ell$ determines a $2$-simplex of $\Delta^n$. If this $2$-simplex is in $\Lambda_i^n$, then this 2-simplex witnesses $f_{\ell,k}\circ f_{k,j} = f_{\ell,j}$. If $n > 3$ then we're done, so we need only consider the case that $n = 3$ and $\{j,k,\ell\} = [n]\backslash\{i\}$. Since $n = 3$ we also have $i = 1,2$. Let $\tau$ be the 2-simplex corresponding to $\{j,k,\ell\}$. Note that $\Lambda_i^3$ has all other nondegenerate $2$-simplices of $\Delta^3$ other than $\tau$. Applying $\sigma_0$ we either have
$$f_{3,0} = f_{3,1}\circ f_{1,0}\,\,\,f_{3,1} = f_{3,2}\circ f_{2,1}\,\,\, f_{2,0} = f_{2,1}\circ f_{1,0}$$
if $i = 1$ and 
$$f_{3,0} = f_{3,2}\circ f_{2,0}\,\,\,f_{3,1} = f_{3,2}\circ f_{2,1}\,\,\, f_{2,0} = f_{2,1}\circ f_{1,0}$$
if $i = 2$. Then we can compute
$$f_{3,0} = f_{3,1}\circ f_{1,0} = f_{3,2}\circ f_{2,1}\circ f_{1,0} = f_{3,2}\circ f_{2,0}$$
if $i = 1$ and 
$$f_{3,0} = f_{3,2}\circ f_{2,0} = f_{3,2} \circ f_{2,1}\circ f_{1,0} = f_{3,1}\circ f_{1,0}$$
if $i = 2$, as desired.

It remains to consider the case of $n = 2$ and $i = 1$. The morphism $\sigma_0:\Lambda_1^2\to N_\bullet(\mathcal{C})$ can be identified with the composable morphisms $f_{1,0}:C_0\to C_1$ and $f_{2,1}:C_1\to C_2$ in $\mathcal{C}$. In this case no composition condition needs to be satisfied, so we get a unique extension to a $2$-simplex $\sigma$ such that $d_1^2(\sigma) = f_{2,1}\circ f_{1,0}$.
`\end{proof}`

>[!lem] Isos of Simplicial Sets with Inner Horn Fillings
>If $f:S_\bullet\to T_\bullet$ is a map of simplicial sets satisfying the unique inner horn filling condition such that $f_0$ and $f_1$ are bijections, then $f$ is an isomorphism.

^e741c1

`\begin{proof}`
To prove the claim by showing that $f$ induces a bijection on representable functors $y^{S_\bullet}$ and $y^{T_\bullet}$, leveraging the yoneda embedding. Since these functors preserve colimits, and we can write any simplicial set as a colimit over its skeleta, it suffices to show that the components $\mathsf{sSet}(K_\bullet,S_\bullet)\to \mathsf{sSet}(K_\bullet,T_\bullet)$ where $K_\bullet$ has dimension $\leq n$ is a bijection. Hence, we can proceed by induction on $n$. If $n = -1$ $K_\bullet$ is the empty simplicial set and the claim is true always.

Otherwise, suppose $n \geq 0$, and we can write $K_\bullet$ as a pushout of $\text{sk}_{n-1}(K_\bullet)$. By the inductive hypothesis when we plug in $\text{sk}_{n-1}(K_\bullet)$ or $\coprod\partial\Delta^n$ we obtain a bijection, so it remains to show that $\coprod\Delta^n$, and hence $\mathsf{sSet}(\Delta^n,S_\bullet)\to \mathsf{sSet}(\Delta^n,T_\bullet)$ is a bijection. If $n \leq 1$ this is by assumption. Otherwise, suppose $n \geq 2$. Then we have a commutative square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BsSet%7D(%5Cmathbf%7B%5CDelta%7D%5En%2CS_%5Cbullet)%7D%20%26%26%20%7B%5Cmathsf%7BsSet%7D(%5CLambda_1%5En%2CS_%5Cbullet)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathsf%7BsSet%7D(%5Cmathbf%7B%5CDelta%7D%5En%2CT_%5Cbullet)%7D%20%26%26%20%7B%5Cmathsf%7BsSet%7D(%5CLambda_1%5En%2CT_%5Cbullet)%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{sSet}(\mathbf{\Delta}^n,S_\bullet)} &amp;&amp; {\mathsf{sSet}(\Lambda_1^n,S_\bullet)} \\
	\\
	{\mathsf{sSet}(\mathbf{\Delta}^n,T_\bullet)} &amp;&amp; {\mathsf{sSet}(\Lambda_1^n,T_\bullet)}
	\arrow[from=1-1, to=1-3]
	\arrow[from=1-1, to=3-1]
	\arrow[from=1-3, to=3-3]
	\arrow[from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where the right vertical map is a bijection by the inductive hypothesis. However, the horizontal maps are bijective by the filling assumption, so the left hand map must be bijective.
`\end{proof}`

We now proceed to the proof of [[Categories and Simplicial Sets#^50e2ab]].

`\begin{proof}[Proof of Essential Image of Nerve.]`
It remains to show that if $S_\bullet$ is a simplicial set with unique horn fillings that it is isomorphic to the nerve of some category. Equivalently, we must show that the unit $S_\bullet\to N_\bullet(h(S_\bullet))$ is an isomorphism. Note that the co-unit $h(N_\bullet(\mathcal{C}))\to \mathcal{C}$ is an isomorphism since the right adjoint, $N_\bullet$, is fully-faithful.

Now, recall that $h(S_\bullet)$ has as objects the $0$-simplices of $S_\bullet$, so the unit is the identity on $0$-simplices. Further, the morphisms in $h(S_\bullet)$ are generated by the $1$-simplices in $S_\bullet$ under composition such that composites agree with $2$-simplices in $S_\bullet$ and identities are of the form $s_0^0(x)$ for $x$ a $0$-simplex in $S_\bullet$. Note that a pair of composable $1$-simplices in $S_\bullet$ is exactly an inner horn $\Lambda_1^2\to S_\bullet$, and hence has a unique composite $\Delta^2\to S_\bullet$. This shows that the morphisms $x\to y$ in $h(S_\bullet)$ are exactly the $1$-cells $\sigma$ with $d_0^1\sigma = y$ and $d_1^1\sigma = x$. 

Therefore, the unit is also the identity on the level of $1$-simplices, so [[Categories and Simplicial Sets#^e741c1]] together with [[Categories and Simplicial Sets#^1e6087]] imply that the unit is an isomorphism for $S_\bullet$, so $S_\bullet$ is in the essential image of the nerve.
`\end{proof}`


Since categories can be recovered from nerves using the counit of the homotopy category-nerve adjunction, we can begin formulating categorical properties in terms of the simplicial set $N_\bullet(\mathcal{C})$.

For example, a category $\mathcal{C}$ being a groupoid is the same as its nerve being a Kan complex, since filling outer horns corresponds to adding inverses of morphisms.

>[!example] Classifying Space for a Group
>If $G$ is a group its category $BG$ is a groupoid, so $B_\bullet G$ is a Kan complex. The geometric realization, $|B_\bullet G|$, is called the **classifying space** of $G$ and can be characterized as a CW complex with either of the following properties:
>1. $|B_\bullet G|$ is connected and $\pi_n(|B_\bullet G|) \cong G$ if $n = 1$ and $0$ if $n > 1$.
>2. For any paracompact topological space $X$, there is a bijection between homotopy classes of maps $f:X\to |B_\bullet G|$ and isomorphism classes of $G$-torsors $P\to X$.

For a category $\mathcal{C}$, we will write $\mathcal{C}^{\cong}$ for the wide subcategory of $\mathcal{C}$ consisting only of isomorphisms. We call $\mathcal{C}^{\cong}$ the **core** of $\mathcal{C}$. $\mathcal{C}^{\cong}$ is the largest groupoid which is a subcategory of $\mathcal{C}$.

Although in general the homotopy category is difficult to describe, as we now show there admits a simple description in the case of singular complexes for spaces, and later quasi-categories more generally.

>[!claim] Homotopy Category of Singular Simplices
>Let $X$ be a topological space and let $\pi_{\leq 1}(X)$ be its fundamental groupoid. Then $h(\text{Sing}_\bullet(X))\cong \pi_{\leq 1}(X)$.

`\begin{proof}`
It suffices to witness a map $u:\text{Sing}_\bullet(X)\to N_\bullet(\pi_{\leq 1}(X))$ which is initial in the slice category $\text{Sing}_\bullet(X)/N_\bullet$. 

We define $u_0(x) = x$ for each point $|\Delta^0|\to X$, and $u_1(p) = [p]$ for each path $p:|\Delta^1|\to X$. Now, consider an $n$-simplex $\sigma:|\Delta^n|\to X$ in $X$. Then $u_n(\sigma) = ([p_1],...,[p_n])$ for some tuple of homotopy classes of composable paths. The inclusion $[1]\cong \{i,i+1\}\hookrightarrow [n]$ for $0\leq i < n$ on the right outputs $[p_i]$ while on the left, assuming $u_n$ is a map of simplicial sets, gives $u_1(\sigma\circ \iota_i)$, so $u$ is fully determined by $u_0$ and $u_1$. Further, this does indeed define a map of simplicial sets. Now, suppose we have another map of simplicial sets $v:\text{Sing}_\bullet(X)\to N_\bullet(\mathcal{C})$. Then we can define $F:\pi_{\leq 1}(X)\to \mathcal{C}$ by $F(x) = v_0(x)$ and $F([p]) = v_1(p)$. Note that a homotopy of paths can be realized as a 2-simplex with one edge an identity, so as $v$ is a morphism of simplicial sets $F$ is well-defined, and further $F$ is functorial. A similar argument to that for constructing $u$ shows that $v$ factors through $u$ via $N_\bullet(F)$, and since the maps are determined by their action on $0$ and $1$-simplices, this factorization is unique.
`\end{proof}`

Another simple type of homotopy category is given for those simplicial sets $G_\bullet$ of dimension $\leq 1$ (i.e. those arising, at least up to isomorphism, from directed graphs). In this case $h(G_\bullet)\cong \text{Path}[G]$, the **path category** for $G$.



#### References

[^1]: Lurie, J. (n.d.). Kerodon. https://kerodon.net/. Accessed 16 May 2024