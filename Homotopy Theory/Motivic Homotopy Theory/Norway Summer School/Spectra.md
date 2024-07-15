---
date: 2024-07-07T00:06:00
tags:
  - Simplicial
  - Homotopy
  - Spectra
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
In these notes we begin introducing the theory of spectra as a preliminary for the study of stable and motivic homotopy theory. We follow the work in[^1].

By "stable", we often informally mean that taking a suspension merely acts as some kind of shift. For generalized cohomology theories, gluing of spaces can be understood through **excision**, and **Brown representability** says that any cohomology theory is a representable functor, represented by a "spectrum". In this context, **Spectra** are a good in-between for spaces and abelian groups where cohomology theories lie. Suspension is then equivalent to shifting and finite coproducts are equivalent to products in the theory of spectra. Further, the category of Spectra itself has a similar structure to the category of spaces, and hence becomes a suitable substitute for analysis, especially in the context of $\infty$-category theory.

>[!def] Spectrum
>In algebraic topology a **spectrum** is a sequence of pointed simplicial sets $E^0,E^1,E^2,...$ together with **structure maps**
>$$S^1\land E^k = \Sigma E^k\to E^{k+1}$$
>for $k \geq 0$. A map of spectra $f:E\to F$ is a sequence of maps $f^k:E^k\to F^k$ compatible with the structure maps. Let $\mathsf{Spt}$ denote the resulting category of spectra.

>[!example] Important Examples
>1. The **sphere spectrum** $\underline{\mathcal{S}}$ given by $k\mapsto S^k = S^1\land \cdots \land S^1$, and where $\Sigma S^k\to S^{k+1}$ is the identity
>2. The **integral Eilenberg-Mac Lane spectrum** $H\mathbb{Z}$ where $k\mapsto \widetilde{\mathbb{Z}}[S^k]$, and the structure map is induced by the natural map $\widetilde{\mathbb{Z}}[X]\land Y\to \widetilde{\mathbb{Z}}[X\land Y]$.

The Eilenberg-Mac Lane spectrum's structure maps give rise to equivalences $\widetilde{\mathbb{Z}}[S^k]\to \underline{\mathsf{sSet}_*}(S^1,\widetilde{\mathbb{Z}}[S^{k+1}])$ is an equivalence. In general we refer to spectra with this property as **$\Omega$-spectra**. 


## Stability

The category $\mathsf{Spt}$ is naturally tensored and cotensored over $\mathsf{sSet}_*$, where for a pointed simplicial set $X$ and a spectrum $E$, we have the spectrum $E\land X$ where $k\mapsto E^k\land X$, and $E^X$ is the spectrum with $k\mapsto \underline{\mathsf{sSet}_*}(X,E^k)$. 

With these constructions we obtain a pair of adjoint functors

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSpt%7D%7D%20%26%26%20%7B%5Cmathsf%7BsSet%7D_*%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22R%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5CSigma%5E%5Cinfty%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Spt}} &amp;&amp; {\mathsf{sSet}_*}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;R&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\Sigma^\infty}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>

where $\Sigma^\infty X$ is the **suspension spectrum**, $\underline{\mathcal{S}}\land X$, and the right adjoint $RE = E^0$ is the **zeroth space**.

>[!def] Underlying Infinite Loop Space
>If $E$ is a spectrum, its **underlying infinite loop space** is given by
>$$\Omega^\infty E = \lim_{\to n}\Omega^nE^n$$
>where the maps $\Omega^nE^n\to \Omega^{n+1}E^{n+1}$ is defined by applying $\Omega^n$ to the adjoint of the structure map.

The connection between spectra and cohomology theories comes with the following notion of equivalence for spectra:

>[!def] Stable Homotopy Groups
>Let $E$ be a spectrum. The **stable homotopy groups** of $E$ are defined as $$\pi_nE := \lim_{\to k}\pi_{n+k}E^k$$
>where the colimit is over the maps $\pi_{n+k}E^k\to \pi_{n+k}\Omega E^{k+1}\cong \pi_{n+k+1}E^{k+1}$ for $k \geq -n$.

The stable homotopy groups assemble into a functor $\pi_*$ from Spectra into $\mathbb{Z}$-graded abelian groups.

>[!def] Stable Equivalence
>A map of spectra $f:E\to F$ is a **stable equivalence** if it induces an isomorphism on stable homotopy groups.

Given spectra $E$ and $F$ we can form the spectra $E\lor F$, which has structure maps
$$S^1\land(E^k\lor F^k)\cong (S^1\land E^k)\lor (S^1\land F^k)\to E^{k+1}\lor F^{k+1}$$

As with equivalence in other settings, stable equivalences can be used to form the **stable homotopy category** $\mathsf{HoSpt}$, obtained from the category of spectra by formally inverting stable equivalences. This is sometimes referred as the **stable category**.

### Homology Theories

