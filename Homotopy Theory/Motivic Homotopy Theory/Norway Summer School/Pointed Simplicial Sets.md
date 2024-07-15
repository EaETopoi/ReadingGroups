---
date: 2024-07-06T19:07:00
tags:
  - Homotopy
  - Simplicial
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
In these notes we introduce the basic theory of pointed simplicial sets in homotopy theory, as well as some standard constructions, as they appear in [^1].

## Pointed Simplicial Sets

As with the category of simplicial sets, $\mathsf{sSet} = \mathbb{\Delta}^{op}\to \mathsf{Set}$, the category of pointed simplicial sets $\mathsf{sSet}_*$ can be naturally identified with a pre-sheaf category, namely $\mathbb{\Delta}^{op}\to \mathsf{Set}_*$. Due to this, $\mathsf{sSet}_*$ is naturally seen to be complete and cocomplete, with limits given by termwise evaluations.

The limit and colimit structure, as well as the symmetric monoidal structure in $\mathsf{sSet}_*$ will be very important for the study of homotopy theory. First, as in $\mathsf{Set}_*$, the coproduct of two pointed simplicial sets $X$ and $Y$ is the wedge sum $X\lor Y$, with explicit model
$$(X\lor Y)_n = X_n\lor Y_n = \{(x,y_n) \in X_n\times Y_n\,:\,x \in X_n\}\cup\{(x_n,y) \in X_n\times Y_n\,:\,y \in Y_n\}$$
where $x_n \in X_n$ and $y_n \in Y_n$ are the basepoints for the pointed sets. Equivalently, we can write
$$X_n\lor Y_n = (X_n\amalg Y_n)/\{x_n\sim y_n\}$$

Note that we have a natural free-forgetful adjunction

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BsSet%7D_*%7D%20%26%26%20%7B%5Cmathsf%7BsSet%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22U%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B(-)_%2B%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{sSet}_*} &amp;&amp; {\mathsf{sSet}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;U&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{(-)_+}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

where $(X_+)_n = (X_n)_+$ is the free pointed simplicial set obtained by adding a basepoint $+$ to each component of a simplicial set. Due to this, the limits in $\mathsf{sSet}_*$ look like limits in $\mathsf{sSet}$. If $(X,x_0)$ and $(Y,y_0)$ are pointed sets, then their product $X\times Y$ is the product in $\mathsf{Set}$ with basepoint $(x_0,y_0)$.

However, instead of being interested in the product in $\mathsf{sSet}_*$, the more useful symmetric monoidal structure for homotopy theory is induced by the **smash product**:
$$X\land Y := \text{coeq}\left(X\lor Y\rightrightarrows X\times Y\right)$$
where the bottom arrow factors through $\Delta^0=*$, and the top arrow is given by inclusion. In the case of sets $X\land Y$ is given by
$$X\land Y = (X\times Y)/\{(x,y) \in X\times Y\,:\,x = x_0\;\text{or}\;y=y_0\}$$
with basepoint $(x_0,y_0)$. Indeed, if $(Z,z_0)$ is a pointed set, and $f:X\times Y\to Z$ is a set function such that $f(x_0,y_0) = z_0$, and further $f(x,y) = z_0$ if $x_0 = x$ or $y_0  = y$. Then we have a unique map $g:X\land Y\to Z$ such that $g(x,y) = f(x,y)$. In particular, $g(x_0,y_0) = f(x_0,y_0) = z_0$, so $g$ is a map of pointed sets.

The reason for working with the smash product rather than the categorical product is that it will give us the appropriate notion of homotopies of pointed maps. Further, since the smash product is defined as a colimit, for a fixed pointed simplicial set $X$, $X\land-$ preserves colimits. Since pre-sheaf categories are well-powered and have a small generating set, given by the representable pre-sheaves, $X\land -$ has a right adjoint by the special adjoint functor theorem. Namely, the right adjoint is given by
$$\underline{\mathsf{sSet_*}}(X,Y)_n := \mathsf{sSet_*}(X\land \Delta^n_+,Y)$$
where the basepoint is the map $X\land\Delta^n_+\to Y$ sending everything to appropriate basepoints in $Y$. Indeed, to see that this gives an adjunction observe that for a representable pre-sheaf we have
$$\mathsf{sSet}_*(\Delta^n_+,\underline{\mathsf{sSet}_*}(X,Y)) \cong \mathsf{sSet}_*(X\land \Delta^n_+,Y)$$
by the yoneda lemma and the adjunction $(-)_+\dashv U$. Then if $Z$ is any other pre-sheaf of pointed simplicial sets, we can write $Z = \text{colim}_{\int Z}\Delta^n_+$ as a colimit of representables, so we have
$$\mathsf{sSet}_*(Z,\underline{\mathsf{sSet}_*}(X,Y))\cong \lim_{\int Z}\mathsf{sSet}_*(\Delta_+^n,\underline{\mathsf{sSet}_*}(X,Y))\cong \lim_{\int Z}\mathsf{sSet}_*(X\land \Delta^n_+,Y)\cong \mathsf{sSet}_*(X\land Z,Y)$$
and hence with this smash-product $\mathsf{sSet}_+$ becomes a symmetric monoidal closed category.

The smash-product is also important for defining suspensions. 

>[!def] Suspension
>Let $X$ be a pointed simplicial set. The **suspension** of $X$ is the smash-product $\Sigma X :=S^1\land X$, where $S^1 := \Delta^1/\partial\Delta^1$, with basepoint given by the equivalence class from $\partial\Delta^1$. In general, for $n \geq 2$, we define
>$$S^n := \Sigma S^{n-1} = S^1\land S^{n-1}$$
>and $S^0 = \partial\Delta^1$.

### Simplicial Abelian Groups

We have a natural adjunction

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BAb%7D%7D%20%26%26%20%7B%5Cmathsf%7BSet%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22U%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathbb%7BZ%7D%5B-%5D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Ab}} &amp;&amp; {\mathsf{Set}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;U&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\mathbb{Z}[-]}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

