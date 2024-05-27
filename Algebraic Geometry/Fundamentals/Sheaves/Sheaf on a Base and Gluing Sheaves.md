---
date: 2024-05-25T10:50:00
tags:
  - AlgebraicGeometry
  - Sheaves
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

In this set of notes we go over the structure of sheaves on a base of a topological space and how to extend them to sheaves on the whole space.

## Sheaves of Spaces on a Base

^e3abb5

Let $\mathcal{B}$ be a base of open sets on a topological space $X$. Then we can think of $\mathcal{B}$ as a full-subcategory of $\mathsf{Top}(X)$, with inclusion $\iota:\mathcal{B}\hookrightarrow \mathsf{Top}(X)$. Then from our theory of [[Kan Extensions]], as long as we are valued in a (co)complete category $\mathcal{E}$
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D_%5Cmathcal%7BE%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BPs%7D_%5Cmathcal%7BE%7D(%5Cmathcal%7BB%7D)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathcal%7BE%7D%5E%5Ciota%7D%22'%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ctext%7BRan%7D_%5Ciota%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ctext%7BLan%7D_%5Ciota%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-91%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-89%7D%2C%20draw%3Dnone%2C%20from%3D2%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Ps}_\mathcal{E}(X)} &amp;&amp; {\mathsf{Ps}_\mathcal{E}(\mathcal{B})}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathcal{E}^\iota}&quot;', from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\text{Ran}_\iota}&quot;', bend right = 60, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{\text{Lan}_\iota}&quot;', bend right = 60, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-91}, draw=none, from=0, to=1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-89}, draw=none, from=2, to=0]
\end{tikzcd}
" /></p>
Now, we have a natural notion of sheaves on a base.

>[!def] Sheaves on a Base
>A pre-sheaf $\mathcal{F}:\mathcal{B}^{op}\to \mathcal{E}$ on the base $\mathcal{B}$ is a sheaf with respect to the open covering site on $\mathcal{B}$, which consists of all sieves whose union over domains cover the codomain of the sieve.

^9365dd

