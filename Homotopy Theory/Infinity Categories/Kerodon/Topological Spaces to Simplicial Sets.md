---
date: 2024-06-24T11:38:00
tags:
  - InfinityCategories
  - CategoryTheory
  - Homotopy
  - HigherCategories
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

In this section we link simplicial sets with topological spaces and begin to understand how simplicial sets provide a combinatorial model for topological spaces, following the work in [Kerodon](https://kerodon.net/)[^1].

Recall that for any topological space $X$ we have its associated simplicial set $\text{Sing}_\bullet(X)$ of singular $n$-simplices, which are continuous maps from the space
$$|\Delta^n|=\left\{(t_0,\dots,t_n) \in [0,1]^{n+1}\mid \sum_{i=0}^nt_i=1\right\}$$
into $X$. On the other hand, if we are given a simplicial set $S_\bullet$, we can consider it as the combinatorial data needed to construct a topological space $|S_\bullet|$, namely its **geometric realization**
$$|S_\bullet| = \int^{n:\mathbb{\Delta}}|\Delta^n| \cdot S_n$$
which is a special case for the co-end formula for Kan extensions in [[Kan Extensions#^79496e]], as geometric realization $|-|$ is the left Kan extension of the restricted geometric realization $|-|:\mathbb{\Delta}\to \mathsf{Top}$ described above along the yoneda embedding $y:\mathbb{\Delta}\to \mathsf{sSet}$.

Since $\mathbb{\Delta}$ is a small category, and $\mathsf{Top}$ is complete and cocomplete this geometric realization functor, which is defined in terms of colimits, exists and has a right adjoint $R:\mathsf{Top}\to \mathsf{sSet}$ given by
$$(R X)_n \cong \mathsf{sSet}(\Delta^n,R X) \cong \mathsf{Top}(L\Delta^n,X) = \mathsf{Top}(|\Delta^n|,X) = \text{Sing}_n(X)$$
so $R = \text{Sing}_\bullet$.

Given certain assumptions on the space $X$ we will see that the co-unit of the adjunction $|\text{Sing}_\bullet(X)|\to X$ will be a weak homotopy equivalence (so a homotopy equivalence when $X$ has the homotopy type of a CW complex).

## Connected Components of Simplicial Sets

^427e97

Continuing with our connection between simplicial sets and spaces, in this section we show that simplicial sets can be decomposed as disjoint unions of connected components, and define a $\pi_0$ functor on simplicial sets.

Note that the statement that a simplicial set $S_\bullet$ decomposes as a disjoint union $S_\bullet'\amalg S_\bullet''$ is equivalent to the requirement that we have a sub-simplicial set $S_\bullet'\subseteq S_\bullet$ for which the assignment $[n]\mapsto S_n\backslash S_n'$ with induced restriction maps is functorial (i.e. the $S_n\backslash S_n'$ are preserved by face and degeneracy maps).

Using this characterization we can see that summands, such as $S_\bullet'$, are closed under unions and intersections, and further summands are transitive in the sense that a summand of $S_\bullet'$ will also be a summand of $S_\bullet$. 

Note that summands are also preserved under base change. Indeed, if we have a map of simplicial sets $f:S_\bullet\to T_\bullet$ as well as a decomposition $T_\bullet = T_\bullet'\amalg T_\bullet''$, then for $f^{-1}(T_\bullet') = S_\bullet\times_{T_\bullet}T_\bullet'$ and $f^{-1}(T_\bullet'') = S_\bullet\times_{T_\bullet}T_\bullet''$ we have that $S_\bullet = f^{-1}(T_\bullet')\amalg f^{-1}(T_\bullet'')$, which can be thought as resulting from deMorgan's laws and the fact limits are computed term-wise.

We can now define what it means for a simplicial set to be connected.

>[!def] Connected Simplicial Set
>A simplicial set $S_\bullet$ is said to be **connected** if it is non-empty (i.e. not the initial simplicial set) and it has no non-trivial summands.

