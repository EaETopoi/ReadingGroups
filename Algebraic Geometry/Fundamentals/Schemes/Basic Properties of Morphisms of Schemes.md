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
>A morphism of schemes $\pi:X\to Y$ is an **open immersion** if $\pi$ factors as
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
Property **(3)** is immediate by definition. To show **(1)** let $\pi:X\to Y$ be a map of schemes. First, suppose $\pi$ is an open embedding so $\pi$ factors through an isomorphism $\rho:X\to U$ for some open subset $U \subseteq Y$. Then if $V \subseteq Y$ is open, $\pi\vert_{\pi^{-1}(V)}$ factors as a morphism
$$\pi^{-1}(V)\to U\cap V\to U \to Y$$
Now, the left most map is the restriction of an isomorphism of schemes, and hence is again an isomorphism of schemes, so $\pi\vert_{\pi^{-1}(V)}$ is an open immersion. On the other hand, let $\{V_i\}_{i \in I}$ be an open cover of $Y$ such that $\pi\vert_{\pi^{-1}(V_i)}:\pi^{-1}(V_i)\to V_i$ is an open immersion for all $i \in I$. Then $U = \pi(X) = \bigcup_{i \in I}\pi(\pi^{-1}(V_i))$ is open in $Y$, since each $V_i$ is open in $Y$, and on the level of topological spaces the co-restriction $\rho:X\to U$ is an isomorphism. On the other hand, $\rho^\#:\mathcal{O}_Y\vert_U\to \rho_*\mathcal{O}_X$ is a map of schemes which is an isomorphism when restricted to $V_i$ for each $i$. In particular, it follows that $\rho^\#$ is an isomorphism on the level of stalks and hence on the level of sheaves. This finishes **(1)**.

Let $f:X\to Y$ and $g:Y\to Z$ be open immersions, so we have $f':X\xrightarrow{\cong}U$ and $g':Y\xrightarrow{\cong}V$. Then $g'\vert_{U}:U\xrightarrow{\cong} g'(U)\cap V$ and so $g'\vert_U\circ f':X\xrightarrow{\cong}g'(U)\cap V$ gives an isomorphism of schemes onto an open subscheme which $g\circ f$ factors through. Thus **(2)** is satisfied.

For **(4)** first note that pulling back along the inclusion of an open subset gives the fiber of a map of schemes, which is again the inclusion of an open subset. On the other hand, the pullback of an isomorphism, in any category, is again an isomorphism, and since pullbacks of composites can be done one square at a time we obtain the desired result.
`\end{proof}`