The definition in [[Sheaf on a Base and Gluing Sheaves#^9365dd]] implies that $\mathcal{E}^\iota$ preserves sheaves, and hence induces a functor $\mathsf{Sh}_\mathcal{E}(X)\to \mathsf{Sh}_\mathcal{E}(\mathcal{B})$. Further, since $\text{Ran}_\iota$ is a right adjoint it also preserves sheaves. Composing with our associated sheaf adjunction we obtain the triple adjunction
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D_%5Cmathcal%7BE%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D_%5Cmathcal%7BE%7D(%5Cmathcal%7BB%7D)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathcal%7BE%7D%5E%5Ciota%7D%22'%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ctext%7BRan%7D_%5Ciota%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%5Ccirc%20%5Ctext%7BLan%7D_%5Ciota%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-91%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-89%7D%2C%20draw%3Dnone%2C%20from%3D2%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Sh}_\mathcal{E}(X)} &amp;&amp; {\mathsf{Sh}_\mathcal{E}(\mathcal{B})}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathcal{E}^\iota}&quot;', from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\text{Ran}_\iota}&quot;', bend right = 60, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{\mathfrak{a}\circ \text{Lan}_\iota}&quot;', bend right = 60, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-91}, draw=none, from=0, to=1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-89}, draw=none, from=2, to=0]
\end{tikzcd}
" /></p>
Further, since the inclusion $\iota$ is fully-faithful and these are all pointwise Kan extensions, as $\mathcal{E}$ is (co)complete, it follows that the universal natural transformation at a pre-sheaf $\mathcal{F}$ on $\mathcal{B}$, $\eta_\mathcal{F}:\mathcal{F}\Rightarrow \text{Lan}_\iota\mathcal{F}\circ \iota$, is a natural isomorphism by [[Kan Extensions#^90826e]], and likewise when we whisker with the associated sheaf functor. Explicitly, we have that at an open set $U$ in $X$
$$\text{Lan}_\iota\mathcal{F}(U) \cong \int^{B:\mathcal{B}^{op}}\mathsf{Top}(X)(U,B)\times \mathcal{F}(B) \cong \text{colim}\left((\iota\vert U)^{op}\xrightarrow{\pi_0}\mathcal{B}^{op}\xrightarrow{\mathcal{F}}\mathcal{E}\right) = \lim\limits_{\to U\subseteq B} \mathcal{F}(B)$$
As becomes clear in the formula, $\text{Lan}_\iota$ is really just a special case of $\iota^*_{pre}$ given in [[Important Adjunctions for Sheaves#^2a1b9e|push-pull adjunctions]]. 


Since a base of a topology gives a (co)-final subcategory of a directed category, colimits over $\mathsf{Top}(X)^{op}$ can be computed in $\mathcal{B}^{op}$ by the following lemma, so in particular we can compute stalks using basic open sets.

>[!lemma] Co-final Subcategory
>Let $\mathcal{C}$ be a category with directed limits. Let $(I,\leq)$ be a directed set, identified with its category, and let $J \subseteq I$ be a cofinal subset (i.e.\ for all $i \in I$, there exists $j \in J$ such that $i \leq j$). Then if $D:(I,\leq)\to \mathcal{C}$ is a diagram in $\mathcal{C}$ and $\iota:(J,\leq)\hookrightarrow (I,\leq)$ is the inclusion of the cofinal subcategory, then there is an isomorphism
>$$\lim\limits_{\to I}D \cong \lim\limits_{\to J}(D\circ \iota)$$

`\begin{proof}`
Let $\mathcal{C}$, $\iota:(J,\leq)\hookrightarrow (I,\leq)$, and $D:(I,\leq)\to \mathcal{C}$ be as in the claim. Note that $J$ being cofinal in $I$ implies that it is also directed, since if $j,j' \in J$, there exists $i \in I$ and $j'' \in J$ such that $j,j' \leq i$ and $i \leq j''$, so $j,j' \leq j''$. Since $\mathcal{C}$ has directed limits we have that $\lim\limits_{\to I}D$ and $\lim\limits_{\to J}(D\circ \iota)$ exist. 

For each $i \in I$ let $\varphi_i:D(i)\to \lim\limits_{\to I}D$ denote the inclusion for the colimit over $D$, and for each $j \in J$ let $\psi_j:D(j)\to \lim\limits_{\to J}(D\circ \iota)$ denote the inclusion for the colimit over $D\circ \iota$. Then for each $j \leq j'$ in $J$, we have that the triangle
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%26%20%7B%5Clim%5Climits_%7B%5Cto%7DD%7D%20%5C%5C%0A%20%20%20%20%09%7BD(j)%7D%20%26%26%20%7BD(j')%7D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(j%5Cleq%20j')%7D%22'%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	&amp; {\lim\limits_{\to}D} \\
    	{D(j)} &amp;&amp; {D(j')}
    	\arrow[&quot;{D(j\leq j')}&quot;', from=2-1, to=2-3]
    	\arrow[from=2-1, to=1-2]
    	\arrow[from=2-3, to=1-2]
    \end{tikzcd}
" /></p>
commutes by definition of the colimit. It follows by the universal property of $\lim\limits_{\to J}(D\circ \iota)$ that there exists a unique map $\alpha:\lim\limits_{\to J}(D\circ \iota) \to \lim\limits_{\to I}D$ such that for any $j \in J$, the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7B%5Clim%5Climits_%5Cto%20(D%5Ccirc%20%5Ciota)%7D%20%26%26%20%7B%5Clim%5Climits_%5Cto%20D%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7BD(j)%7D%0A%20%20%20%20%09%5Carrow%5B%22%5Calpha%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_j%7D%22%2C%20from%3D2-2%2C%20to%3D1-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cvarphi_j%7D%22'%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{\lim\limits_\to (D\circ \iota)} &amp;&amp; {\lim\limits_\to D} \\
    	&amp; {D(j)}
    	\arrow[&quot;\alpha&quot;, from=1-1, to=1-3]
    	\arrow[&quot;{\psi_j}&quot;, from=2-2, to=1-1]
    	\arrow[&quot;{\varphi_j}&quot;', from=2-2, to=1-3]
    \end{tikzcd}
" /></p>
commutes.

On the other hand, if $i \in I$, then since $J$ is cofinal there exists $j \in J$ such that $i \leq j$. Then we can define $\psi_i:D(i)\to \lim\limits_{\to J}(D\circ \iota)$ by $\psi_i := \psi_j\circ D(i\leq j)$. This definition is independent of the choice of $j$. Indeed, if $j,j' \in J$ such that $i \leq j,j'$, since $J$ is directed there exists $j''$ such that $j,j' \leq j''$. Then we have a commuting diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%26%20%7B%5Clim%5Climits_%5Cto(D%5Ccirc%20%5Ciota)%7D%20%5C%5C%0A%20%20%20%20%09%7BD(j)%7D%20%26%20%7BD(j'')%7D%20%26%20%7BD(j')%7D%20%5C%5C%0A%20%20%20%20%09%5C%5C%0A%20%20%20%20%09%26%20%7BD(i)%7D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_%7Bj''%7D%7D%22%2C%20from%3D2-2%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_j%7D%22%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(j%5Cleq%20j'')%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(j'%5Cleq%20j'')%7D%22%2C%20from%3D2-3%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_%7Bj'%7D%7D%22'%2C%20from%3D2-3%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(i%5Cleq%20j)%7D%22%2C%20curve%3D%7Bheight%3D-12pt%7D%2C%20from%3D4-2%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(i%5Cleq%20j'')%7D%22%2C%20from%3D4-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(i%5Cleq%20j')%7D%22'%2C%20curve%3D%7Bheight%3D12pt%7D%2C%20from%3D4-2%2C%20to%3D2-3%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	&amp; {\lim\limits_\to(D\circ \iota)} \\
    	{D(j)} &amp; {D(j'')} &amp; {D(j')} \\
    	\\
    	&amp; {D(i)}
    	\arrow[&quot;{\psi_{j''}}&quot;, from=2-2, to=1-2]
    	\arrow[&quot;{\psi_j}&quot;, from=2-1, to=1-2]
    	\arrow[&quot;{D(j\leq j'')}&quot;', from=2-1, to=2-2]
    	\arrow[&quot;{D(j'\leq j'')}&quot;, from=2-3, to=2-2]
    	\arrow[&quot;{\psi_{j'}}&quot;', from=2-3, to=1-2]
    	\arrow[&quot;{D(i\leq j)}&quot;, curve={height=-12pt}, from=4-2, to=2-1]
    	\arrow[&quot;{D(i\leq j'')}&quot;, from=4-2, to=2-2]
    	\arrow[&quot;{D(i\leq j')}&quot;', curve={height=12pt}, from=4-2, to=2-3]
    \end{tikzcd}
" /></p>
where the bottom triangles commute by functoriality of $D$ and the top triangles commute by definition of the colimit $\lim\limits_{\to J}(D\circ \iota)$. It follows that 
$$
\begin{align*}
	\psi_j\circ D(i\leq j) &= \psi_{j''}\circ D(j\leq j'')\circ D(i\leq j) \\
	&= \psi_{j''}\circ D(i\leq j'') \\
	&= \psi_{j''}\circ D(j'\leq j'')\circ D(i\leq j') \\
	&= \psi_{j'}\circ D(i\leq j')
\end{align*}
$$
so the $\psi_i$ are well-defined for any $i \in I$. Further, if $i,i' \in I$ such that $i \leq i'$, and we choose $j \in J$ such that $i' \leq j$, then the outer triangle in the following diagram commutes
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%26%20%7B%5Clim%5Climits_%5Cto(D%5Ccirc%20%5Ciota)%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7BD(j)%7D%20%5C%5C%0A%20%20%20%20%09%7BD(i)%7D%20%26%26%20%7BD(i')%7D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_j%7D%22%2C%20from%3D2-2%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(i%5Cleq%20i')%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(i%5Cleq%20j)%7D%22'%2C%20from%3D3-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7BD(i'%5Cleq%20j)%7D%22%2C%20from%3D3-3%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_%7Bi'%7D%7D%22'%2C%20curve%3D%7Bheight%3D12pt%7D%2C%20from%3D3-3%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_i%7D%22%2C%20curve%3D%7Bheight%3D-12pt%7D%2C%20from%3D3-1%2C%20to%3D1-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	&amp; {\lim\limits_\to(D\circ \iota)} \\
    	&amp; {D(j)} \\
    	{D(i)} &amp;&amp; {D(i')}
    	\arrow[&quot;{\psi_j}&quot;, from=2-2, to=1-2]
    	\arrow[&quot;{D(i\leq i')}&quot;', from=3-1, to=3-3]
    	\arrow[&quot;{D(i\leq j)}&quot;', from=3-1, to=2-2]
    	\arrow[&quot;{D(i'\leq j)}&quot;, from=3-3, to=2-2]
    	\arrow[&quot;{\psi_{i'}}&quot;', curve={height=12pt}, from=3-3, to=1-2]
    	\arrow[&quot;{\psi_i}&quot;, curve={height=-12pt}, from=3-1, to=1-2]
    \end{tikzcd}
" /></p>
since the bottom triangle commutes by functoriality of $D$ and the side triangles commute by definition of the $\psi_i$. Thus, we have that $\lim\limits_{\to J}(D\circ \iota)$ is a colimit cone under $D$. By the universal property of $\lim\limits_{\to I}D$ there exists a unique $\beta:\lim\limits_{\to I}D\to \lim\limits_{\to J}(D\circ \iota)$ such that for any $i \in I$ the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7B%5Clim%5Climits_%5Cto%20D%7D%20%26%26%20%7B%5Clim%5Climits_%5Cto%20(D%5Ccirc%20%5Ciota)%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7BD(i)%7D%0A%20%20%20%20%09%5Carrow%5B%22%5Cbeta%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cvarphi_i%7D%22%2C%20from%3D2-2%2C%20to%3D1-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cpsi_i%7D%22'%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{\lim\limits_\to D} &amp;&amp; {\lim\limits_\to (D\circ \iota)} \\
    	&amp; {D(i)}
    	\arrow[&quot;\beta&quot;, from=1-1, to=1-3]
    	\arrow[&quot;{\varphi_i}&quot;, from=2-2, to=1-1]
    	\arrow[&quot;{\psi_i}&quot;', from=2-2, to=1-3]
    \end{tikzcd}
" /></p>
But then by uniqueness of the map from the universal property of the colimit we must have that $\alpha\circ \beta$ is the identity on $\lim\limits_{\to I} D$ and $\beta\circ \alpha$ is the identity on $\lim\limits_{\to J}(D\circ \iota)$. Hence, $\beta$ is an isomorphism between $\lim\limits_{\to I} D$ and $\lim\limits_{\to J}(D\circ \iota)$ are isomorphic as direct limit objects.
`\end{proof}`

>[!remark]
>All of this work extends to the theory of $\mathcal{O}_X$-modules and $\mathcal{O}_X$-modules on a base.



## Gluing Sheaves on a Space

Commonly in algebraic geometry, such as in the case of schemes, we are interested in gluing structures from ones defined on opens. Thus, in this section we show that, given certain conditions, this is possible. First, let us consider the case of a topological space $X$ covered in opens $\bigcup_{i\in I}U_i$.

>[!theorem] Gluing Sheaves on a Space
>Let $X$ be a topological space and let $\{U_i\}_{i \in I}$ be an open cover of $X$. Let $\mathcal{F}_i$ be a sheaf on $U_i$ for each $i \in I$, and let $\phi_{ij}:\mathcal{F}_i\vert_{U_i\cap U_j}\to \mathcal{F}_j\vert_{U_i\cap U_j}$ be a collection of isomorphisms of sheaves such that $\phi_{ii} = 1_{\mathcal{F}_i}$ and for each $i,j,k \in I$, the **1-cocycle condition**
>$$\phi_{ik}\vert_{U_i\cap U_j\cap U_k} = \phi_{jk}\vert_{U_i\cap U_j\cap U_k}\circ \phi_{ij}\vert_{U_i\cap U_j\cap U_k}$$
>holds. Then there exists a sheaf $\mathcal{F}$ on $X$ such that $\mathcal{F}_i\cong \mathcal{F}\vert_{U_i}$ for all $i \in I$, and $\mathcal{F}$ is unique up to unique isomorphism.

^ddc1f7

`\begin{proof}`
This theorem is an immediate consequence of the fact that $\mathsf{Sh}(X)$ is complete. However, the result in this formulation holds when considering cases such as schemes, where not all colimits exist. Thus, as an instructive exercise we provide the proof for this claim here.

Define a pre-sheaf $\mathcal{F}$ on $X$ by setting its value at an open set $U$ to be
$$\mathcal{F}(U) = \{(s_i \in \mathcal{F}_i(U_i\cap U))_{i \in I}\mid \phi_{ij,U_i\cap U_j\cap U}(s_i\vert_{U_i\cap U_j\cap U}) = s_j\vert_{U_i\cap U_j \cap U}\}$$
First let us give isomorphisms for each open. We define $\phi_i:\mathcal{F}_i\to \mathcal{F}\vert_{U_i}$ by defining $\phi_{i,U}:\mathcal{F}_i(U)\to \mathcal{F}(U\cap U_i)$ to be the map that sends a section $s \in \mathcal{F}_i(U)$ to $(s_i)_{i \in I} \in \mathcal{F}(U\cap U_i)$ where $s_j = \phi_{ij,U\cap U_i\cap U_j}(s)$ for all $j \in I$. This is naturally well-defined and injective, since $\mathcal{F}_i$ is a sheaf, and is surjective by the constraint defining $\mathcal{F}(U\cap U_i)$. At this point we could stop, take the associated sheaf functor of $\mathcal{F}$, use that it commutes with restrictions, and obtain our result, but I claim that $\mathcal{F}$ is already a sheaf. One way to see this is that $\mathcal{F}$ is defined as a limit and since equalizers are limits and limits commute, $\mathcal{F}$ will satisfy the sheaf condition since each $\mathcal{F}_i$ does.

Let $((s_{i,k})_{i \in I})_{k \in K}$ denote a collection of compatible sections of $\mathcal{F}$ for a cover $V = \bigcup_{k \in K}V_k$. For each $i \in I$ this gives a collections of compatible sections of $\mathcal{F}_i$, which is a sheaf, so we have a *unique* amalgamation $s_i \in \mathcal{F}_i(V)$. It suffices to show that $(s_i)_{i \in I}$ is an element of $\mathcal{F}(V)$. But, since $\phi_{ij}$ is a map of sheaves, it commutes with restrictions, and since the $\mathcal{F}_i$ are sheaves, it follows that $(s_i)_{i \in I}$ is unique.
`\end{proof}`
We can extend this to a gluing of sheaves and spaces.

>[!theorem] Gluing Ringed Spaces
>Let $\{(X_i,\mathcal{O}_{X_i})\}_{i \in I}$ be a family of ringed spaces, and for each $i,j \in I$, let $U_{ij} \subseteq X_i$ be an open subset. Let $\varphi_{ij}:U_{ij}\to U_{ji}$ for all $i,j \in I$ be isomorphisms of ringed spaces such that $\varphi_{ii} = 1_{U_{ii}}$ and for any $i,j,k \in I$ the **1-cocycle condition** is satisfied
>$$\varphi_{ik}\vert_{U_{ij}\cap U_{ik}} = \varphi_{jk}\vert_{U_{ji}\cap U_{jk}}\circ \varphi_{ij}\vert_{U_{ij}\cap U_{ik}}$$
>Then there exists a ringed space $(X,\mathcal{O}_X)$ and open subsets $X_i'\subseteq X$ for all $i \in I$ which cover $X$ together with isomorphisms of ringed spaces $\psi_i:X_i\to X_i'$ satisfying $\psi_i\vert_{U_{ij}} = \psi_j\circ \varphi_{ij}$ for all $i,j \in I$. When the $X_i$ are locally ringed spaces (resp. schemes), so is $X$.

^afca9a

`\begin{proof}`
First, we can forget to $\mathsf{Top}$ to obtain a gluing diagram, and then take the colimit of the diagram to obtain $X$. Thus, we have open embeddings $\psi_i:X_i\to X$ for all $i \in I$ which cover $X$ and such that $\psi_i\vert_{U_{ij}} = \psi_j\circ \varphi_{ij}$ for all $i,j \in I$. Note that in particular this implies $\psi_i(X_i)\cap \psi_j(X_j) = \psi_i(U_{ij})$. Further, for each $i \in I$ we obtain a sheaf $(\psi_i)_*\mathcal{O}_{X_i}$ on $X$, together with sheaf isomorphisms
$$(\psi_i)_*\varphi_{ij}:(\psi_i)_*\mathcal{O}_{X_i}\vert_{\psi_i(X_i)\cap \psi_j(X_j)} \to (\psi_j)_*\mathcal{O}_{X_j}\vert_{\psi_i(X_i)\cap \psi_j(X_j)}$$
which satisfies the **1-cocycle** condition since pushforward strictly preserves restrictions. By [[Sheaf on a Base and Gluing Sheaves#^ddc1f7]] we obtain a unique sheaf $\mathcal{O}_X$ on $X$ together with natural isomorphisms $(\psi_i)_*\mathcal{O}_{X_i}\cong \mathcal{O}_X\vert_{\psi_i(X_i)}$, and this produces our desired ringed space $(X,\mathcal{O}_X)$ which is locally determined by the $X_i$ which embed into $X$ via open immersions, so by the work in [[Basic Properties of Morphisms of Schemes]] we have that if the $X_i$ are locally ringed spaces or schemes, so is $X$ and the embeddings are maps of locally ringed spaces.
`\end{proof}`




#### References