For example, as one would hope based on its geometry, the standard $n$-simplex $\Delta^n = \mathbb{\Delta}(-,[n])$ is connected. Indeed, if $\Delta^n = S_\bullet'\amalg S_\bullet''$, then either $S_\bullet'$ or $S_\bullet''$ contain $1_{[n]}:[n]\to [n]$. Without loss of generality suppose it is $S_\bullet'$. Then for  any $f:[k]\to [n]$ we have that $S_\bullet'(f)(1_{[n]}) = f$, so $f \in S_\bullet'$. Thus, $S_\bullet' = \Delta^n$, and so $S_\bullet'' = \emptyset$.

>[!def] Connected Components of a Simplicial Set
>Let $S_\bullet$ be a simplicial set. A simplicial subset $S_\bullet'\subseteq S_\bullet$ is a **connected component** of $S_\bullet$ if it is a summand and is connected. Let $\pi_0(S_\bullet)$ denote the set of all connected components of $S_\bullet$.

We will soon come across a number of important descriptions of the set $\pi_0(S_\bullet)$. Due to this, we may view $I = \pi_0(S_\bullet)$ as simply an index set with a bijection to the set of connected components of $S_\bullet$.

For example, $\pi_0:\mathsf{sSet}\to \mathsf{Set}$ can be realized as the left Kan extension of the constant functor $Q:\mathbb{\Delta}\to \mathsf{Set}$ with value $\{*\}$ along the Yoneda embedding. Namely, it is a special type of geometric realization

$$\pi_0(S_\bullet) = \int^{n:\mathbb{\Delta}}\pi_0(\Delta^n) \cdot S_n = \int^{n:\mathbb{\Delta}}S_n$$

**TBC**


## Singular Simplicial Set and Geometric Realization

In general if $\mathcal{C}$ is a small category and $\mathcal{E}$ is a cocomplete category, any functor $F:\mathcal{C}\to \mathcal{E}$ has a left Kan extension along the yoneda embedding $y:\mathcal{C}\to \mathsf{Set}^{\mathcal{C}^{op}}$, which is a pointwise left Kan extension given by
$$LX \cong \int^{c:\mathcal{C}}\mathsf{Set}^{\mathcal{C}^{op}}(y^c,X)\cdot Fc \cong \int^{c:\mathcal{C}}Xc \cdot Fc$$
Note that on a representable presheaf $L$ must be given by
$$Ly^d = \int^{c:\mathcal{C}}\mathcal{C}(c,d)\cdot Fc\cong Fd$$
using the density theorem/co-Yoneda lemma. Since $L$ is given in terms of a co-end, and hence a colimit, it commutes with all colimits. Thus by the special adjoint functor theorem, assuming $\mathcal{E}$ is locally small, we have a right adjoint $R$. Further, such a right adjoint must take the form
$$(RX)_c\cong \mathsf{Set}^{\mathcal{C}^{op}}(y^c,RX) \cong \mathcal{E}(Ly^c,X)\cong \mathcal{E}(Fc,X)$$
which is the generalization of the geometric realization-singular simplices adjunction.

Now, let us return to the special case of geometric realization and singular simplices. First, we must define some notation.

>[!def] Subset of Standard Simplex
>Let $n \geq 0$ be an integer and let $\mathcal{U}$ be a collection of nonempty subsets of $[n]$. We say $\mathcal{U}$ is **downward closed** if for all $J \in \mathcal{U}$ and all $I \subseteq J$, with $I \neq \emptyset$, $I \in \mathcal{U}$. In this case write $\Delta^n_\mathcal{U}$ be the simplicial subset of $\Delta^n$ consisting of $m$-simplices, $\alpha:[m]\to [n]$, for which $\text{im}(\alpha) \in \mathcal{U}$.

