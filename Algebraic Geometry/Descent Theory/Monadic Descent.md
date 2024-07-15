---
date: 2024-07-07T22:42:00
tags:
  - AlgebraicGeometry
  - CategoryTheory
  - Descent
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
In these notes we study the notion of descent, as envisioned originally by Grothendieck, through the lens of monadic descent. These notes follows the articles[^1] and[^2] by Janelidze and Tholen.

Descent theory was originally developed by Grothendieck in the context of fibered categories (e.g. see [[Basic Fibered Categories]]). As motivation consider the case of bundles over a base space $B$, i.e. consider elements of the slice category $\mathsf{Top}/B$. As in the case of sheaves, are we able to recover a space $\alpha:A\to B$ over $B$ from the data of an open cover $(U_i)_{i\in I}$ of $B$ and spaces $\gamma_i:E_i\to U_i$ over each $U_i$, analogously to the sheaf condition? Note that in this context we want to consider a diagram of functors
$$\mathsf{Top}/B\to \prod_{i \in I}\mathsf{Top}/U_i\rightrightarrows \prod_{i,j\in I}\mathsf{Top}/(U_i\cap U_j)$$
where the maps are given by pullbacks along $U_i\to B$ in the first case, and either $U_i\cap U_j\to U_i$ or $U_i\cap U_j\to U_j$ in the second (depending on if its the top or bottom map). **WARNING**: since pullbacks are only determined up to unique isomorphism, we must be careful about what it means for this diagram to be commutative. For example, when given our space $\gamma_i:E_i\to U_i$ from which we want to build $\alpha:A\to B$, whose pullbacks along the $U_i\hookrightarrow B$ give $\gamma_i:E_i\to U_i$, we should also provide isomorphisms $\xi_{i,j}:\gamma_i^{-1}(U_i\cap U_j)\to \gamma_j^{-1}(U_i\cap U_j)$ between the pullback data such that $\xi_{i,i} = \text{id}_{E_i}$ and the **1-cocycle condition**
$$\xi_{j,k}^i\xi_{i,j}^k=\xi_{i,k}^j$$
where $\xi_{i,j}^k:\gamma_i^{-1}(U_i\cap U_j\cap U_k)\to \gamma_j^{-1}(U_i\cap U_j\cap U_k)$ is the pullback

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cgamma_i%5E%7B-1%7D(U_i%5Ccap%20U_j%5Ccap%20U_k)%7D%20%26%26%20%7B%5Cgamma_j%5E%7B-1%7D(U_i%5Ccap%20U_j%5Ccap%20U_k)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cgamma_i%5E%7B-1%7D(U_i%5Ccap%20U_j)%7D%20%26%26%20%7B%5Cgamma_j%5E%7B-1%7D(U_i%5Ccap%20U_j)%7D%0A%09%5Carrow%5B%22%7B%5Cxi_%7Bi%2Cj%7D%5Ek%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cxi_%7Bi%2Cj%7D%7D%22%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\gamma_i^{-1}(U_i\cap U_j\cap U_k)} &amp;&amp; {\gamma_j^{-1}(U_i\cap U_j\cap U_k)} \\
	\\
	{\gamma_i^{-1}(U_i\cap U_j)} &amp;&amp; {\gamma_j^{-1}(U_i\cap U_j)}
	\arrow[&quot;{\xi_{i,j}^k}&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=3-3]
	\arrow[hook, from=1-3, to=3-3]
	\arrow[&quot;{\xi_{i,j}}&quot;, from=3-1, to=3-3]
\end{tikzcd}
" /></p>

We call such a system of homeomorphisms a **descent data** which is carried with the family $(\gamma_i:E_i\to U_i)_{i \in I}$. As we will soon show, descent theory gives a new perspective on the idea of localization through the theory of monads.

Let us begin hinting at this perspective. Consider the induced map $p:E\to B$ where $E = \coprod_{i \in I}U_i$. Note that a map $f:X\to E$ can be equivalently characterized as a family of maps $f_i:f^{-1}(U_i)\to U_i$, due to the gluing of continuous maps. This implies that we have an isomorphism of categories
$$\prod_{i \in I}\mathsf{Top}/U_i\cong \mathsf{Top}/E$$
We then have a pullback functor $p^*:\mathsf{Top}/B\to \mathsf{Top}/E$, and in this context descent theory asks whether $\mathsf{Top}/B$ can be presented algebraically in terms of objects of $\mathsf{Top}/E$. More precisely, this is asking whether $p^*$ is monadic, which says that $p^*$ has a left adjoint, $p_*\dashv p^*$, such that the $\mathsf{Top}/B$ is isomorphic to the category of Eilenberg-Moore algebraic for the monad $p^*\circ p_*$ on $\mathsf{Top}/E$. Descent data in this context represents algebraic structures, while the **1-cocycle condition** becomes an associative law.