which upon post-composition gives an adjunction of pre-sheaf categories

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BsAb%7D%7D%20%26%26%20%7B%5Cmathsf%7BsSet%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22U%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathbb%7BZ%7D%5B-%5D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{sAb}} &amp;&amp; {\mathsf{sSet}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;U&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\mathbb{Z}[-]}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

which factors through the adjunctions

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BsAb%7D%7D%20%26%26%20%7B%5Cmathsf%7BsSet%7D_*%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22U%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cwidetilde%7B%5Cmathbb%7BZ%7D%7D%5B-%5D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{sAb}} &amp;&amp; {\mathsf{sSet}_*}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;U&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\widetilde{\mathbb{Z}}[-]}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

and

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BsSet%7D_*%7D%20%26%26%20%7B%5Cmathsf%7BsSet%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22U%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B(-)_%2B%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{sSet}_*} &amp;&amp; {\mathsf{sSet}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;U&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{(-)_+}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

where $\widetilde{Z}[X] = \mathbb{Z}[X]/\mathbb{Z}[*]$. As with simplicial sets and pointed simplicial sets, $\mathsf{sAb}$ has a closed monoidal structure with tensor given by $(M\otimes N)_n := M_n\otimes_\mathbb{Z} N_n$, and $\underline{\mathsf{sAb}}(M,N)\cong \mathsf{sAb}(M\otimes \mathbb{Z}[\Delta^n],N)$.

We have the following identities:

1. $X_+\land Y_+\cong (X\times Y)_+$ since
   $$X_+\land Y_+= \text{coeq}\left(X_+\lor Y_+\rightrightarrows X_+\times Y_+\right) = \text{coeq}\left(X_+\lor Y_+\rightrightarrows (X\times Y)\amalg(X_+\lor Y_+)\right) \cong (X\times Y)_+$$
2. $X\land (Y_1\lor Y_2)\cong (X\land Y_1)\lor (X\land Y_2)$ since $\land$ commutes with colimits.
3. $S^0\land X \cong X$
4. $\widetilde{\mathbb{Z}}[X\lor Y]\cong \widetilde{\mathbb{Z}}[X]\oplus \widetilde{\mathbb{Z}}[Y]$ since $\widetilde{\mathbb{Z}}$ commutes with colimits.
5. $\widetilde{\mathbb{Z}}[X\land Y]\cong \widetilde{\mathbb{Z}}[X]\otimes \widetilde{\mathbb{Z}}[Y]$ given by
   $$(x,y)\mapsto x\otimes y$$
   which is surjective with kernel generated by $(x,y)$ where $x = x_0$ or $y = y_0$, which is zero in $\widetilde{\mathbb{Z}}[X\land Y]$. 
6. If $A \subseteq X$ is a pointed simplicial subset, then
   $$0\to \widetilde{\mathbb{Z}}[A]\to \widetilde{\mathbb{Z}}[X]\to \widetilde{\mathbb{Z}}[X/A]\to 0$$
   is exact.

Note that both the symmetric monoidal closed structure on $\mathsf{sSet}_+$ and that on $\mathsf{sAb}$ witness these categories as enriched over $\mathsf{sSet}$.


### Loop Spaces and Cohomology

Recall that if $X$ is a pointed simplicial set, then the right adjoint to the suspension of $X$ is $\underline{\mathsf{sSet}_+}(S^1,X)$. Further, writing $\Omega$ for the loop space for spaces, observe that

$$
\begin{align*}
\mathsf{sSet}_*(Y,\text{Sing}_\bullet(\Omega|X|)) &\cong \mathsf{Top}(|Y|,\Omega|X|)\\
&\cong \mathsf{Top}(\Sigma|Y|,|X|)\\
&\cong \mathsf{Top}(|\Sigma Y|,|X|) \\
&\cong \mathsf{sSet}_*(\Sigma Y,\text{Sing}_\bullet(|X|))\\
&\cong \mathsf{sSet}_*(Y,\underline{\mathsf{sSet}_*}(S^1,\text{Sing}_\bullet(|X|)))
\end{align*}$$
using the fact that geometric realization is exact, i.e. commutes with finite products. Thus, by the Yoneda embedding we have that
$$\text{Sing}_\bullet(\Omega|X|)\cong \underline{\mathsf{sSet}_*}(S^1,\text{Sing}_\bullet(|X|))$$

>[!def] Homotopy Group of Simplicial Sets
>Let $X$ be a simplicial set. Then its $n$-th homotopy group is given by $\pi_nX := \pi_n|X|$.

For these notes the pointed simplicial set $\underline{\mathsf{sSet}_*}(A,\text{Sing}_\bullet(|X|))$, where $\text{Sing}_\bullet(|X|)$ is pointed when $X$ is pointed via the unit $X\to \text{Sing}_\bullet(|X|)$. Then we define the **loop space** of a pointed simplicial set $X$ to be the pointed simplicial set
$$\Omega X := \underline{\mathsf{sSet}_*}(S^1,\text{Sing}_\bullet(|X|))\cong \text{Sing}_\bullet(\Omega|X|)$$
However, this implies that the suspension and loop are not adjoint in pointed simplicial sets. But, a map $S^1\land X\to Y$ still induces a map $X\to \Omega Y$ by applying the adjunction to the composite $S^1\land X\to Y\to \text{Sing}_\bullet(|Y|)$. Further, this definition of the simplicial loop space gives the "right" homotopy type.

>[!def] Cohomology
>Let $X$ be a pointed simplicial set. Then **$n$th reduced/integral cohomology** of $X$ is given by the group
>$$\widetilde{H}^n(X)\cong \pi_0\underline{\mathsf{sSet}_*}(X,\widetilde{\mathbb{Z}}[S^n])$$



#### References

[^1]: Dundas, B. I., Levine, M., Østvær, P. A., Röndigs, O., & Voevodsky, V. (Eds.). (2007). Motivic Homotopy Theory. Berlin, Heidelberg: Springer. https://doi.org/10.1007/978-3-540-45897-5