Note that we can realize $\Delta^n_\mathcal{U}$ as the union of the sub-simplices index $\Delta^I$ for $I \in \mathcal{U}$. Explicitly,
$$\Delta^n_\mathcal{U} = \text{coeq}\left(\coprod_{I,J \in \mathcal{U}}\Delta^{I\cap J} \rightrightarrows \coprod_{I \in \mathcal{U}}\Delta^{I}\right)$$
where for each $I \in \mathcal{U}$, the top-arrow is given by post-composition along the inclusion $I\cap J\hookrightarrow I$, while the bottom arrow is given by post-composition along the inclusion $J\cap I\hookrightarrow I$. Taking geometric realizations, and using the fact that geometric realization commutes with colimits we have 
$$|\Delta^n_\mathcal{U}| = \text{coeq}\left(\coprod_{I,J \in \mathcal{U}}|\Delta^{I\cap J}| \rightrightarrows \coprod_{I \in \mathcal{U}}|\Delta^{I}|\right)$$
As a subset of $\Delta^n$ we can realize this coequalizer as follows
$$|\Delta^n_\mathcal{U}| = \{(t_0,\dots,t_n)\in |\Delta^n|\,:\,\{i \in [n]\,:\,t_i\neq 0\}\in \mathcal{U}\}$$
Note that the boundary $\partial\Delta^n$ is a special case of this construction, where $\mathcal{U}$ in this case is all non-empty proper subsets of $[n]$. This is actually true of all subsimplicial sets of $\Delta^n$.

>[!claim]
>All subsimplicial sets of $\Delta^n$ are of the form $\Delta^n_\mathcal{U}$ for some uniquely determined $\mathcal{U}$.

`\begin{proof}`
Let $S_\bullet \subseteq \Delta^n$ be a simplicial subset. Let $\mathcal{U} = \{\text{im}(f)\,:\,f \in S_\bullet\}$. Then $\mathcal{U}$ is downward closed since for any $\text{im}(f) \subseteq [n]$, where $f:[m]\to [n]$, and any subset $I \subseteq \text{im}(f)$, we have a unique non-decreasing bijection $g:[|f^{-1}(I)|]\to [m]$ with image $f^{-1}(I)$, so $f\circ g$ has image $I$, and is in $S_\bullet$.

By construction it follows that $S_\bullet \subseteq \Delta^n_\mathcal{U}$. On the other hand, suppose $g:[m]\to [n]$ is in $\Delta^n_\mathcal{U}$. Then there exists some $f:[k]\to [n]$ in $S_\bullet$ such that $\text{im}(g) = \text{im}(f) = \{i_1<\dots<i_r\}$. Choose $j_1,...,j_r \in [k]$ such that $j_1 < \cdots < j_r$ and $f(j_\ell) = i_\ell$ for each $1 \leq \ell \leq r$. Then define $h:[m]\to [k]$ by setting $h(g^{-1}(\{i_\ell\})) = \{j_\ell\}$ for each $1 \leq \ell \leq r$, which is a non-decreasing map since $g$ is. It follows that $f\circ h = g$, and so $g \in S_\bullet$. Thus $S_\bullet = \Delta^n_\mathcal{U}$.
`\end{proof}`

Note that since we can construct a simplicial set through a sequence of pushout diagrams of the form

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ccoprod_%7B%5Csigma%20%5Cin%20S_n%5E%7Bnondeg%7D%7D%5Cpartial%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7Bsk%7D_%7Bn-1%7D(S_%5Cbullet)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Ccoprod_%7B%5Csigma%20%5Cin%20S_n%5E%7Bnondeg%7D%7D%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7Bsk%7D_n(S_%5Cbullet)%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D180%7D%2C%20draw%3Dnone%2C%20from%3D3-3%2C%20to%3D1-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\coprod_{\sigma \in S_n^{nondeg}}\partial\Delta^n} &amp;&amp; {\text{sk}_{n-1}(S_\bullet)} \\
	\\
	{\coprod_{\sigma \in S_n^{nondeg}}\Delta^n} &amp;&amp; {\text{sk}_n(S_\bullet)}
	\arrow[from=1-1, to=1-3]
	\arrow[from=1-1, to=3-1]
	\arrow[from=1-3, to=3-3]
	\arrow[from=3-1, to=3-3]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=180}, draw=none, from=3-3, to=1-1]
\end{tikzcd}
" /></p>

and since geometric realization preserves colimits, these pushouts give $|S_\bullet|$ the structure of a CW complex, with one cell of dimension $n$ for each non-degenerate $n$-simplex of $S_\bullet$. 

We now move on to an important lemma for the whole of quasi-category theory.