If $E$ is a spectrum and $X$ is a simplicial set, we can obtain an associated (co)homology theory as follows. Define 
$$E_n(X) := \pi_n(E\land X)$$
and $$E^n(X)=\pi_{-n}E^X$$
both of which are pointed simplicial sets. The **stable homotopy group** $\pi_n^S(X)$ of a pointed simplicial set $X$ is by definition
$$\underline{\mathcal{S}}_n(X) :=\pi_n(\underline{\mathcal{S}}\land X) = \lim_{\to k}\pi_{n+k}(S^k\land X)$$

>[!thm] Homology/Cohomology From Spectra
>There are natural isomorphisms
>$$(H\mathbb{Z})_n(X)\cong \widetilde{H}_n(X)$$
>and $$(H\mathbb{Z})^n(X) \cong \widetilde{H}^n(X)$$
>where $H\mathbb{Z}$ is the integral Eilenberg-Mac Lane spectrum.

`\begin{proof}[Proof Idea.]`
For the homology part note that $$\widetilde{H}_n(X) \cong \pi_0\underline{\mathsf{sSet}_*}(X,\widetilde{\mathbb{Z}}[S^n])\cong \pi_0\underline{\mathsf{sSet}_*}(X\land S^k,\widetilde{\mathbb{Z}}[S^{n+k}]) \cong \widetilde{H}_{n+k}(S^k\land X)\cong \pi_{n+k}\widetilde{\mathbb{Z}}[S^k\land X]$$
The desired natural isomorphism is then given by the colimit over the maps
$$\pi_{n+k}((H\mathbb{Z}\land X)^k)=\pi_{n+k}(\widetilde{\mathbb{Z}}[S^k]\land X)\to \pi_{n+k}(\widetilde{\mathbb{Z}}[S^k\land X])$$
which is an isomorphism for $k > n$ by a "stability result".

For the cohomology part,
$$\widetilde{H}^n(X) = \widetilde{H}^k(S^{k-n}\land X)=\pi_0\underline{\mathsf{sSet}_*}(S^{k-n}\land X,\widetilde{\mathbb{Z}}[S^k])\cong \pi_{k-n}\underline{\mathsf{sSet}_*}(X,\widetilde{\mathbb{Z}}[S^k])$$
for $k \geq n$.
`\end{proof}`

### Connection to Chain Complexes.

Note that if $C_\bullet$ is a chain complex, not necessarily non-negatively graded, we can obtain a chain of chain complexes $C_\bullet^0,C_\bullet^1,C_\bullet^2$, where $C^k_n = C_{n-k}$ for $n\geq 0$, and $C_n^k = 0$ for $n < 0$. Then each $C_\bullet^k$ is a non-negatively graded chain complex, and we have isomorphisms $C_n^k\cong C_{n+1}^{k+1}$ for $n\geq 0$. We can then recover the homology of $C_\bullet$ as the colimit
$$H_k(C_\bullet) = \lim\limits_{\to n}H_{n+k}(C_\bullet^n)$$
where $H_{n+k}(C^n_\bullet)\to H_{n+1+k}(C^{n+1}_\bullet)$ is given by the isomorphisms, or zero maps, depending whether $n+k \geq 0$.

If $\mathbb{Z}[1]$ is the chain complex with $\mathbb{Z}$ concentrated in degree $1$, then the isomorphisms $C_n^k\cong C_{n+1}^{k+1}$ can be reformulated as a map
$$\mathbb{Z}[1]\otimes C_\bullet^k\to C_\bullet^{k+1}$$
which is an isomorphism in positive degrees. Recall that the tensor product of chain complexes $C_\bullet$ and $D_\bullet$ is given by
$$(C_\bullet \otimes D_\bullet)_n =\bigoplus_{p+q=n}(C_p\otimes D_q)$$
which is well-behaved if $C_\bullet$ or $D_\bullet$ is non-negatively graded.

If we replace $(\mathsf{sSet},\land,S^1)$ with $(\mathsf{sAb},\otimes, \widetilde{\mathbb{Z}}[S^1])$, $(\mathsf{Ch}(\mathsf{Ab})_{\geq 0},\otimes, \mathbb{Z}[1])$, or $(\mathsf{Ch}(\mathsf{Ab}),\otimes,\mathbb{Z}[1])$ in the definition of spectra, we obtain categories $\mathsf{Spt}(\mathsf{sAb}), \mathsf{Spt}(\mathsf{Ch}(\mathsf{Ab})_{\geq 0})$, and $\mathsf{Spt}(\mathsf{Ch}(\mathsf{Ab}))$, which are connected by a chain of associated adjunctions.


#### References

[^1]: Dundas, B. I., Levine, M., Østvær, P. A., Röndigs, O., & Voevodsky, V. (Eds.). (2007). Motivic Homotopy Theory. Berlin, Heidelberg: Springer. https://doi.org/10.1007/978-3-540-45897-5