## Topological Descent Theory

Throughout let $B$ be a fixed topological base space and let $\mathbb{E}$ denote a class of continuous functions closed under composition by homeomorphisms. Let $\mathbb{E}(B)$ be the full subcategory of $\mathsf{Top}/B$ whose objects belong to $\mathbb{E}$ (e.g. consider the small etale site). We want to now consider conditions on a space $E$ over $B$ where the category of $\mathbb{E}$-bundles over $B$ is equivalent to the category of $\mathbb{E}$-bundles over $E$ together with certain algebraic data.

Let $p:E\to B$ be a continuous map and consider an $\mathbb{E}$-bundle $\gamma:C\to E$. Consider the fiber product $E\times_BC$. For each $x,y \in E$ which the bundle morphism $p$ identifies, i.e. for which $p(x)=p(y)$, we have a natural embedding
$$j_{x,y}:\gamma^{-1}(y)\hookrightarrow E\times_BC$$
sending $c\mapsto (x,c)$, so $E\times_BC = \bigcup_{x,y \in E}j_{x,y}(\gamma^{-1}(y))$.

>[!def] Descent Data for a Topological Bundle
>**Descent data** for $\gamma:C\to E$ relative to $p:E\to B$ are given by a family of maps
>$$\xi_{x,y}:\gamma^{-1}(x)\to \gamma^{-1}(y),\;\;x,y \in E,\;\;p(x)=p(y)$$
>such that $\xi:E\to \mathsf{Top}$ defines a functor, where $E$ is considered as a category with a unique map between each point (this is called the **functriality condition**), and the **gluing condition** which states that $E\times_BC\cong \text{colim}_{x \in E}\gamma^{-1}x$ with connecting maps the $\xi_{x,y}$, and that the unique map $\overline{\xi}$ induced by the diagrams
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cgamma%5E%7B-1%7D(x)%7D%20%26%26%20%7B%5Cgamma%5E%7B-1%7D(y)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7BE%5Ctimes_BC%7D%20%26%26%20%7BE%5Ctimes_BC%7D%0A%09%5Carrow%5B%22%7B%5Cxi_%7Bx%2Cy%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bj_%7By%2Cx%7D%7D%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bj_%7Bx%2Cy%7D%7D%22%2C%20hook%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Coverline%7B%5Cxi%7D%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\gamma^{-1}(x)} &amp;&amp; {\gamma^{-1}(y)} \\	\\	{E\times_BC} &amp;&amp; {E\times_BC}	\arrow[&quot;{\xi_{x,y}}&quot;, from=1-1, to=1-3]	\arrow[&quot;{j_{y,x}}&quot;', hook, from=1-1, to=3-1]	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=3-3]	\arrow[&quot;{j_{x,y}}&quot;, hook, from=1-3, to=3-3]	\arrow[&quot;{\overline{\xi}}&quot;', from=3-1, to=3-3]\end{tikzcd}" /></p>
>
>is continuous, where explicitly $\overline{\xi}(y,c) = (x,\xi_{x,y}(c))$ with $x = \gamma(c)$.

If $\mathbb{E}$ is stable under pullback along $p:E\to B$, then every $\mathbb{E}$-bundle $\alpha:A\to B$ induces a $\mathbb{E}$-bundle $p^*\alpha:E\times_BA\to E$. In this case $p^*\alpha$ comes naturally equipped with descent data
$$\varphi_{x,y}:\pi_1^{-1}(x)\to \pi_1^{-1}(y)$$
given by $(x,a)\mapsto (y,a)$, and so we have $\overline{\varphi}:E\times_B(E\times_BA)\to E\times_B(E\times_BA)$ which is the involution $(y,(x,a))\mapsto (x,(y,a))$.**TBC**

#### References

[^1]: Janelidze, G., & Tholen, W. (1994). Facets of descent, I. Applied Categorical Structures, 2(3), 245–281. https://doi.org/10.1007/BF00878100
[^2]: Janelidze, G., & Tholen, W. (1997). Facets of Descent, II. Applied Categorical Structures, 5(3), 229–248. https://doi.org/10.1023/A:1008697013769