>[!lem] Generating Simplicial Sets
>Let $\mathcal{W}$ be a full subcategory of $\mathsf{sSet}$ such that $\mathcal{W}$ satisfies the following properties:
>1. If $f:X\to Y$ is a monomorphism in $\mathcal{W}$, and $g:X\to X'$ is any other morphism of simplicial sets in $\mathcal{W}$, then the pushout of $g$ along $f$ is in $\mathcal{W}$ (and since $\mathcal{W}$ is full, it is immediate that the pushout of $f$ along $g$ is in $\mathcal{W}$)
>2. If $X(0)\hookrightarrow X(1)\hookrightarrow X(2)\hookrightarrow \cdots$ is a sequence of monomorphisms in $\mathcal{W}$, then the sequential colimit $\lim_{\to m}X(m)$ belongs to $\mathcal{W}$
>3. Arbitrary copowers of $\Delta^n$ belong to $\mathcal{W}$ (i.e. $\amalg_{i \in I}\Delta^n$ is in $\mathcal{W}$ for any index set $I$)
>
>Then $\mathcal{W} = \mathsf{sSet}$.

^35ddf6

`\begin{proof}`
Let $S_\bullet$ be a simplicial set. Then $S_\bullet$ is a colimit of a countable sequence of monomorphisms given by its skeleta, $\lim_{\to n}\text{sk}_n(S_\bullet)$. Thus, it suffices to show that bounded simplices are in $\mathcal{W}$. Thus, suppose the dimension of $S_\bullet$ is $n$, and we proceed by induction on $n$. If $n = -1$ then $S_\bullet$ is empty, which is in $\mathcal{W}$ by **(3)**. 

To carry out the inductive step we have a pushout diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ccoprod_%7B%5Csigma%20%5Cin%20S_n%5E%7Bnondeg%7D%7D%5Cpartial%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7Bsk%7D_%7Bn-1%7D(S_%5Cbullet)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Ccoprod_%7B%5Csigma%20%5Cin%20S_n%5E%7Bnondeg%7D%7D%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7Bsk%7D_n(S_%5Cbullet)%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D180%7D%2C%20draw%3Dnone%2C%20from%3D3-3%2C%20to%3D1-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\coprod_{\sigma \in S_n^{nondeg}}\partial\Delta^n} &amp;&amp; {\text{sk}_{n-1}(S_\bullet)} \\
	\\
	{\coprod_{\sigma \in S_n^{nondeg}}\Delta^n} &amp;&amp; {\text{sk}_n(S_\bullet)}
	\arrow[from=1-1, to=1-3]
	\arrow[from=1-1, to=3-1]
	\arrow[from=1-3, to=3-3]
	\arrow[from=3-1, to=3-3]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=180}, draw=none, from=3-3, to=1-1]
\end{tikzcd}
" /></p>

The left hand map is a monomorphism and the corners $\text{sk}_{n-1}(S_\bullet)$ and $\coprod_{\sigma \in S_n^{nondeg}}\Delta^n$ are in $\mathcal{W}$ by the inductive hypothesis and property **(3)**. However, $\coprod_{\sigma \in S_n^{nondeg}}\partial \Delta^n$ is also of degree $n-1$, and so by the inductive hypothesis it is in $\mathcal{W}$. Thus by **(1)** we have that $\text{sk}_n(S_\bullet)$ is in $\mathcal{W}$.
`\end{proof}`