Note that if $\pi:X\to Y$ is an open embedding and $Y$ is locally Noetherian (i.e. has a cover by Noetherian affine opens, or by [[Basic Properties of Morphisms of Schemes#^b058ea]], all affine opens are Noetherian), then so is $X$. If $Y$ is actually Noetherian, then $X$ is too since it implies $Y$ is topologically Noetherian, so every open is quasi-compact, and hence $X$ is quasi-compact.

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
An important point is that mappings out of Noetherian schemes are always compact.

>[!proposition] Mapping out of (locally) Noetherian Schemes
>1. If $N$ is a Noetherian scheme and $f:N\to X$ is a map of schemes, then $f$ is quasi-compact
>2. If $f:X\to Y$ is a map of schemes where $X$ is quasi-separated, then $f$ is quasi-separated.
>3. Being quasi-compact (resp. quasi-separated) is affine-local on the target.

^2f7d03

`\begin{proof}`
**(1)** follows immediately from the fact that Noetherian schemes are also Noetherian topological spaces, by [[Basic Properties of Schemes#^59024f]].

For **(2)**, observe that if $X$ is quasi-separated then so is any open subscheme since an open subset of an open subset is open in the whole space.

For **(3)** we can use the [[Basic Properties of Morphisms of Schemes#^b058ea]]. First note that if $f:X\to Y$ is quasi-compact (-separated), then its restriction is also quasi-compact (-separated). If $f:X\to \mathsf{Spec}(A)$ is a map of schemes and $f_1,...,f_n$ generate $A$ such that each $f\vert_{\mathsf{Spec}(A_{f_i})}:f^{-1}(\mathsf{Spec}(A_{f_i}))\to \mathsf{Spec}(A_{f_i})$ is quasi-compact (-separated), then the pre-image of any affine open subscheme is a finite union of quasi-compact (-separated) open subsets, which is quasi-compact (-separated). Finally, suppose $f:X\to Y$ is map of schemes such that for any affine open subset $V$ of $Y$, $f\vert_{f^{-1}(V)}:f^{-1}(V)\to V$ is quasi-compact (-separated), which means $f:X\to Y$ is quasi-compact (-separated) by definition.
`\end{proof}`

A property which subsumes these two is that of being **affine**.

>[!def] Affine Morphism
>A morphism of schemes $\pi:X\to Y$ is **affine** if for each affine open $U$ of $Y$, $\pi^{-1}(U)$ is an affine open in $X$.

It is immediate that affine opens are closed under isomorphisms and composition. Further, as commented above affine morphisms are qcqs. In order to show that affine morphisms can be determined locally we first determine a property of qcqs morphisms.

>[!lemma] QCQS Lemma
>If $X$ is a qcqs scheme and $s \in \Gamma(X,\mathcal{O}_X)$, then the natural map $\Gamma(X,\mathcal{O}_X)_s\to \Gamma(X_s,\mathcal{O}_X\vert_{X_s})$ is an isomorphism.

^4ddbb6

`\begin{proof}`
Here $X_s = \{p \in X\mid s\neq 0\text{ in }\mathcal{O}_{X,p} / \mathfrak{m}_p\mathcal{O}_{X,p}\}$. Note that if $p \in X_s$, then there is an open neighborhood of points around $p$ where $s$ doesn't vanish, so $X_s$ is an open subscheme of $X$. Let $\{U_i\}_{i \in I}$ be an affine open cover of $X$, necessarily finite since $X$ is quasi-compact. Now, each $U_i\cap U_j$ can be written as a finite union of affine opens $U_{ijk}$ since $X$ is quasi-separated. Note that if $X$ is affine, then $X_s$ is exactly $D(s) = \{\mathfrak{p} \in X\mid s \notin \mathfrak{p}\}$, in which case $\mathcal{O}_X(D(s)) = \mathcal{O}_X(X)_s$ by construction of the scheme structure on a ring spectra.

Note that if $s \neq 0$ in $\mathcal{O}_{X,p}/\mathfrak{m}_p\mathcal{O}_{X,p}$, then $s$ is not contained in the only maximal ideal in $\mathcal{O}_{X,p}$, and hence is a unit. Thus, as this holds at all stalks at points in $X_s$ we have that $s\vert_{X_s} \in \Gamma(X_s,\mathcal{O}_X\vert_{X_s})$ is invertible, so we have a unique map $\Gamma(X,\mathcal{O}_X)_s\to \Gamma(X_s,\mathcal{O}_X\vert_{X_s})$. Now, from the sheaf condition we have an exact sequence
$$0\to \Gamma(X,\mathcal{O}_X)\to \prod_{i \in I}\Gamma(U_i,\mathcal{O}_X\vert_{U_i})\to \prod_{i,j \in I}\Gamma(U_i\cap U_j,\mathcal{O}_X\vert_{U_i\cap U_j})$$
Applying the sheaf condition again on our finite covers of each $U_i\cap U_j$ we have the exact sequence
$$0\to \Gamma(X,\mathcal{O}_X)\to \prod_{i \in I}A_i\to \prod_{i,j \in I,k\in J_{ij}}A_{ijk}$$
where $U_i\cong \mathsf{Spec}(A_i)$ and $U_{ijk}\cong \mathsf{Spec}(A_{ijk})$. Since localization is an exact functor and our products are finite we have the exact sequence
$$0\to \Gamma(X,\mathcal{O}_X)_s\to \prod_{i \in I}(A_i)_{s\vert_{U_i}}\to \prod_{i,j \in I,k\in J_{ij}}(A_{ijk})_{s\vert_{U_{ijk}}}$$
On the other hand, $X_s\cap \mathsf{Spec}(A)\cong \mathsf{Spec}(A_{s\vert_A})$, and so we also have the exact sequence
$$0\to \Gamma(X_s,\mathcal{O}_X\vert_{X_s})\to \prod_{i \in I}(A_i)_{s\vert_{U_i}}\to \prod_{i,j \in I,k\in J_{ij}}(A_{ijk})_{s\vert_{U_{ijk}}}$$
Thus, by uniqueness of limits we have the desired isomorphism.
`\end{proof}`

We can now show that a morphism being affine is affine-local on the target.

>[!proposition] Affine is Affine-local
>A map of schemes $f:X\to Y$ is affine if there is a cover of $Y$ by affine open sets such that the restrictions are affine (equivalently there exists a cover $Y = \bigcup_{i \in I}U_i$ such that $f^{-1}(U_i)$ is affine for each $i$).

`\begin{proof}`
We proceed by using the [[Basic Properties of Morphisms of Schemes#^b058ea]]. Note first that the restriction of an affine morphism is necessarily affine, so we need only prove the second part of the Affine Communication Lemma. Note that in particular if $f^{-1}(\mathsf{Spec}(B)) = \mathsf{Spec}(A)$, then for any $s \in B$, $f^{-1}(\mathsf{Spec}(B_s)) = \mathsf{Spec}(A_{f^\#s})$. 

For this suppose $f:X\to \mathsf{Spec}(B)$ is a map of schemes and $s_1,...,s_n$ generate $B$ such that $f^{-1}(\mathsf{Spec}(B_{s_i})) \cong \mathsf{Spec}(A_i)$ is affine. Note that
$$f^{-1}(\mathsf{Spec}(B_{s_i})) = \{p \in X\mid s_i\neq 0 \text{ in }B_{f(p)}/f(p)B_{f(p)}\}$$
Note that we have an induced map $f^\#:B_{f(p)}/f(p)B_{f(p)}\to \mathcal{O}_{X,p}/\mathfrak{m}_p\mathcal{O}_{X,p}$, where $(f^\#)^{-1}(\mathfrak{m}_p) = f(p)$, and so $f^\#(s) \neq 0$. Thus, $f^{-1}(\mathsf{Spec}(B_{s_i})) = X_{f^\#s_i}$. We wish to show that $X$ itself is affine. Let $A = \Gamma(X,\mathcal{O}_X)$. Then $f$ factors through the map $\alpha:X\to \mathsf{Spec}(A)$ via $g:\mathsf{Spec}(A)\to \mathsf{Spec}(B)$. Note that for each $i$, $g^{-1}(D(s_i)) = D(g^\#s_i) \cong \mathsf{Spec}(A_{g^\#s_i})$. By [[Basic Properties of Morphisms of Schemes#^2f7d03]] part (3) we have that  $X$ is qcqs. Then by [[Basic Properties of Morphisms of Schemes#^4ddbb6]] we have that $A_i\cong A_{g^\#s_i}$ for each $i$, and so $\alpha$ is locally an isomorphism, and hence an isomorphism $X \cong \mathsf{Spec}(A)$.
`\end{proof}`

### Finite and Integral Morphisms

>[!def] Finite Morphism
>A morphism of schemes $f:X\to Y$ is **finite** if for every affine open $U\cong \mathsf{Spec}(B)$ of $Y$, $f^{-1}(U)$ is affine with coordinate ring a $B$-algebra which is finitely generated as a $B$-module.

Note that finiteness, like many other conditions we have encountered so far, is affine-local on the target, which can be proving by leveraging the [[Basic Properties of Morphisms of Schemes#^b058ea]]. Since the property of being finitely generated as a module over a ring is transitive, finite morphisms compose. Further, all isomorphisms are finite. We now show finite morphisms are preserved by pullbacks and have finite fibers.

>[!proposition] Finite maps stable under base change
>Let $f:X\to Z$ and $g:Y\to Z$ be maps of schemes such that $f$ is finite. Then the pullback of $f$ along $g$ is finite.

^3c1ceb

`\begin{proof}`
Consider the pullback
$$\begin{CD}X\times_ZY @>f'>> Y \\ @Vg'VV @VVgV \\ X @>>f> Z\end{CD}$$
Since being finite is affine-local on the target begin by letting $W_i \cong \mathsf{Spec}(C_i)$ be an affine cover of $Z$, and let $V_{ij}\cong \mathsf{Spec}(B_{ij})$ be compatible affine covers of $Y$. By assumption we have that for each $i$, $f^{-1}(W_i) \cong \mathsf{Spec}(A_i)$ for some $A_i$ which are finitely generated as $C_i$-modules. Then ${f'}^{-1}(V_{ij}) \cong V_{ij}\times_{W_i}f^{-1}(W_i)$, which is the affine scheme $\mathsf{Spec}(A_i\otimes_{C_i}B_{ij})$. Let $a_1,...,a_n$ be a generating set of $A_i$ over $C_i$. I claim that $a_i\otimes 1$ is a generating set of $A_i\otimes_{C_i}B_{ij}$ as a $B_{ij}$ module. Observe that if $a\otimes b$ is an arbitrary pure tensor, then $a\otimes b = \sum_{j=1}^n(a_j\otimes 1)c_jb$ for some $c_j \in C_i$, as desired. This completes the proof.
`\end{proof}`

>[!proposition] Finite Fibers
>Finite morphisms have finite fibers.

`\begin{proof}`
Let $f:X\to Y$ be a finite morphism of schemes and let $p \in Y$. Since $f$ is affine we can assume that $X \cong \mathsf{Spec}(A)$ and $Y \cong \mathsf{Spec}(B)$. Then $f$ is represented by a map of crings $g:B\to A$ such that $A$ is finitely generated as a module over $B$. Note that $f^{-1}(\{p\}) \subseteq V(g(p)A)$, and so we can restrict to the affine subscheme $\mathsf{Spec}(A/g(p)A)$, which factors through $\mathsf{Spec}(B/p)$. Thus, we are reduced to the case where $Y$ is the spectrum of an integral domain and $p$ is the generic point (i.e. $V(p) = Y$). In this context we are interested in those primes $\mathfrak{p}$ in $A$ such that $g^{-1}(\mathfrak{p}) = \langle 0 \rangle$. Consider the map $B\to k_B$ from $B$ to its fraction field, and pull-back along $f$ to obtain $f^{-1}(\{p\})\cong \mathsf{Spec}(A\otimes_Bk_B) \cong \mathsf{Spec}(S^{-1}A)$ where $S = g(B\backslash \{0\})$. Under these steps we have that $S^{-1}A$ is a finite $k_B$-vector space. Since finite algebras over a field are Artinian by Atiyah[^2] we have that $S^{-1}A$ is Artinian and hence a finite product of Artinian local rings, each of which has finitely many prime ideals. Thus the fiber is finite.
`\end{proof}`

We now move on to integral morphisms.

>[!def] Integral Morphism of Schemes
>A map of schemes $f:X\to Y$ is **integral** if $f$ is affine and for every affine open $\mathsf{Spec}(B)$ of $Y$, $f^{-1}(\mathsf{Spec}(B))\cong \mathsf{Spec}(A)$, and the induced map $B\to A$ is an **integral ring homomorphism** (i.e. $A$ is integral over $B$ relative to this morphism).

Once again this is an affine local condition, which can be shown using the [[Basic Properties of Morphisms of Schemes#^b058ea]]. By transitivity of integrality integral morphisms compose, and they also contain all isomorphisms. A similar proof to that given for finite morphisms can show they are stable under base change. Note that finite morphisms provide a wide class of examples of integral morphisms. 

>[!def] Finite Type Morphisms
>A map of schemes $f:X\to Y$ is **locally of finite type** if for every affine open subset $U\cong \mathsf{Spec}(B)$ of $Y$, and every affine open $V = \mathsf{Spec}(A)$ subset of $f^{-1}(U)$, the induced map on crings, $B\to A$, gives $A$ the structure of a finitely generated $B$-algebra. A morphism is of **finite type** if it is locally of finite type and quasi-compact.

It turns out that being finite is equivalent to being of finite type and integral.

>[!proposition] Finite = Integral + Finite Type
>A morphism of schemes is finite if and only if it is of finite type and integral.


>[!def] Quasi-finite
>A map $f:X\to Y$ of schemes is **quasi-finite** if it is of finite type and for any $p \in Y$, $f^{-1}(\{p\})$ is a finite set.


>[!def] Finite Presentation
>A map of schemes $f:X\to Y$ is **locally of finite presentation** if for each affine open set $\mathsf{Spec}(B)$ of $Y$, $f^{-1}(\mathsf{Spec}(B))$ is covered by affine opens $\mathsf{Spec}(A_i)$ such that $B\to A_i$ is finitely presented. $f$ is **of finite presentation** if it is locally of finite presentation and quasi-compact and quasi-separated.

A useful characterization of locally of finite presentation can be given in terms of limit formulations, as done in [EGA, IV_3,8.14.2], where $f:X\to Y$ is locally of finite presentation if and only if for every projective system of $Y$-schemes $\{S_\lambda\}_{\lambda \in I}$ with each $S_\lambda$ an affine scheme, the natural map
$$\lim\limits_{\to \lambda}\mathsf{Hom}_Y(S_\lambda,X) \to \mathsf{Hom}_Y(\lim\limits_{\leftarrow \lambda}S_\lambda,X)$$
is a bijection. Recall a projective or inverse system in a category $\mathcal{C}$ is a contravariant functor $F:(I,\leq)^{op}\to \mathcal{C}$ where $(I,\lambda)$ is a poset category (often directed).


## Separated Morphisms

Schemes in algebraic geometry are rarely Hausdorff. However, we would still like to use many of the amazing properties that come with the assumption on a space being Hausdorff. Thus, we define an algebraic version of Hausdorff-ness, and as with are general philosophy, assign it as a property of morphisms.

Recall that the Hausdorff condition can be characterized as the diagonal of a space being closed. We can replace this condition by the statement that the diagonal morphism for a map $\pi:X\to Y$ of schemes, $\Delta_\pi:X\to X\times_YX$, is a closed immersion. In general we always have that the diagonal is closed in some open subscheme.

>[!proposition] Diagonal Locally Closed
>Let $\pi:X\to Y$ be a map of schemes. The diagonal $\Delta_\pi:X\to X\times_YX$ is a locally closed embedding.

^4e7559

`\begin{proof}`
Let $V_i$ be a cover of $Y$ by affine opens, and let $U_{ij}$ be a compatible cover of $X$ (i.e. $\pi(U_{ij}) \subseteq V_i$). Then $U_{ij}\times_{V_i}U_{ij}$ is an affine open subscheme of the fiber product for all $i$ and $j$. Further, $\Delta_\pi^{-1}(U_{ij}\times_{V_i}U_{ij}) = U_{ij}$. Now, let $V_i = \mathsf{Spec}(B)$ and $U_{ij} = \mathsf{Spec}(A)$. Then the restriction $\Delta_{\pi}\vert_{U_{ij}}$ corresponds to the ring map $A\otimes_BA\to A$ given by $a_1\otimes a_2 = a_1a_2$, which is evidently surjective and hence induces a closed immersion. Since closed immersions can be checked locally it follows that the diagonal is a closed subscheme of the open subscheme
$$\bigcup_i\bigcup_jU_{ij}\times_{V_i}U_{ij}$$
`\end{proof}`

>[!def] Separated Morphism
>A morphism $\pi:X\to Y$ is **separated** if the diagonal morphism $\Delta_\pi:X\to X\times_YX$ is a closed embedding. An $S$ scheme $X$ is said to be **separated** if the structure morphism $X\to S$ is separated.

From the proof of [[Basic Properties of Morphisms of Schemes#^4e7559]] we observe that morphisms of affine schemes are separated, and more generally by gluing it follows that affine morphisms of schemes are separated.

>[!lemma] Separated on Cover
>Let $\varphi:X\to Y$ be a map of schemes. Let $Y = \bigcup_{\alpha \in A}U_\alpha$ be an open cover of $Y$. Then $\varphi$ is separated if and only if its restriction to $\varphi^{-1}(U_\alpha)$ is separated for all $\alpha \in A$.

`\begin{proof}`
Let $\varphi:X\to Y$ be a map of schemes. Let $Y = \bigcup_{\alpha \in A}U_\alpha$ be an open cover of $Y$. Then $X = \bigcup_{\alpha \in A}\varphi^{-1}(U_\alpha)$ is an open cover of $X$. We form the pullback and diagonal

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09X%20%5C%5C%0A%20%20%20%20%09%26%20%7BX%5Ctimes_YX%7D%20%26%20X%20%5C%5C%0A%20%20%20%20%09%26%20X%20%26%20Y%0A%20%20%20%20%09%5Carrow%5B%22%5Cvarphi%22'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Cvarphi%22%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_1%7D%22'%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_2%7D%22%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%5CDelta%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B1_X%7D%22%2C%20bend%20left%20%3D%2030%2C%20from%3D1-1%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B1_X%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	X \\
    	&amp; {X\times_YX} &amp; X \\
    	&amp; X &amp; Y
    	\arrow[&quot;\varphi&quot;', from=3-2, to=3-3]
    	\arrow[&quot;\varphi&quot;, from=2-3, to=3-3]
    	\arrow[&quot;{p_1}&quot;', from=2-2, to=3-2]
    	\arrow[&quot;{p_2}&quot;, from=2-2, to=2-3]
    	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=2-2, to=3-3]
    	\arrow[&quot;\Delta&quot;, from=1-1, to=2-2]
    	\arrow[&quot;{1_X}&quot;, bend left = 30, from=1-1, to=2-3]
    	\arrow[&quot;{1_X}&quot;', bend right = 30, from=1-1, to=3-2]
    \end{tikzcd}
" /></p>

Note that for each $\alpha \in A$, $p_1^{-1}(\varphi^{-1}(U_\alpha)) = (\varphi\circ p_1)^{-1}(U_\alpha) = (\varphi\circ p_2)^{-1}(U_\alpha) = p_2^{-1}(\varphi^{-1}(U_\alpha))$, so $p_1^{-1}(\varphi^{-1}(U_\alpha)) = p_1^{-1}(\varphi^{-1}(U_\alpha)) \cap p_2^{-1}(\varphi^{-1}(U_\alpha))$. From the construction of pullbacks in $\mathsf{Sch}$, we have the pullback diagram along with the restricted diagonal map

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7Bp_1%5E%7B-1%7D(%5Cvarphi%5E%7B-1%7D(U_%5Calpha))%7D%20%26%20%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%20%26%20%7BU_%5Calpha%7D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cvarphi%5Cvert_%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%7D%22'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cvarphi%5Cvert_%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%7D%22%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_1%7D%22'%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_2%7D%22%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5CDelta%5Cvert_%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B1_%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%7D%22%2C%20bend%20left%20%3D%2030%2C%20from%3D1-1%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B1_%7B%5Cvarphi%5E%7B-1%7D(U_%5Calpha)%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{\varphi^{-1}(U_\alpha)} \\
    	&amp; {p_1^{-1}(\varphi^{-1}(U_\alpha))} &amp; {\varphi^{-1}(U_\alpha)} \\
    	&amp; {\varphi^{-1}(U_\alpha)} &amp; {U_\alpha}
    	\arrow[&quot;{\varphi\vert_{\varphi^{-1}(U_\alpha)}}&quot;', from=3-2, to=3-3]
    	\arrow[&quot;{\varphi\vert_{\varphi^{-1}(U_\alpha)}}&quot;, from=2-3, to=3-3]
    	\arrow[&quot;{p_1}&quot;', from=2-2, to=3-2]
    	\arrow[&quot;{p_2}&quot;, from=2-2, to=2-3]
    	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=2-2, to=3-3]
    	\arrow[&quot;{\Delta\vert_{\varphi^{-1}(U_\alpha)}}&quot;, from=1-1, to=2-2]
    	\arrow[&quot;{1_{\varphi^{-1}(U_\alpha)}}&quot;, bend left = 30, from=1-1, to=2-3]
    	\arrow[&quot;{1_{\varphi^{-1}(U_\alpha)}}&quot;', bend right = 30, from=1-1, to=3-2]
    \end{tikzcd}
" /></p>

Note that $\varphi^{-1}(U_\alpha) = (p_1\circ \Delta)^{-1}(\varphi^{-1}(U_\alpha)) = \Delta^{-1}(p_1^{-1}(\varphi^{-1}(U_\alpha)))$. Then since closed immersions are local, if $\varphi$ is separated then each $\varphi\vert_{\varphi^{-1}(U_\alpha)}$ is separated, since the diagonal for $\varphi\vert_{\varphi^{-1}(U_\alpha)}$ is a restriction of the diagonal of $\varphi$ to an open subscheme.

Conversely, suppose each $\varphi\vert_{\varphi^{-1}(U_\alpha)}$ is separated, so that $\Delta\vert_{\varphi^{-1}(U_\alpha)}$ is a closed immersion for all $\alpha \in A$. Note that since $X = \bigcup_{\alpha \in A}\varphi^{-1}(U_\alpha)$ is an open cover of $X$, $X\times_YX = \bigcup_{\alpha \in A}p_1^{-1}(\varphi^{-1}(U_\alpha))$ is an open cover of the pullback. Then since closed immersions are local $\Delta$ is a closed immersion, and hence $\varphi$ is separated, as desired.
`\end{proof}`

This result will help us prove that a number of types of morphisms are locally closed. We start by showing that separated morphisms compose and are preserved by base change.

>[!lemma] Base Change is an immersion
>Let $f:X\to T$ and $g:Y\to T$ be morphisms of schemes, and let $h:T\to S$ be another morphism of schemes. Then the induced morphism $i:X\times_TY\to X\times_SY$ is an immersion. If $T\to S$ is separated, then $i$ is a closed immersion, and if $T\to S$ is quasi-separated (i.e. diagonal is quasi-compact) then $i$ is a quasi-compact morphism.

^630ce1

`\begin{proof}`
First, I claim we have a pullback square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BX%5Ctimes_TY%7D%20%26%20%7BX%5Ctimes_SY%7D%20%5C%5C%0A%09T%20%26%20%7BT%5Ctimes_ST%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{X\times_TY} &amp; {X\times_SY} \\
	T &amp; {T\times_ST}
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[from=2-1, to=2-2]
\end{tikzcd}
" /></p>

with top part coming from the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BX%5Ctimes_TY%7D%20%5C%5C%0A%09%26%20%7BX%5Ctimes_SY%7D%20%26%26%20Y%20%5C%5C%0A%09%26%26%20%7BT%5Ctimes_ST%7D%20%26%20T%20%5C%5C%0A%09%26%20X%20%26%20T%20%26%20S%0A%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D4-2%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D4-2%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D2-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bfrom%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bfrom%3D3-3%2C%20to%3D4-3%5D%0A%09%5Carrow%5Bfrom%3D3-4%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D4-2%2C%20to%3D4-3%5D%0A%09%5Carrow%5Bfrom%3D4-3%2C%20to%3D4-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{X\times_TY} \\
	&amp; {X\times_SY} &amp;&amp; Y \\
	&amp;&amp; {T\times_ST} &amp; T \\
	&amp; X &amp; T &amp; S
	\arrow[dashed, from=1-1, to=2-2]
	\arrow[from=1-1, to=2-4]
	\arrow[from=1-1, to=4-2]
	\arrow[from=2-2, to=2-4]
	\arrow[dashed, from=2-2, to=3-3]
	\arrow[from=2-2, to=4-2]
	\arrow[&quot;g&quot;, from=2-4, to=3-4]
	\arrow[from=3-3, to=3-4]
	\arrow[from=3-3, to=4-3]
	\arrow[from=3-4, to=4-4]
	\arrow[&quot;f&quot;', from=4-2, to=4-3]
	\arrow[from=4-3, to=4-4]
\end{tikzcd}
" /></p>

To see that this is a pullback suppose we have morphisms $Z\to T$ and $Z\to X\times_SY$ such that the composites $Z\to T\to T\times_ST$ and $Z\to X\times_SY\to T\times_ST$ agree. composing with a projection onto either of the factors gives either $Z\to Y\to T$, or  $Z\to X\to T$, both of which must equal $Z\to T$, and so we have a unique map $Z\to X\times_TY$ such that $Z\to X\times_TY\to X = Z\to X\times_SY\to X$ and $Z\to X\times_TY\to Y = Z\to X\times_SY\to  Y$, and so $Z\to X\times_TY\to X\times_SY= Z\to X\times_SY$. Additionally, $Z\to T = Z\to X\times_SY\to X\to T = Z\to X\times_TY\to X\times_SY\to T$, and so $Z\to T\to T\times_ST = Z\to X\times_TY\to X\times_SY\to T$.

If we had another such morphism $Z\to X\times_TY$, then it must have the same projections $Z\to X = Z\to X\times_TY\to X\times_SY\to X$ and $Z\to Y = Z\to X\times_TY\to X\times_SY\to Y$, so the map is unique.

Now, with the pullback

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BX%5Ctimes_TY%7D%20%26%20%7BX%5Ctimes_SY%7D%20%5C%5C%0A%09T%20%26%20%7BT%5Ctimes_ST%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{X\times_TY} &amp; {X\times_SY} \\
	T &amp; {T\times_ST}
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[from=2-1, to=2-2]
\end{tikzcd}
" /></p>
since the diagonal is always a locally closed immersion, and such maps are preserved by base change, so is $X\times_TY\to X\times_SY$. The other claims follow similarly if further the diagonal is a closed immersion or is quasi-compact.
`\end{proof}`

>[!lemma] Morphism Into Fiber Immersion Cases
>Let $f:X\to Y$ be a morphism of schemes over a scheme $S$. The induced morphism $i:X\to X\times_SY$ is an immersion. If $Y$ is separated over $S$ it is a closed immersion and if $Y$ is quasi-separated it is quasi-compact.

^414a84

`\begin{proof}`
This follows from [[Basic Properties of Morphisms of Schemes#^630ce1]] and the fact that $X\times_YY\cong X$ since pulling back along an identity is an identity.
`\end{proof}`

>[!lemma] Separated Morphisms Compose and are Preserved by Base Change
>If $\pi:X\to Y$ and $\rho:Y\to Z$ are separated, so is $\rho\circ \pi$. If $\pi:X\to Y$ is separated and $f:W\to Y$ is any other morphism of schemes, then the pullback of $\pi$ along $f$ is separated.

^553038

`\begin{proof}`
By assumption we have that the diagonals $\Delta_{X/Y}:X\to X\times_YX$ and $\Delta_{Y/Z}:Y\to Y\times_ZY$ are closed immersions. It follows by [[Basic Properties of Morphisms of Schemes#^630ce1]] that the composite $X\to X\times_YX\to X\times_ZX$ is a closed immersion. But the projection maps for this composite are both the identity map for $X$, and so this composite is the diagonal $\Delta_{X/Z}$. Thus $\rho\circ \pi$ is separated.

Now, suppose $\pi:X\to Y$ is separated and $f:W\to Y$ is an arbitrary morphism of schemes. Observe that we have the iterated pullback diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BX%5Ctimes_YW%7D%20%26%20%7B(X%5Ctimes_YW)%5Ctimes_W(X%5Ctimes_YW)%7D%20%5C%5C%0A%09%26%20%7B(X%5Ctimes_YW)%5Ctimes_YX%7D%20%26%20%7BX%5Ctimes_YW%7D%20%26%20X%20%5C%5C%0A%09%26%20%7BX%5Ctimes_YW%7D%20%26%20W%20%26%20Y%0A%09%5Carrow%5B%22%5CDelta%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B%5Clangle%201_%7BX%5Ctimes_YW%7D%2C%5Cpi_0%5Crangle%7D%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Ccong%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cpi_0%7D%22%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7B%5Cpi_1%7D%22%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D2-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%5Cpi%22%2C%20from%3D2-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7B%5Cpi_1%7D%22'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{X\times_YW} &amp; {(X\times_YW)\times_W(X\times_YW)} \\
	&amp; {(X\times_YW)\times_YX} &amp; {X\times_YW} &amp; X \\
	&amp; {X\times_YW} &amp; W &amp; Y
	\arrow[&quot;\Delta&quot;, from=1-1, to=1-2]
	\arrow[&quot;{\langle 1_{X\times_YW},\pi_0\rangle}&quot;', from=1-1, to=2-2]
	\arrow[&quot;\cong&quot;, from=1-2, to=2-2]
	\arrow[from=2-2, to=2-3]
	\arrow[from=2-2, to=3-2]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=2-2, to=3-3]
	\arrow[&quot;{\pi_0}&quot;, from=2-3, to=2-4]
	\arrow[&quot;{\pi_1}&quot;, from=2-3, to=3-3]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=2-3, to=3-4]
	\arrow[&quot;\pi&quot;, from=2-4, to=3-4]
	\arrow[&quot;{\pi_1}&quot;', from=3-2, to=3-3]
	\arrow[&quot;f&quot;', from=3-3, to=3-4]
\end{tikzcd}
" /></p>

so up to an isomorphism, the diagonal of the pullback map is given by $X\times_YW\to (X\times_YW)\times_YX$. By [[Basic Properties of Morphisms of Schemes#^414a84]] we have that the map is a closed immersion since $X$ is separated over $Y$. Thus, $X\times_YW$ is separated over $W$, completing the proof.
`\end{proof}`

>[!proposition] Embeddings are Separated
>1. Locally closed embeddings are separated
>2. Monomorphisms in $\mathsf{Sch}$ are separated

`\begin{proof}`
For **(1)** let $\pi:X\to Y$ be a locally closed embedding. Then there exists an open subset $U \subseteq Y$ such that $\pi:X\to U$ is a closed immersion. Thus, by [[Basic Properties of Morphisms of Schemes#^553038]] it suffices to show that open immersions and closed immersions are separated.

Suppose $\pi:X\to Y$ is a closed immersion. Denoting closed immersions by double arrows, and using [[Closed Subschemes and Immersions#^42a50b]] we have the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09X%20%5C%5C%0A%09%26%20%7BX%5Ctimes_YX%7D%20%26%20X%20%5C%5C%0A%09%26%20X%20%26%20Y%0A%09%5Carrow%5B%22%7B%5CDelta_%7BX%2FY%7D%7D%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	X \\
	&amp; {X\times_YX} &amp; X \\
	&amp; X &amp; Y
	\arrow[&quot;{\Delta_{X/Y}}&quot;, from=1-1, to=2-2]
	\arrow[two heads, from=2-2, to=2-3]
	\arrow[two heads, from=2-2, to=3-2]
	\arrow[two heads, from=2-3, to=3-3]
	\arrow[two heads, from=3-2, to=3-3]
\end{tikzcd}
" /></p>

Now, since closed immersions are stable under composition on the right, by [[Closed Subschemes and Immersions#^4164ff]], and since all isomorphisms (and hence identities) are closed immersions, it follows that $\Delta_{X/Y}$ is a closed immersion.

Now, suppose $U$ is an open subscheme of $X$ with inclusion $\iota:U\to X$. Note that the identity, $X\to X$, is a closed immersion, and hence is separated. Thus, the claim follows from a more general result, which is that if $\alpha:X\to S$ is separated, then so is $U\to S$. If $p_1,p_2:X\times_SX\to X$ denote the projections, recall that we have the model $U\times_SU\cong p_1^{-1}(U)\cap p_2^{-1}(U)$. Then by [[Closed Subschemes and Immersions#^42a50b]] it suffices to show that the square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09U%20%26%20%7Bp_1%5E%7B-1%7D(U)%5Ccap%20p_2%5E%7B-1%7D(U)%7D%20%5C%5C%0A%20%20%20%20%09X%20%26%20%7BX%5Ctimes_SX%7D%0A%20%20%20%20%09%5Carrow%5B%22%5CDelta%22'%2C%20two%20heads%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22open%22%2C%20hook%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5CDelta_U%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22open%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	U &amp; {p_1^{-1}(U)\cap p_2^{-1}(U)} \\
    	X &amp; {X\times_SX}
    	\arrow[&quot;\Delta&quot;', two heads, from=2-1, to=2-2]
    	\arrow[&quot;open&quot;, hook, from=1-2, to=2-2]
    	\arrow[&quot;{\Delta_U}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;open&quot;', hook, from=1-1, to=2-1]
    \end{tikzcd}
" /></p>

is a pullback square. Note that this square commutes, so we need only show it satisfies the desired universal property. 

To prove the claim let $Z$ be a scheme with maps $\varphi:Z\to p_1^{-1}(U)\cap p_2^{-1}(U)$ and $\psi:Z\to X$ making the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09Z%20%5C%5C%0A%20%20%20%20%09%26%26%20%7Bp_1%5E%7B-1%7D(U)%5Ccap%20p_2%5E%7B-1%7D(U)%7D%20%5C%5C%0A%20%20%20%20%09%26%20X%20%26%20%7BX%5Ctimes_SX%7D%0A%20%20%20%20%09%5Carrow%5B%22%5CDelta%22'%2C%20two%20heads%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22open%22%2C%20hook%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Cpsi%22'%2C%20curve%3D%7Bheight%3D12pt%7D%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Cvarphi%22%2C%20curve%3D%7Bheight%3D-12pt%7D%2C%20from%3D1-1%2C%20to%3D2-3%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	Z \\
    	&amp;&amp; {p_1^{-1}(U)\cap p_2^{-1}(U)} \\
    	&amp; X &amp; {X\times_SX}
    	\arrow[&quot;\Delta&quot;', two heads, from=3-2, to=3-3]
    	\arrow[&quot;open&quot;, hook, from=2-3, to=3-3]
    	\arrow[&quot;\psi&quot;', curve={height=12pt}, from=1-1, to=3-2]
    	\arrow[&quot;\varphi&quot;, curve={height=-12pt}, from=1-1, to=2-3]
    \end{tikzcd}
" /></p>

commute. Then on the level of topological spaces, for all $z \in Z$, $\Delta(\psi(z)) \in p_1^{-1}(U)\cap p_2^{-1}(U)$, so $\psi(z) = p_1(\Delta(\psi(z))) \in U$. Thus, since morphisms of schemes factor through open immersions as long as they factor through the open set as topological spaces, $\psi$ factors through $U$ via a unique $\psi':Z\to U$ so that if $\iota':p_1^{-1}(U)\cap p_2^{-1}(U)\to X\times_SX$ is the inclusion for the open subscheme, then
$$\iota'\circ \Delta_U\circ \psi' = \Delta\circ \iota\circ \psi' = \Delta\circ \psi = \iota'\circ \varphi$$
As $\iota'$ is an open immersion it follows that $\varphi = \Delta_U\circ \psi'$, since open immersions are monic. Since the factorization of $\psi$ through $U$ was unique, this proves that $U$ is the desired pullback. Hence the diagonal $\Delta_U:U\to U\times_SU$ is a closed immersion, so $U$ is separated over $S$, completing the proof.

Finally, suppose $\pi:X\to Y$ is a monomorphism of schemes. This follows from the fact that in any category, $\pi:X\to Y$ is a monomorphism if and only if its pullback along itself is isomorphic to $X$, and so the diagonal map is an isomorphism in this case.
`\end{proof}`

In addition to affine schemes being separated, we now show that projective schemes are separated. Since being separated is preserved under base-change, it suffices to show that $\mathbb{P}^n\to \mathsf{Spec}(\mathbb{Z})$ is separated. Let $U_0,...,U_n$ be the usual affine open cover of $\mathbb{P}^n$, so $U_i \cong \mathsf{Spec}(\mathbb{Z}[x_0/x_i,...,x_n/x_i])$. Now the map $U_i\cap U_j\to U_i\times_\mathbb{Z}U_j$, which is the restriction of the diagonal, is opposite to the map of rings
$$\mathbb{Z}[x_0/x_i, \dots,x_n/x_i,y_0/y_j, \dots,y_n/y_j]\to \mathbb{Z}[x_0/x_i , \dots x_n/x_i, x_j/x_i^{-1}]/(x_i/x_i-1)$$
given by $x_k/x_i\mapsto x_k/x_i$ and $y_k/y_j\mapsto (x_k/x_i)/(x_j/x_i)$, and so is a surjection. Thus, by [[Closed Subschemes and Immersions#^6ab1a3]] we have that $U_i\cap U_j\to U_i\times_\mathbb{Z}U_j$ is a closed immersion, and hence by [[Closed Subschemes and Immersions#^7a90ce]] we have that the diagonal is a closed immersion.

Alternatively, we could use [[Closed Subschemes and Immersions#^4164ff]] and the fact that composing $\Delta:\mathbb{P}^n\to \mathbb{P}^n\times_\mathbb{Z}\mathbb{P}^n$ with the **Segre embedding** $S:\mathbb{P}^n\times_\mathbb{Z}\mathbb{P}^n\to \mathbb{P}^{n^2+2n}$, which is a closed embedding, is equal to the composite of the **second Veronese embedding**, $\nu_2:\mathbb{P}^n\to \mathbb{P}^{{n+2\choose 2}-1}$ followed by a linear map $L:\mathbb{P}^{{n+2 \choose 2}-1}\to \mathbb{P}^{n^2+2n}$, which are both closed immersions, and so $S\circ \Delta$ is a closed immersion.

Here $S$ is given on a coordinate patch $U_i\times_\mathbb{Z}U_j$ by the ring map $\mathbb{Z}[x_{00}/x_{ij},...,x_{nn}/x_{ij}]\to \mathbb{Z}[x_0/x_i,...,x_n/x_i,y_0/y_j,...,y_n/y_j]$ which sends $x_{lk}/x_{ij}\mapsto (x_l/x_i)(y_k/y_j)$.

Note that if $U,V \subseteq X$ are open, and $X\to S$ is an $S$-scheme, then the pullback square in the proof of [[Basic Properties of Morphisms of Schemes#^630ce1]] gives the pullback square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BU%5Ctimes_XV%7D%20%26%20%7BU%5Ctimes_AV%7D%20%5C%5C%0A%09X%20%26%20%7BX%5Ctimes_AX%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{U\times_XV} &amp; {U\times_AV} \\
	X &amp; {X\times_AX}
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[from=2-1, to=2-2]
\end{tikzcd}
" /></p>

so we have an isomorphism
$$X\times_{X\times_AX}(U\times_AV)\cong U\times_XV\cong U\cap V$$

Separatedness becomes very handy when we want to deal with intersections of affine opens.

>[!proposition] Intersection of Affine Open in Separated Scheme
>Suppose $X\to \mathsf{Spec}(A)$ is a separated morphism to an affine scheme, and $U$ and $V$ are affine open subsets of $X$. Then $U\cap V$ is an affine open subset of $X$.

`\begin{proof}`
Let $U \cong \mathsf{Spec}(B)$ and $V \cong \mathsf{Spec}(C)$ be affine open subsets. Then $U\times_AV\cong \mathsf{Spec}(B\otimes_AC)$, which is affine. Now, by the pullback preceding the lemma, and the fact that the structure morphism is separated, we have that $U\cap V\to \mathsf{Spec}(B\otimes_AC)$ is a closed immersion. But closed immersions are affine, so $U\cap V$ must be affine, as desired.
`\end{proof}`

### Properties of Morphisms and Graphs

Besides allowing us to discuss notions of separatedness and quasiseparatedness, diagonal morphisms can be extremely useful for extrapolating properties of morphisms. A perspective that is important for this use of the diagonal morphism is that of graph morphisms, similar to those which define manifolds in differential geometry.

>[!def] Graph of a Morphism
>Let $\pi:X\to Y$ be a morphism of $Z$-schemes. The morphisms $\Gamma_\pi:X\to X\times_ZY$ given by $\Gamma_\pi = \langle 1_X,\pi\rangle$ is called the **graph morphism** associated with $\pi$. 

>[!proposition] Graph is Locally Closed
>The graph morphism $\Gamma_\pi$ associated with a morphism $\pi$ is a locally closed embedding. If $Y$ is separated over $Z$, then $\Gamma_\pi$ is a closed embedding. If $Y$ is quasi-separated, then $\Gamma_\pi$ is quasi-compact.

^c8c1e8

`\begin{proof}`
The pullback square in the proof of [[Basic Properties of Morphisms of Schemes#^630ce1]] with $T = Y$ and $A = Z$ gives the pullback diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09X%20%26%20%7BX%5Ctimes_ZY%7D%20%5C%5C%0A%09Y%20%26%20%7BY%5Ctimes_ZY%7D%0A%09%5Carrow%5B%22%7B%5CGamma_%5Cpi%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cpi%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5CDelta_%7BY%2FZ%7D%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	X &amp; {X\times_ZY} \\
	Y &amp; {Y\times_ZY}
	\arrow[&quot;{\Gamma_\pi}&quot;, from=1-1, to=1-2]
	\arrow[&quot;\pi&quot;', from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[&quot;{\Delta_{Y/Z}}&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

where we use the fact that $X\times_YY \cong X$. Then any property of $\Delta_{Y/Z}$ that is preserved by pullback is also shared by $\Gamma_\pi$.
`\end{proof}`


>[!thm] Cancellation Theorem for a Property $P$ of Morphisms
>Let $P$ be a class of morphisms that is preserved by base change and composition. Suppose $\pi:X\to Y$ and $\rho:Y\to Z$ are morphisms of schemes. If $\Delta_\rho:Y\to Y\times_ZY$ is in $P$, and $\rho\circ \pi$ is in $P$, then $\pi:X\to Y$ is in $P$.

^d4533c

`\begin{proof}`
By [[Basic Properties of Morphisms of Schemes#^c8c1e8]] we have the cartesian square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09X%20%26%20%7BX%5Ctimes_ZY%7D%20%5C%5C%0A%09Y%20%26%20%7BY%5Ctimes_ZY%7D%0A%09%5Carrow%5B%22%7B%5CGamma_%5Cpi%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cpi%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5CDelta_%7BY%2FZ%7D%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	X &amp; {X\times_ZY} \\
	Y &amp; {Y\times_ZY}
	\arrow[&quot;{\Gamma_\pi}&quot;, from=1-1, to=1-2]
	\arrow[&quot;\pi&quot;', from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[&quot;{\Delta_{Y/Z}}&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

Then $\Gamma_\pi$ is in $P$ since  $\Delta_\rho$ is in $P$ and $P$ is preserved by base change. Forming another pullback square,

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BX%5Ctimes_ZY%7D%20%26%20Y%20%5C%5C%0A%09X%20%26%20Z%0A%09%5Carrow%5B%22%7Bp_2%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%5Crho%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Crho%5Ccirc%20%5Cpi%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{X\times_ZY} &amp; Y \\
	X &amp; Z
	\arrow[&quot;{p_2}&quot;, from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[&quot;\rho&quot;, from=1-2, to=2-2]
	\arrow[&quot;{\rho\circ \pi}&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

we see that the projection $p_2$ is also in $P$, and since $P$ is closed under composites $\pi = p_2\circ \Gamma_\pi$ is in $P$.
`\end{proof}`

As an immediate corollary, we see that if $X\to S$ is a scheme over $S$, and $S\to T$ is a separated scheme over $T$, then $X$ is separated over $S$ if and only if it is separated over $T$. Indeed, if it is separated over $S$ then [[Basic Properties of Morphisms of Schemes#^553038]] implies that $X$ is separated over $T$. On the other hand, since closed immersions are separated the result follows by [[Basic Properties of Morphisms of Schemes#^d4533c]].

>[!proposition] Sections are Locally Closed
>Let $\mu:Z\to X$ be a morphism of schemes and let $\sigma:X\to Z$ be a section of $\mu$. Then $\sigma$ is a locally closed embedding, and if $\mu$ is separated, then $\sigma$ is a closed embedding.

`\begin{proof}`
Note that by [[Basic Properties of Morphisms of Schemes#^4e7559]] the diagonal is always locally closed, and $\mu\circ \sigma = 1_X$, which is also locally closed. Thus by [[Basic Properties of Morphisms of Schemes#^d4533c]] we have that $\sigma$ is a locally closed embedding.

If $\mu$ is separated then the diagonal is a closed immersion, and all isomorphisms are closed immersions, so $\sigma$ is a closed immersion by [[Basic Properties of Morphisms of Schemes#^d4533c]] again.
`\end{proof}`


## Proper Morphisms


Before we define proper morphisms for schemes, let us recall that a map of topological spaces is said to be **proper** if it pulls back compact sets to compact sets. In schemes properness will not simply be a morphism which is proper in the topological sense (which is closer to that of quasi-compact morphisms for us), but instead we will add certain characteristics to ensure that it yields similar properties to the topological case. In particular, this will be a nice property satisfied by projective schemes.

We will begin with universally closed morphisms.

>[!def] Universally Closed
>A morphism of schemes $\pi:X\to Y$ is **universally closed** if for every $Z\to Y$ the induced morphism obtained by pullback, $Z\times_YX\to Z$, is closed.

In general, if $P$ is some property of schemes/morphisms of schemes, then a morphism of schemes is said to be **universally $P$** if it remains $P$ under base change. Note that in fact the base change of a universally $P$ morphism will itself be universally $P$, since iterated base-changes can be identified with a single base-change in a rectangle like diagram.

Recall that for locally compact Hausdorff spaces with countable bases for their topologies, being universally closed is equivalent to being proper.

>[!def] Proper Morphism
>We say a morphism of schemes $\pi:X\to Y$ is **proper** if it is separated, of finite type (i.e. locally of finite type and quasi-compact), and universally closed. An $S$ scheme $X$ is **proper** if the structure morphism $X\to S$ is proper.

A wealth of examples of proper morphisms come from finite morphisms.

>[!proposition] Finite Morphisms are Proper
>If $\pi:X\to Y$ is a finite morphism, then $\pi$ is proper.

`\begin{proof}`
Since finite morphisms are affine, $\pi$ is separated. $\pi$ is also trivially of finite type. Note that finite morphisms are stable under base change by [[Basic Properties of Morphisms of Schemes#^3c1ceb]], so it suffices to show that finite morphisms are closed. Finite morphisms are closed, but this point is a bit subtle **TBD**.
`\end{proof}`

We now show that proper morphisms are another class of **good morphisms**.

>[!proposition] Properties of Proper Morphisms
>1. Proper morphisms are stable under base change
>2. Proper morphisms are local on the target
>3. Proper morphisms are closed under composition
>4. Proper morphisms are closed under product
>5. If $X\xrightarrow{\pi}Y\xrightarrow{\rho}$ is proper and $\rho$ is separated, then $\pi$ is proper.

`\begin{proof}`


#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024
[^2]: Introduction to Commutative Algebra | Mathematical Association of America. (n.d.). https://maa.org/press/maa-reviews/introduction-to-commutative-algebra. Accessed 20 May 2024
