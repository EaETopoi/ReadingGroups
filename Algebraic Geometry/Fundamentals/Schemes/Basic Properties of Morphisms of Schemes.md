---
date: 2024-05-24T07:35:00
tags:
  - AlgebraicGeometry
  - Sheaves
  - Schemes
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

In this note we recall a number of basic types of morphisms of schemes and their properties following the work of Vakil[^1].

## Maps of Ringed Spaces

Recall that a **ringed space** is a pair $(X,\mathcal{O}_X)$ of a topological space $X$ and a sheaf of rings on $X$. 

>[!def] Morphism of Ringed Spaces
>A morphism of ringed spaces $(X,\mathcal{O}_X)\to (Y,\mathcal{O}_Y)$ is a pair $(f,f^\#)$ where $f:X\to Y$ is a continuous map and  $$f^\#:\mathcal{O}_Y\to f_*\mathcal{O}_X$$
>is a map of sheaves on $Y$. By [[Important Adjunctions for Sheaves#^48a080]], $f^\#$ is equivalent to a map of sheaves on $X$ $$f^\flat:f^*\mathcal{O}_Y\to \mathcal{O}_X$$

A natural first kind of ringed space morphism is given by looking at immersions of subspaces.

>[!def] Open Immersion
>A map of ringed spaces $(f,f^\#):(X,\mathcal{O}_X)\to (Y,\mathcal{O}_Y)$ is an **open immersion** if $f:X\to Y$ is a homeomorphism onto an open subset $V$ of $Y$, and restricting to this subset induces an isomorphism $(f,f^\#):(X,\mathcal{O}_X)\xrightarrow{\cong}(V,\mathcal{O}_Y\vert_V)$.

Before continuing with morphisms of ringed spaces we show that we can glue morphisms up from an open cover.

>[!proposition] Gluing of Ringed Space Morphisms
>Let $(X,\mathcal{O}_X)$ be a ringed space and let $X = \bigcup_{i \in I}U_i$ be an open cover of $X$. For each $i \in I$ let $\pi_i:(U_i,\mathcal{O}_X\vert_{U_i})\to (Y,\mathcal{O}_Y)$ be a morphism of ringed spaces such that $\pi_i\vert_{U_i\cap U_j} = \pi_j\vert_{U_i\cap U_j}$ on topological spaces and $$(\pi_i)_*\iota_{U_i\cap U_j}^\#\circ \pi_i^\# = (\pi_j)_*\iota_{U_i\cap U_j}^\#\circ \pi_j^\#:\mathcal{O}_Y\to (\pi_i)_*(\iota_{U_i\cap U_j})_*(\mathcal{O}_X\vert_{U_i\cap U_j})$$
> Then there exists a unique morphism of ringed spaces $\pi:(X,\mathcal{O}_X)\to (Y,\mathcal{O}_Y)$ such that $\pi\vert_{U_i} = \pi_i$. 

^885e6a

`\begin{proof}`
On topological spaces let $\pi:X\to Y$ be given by $\pi(x) = \pi_i(x)$ if $x \in U_i$. This is well-defined since the maps agree on overlaps and the $U_i$ cover $X$. Since $X$ is open it follows that $\pi$ is continuous. 

Next, to define $\pi^\#:\mathcal{O}_Y\to \pi_*\mathcal{O}_X$, let $U \subseteq X$ be open. Then we have an open cover $U = \bigcup_{i \in I}(U\cap U_i)$, and as $\mathcal{O}_X$ is a sheaf we also have a corresponding equalizer diagram
$$\mathcal{O}_X(U)\to \prod_{i \in I}\mathcal{O}_X(U\cap U_i)\rightrightarrows \prod_{i,j \in I}\mathcal{O}_X(U\cap U_i\cap U_j)$$
The $(\pi_i^\#)_{V}:\mathcal{O}_Y(V)\to \mathcal{O}_X(f^{-1}(V)\cap U_i)$ for $V$ open in $Y$ then give a product map which induces a unique map $(\pi^\#)_V:\mathcal{O}_Y(V)\to \mathcal{O}_X(f^{-1}(V)\cap U_i)$ from the equalizer diagram. By uniqueness and the fact that the $\pi_i^\#$ are maps of sheaves we have that $\pi^\#$ is also a map of sheaves. 
`\end{proof}`
Note that any property which can be defined locally will be preserved by this construction. For example if we were working with the subcategory of locally ringed spaces or that of schemes. Recall that a morphism of either of these structures is defined as follows:

>[!def] Morphism of Locally Ringed Spaces
>If $(X,\mathcal{O}_X),(Y,\mathcal{O}_Y)$ are locally ringed spaces, a morphism of **locally ringed spaces** between them is a morphism of ringed spaces $(f,f^\#):(X,\mathcal{O}_X)\to (Y,\mathcal{O}_Y)$ such that for every point $x \in X$, the induced map on stalks $$\mathcal{O}_{Y,f(x)}\xrightarrow{f^\#_x}(f_*\mathcal{O}_X)_{f(x)}\to \mathcal{O}_{X,x}$$
>is a map of local rings, which is to say that the image of $\mathfrak{m}_{Y,f(x)}$ under the composite is contained in $\mathfrak{m}_{X,x}$. (equivalently, the pre-image of $\mathfrak{m}_{X,x}$ is $\mathfrak{m}_{Y,f(x)}$)

^203ccf

Intuitively, [[Basic Properties of Morphisms of Schemes#^203ccf]]
 says that if $p$ maps to $q$, and $g$ is a function vanishing at $q$, then when we pull it back we should obtain a function vanishing at $p$. The converse is also true since we are dealing with maximal ideals (i.e. if $g$ is a function not-vanishing at $q$, then when we pull it back we should obtain a function not-vanishing at $p$).

Recall that a scheme is a locally ringed space $(X,\mathcal{O}_X)$ which locally looks like an affine scheme. Thus, to understand morphisms of schemes it is important to understand first morphisms of affine schemes.

>[!theorem] Spec-Global Sections Adjunction
>The global sections functor, $\Gamma:\mathsf{LRSpace}\to \mathsf{CRing}^{op}$ is left adjoint to the $\mathsf{Spec}$ functor, $\mathsf{Spec}:\mathsf{CRing}^{op}\to \mathsf{LRSpace}$.

^3c5807

`\begin{proof}`
To show that $\Gamma \dashv \mathsf{Spec}$, we provide an isomorphism
$$\mathsf{CRing}(A,\Gamma(X,\mathcal{O}_X))\mathrel{\mathop{\rightleftarrows}^{(-)^\flat}_{(-)^\#}} \mathsf{LRSpace}((X,\mathcal{O}_X),(\mathsf{Spec}(A),\mathcal{O}_{\mathsf{Spec}(A)}))$$
for any cring $A$ and locally ringed space $(X,\mathcal{O}_X)$, such that the isomorphism satisfies additional naturality conditions. One direction is given by sending a map of locally ringed spaces $(\varphi,\varphi^\#):(X,\mathcal{O}_X)\to(\mathsf{Spec}(A),\mathcal{O}_{\mathsf{Spec}(A)})$ to its global sections, $(\varphi,\varphi^\#)^\# := \Gamma(\varphi,\varphi^\#):A\to \mathcal{O}_X(X) = \Gamma(X,\mathcal{O}_X)$.

For the other direction, it is sufficient to show that for any cring $A$ and any locally ringed space $(X,\mathcal{O}_X)$, if $f:A\to \Gamma(X,\mathcal{O}_X)$ is a map of crings, there exists a unique map of locally ringed spaces $f^\flat := (\varphi,\varphi^\#):(X,\mathcal{O}_X)\to (\mathsf{Spec}(A),\mathcal{O}_{\mathsf{Spec}(A)})$ making the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09A%20%26%20%7B%5CGamma(%5Cmathsf%7BSpec%7D(A)%2C%5Cmathcal%7BO%7D_%7B%5Cmathsf%7BSpec%7D(A)%7D)%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7B%5CGamma(X%2C%5Cmathcal%7BO%7D_X)%7D%0A%20%20%20%20%09%5Carrow%5B%22%7B1_A%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5CGamma(%5Cvarphi%2C%5Cvarphi%5E%5C%23)%7D%22%2C%20dashed%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	A &amp; {\Gamma(\mathsf{Spec}(A),\mathcal{O}_{\mathsf{Spec}(A)})} \\
    	&amp; {\Gamma(X,\mathcal{O}_X)}
    	\arrow[&quot;{1_A}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;f&quot;', from=1-1, to=2-2]
    	\arrow[&quot;{\Gamma(\varphi,\varphi^\#)}&quot;, dashed, from=1-2, to=2-2]
    \end{tikzcd}
" /></p>
commute. To this effect let $f:A\to \Gamma(X,\mathcal{O}_X)$ be such a map of crings. If $x \in X$, let $\mathfrak{m}_x$ denote the unique maximal ideal in the local ring $\mathcal{O}_{X,x}$, and let $\kappa(x)$ denote its residue field. Let $\lambda_{U,x}:\mathcal{O}_X(U)\to \mathcal{O}_{X,x}$ denote the localization map for $U \subseteq X$ open. Then $(\lambda_{X,x}\circ f)^{-1}(\mathfrak{m}_x)$ is prime, and we have an induced map on localizations making the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09A%20%26%20%7B%5Cmathcal%7BO%7D_X(X)%7D%20%5C%5C%0A%20%20%20%20%09%7BA_%7Bf%5E%7B-1%7D(%5Cmathfrak%7Bm%7D_x)%7D%7D%20%26%20%7B%5Cmathcal%7BO%7D_%7BX%2Cx%7D%7D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_%7BX%2Cx%7D%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_%7Bf%5E%7B-1%7D(%5Cmathfrak%7Bm%7D_x)%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5Bdashed%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	A &amp; {\mathcal{O}_X(X)} \\
    	{A_{f^{-1}(\mathfrak{m}_x)}} &amp; {\mathcal{O}_{X,x}}
    	\arrow[&quot;f&quot;, from=1-1, to=1-2]
    	\arrow[&quot;{\lambda_{X,x}}&quot;, from=1-2, to=2-2]
    	\arrow[&quot;{\lambda_{f^{-1}(\mathfrak{m}_x)}}&quot;', from=1-1, to=2-1]
    	\arrow[dashed, from=2-1, to=2-2]
    \end{tikzcd}
" /></p>
commute. Define a map of topological spaces $\varphi:X\to \mathsf{Spec}(A)$ by $\varphi(x) = (\lambda_{X,x}\circ f)^{-1}(\mathfrak{m}_x)$. To show that $\varphi$ is continuous we can show it for basic open sets. Then if $D_a \subseteq \mathsf{Spec}(A)$ is a basic open for $a \in A$, then
$$
\begin{align*}
	\varphi^{-1}(D_a) = \{x \in X:a \notin (\lambda_{X,x}\circ f)^{-1}(\mathfrak{m}_x)\} = \{x \in X:\lambda_{X,x}(f(a)) \notin \mathfrak{m}_x\} 
\end{align*}
$$
Let $x \in \varphi^{-1}(D_a)$. Since $\mathcal{O}_{X,x}$ is a local ring, $\lambda_{X,x}(f(a)) \notin \mathfrak{m}_x$ implies that $\lambda_{X,x}(f(a))$ is a unit in $\mathcal{O}_{X,x}$. Let $k \in \mathcal{O}_{X,x}$ be its inverse. Then by definition of the stalk there exists an open neighborhood $V$ of $x$ and $k' \in \mathcal{O}_X(V)$ such that $\lambda_{V,x}(k') = k$. It follows that $\lambda_{V,x}(\text{res}_{X,V}(f(a))k') = 1$ in $\mathcal{O}_{X,x}$, where $\text{res}_{X,V}(f(a)) \in \mathcal{O}_X(V)$ is the restriction of $f(a)$. Again by the definition of the stalk there exists an open set $W \subseteq V$ containing $x$ such that $\text{res}_{V,W}(\text{res}_{X,V}(f(a))k')= 1$ in $\mathcal{O}_X(W)$. In particular, this implies that for every $y \in W$, $\lambda_{W,y}(\text{res}_{V,W}(\text{res}_{X,V}(f(a))k')) = 1$ in $\mathcal{O}_{X,y}$, so $\lambda_{W,y}(\text{res}_{X,W}(f(a))) = \lambda_{X,y}(f(a)) \notin \mathfrak{m}_y$. Thus, we have that 
$$x \in W \subseteq \varphi^{-1}(D_a)$$
where $W \subseteq X$ is open. As $x \in \varphi^{-1}(D_a)$ was arbitrary, it follows that $\varphi^{-1}(D_a)$ is open in $X$, so $\varphi$ is indeed a continuous map.

Next, we can define a map of sheaves $\varphi^\#:\mathcal{O}_{\mathsf{Spec}(A)}\to \varphi_*\mathcal{O}_X$ by defining it on basic open sets, which suffices by [[Basic Properties of Morphisms of Schemes#^885e6a]]. To this effect let $a\in A$, so we want to define a map $\varphi^\#_{D_a}:A_a\to \mathcal{O}_X(\varphi^{-1}(D_a))$. But by construction of $\varphi$,
$$\varphi^{-1}(D_a) = \{x \in X:\lambda_{X,x}(f(a)) \notin \mathfrak{m}_x\} $$
so by definition of the stalk, for every $y \in \varphi^{-1}(D_a)$ there exists an open set $V_y \subseteq \varphi^{-1}(D_a)$ containing $y$ such that $\text{res}_{X,V_y}(f(a))$ has a (necessarily unique) inverse $g_y \in \mathcal{O}_X(V_y)$. Further, if $y,z \in \varphi^{-1}(D_a)$ such that $V_y\cap V_z \neq \emptyset$, then $\text{res}_{V_y,V_y\cap V_z}(g_y) = \text{res}_{V_z,V_y\cap V_z}(g_z)$ since both elements will be inverses of $\text{res}_{X,V_y\cap V_z}(f(a))$ because restriction is a cring homomorphism and inverses in crings are unique. Thus, since $\mathcal{O}_X$ is a sheaf and $\varphi^{-1}(D_a) = \bigcup_{y \in \varphi^{-1}(D_a)}V_y$, there exists a unique $g \in \mathcal{O}_X(\varphi^{-1}(D_a))$ such that for every $y \in \varphi^{-1}(D_a)$, $\text{res}_{\varphi^{-1}(D_a),V_y}(g) = g_y$. Additionally, for every such $y$
$$\text{res}_{\varphi^{-1}(D_a),V_y}(\text{res}_{X,\varphi^{-1}(D_a)}(f(a))\cdot g) = \text{res}_{X,V_y}(f(a))\cdot g_y = 1$$
by construction of the $g_y$, so uniqueness from the sheaf axiom implies that $\text{res}_{X,\varphi^{-1}(D_a)}(f(a))\cdot g = 1$. Therefore, $\text{res}_{X,\varphi^{-1}(D_a)}(f(a)) \in \mathcal{O}_X(\varphi^{-1}(D_a))$ is invertible, so by the universal property of the localization we can define $\varphi^\#_{D_a}$ to be the unique map making the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09A%20%26%20%7B%5Cmathcal%7BO%7D_X(X)%7D%20%5C%5C%0A%20%20%20%20%09%7BA_a%7D%20%26%20%7B%5Cmathcal%7BO%7D_X(%5Cvarphi%5E%7B-1%7D(D_a))%7D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7BX%2C%5Cvarphi%5E%7B-1%7D(D_a)%7D%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_a%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cvarphi%5E%5C%23_%7BD_a%7D%7D%22'%2C%20dashed%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	A &amp; {\mathcal{O}_X(X)} \\
    	{A_a} &amp; {\mathcal{O}_X(\varphi^{-1}(D_a))}
    	\arrow[&quot;f&quot;, from=1-1, to=1-2]
    	\arrow[&quot;{\text{res}_{X,\varphi^{-1}(D_a)}}&quot;, from=1-2, to=2-2]
    	\arrow[&quot;{\lambda_a}&quot;', from=1-1, to=2-1]
    	\arrow[&quot;{\varphi^\#_{D_a}}&quot;', dashed, from=2-1, to=2-2]
    \end{tikzcd}
" /></p>
commute.

To show this defines a map of sheaves, consider basic opens $D_a \subseteq D_b$. Recall from Problem 1 this is equivalent to $b/1$ being invertible in $A_a$, so we have a unique map $\lambda_{b,a}:A_b\to A_a$. Then consider the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09A%20%26%20%7B%5Cmathcal%7BO%7D_X(X)%7D%20%26%20%7B%5Cmathcal%7BO%7D_X(%5Cvarphi%5E%7B-1%7D(D_b))%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7BA_b%7D%20%5C%5C%0A%20%20%20%20%09%7BA_a%7D%20%26%26%20%7B%5Cmathcal%7BO%7D_X(%5Cvarphi%5E%7B-1%7D(D_a))%7D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7BX%2C%5Cvarphi%5E%7B-1%7D(D_b)%7D%7D%22%2C%20yshift%3D5pt%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_b%7D%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cvarphi%5E%5C%23_%7BD_b%7D%7D%22'%2C%20dashed%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cvarphi%5E%5C%23_%7BD_a%7D%7D%22'%2C%20dashed%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7B%5Cvarphi%5E%7B-1%7D(D_b)%2C%5Cvarphi%5E%7B-1%7D(D_a)%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_%7Bb%2Ca%7D%7D%22'%2C%20dashed%2C%20from%3D2-2%2C%20to%3D3-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_a%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	A &amp; {\mathcal{O}_X(X)} &amp; {\mathcal{O}_X(\varphi^{-1}(D_b))} \\
    	&amp; {A_b} \\
    	{A_a} &amp;&amp; {\mathcal{O}_X(\varphi^{-1}(D_a))}
    	\arrow[&quot;f&quot;, from=1-1, to=1-2]
    	\arrow[&quot;{\text{res}_{X,\varphi^{-1}(D_b)}}&quot;, yshift=5pt, from=1-2, to=1-3]
    	\arrow[&quot;{\lambda_b}&quot;', from=1-1, to=2-2]
    	\arrow[&quot;{\varphi^\#_{D_b}}&quot;', dashed, from=2-2, to=1-3]
    	\arrow[&quot;{\varphi^\#_{D_a}}&quot;', dashed, from=3-1, to=3-3]
    	\arrow[&quot;{\text{res}_{\varphi^{-1}(D_b),\varphi^{-1}(D_a)}}&quot;, from=1-3, to=3-3]
    	\arrow[&quot;{\lambda_{b,a}}&quot;', dashed, from=2-2, to=3-1]
    	\arrow[&quot;{\lambda_a}&quot;', from=1-1, to=3-1]
    \end{tikzcd}
" /></p>
We need to show commutivity of the bottom right square. The left triangle commutes by the universal property of localization and the top triangle commutes by definition of $\varphi^\#_{D_b}$. Additionally, the outer square commutes by the definition of $\varphi^\#_{D_a}$ since restrictions compose functorially. Then we have that
$$\varphi^\#_{D_a}\circ \lambda_{b,a}\circ \lambda_b = \varphi^\#_{D_a}\circ\lambda_a = \text{res}_{\varphi^{-1}(D_b),\varphi^{-1}(D_a)}\circ \text{res}_{X,\varphi^{-1}(D_b)}\circ f = \text{res}_{\varphi^{-1}(D_b),\varphi^{-1}(D_a)}\circ \varphi^\#_{D_b}\circ \lambda_b$$
But then by the universal property of the localization $A_b$ we must have that
$$\varphi^\#_{D_a}\circ \lambda_{b,a} = \text{res}_{\varphi^{-1}(D_b),\varphi^{-1}(D_a)}\circ \varphi^\#_{D_b}$$
so the bottom right square commutes. Therefore $\varphi^\#$ is a map of sheaves. and by construction $\Gamma(\varphi,\varphi^\#) = \varphi^\#_{\mathsf{Spec}(A)} = f$. Additionally, since the maps on stalks were induced by the universal property of the localization, $(\varphi,\varphi^\#)$ is a map of locally ringed spaces.

To show uniqueness suppose $(\psi,\psi^\#):(X,\mathcal{O}_X)\to (\mathsf{Spec}(A),\mathcal{O}_{\mathsf{Spec}(A)})$ is another map of locally ringed spaces such that $\psi^\#_{\mathsf{Spec}(A)} = f:A\to \mathcal{O}_X(X)$. Then $\psi^\#$ induces a map on the level of stalks making the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09A%20%26%20%7B%5Cmathcal%7BO%7D_X(X)%7D%20%5C%5C%0A%20%20%20%20%09%7BA_%7B%5Cpsi(x)%7D%7D%20%26%20(%5Cpsi_*%5Cmathcal%7BO%7D_X)_%7B%5Cpsi(x)%7D%20%26%20%7B%5Cmathcal%7BO%7D_%7BX%2Cx%7D%7D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_%7BX%2Cx%7D%7D%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Clambda_%7B%5Cpsi(x)%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20%5Carrow%5B%22%7B%5Crho_%7BX%2C%5Cpsi(x)%7D%7D%22'%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Cpsi_%7B%5Cpsi(x)%7D%5E%5C%23%22'%2C%20dashed%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20%5Carrow%5B%22%5Cwidetilde%7B%5Cpsi%7D_%7B%5Cpsi(x)%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	A &amp; {\mathcal{O}_X(X)} \\
    	{A_{\psi(x)}} &amp; (\psi_*\mathcal{O}_X)_{\psi(x)} &amp; {\mathcal{O}_{X,x}}
    	\arrow[&quot;f&quot;, from=1-1, to=1-2]
    	\arrow[&quot;{\lambda_{X,x}}&quot;, from=1-2, to=2-3]
    	\arrow[&quot;{\lambda_{\psi(x)}}&quot;', from=1-1, to=2-1]
            \arrow[&quot;{\rho_{X,\psi(x)}}&quot;', from=1-2, to=2-2]
    	\arrow[&quot;\psi_{\psi(x)}^\#&quot;', dashed, from=2-1, to=2-2]
            \arrow[&quot;\widetilde{\psi}_{\psi(x)}&quot;', from=2-2, to=2-3]
    \end{tikzcd}
" /></p>
commute. But since $(\psi,\psi^\#)$ is a map of locally ringed spaces, $\widetilde{\psi}_{\psi(x)}\circ \psi_{\psi(x)}^\#$ is a map of local rings, so $(\widetilde{\psi}_{\psi(x)}\circ \psi_{\psi(x)}^\#)^{-1}(\mathfrak{m}_x) = \psi(x)A_{\psi(x)}$, the unique maximal ideal of $A_{\psi(x)}$. Using the correspondence for prime ideals in localizations we have that the pre-image of $\psi(x)A_{\psi(x)}$ in $A$ is $\psi(x)$. Since the square commutes this must be $(\lambda_{X,x}\circ f)^{-1}(\mathfrak{m}_x)$, so $\psi(x) = \varphi(x)$. Thus $\varphi = \psi$. But then from our construction we showed that $\varphi^\#$ on basic open sets is uniquely determined by the universal property of the localizations for $f$ given that $\varphi$ is defined as taking the pre-image under $\lambda_{X,x}\circ f$, so $\varphi^\#$ and $\psi^\#$ must agree on basic opens. By [[Basic Properties of Morphisms of Schemes#^885e6a]] it follows that $\varphi^\#=\psi^\#$, so we have uniqueness.

This concludes the proof of the isomorphism. For naturality we observe that if we have locally ringed space maps $h:(X,\mathcal{O}_X)\to (Y,\mathcal{O}_Y)$ and $g:(Y,\mathcal{O}_Y)\to (\mathsf{Spec}(A),\mathcal{O}_{\mathsf{Spec}(A)})$, as well as a ring map $k:B\to A$, then
$$(\mathsf{Spec}(k)\circ g\circ h)^\# = k\circ \Gamma(g)\circ \Gamma(h) = k\circ g^\#\circ \Gamma(h)$$
using the definition of $(-)^\#$ and the fact that $\Gamma$ is functorial. On the other hand, if we have a map of locally ringed spaces $h:(X,\mathcal{O}_X)\to (Y,\mathcal{O}_Y)$ as well as maps of crings $f:A\to \Gamma(Y,\mathcal{O}_Y)$ and $k:B\to A$, then
$$(\Gamma(h)\circ f\circ k)^\flat = \mathsf{Spec}(k)\circ f^\flat \circ h$$
by uniqueness of our map since the global map on sheaves for $\mathsf{Spec}(k)\circ f^\flat \circ h$ is exactly $\Gamma(h)\circ f\circ k$ by construction of $\flat$ and functoriality of $\Gamma$. This is the naturality part of the adjunction, completing the proof.
`\end{proof}`

As a simple corollary we obtain the fact that the spec functor is fully faithful, and so ring homomorphisms fully describe morphisms of schemes between affine schemes.

>[!corollary] Fully-Faithful $\mathsf{Spec}$
>The $\mathsf{Spec}$ functor is fully-faithful.

^930486

`\begin{proof}`
Note that for any $A \in \mathsf{CRing}$ we have $\Gamma\circ \mathsf{Spec}(A) = A$, and for any morphism $f:A\to B$ in $\mathsf{Cring}$, $\Gamma\circ \mathsf{Spec}(f) = f$, by construction of $\mathsf{Spec}(f)$ on basic opens. Hence $\Gamma\circ \mathsf{Spec} = 1_{\mathsf{CRing}}$, so $\mathsf{Spec}$ has a left inverse. This implies that $\mathsf{Spec}$ is faithful, since if $f,g$ are arrows in $\mathsf{CRing}$ for which $\mathsf{Spec}(f) = \mathsf{Spec}(g)$, then $f = \Gamma(\mathsf{Spec}(f)) = \Gamma(\mathsf{Spec}(g)) = g$.

It remains to show that $\mathsf{Spec}$ is full. To this end let $A,B \in \mathsf{CRing}$, and let $(\varphi,\varphi^\#):(\mathsf{Spec}(A),\mathcal{O}_{\mathsf{Spec}(A)})\to (\mathsf{Spec}(B),\mathcal{O}_{\mathsf{Spec}(B)})$ be a map of locally ringed spaces. Let $f = (\varphi,\varphi^\#)^\#:B\to A$ be the associated map on global sections under the adjunction. Then since the adjunction is an isomorphism, $f^\flat= ((\varphi,\varphi^\#)^\#)^\flat= (\varphi,\varphi^\#)$. But by the construction of $f^\flat$ in [[Basic Properties of Morphisms of Schemes#^3c5807]] we have $\varphi = \mathsf{Spec}(f)$ as maps of topological spaces. Additionally, on basic opens $D_b \subseteq \mathsf{Spec}(B)$ for $b \in B$, $\varphi^\#_{D_b}$ must be given by the unique map $B_b\to A_{f(b)}$ induced by the universal property of the localization. But this is precisely the definition of $\mathsf{Spec}(f)^\#$ on basic opens, so $\mathsf{Spec}(f)^\#$ and $\varphi^\#$ agree on basic open sets. By [[Basic Properties of Morphisms of Schemes#^885e6a]], it follows that $(\mathsf{Spec}(f),\mathsf{Spec}(f)^\#) = (\varphi,\varphi^\#)$, so $\mathsf{Spec}$ is also full as a functor into $\mathsf{LRSpace}$, completing the proof.
`\end{proof}`
[[Basic Properties of Morphisms of Schemes#^930486]] and the local definition of morphisms of locally ringed spaces implies that we could equivalently define morphisms of schemes to be morphisms of ringed spaces that restrict to morphisms of affine schemes locally, which is to say morphisms induced by ring maps.

>[!example] Morphism into Projective Space
>Let $R$ be a cring. Let $X$ be the basic open subscheme of $\mathbb{A}^{n+1}_R$ with complement $\{\langle x_0,...,x_n\rangle\}$,  so explicitly $X = \bigcup_{i=0}^nD(x_i)$. On the other hand, recall that $\mathbb{P}_R^{n+1}$ can be given by an open cover $U_i \cong \mathsf{Spec}(R[x_0/x_i,...,\hat{x}_i,...,x_n/x_i])$ for $0 \leq i \leq n$, with gluing isomorphisms $\mathsf{Spec}(R[x_0/x_i,...,\hat{x}_i,...,x_n/x_i]_{x_j})\to \mathsf{Spec}(R[x_0/x_j,...,\hat{x}_j,...,x_n/x_j]_{x_i})$  given in the opposite direction on the level of rings by mapping $x_k/x_j \mapsto (x_k/x_i)/(x_j/x_i)$ for $k \neq i,j$ and $x_i \mapsto 1/x_j$. Note that these maps specify $\mathbb{P}_R^{n+1}$ up to unique isomorphism by [[Sheaf on a Base and Gluing Sheaves#^afca9a]]. 
>
>We define a map $X\to \mathbb{P}_R^{n+1}$ by taking maps on the open cover $D(x_i)$ of $X$ given by $$\varphi_i:D(x_i) = \mathsf{Spec}(R[x_0,...,x_n]_{x_i})\to \mathsf{Spec}(R[x_0 / x_i,\dots,\hat{x}_i, \dots, x_n / x_i]) \cong U_i\hookrightarrow \mathbb{P}_R^{n+1}$$
>where the first map is simply given by mapping $x_j / x_i$ to $x_j/x_i$ on the level of crings (and hence in the opposite direction). In order to apply [[Basic Properties of Morphisms of Schemes#^885e6a]] we need to show that these maps are compatible on intersections. Note that intersections of affine opens inside an affine scheme, when viewed in CRing, are given by pushouts. Recall that for a ring $A$, if $f,g \in A$, $A_f\otimes_AA_g \cong (A_g)_f \cong A_{gf}$, and so $D(x_i)\cap D(x_j)\cong \mathsf{Spec}(R[x_0,...,x_n]_{x_ix_j})$. Note that $\varphi_i\vert_{D(x_i)\cap D(x_j)}$ factors the the inclusion $U_i\cap U_j\hookrightarrow \mathbb{P}_R^{n+1}$. Then on the level of rings $\varphi_i\vert_{D(x_i)\cap D(x_j)}$ and $\varphi_j\vert_{D(x_i)\cap D(x_j)}$ are both given by identities and localizations, which commute with the gluing isomorphism. Thus, we obtain a morphism of schemes
>$$\varphi:\mathbb{A}^{n+1}_R\to \mathbb{P}_R^n$$
>from this gluing data.

### Special Morphisms out of Affine Schemes

The adjunction described in [[Basic Properties of Morphisms of Schemes#^3c5807]] implies that morphisms into affine schemes are simple to describe: A morphism of schemes  $X\to \mathsf{Spec}(A)$ is equivalent to a morphism of rings $A \to \Gamma(\mathcal{O}_X;X)$. On the other hand morphisms out of affine schemes can be more complicated, but there are a few special cases.

>[!example] Morphism out of a Stalk
>Let $(X,\mathcal{O}_X)$ be a scheme with point $p$. By definition of the stalk $\mathcal{O}_{X,p}$, we have a map $i_{U,p}:\mathcal{O}_X(U)\to \mathcal{O}_{X,p}$ for any open $U$ in $X$ such that $p \in U$, and further these inclusions are compatible with restrictions of the structure sheaf. For a moment let $U \subseteq X$ be an affine open subset containing $p$. Then we have $\mathsf{Spec}(i_{U,p}):\mathsf{Spec}(\mathcal{O}_{X,p})\to \mathsf{Spec}(\Gamma(\mathcal{O}_X;U))\cong (U,\mathcal{O}_X\vert_U)$. Composing with the natural inclusion of $(U,\mathcal{O}_X\vert_U)$ into $X$ gives our desired inclusion $i_p:\mathsf{Spec}(\mathcal{O}_{X,p})\to (X,\mathcal{O}_X)$.
>
>It remains to see that this definition of $i_p$ is free of choice. Let $U \cong \mathsf{Spec}(A)$ and $V \cong \mathsf{Spec}(B)$ be affine open neighborhoods of $p$ in $X$. Then $U\cap V$ is an open subscheme of an affine scheme containing $p$, and so we have an affine scheme $W\subseteq U\cap V$ containing $p$. Then since the ring maps and the inclusions commute, we have that $$\iota_U\circ \mathsf{Spec}(i_{U,p}) = \iota_U\circ \mathsf{Spec}(i_{W,p}\circ \text{res}_{U,W}) = \iota_W\circ \mathsf{Spec}(i_{W,p}) = \iota_V\circ \mathsf{Spec}(i_{V,p})$$
>where the last equality follows the same steps as the first. Thus, $i_p$ doesn't depend on the choice of affine open.

^ce4c8f

>[!example] Morphism out of Residue Field
>Let $p$ be a point in a scheme $X$. Then $\mathcal{O}_{X,p}$ is a local ring with maximal ideal $\mathfrak{m}_{X,p}$ and residue field $\kappa(p) = \mathcal{O}_{X,p}/\mathfrak{m}_{X,p}$. The quotient map induces a map of schemes $\mathsf{Spec}(\kappa(p))\to \mathsf{Spec}(\mathcal{O}_{X,p})$. Combining this with [[Basic Properties of Morphisms of Schemes#^ce4c8f]] we obtain a canonical map of schemes $\mathsf{Spec}(\kappa(p))\to X$.

In general, suppose $(A,\mathfrak{m})$ is a local ring and $\pi:\mathsf{Spec}(A)\to X$ is a map of schemes that sends $\mathfrak{m}$ to $p$. Suppose $U$ is an open set containing $p$ in $X$. Then $\pi^{-1}(U)$ is an open set in $\mathsf{Spec}(A)$ containing $\mathfrak{m}$. Note that if $f \in A$, then the basic open set $D(f)$ either does not contain $\mathfrak{m}$ if $f \in \mathfrak{m}$, or does contain $\mathfrak{m}$ if $f \notin \mathfrak{m}$. But if $f \notin \mathfrak{m}$ then $f$ is a unit in $A$, and so $D(f) = \mathsf{Spec}(A)$. Thus, the only open set containing $\mathfrak{m}$ in $\mathsf{Spec}(A)$ is the whole space itself, so $\pi^{-1}(U) = \mathsf{Spec}(A)$, and hence the image of $\pi$ lies in ever open set containing $p$. Thus, for every such open we have a map $\mathcal{O}_X(U)\to A$ which is compatible with restrictions. Thus, by the universal property of the colimit for a stalk we have a unique map $\mathcal{O}_{X,p}\to A$ which the $\mathcal{O}_X(U)\to A$ factor. Taking $\mathsf{Spec}$ gives that $\pi$ factors uniquely as $$\mathsf{Spec}(A)\to \mathsf{Spec}(\mathcal{O}_{X,p})\to X$$
giving a correspondence
$$\mathsf{Sch}(\mathsf{Spec}(A),X)\iff \coprod_{p \in X}\mathsf{CRing}_{loc}(\mathcal{O}_{X,p},A)$$

>[!example] Gluing Relative Maps Into Projective Space
>Let $B$ be a cring and $X$ a $B$-scheme (i.e. $X$ comes equipped with a map of schemes $\pi:X\to \mathsf{Spec}(B)$ (which can be thought of as a map of crings $B\to \Gamma(\mathcal{O}_X;X)$)). Let $f_i:X\to \mathsf{Spec}(B[x_i])$ for $0 \leq i \leq n$ be maps of $B$-schemes. We define maps ... **TBC**


### Maps of Projective Schemes


## Reasonable Morphisms of Schemes

What does it mean for a morphism of schemes to be "reasonable"? Recall that in a Grothendieck school/categorical perspective we should be considering properties of morphisms in order to better understand properties of objects. One thing that makes a property $P$ of morphisms reasonable is when it is locally of property $P$, which is to say in general it is preserved by taking fiber products.

We take a brief detour to discuss when properties can be determined locally on affine covers.

>[!proposition] Affine Intersections in Schemes
>Let $\mathsf{Spec}(A)$ and $\mathsf{Spec}(B)$ be affine open subschemes of a scheme $X$. Then $\mathsf{Spec}(A)\cap \mathsf{Spec}(B)$ is a union of simultaneously distinguished open subschemes of $\mathsf{Spec}(A)$ and $\mathsf{Spec}(B)$.

^fc2bfc

`\begin{proof}`
Let $p \in \mathsf{Spec}(A)\cap \mathsf{Spec}(B)$. Since the intersection is open in $\mathsf{Spec}(A)$ we have a distinguished open set $\mathsf{Spec}(A_f)$ containing $p$ and contained in the intersection. This distinguished open is also open in $\mathsf{Spec}(B)$, so we can find a distinguished open $\mathsf{Spec}(B_g) \subseteq\mathsf{Spec}(A_f)$ containing $p$. Note that this inclusions induce maps $B\to A_f\to B_g$, which sends $g$ to an element $g'$ of $A_f$. Then we have that
$$\mathsf{Spec}(B_g) = \mathsf{Spec}(A_f)\backslash\{[\mathfrak{p}]\mid g' \in \mathfrak{p}\} = \mathsf{Spec}(A_f)_{g'}$$
Write $g' = g''/f^n$ for some $g'' \in A$. Then $\mathsf{Spec}(A_f)_{g'} = \mathsf{Spec}(A_{fg''}))$, nd so the common open is a common distinguished open.
`\end{proof}`

>[!lemma] Affine Communication Lemma
>Let $P$ be a property enjoyed by some affine open subsets of a scheme $X$ such that
>1. if an affine open subset $\mathsf{Spec}(A)\hookrightarrow X$ has property $P$, then for any $f \in A$, $\mathsf{Spec}(A_f)\hookrightarrow X$ also has property $P$.
>2. if $\langle f_1,...,f_n\rangle = A$, and $\mathsf{Spec}(A_{f_i})\hookrightarrow X$ has property $P$ for all $i$, then so does $\mathsf{Spec}(A)\hookrightarrow X$.
>
>If $X = \bigcup_{i \in I}\mathsf{Spec}(A_i)$ where $\mathsf{Spec}(A_i)$ has property $P$, then every affine open subset of $X$ has property $P$ too.

^b058ea

`\begin{proof}`
Let $\mathsf{Spec}(A)$ be an affine open subset of $X$. Then for each $i \in I$, [[Basic Properties of Morphisms of Schemes#^fc2bfc]] implies that $\mathsf{Spec}(A)\cap \mathsf{Spec}(A_i)$ is a union of simultaneous distinguished affine opens. Thus, since each $\mathsf{Spec}(A_i)$ has property $P$, assumption (1) implies that $\mathsf{Spec}(A)$ is a union of distinguished affine open subsets satisfying property $P$. But, since affine schemes are quasi-compact it follows that $\mathsf{Spec}(A)$ is a finite such union, and so property (2) applies and gives that $\mathsf{Spec}(A)$ satisfies property $P$.
`\end{proof}`

A property satisfying the conditions of the Affine Communication Lemma is said to be **affine-local**.

The following is a checklist of desirable characteristics of a "reasonable" family of morphisms $\mathcal{M}$:
1. $\mathcal{M}$ is **local on the target**, which is to say that if $\pi:X\to Y$ is in $\mathcal{M}$, then for every open subset $V$ of $Y$, $\pi\vert_{\pi^{-1}(V)}:\pi^{-1}(V)\to V$ is in $\mathcal{M}$ and if $\pi:X\to Y$ is any morphism for which there exists an open cover $\{V_i\}_{i \in I}$ of $Y$ such that $\pi\vert_{\pi^{-1}(V_i)}:\pi^{-1}(V_i)\to V_i$ is in $\mathcal{M}$ for all $i\in I$, then $\pi$ is in $\mathcal{M}$.
2. $\mathcal{M}$ is closed under composition
3. $\mathcal{M}$ is closed under base change/pullback along arbitrary morphisms

The first class of morphisms we will consider are **open immersions**.

>[!def] Open Immersion
>A morphism of schemes $\pi:X\to Y$ is an open embedding if $\pi$ factors as
>$$(X,\mathcal{O}_X)\xrightarrow[\cong]{\rho}(U,\mathcal{O}_Y\vert_U)\hookrightarrow (Y,\mathcal{O}_Y)$$
>for some open subset $U$ of $Y$, where $\rho$ is an isomorphism of schemes.

We now consider some properties of open immersions:

>[!proposition] Properties of Open Immersions
>Let $\mathcal{M}_O$ be the class of open immersions of schemes. Then we have that 
>1. $\mathcal{M}_O$ is local on the target
>2. $\mathcal{M}_O$ is closed under composition
>3. $\mathcal{M}_O$ contains all isomorphisms
>4. $\mathcal{M}_O$ is closed under base change

`\begin{proof}`
Property **(3)** is immediate by definition. To show **(1)** let $\pi:X\to Y$ be a map of schemes. First, suppose $\pi$ is an open embedding so $\pi$ factors through a isomorphism $\rho:X\to U$ for some open subset $U \subseteq Y$. Then if $V \subseteq Y$ is open, $\pi\vert_{\pi^{-1}(V)}$ factors as a morphism
$$\pi^{-1}(V)\to U\cap V\to U \to Y$$
Now, the left most map is the restriction of an isomorphism of schemes, and hence is again an isomorphism of schemes, so $\pi\vert_{\pi^{-1}(V)}$ is an open immersion. On the other hand, let $\{V_i\}_{i \in I}$ be an open cover of $Y$ such that $\pi\vert_{\pi^{-1}(V_i)}:\pi^{-1}(V_i)\to V_i$ is an open immersion for all $i \in I$. Then $U = \pi(X) = \bigcup_{i \in I}\pi(V_i)$ is open in $Y$, since each $V_i$ is open in $Y$, and on the level of topological spaces the co-restriction $\rho:X\to U$ is an isomorphism. On the other hand, $\rho^\#:\mathcal{O}_Y\vert_U\to \rho_*\mathcal{O}_X$ is a map of schemes which is an isomorphism when restricted to $V_i$ for each $i$. In particular, it follows that $\rho^\#$ is an isomorphism on the level of stalks and hence on the level of sheaves. This finishes **(1)**.

Let $f:X\to Y$ and $g:Y\to Z$ be open immersions, so we have $f':X\xrightarrow{\cong}U$ and $g':Y\xrightarrow{\cong}V$. Then $g'\vert_{U}:U\xrightarrow{\cong} g'(U)\cap V$ and so $g'\vert_U\circ f':X\xrightarrow{\cong}g'(U)\cap V$ gives an isomorphism of schemes onto an open subscheme which $g\circ f$ factors through. Thus **(2)** is satisfies.

For **(4)** first note that pulling back along the inclusion of an open subset gives the fiber of a map of schemes, which is again the inclusion of an open subset. On the other hand, the pullback of an isomorphism, in any category, is again an isomorphism, and since pullbacks of composites can be done one square at a time we obtain the desired result.
`\end{proof}`

In addition to our three "preferred" properties we would like classes of morphisms to satisfy, there are many others that appear naturally in the study of algebraic geometry.

>[!def] Local on the Source
>A property $P$ of morphisms is said to be **local on the source** if to check that $\pi:X\to Y$ has property $P$ it suffices to check that for any open cover $\{U_i\}_{i \in I}$ of $X$, $\pi\vert_{U_i}:U_i \to Y$ has property $P$.
>


We also say that a property is **affine-local on the source** (resp. **affine-local on the target**) if it suffices to check on an affine open cover of the source (resp. target). Local on the target need not imply local on the source. 


## Finiteness Conditions

Finiteness conditions play a central role in all parts of mathematics, algebraic geometry especially so. In this section we cover a number of finiteness conditions, discuss their properties, and provide select examples. 

>[!def] Quasi-Compact
>A morphism of schemes $\pi:X\to Y$ is said to be **quasi-compact** if for every open affine subset $U$ of $Y$, $\pi^{-1}(U)$ is quasi-compact. (Equivalently, the pre-image of any quasi-compact open subset is quasi-compact).

Note that **quasi-compact** morphisms are naturally affine-local on the target.


>[!proposition] Quasi-Compact in terms of Affines
>A map of schemes $f:X\to Y$ is quasi-compact if and only if there exists an affine open cover $\{U_i\}_{i \in I}$ of $Y$ such that each $f^{-1}(U_i)$ is a union of finitely many affine open subsets in $X$.

^dd8c38

`\begin{proof}`
First, if $U$ is an affine open subset of $Y$ such that $\pi^{-1}(U)$ is quasi-compact, and hence a finite union of open affines, the pre-image of a distinguished open $U_f$ would be a finite union of distinguished open affines in the original open affines. On the other hand, if $U \cong \mathsf{Spec}(A)$ is generated by $f_1,...,f_n$ such that $\pi^{-1}(U_{f_i})$ is quasi-compact for each $i$, then $U = \bigcup_{i=1}^nU_{f_i}$,and so $\pi^{-1}(U)$ is quasi-compact being a finite union of quasi-compact spaces.  By the [[Basic Properties of Morphisms of Schemes#^b058ea]] this finishes the proof.
`\end{proof}`

Another "quasi-finiteness" condition is known as being quasi-separated.

>[!def] Quasi-separated
>A morphism of schemes $\pi:X\to Y$ is **quasi-separated** if for every affine open subset $U$ of $Y$, $\pi^{-1}(U)$ is a quasi-separated scheme (i.e. $\pi^{-1}(U)$ is **quasi-separated as a topological space**, which is to say the intersection of any two quasi-compact open subsets is quasi-compact).

Note that affine schemes are quasi-separated since they are quasi-compact and the intersection of affine subschemes in an affine scheme is again affine (consider the intersection as a pullback). It follows that affine morphisms in particular are quasi-separated and quasi-compact. As these types of morphisms often come in pairs we will refer to such maps with the abbreviation **qcqs**. 

>[!proposition] Composition
>Quasi-compact (resp. quasi-separated) morphisms are closed under composition.

`\begin{proof}`
The proof for quasi-compact follows easily either from the definition [[Basic Properties of Morphisms of Schemes#^dd8c38]]. **Quasi-separated LATER**.
`\end{proof}`
A property which subsumes these two is that of being **affine**.

>[!def] Affine Morphism
>A morphism of schemes $\pi:X\to Y$ is **affine** if for each affine open $U$ of $Y$, $\pi^{-1}(U)$ is an affine open in $X$.

It is immediate that affine opens are closed under isomorphisms and composition. Further, as commented above affine morphisms are qcqs. In order to show that affine morphisms can be determined locally we first determine a property of qcqs morphisms.

>[!lemma] QCQS Lemma
>If $X$ is a qcqs scheme and $s \in \Gamma(X,\mathcal{O}_X)$, then the natural map $\Gamma(X,\mathcal{O}_X)_s\to \Gamma(X_s,\mathcal{O}_X\vert_{X_s})$ is an isomorphism.

`\begin{proof}`
Here $X_s = \{p \in X\mid s\neq 0\text{ in }\mathcal{O}_{X,p}\}$. Note that if $p \in X_s$, then there is an open neighborhood of points around $p$ where $s$ doesn't vanish, so $X_s$ is an open subscheme of $X$. Let $\{U_i\}_{i \in I}$ be an affine open cover of $X$, necessarily finite since $X$ is quasi-compact. Now, each $U_i\cap U_j$ can be written as a finite union of affine opens $U_{ijk}$ since $X$ is quasi-separated.  **TBC**
`\end{proof}`





#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024