Note that we can replace **(3)** in [[Topological Spaces to Simplicial Sets#^35ddf6]] by the assumption that $\mathcal{W}$ has all standard simplices and is closed under copowers (or coproducts more generally).

We now have the following equivalent conditions relating the connectedness of a simplicial set with the connectedness of its geometric realization.

>[!proposition] Connected Simplicial Set vs Connected Geometric Realization
>Let $S_\bullet$ be a simplicial set. Then the following are equivalent:
>1. The geometric realization $|S_\bullet|$ is path-connected
>2. The geometric realization $|S_\bullet|$ is connected
>3. The simplicial set $S_\bullet$ is connected

^662739

`\begin{proof}`
**(1)** trivially implies **(2)**. **(2)** implies **(3)** since geometric realization preserves colimits.

Finally, **(3)** implies **(1)** since $S_\bullet$ can be written as a colimit of representables over its category of elements, which implies that its geometric realization also is isomorphic to a colimit over representables. Finally, since $\pi_0$ preserves colimits we have that $\pi_0(S_\bullet)\cong \pi_0(|S_\bullet|)$.
`\end{proof}`

## Horns

An important object in the theory of simplicial sets which will be helpful for our development of quasi-categories are horns. If $0 \leq i \leq n$, with $n > 0$, we have a simplicial set $\Lambda_i^n:\mathbb{\Delta}^{op}\to \mathsf{Set}$ given by the formula
$$\Lambda_i^n([m]) = \{\alpha \in \mathbb{\Delta}([m],[n])\,:\,[n]\nsubseteq \alpha([m])\cup \{i\} \}$$
so $\Lambda_i^n$ is a sub-simplicial set of the boundary $\partial\Delta^n$ which doesn't include the $i$th face (the face opposite the $i$th vertex). $\Lambda_i^n$ is called the **$i$th horn** of $\Delta^n$. When $0 < i < n$, we refer to $\Lambda_i^n$ as an **inner horn**, while $\Lambda_0^n$ and $\Lambda_n^n$ are **outer horns**.

By **TBD**, the horns $\Lambda_i^n$ are all connected (as one would expect geometrically). This can also be seen from [[Topological Spaces to Simplicial Sets#^662739]] and the topological interpretation of the horn. 
$$|\Lambda_i^n| = \{(t_0,\dots,t_n)\in |\Delta^n|\,:\,\exists j\neq i,t_j=0\}$$
We have the following characterization of the horn.

>[!proposition] Map Classification of Horn
>Let $0 \leq i \leq n$ with $n > 0$. Then for any simplicial set $S_\bullet$, the map $\mathsf{sSet}(\Lambda_i^n,S_\bullet)\to (S_{n-1})^n$ given by $f\mapsto (f\circ \delta_n^j)_{0\leq j\leq n,j\neq i}$, where $\delta_n^j$ are the face operators, is an injection, with image the collection of sequences $\sigma_0,...,\sigma_{i-1},\sigma_{i+1},...,\sigma_n$ of $(n-1)$-simplices such that $d_j^{n-1}(\sigma_k) = d_{k-1}^{n-1}(\sigma_j)$ for $j,k \in [n]\backslash \{i\}$ with $j < k$.

^f48f55

`\begin{proof}`
**TBC**
`\end{proof}`

[[Topological Spaces to Simplicial Sets#^f48f55]] allows us to realize the horn as the following colimit:
$$\Lambda_i^n \cong \text{coeq}\left(\coprod_{0\leq j < \ell \leq n, j,\ell \neq i}\Delta^{n-2}\to \coprod_{0\leq \ell\leq n,\ell \neq i}\Delta^{n-1}\right)$$

## Kan Complexes

Now that we have the language of horns we can introduce the notion of Kan complexes.

>[!def] Kan Complex
>A simplicial set $S_\bullet$ is said to be a **Kan complex** if it satisfies the following condition:
>- For every $0 \leq i \leq n$ with $n > 0$, every morphism of simplicial sets $\sigma_0:\Lambda_i^n\to S_\bullet$ extends to a morphism $\sigma:\Delta^n\to S_\bullet$ (i.e. an $n$-simplex).

Note that the standard simplex $\Delta^n$ is **not** a Kan complex. Indeed, this comes down to the fact that $\mathbb{\Delta}^n$ does not have inverses to all of its maps. For example, consider the horn $\Lambda_0^2\to \Delta^n$ that sends $0$ to $0$, $2$ to $0$, and $1$ to $1$. In order to fill such a horn map one would need a non-decreasing map $f:[2]\to [n]$ such that $f(0) = 0 = f(2)$ and $f(1) = 1$, which is impossible.

Note that since Kan complexes are defined by a mapping in condition, a product of Kan complexes is again a product.  **DO CONNECTEDNESS FIRST** 

#### References

[^1]: Lurie, J. (n.d.). Kerodon. https://kerodon.net/. Accessed 16 May 2024