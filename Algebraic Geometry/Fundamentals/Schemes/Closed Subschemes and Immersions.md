---
date: 2024-06-08T13:49:00
tags:
  - AlgebraicGeometry
  - Sheaves
  - Schemes
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

In these notes we investigate properties and characterizations of closed subschemes and closed immersions, following the work of Vakil[^1]. Unlike open subschemes which were largely determined by their underlying set we will see that closed subschemes can be much more nuanced. For instance, if $B$ is a cring and $I,J$ are distinct ideals of $B$ for which $V(I) = V(J)$ (i.e. $\sqrt{I} = \sqrt{J}$), then as point sets the schemes $\mathsf{Spec}(B/I)$ and $\mathsf{Spec}(B/J)$ agree, but as schemes they differ.

## Closed Immersions

We define the notion of closed immersions via local models, observing that in an affine scheme $\mathsf{Spec}(B)$, closed subschemes are quotients $\mathsf{Spec}(B/I)\hookrightarrow \mathsf{Spec}(B)$.

>[!def] Closed Immersion
>A morphism of schemes $f:X\to Y$ is a **closed immersion** if it is affine and for every affine open subset $\mathsf{Spec}(B)$ in $Y$ with $f^{-1}(\mathsf{Spec}(B))\cong \mathsf{Spec}(A)$, the map $B\to A$ is surjective (i.e. $A\cong B/I$ for some ideal $I$ of $B$). If $X$ is a subset of $Y$ and $f$ is the inclusion on the level of topological spaces, we say that $X$ is a **closed subscheme** of $Y$.

We will soon come across a number of equivalent formulations of the notion of a closed immersion/embedding. Observe that from the definition we have that **all closed immersions are finite morphisms**, and hence also of **finite type**.


First we observe that being a homeomorphism onto a closed set is local on the target.

>[!lem] Closed Homeomorphism Local on Target
>Let $f:X\to Y$ be a map of topological spaces. Suppose $Y = \bigcup_{i \in I}U_i$ is an open cover of $Y$ such that $f\vert_{f^{-1}(U_i)}:f^{-1}(U_i)\to U_i$ is a homeomorphism onto a closed subset of $U_i$ for each $i$. Then $f$ is a homeomorphism onto a closed subset.

^98159f

`\begin{proof}`
Let $f:X\to Y$ be a map of topological spaces as in the statement of the lemma, and let $Y = \bigcup_{i \in I}U_i$ be the open cover described in the lemma. By assumption for each $i \in I$ we have a continuous map $g_i:f(f^{-1}(U_i))\to f^{-1}(U_i)$ which is the inverse of $f\vert_{f^{-1}(U_i)}$. 

First, note that by assumption $f(f^{-1}(U_i))$ is a closed subset of $U_i$ for each $i$. Additionally, $f(X)\cap U_i = f(f^{-1}(U_i))$. Now, $(Y\backslash f(X))\cap U_i = U_i\backslash f(f^{-1}(U_i))$ is open in $U_i$, and hence in $Y$, for all $i \in I$ as each $U_i$ is open in $Y$. Since the $U_i$ cover $Y$ this implies that $Y\backslash f(X) = \bigcup_{i \in I}(Y\backslash f(X))\cap U_i$ is open, being the union of open sets, and so $f(X)$ is closed in $Y$.

Now, note that $f(f^{-1}(U_i))$ are open in $f(X)$ under the subspace topology. Further, for $i,j \in I$, since $f\vert_{f^{-1}(U_i)}$ and $f\vert_{f^{-1}(U_j)}$ are homeomorphisms onto their images which agree on their intersection, their inverses $g_i$ and $g_j$ must also agree on their intersection by uniqueness of the inverse to a function. Then as the $g_i:f(f^{-1}(U_i))\to f^{-1}(U_i)$ for $i \in I$ are continuous maps which agree on their intersections, and whose domains form an open cover of $f(X)$, it follows that we have a unique continuous map $g:f(X)\to X$ given by the $g_i$, $i \in I$, from Analysis I. In particular, for all $x \in X$ we have that $x \in f^{-1}(U_i)$ for some $i$, so 
$$g(f(x)) = g_i(f(x)) = x$$
and consequently $f(g(f(x))) = f(x)$, so $g:f(X)\to X$ and $f:X\to f(X)$ are inverse. This completes the proof that $f$ is a homeomorphism onto a closed subset of $Y$.
`\end{proof}`

Note that $\mathsf{Spec}(B/I)\hookrightarrow \mathsf{Spec}(B)$ is a homeomorphism onto the closed subset $V(I)$ on the level of topological spaces. Thus, [[Closed Subschemes and Immersions#^98159f]] implies that a closed immersion $f:X\to Y$ is necessarily a homeomorphism onto a closed subset of $Y$. This already gives us a very powerful tool when it comes to computing stalks in the presence of closed immersions.

>[!lem] Stalks for Closed Mappings
>If $f:X\to Y$ is a map of schemes where $f$ is a homeomorphism onto a closed subset of $Y$, then for $x \in X$,
>$$(f_*\mathcal{O}_X)_{f(x)} \cong \mathcal{O}_{X,x} $$
>and for $y \in Y\backslash f(X)$, $(f_*\mathcal{O}_X)_y \cong 0$.

`\begin{proof}`
By definition of the stalk at a point, we have that for $x \in X$,
$$(f^*\mathcal{O}_X)_{f(x)} \cong \lim\limits_{\to,f(x) \in U}\mathcal{O}_X(f^{-1}(U))$$
But, as $f$ is a homeomorphism onto a closed subset of $Y$, for every $V \subseteq X$ open there exists $U \subseteq Y$ open such that $f(V) = U\cap f(X)$, and $f^{-1}(U) = V$, as $f$ is injective. Thus, the colimit $\lim\limits_{\to,x \in V}\mathcal{O}_X(V)$ is taken over the same set of opens, so 
$$(f^*\mathcal{O}_X)_{f(x)} \cong \lim\limits_{\to,f(x) \in U}\mathcal{O}_X(f^{-1}(U)) = \lim\limits_{\to,x \in V}\mathcal{O}_X(V) \cong \mathcal{O}_{X,x}$$
as desired.

Now, let $y \in Y\backslash f(X)$. Since $f(X)$ is closed, $Y\backslash f(X)$ is open, so from Assignment 1 the stalk $(f_*\mathcal{O}_X)_y$ can be computed using opens in $Y\backslash f(X)$ containing $y$. But for any $V \subseteq Y\backslash f(X)$ open, $(f_*\mathcal{O}_X)(V) = \mathcal{O}_X(\emptyset) \cong 0$, which is the zero ring. This last isomorphism follows by the sheaf condition since we can take an empty cover of $\emptyset$, and the sheaf condition for this cover is equivalent to the statement that $\mathcal{O}_X(\emptyset)$ is the terminal object in the category of commutative rings with identity, which is the zero ring. This completes the proof.
`\end{proof}`
In addition to being a homeomorphism onto a closed subset, the local definition of a closed immersion implies that all closed immersions $f:X\to Y$ induce epic maps on the level of structure sheaves, $f^\#:\mathcal{O}_Y\to f_*\mathcal{O}_X$, which corresponds to surjections on the level of stalks. These two properties in fact fully characterize closed immersions. By the [[Basic Properties of Morphisms of Schemes#^b058ea]] it suffices to show that these properties are equivalent to the existence of an affine cover of $Y$ satisfying the properties of a closed immersion. We prove this in the following three lemmas.

>[!lem] Closed Immersion Affine Auxillary Lemma
>If $A$ is a cring, then $\mathsf{Spec}(f):\mathsf{Spec}(B)\to \mathsf{Spec}(A)$ is surjective on the level of stalks and a homeomorphism onto a closed subset if and only if $f:A\to B$ is surjective.

^6ab1a3

`\begin{proof}`
If $f:A\to B$ is surjective, then for any $\mathfrak{p} \in \mathsf{Spec}(B)$ with pre-image $q^{-1}(\mathfrak{p}) \in \mathsf{Spec}(A)$, the induced map on localizations in the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09A%20%26%20%7BB%7D%20%5C%5C%0A%20%20%20%20%09%7BA_%7Bq%5E%7B-1%7D(%5Cmathfrak%7Bp%7D)%7D%7D%20%26%20%7BB_%5Cmathfrak%7Bp%7D%7D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf_%5Cmathfrak%7Bp%7D%7D%22'%2C%20dashed%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	A &amp; {B} \\
    	{A_{q^{-1}(\mathfrak{p})}} &amp; {B_\mathfrak{p}}
    	\arrow[&quot;f&quot;, from=1-1, to=1-2]
    	\arrow[from=1-2, to=2-2]
    	\arrow[from=1-1, to=2-1]
    	\arrow[&quot;{f_\mathfrak{p}}&quot;', dashed, from=2-1, to=2-2]
    \end{tikzcd}
" /></p>
is surjective.

Now, $f$ being surjective implies $B\cong A/\ker(f)$, and so on the level of topological spaces $\mathsf{Spec}(f)$ induces a homeomorphism with the closed subset $V(\ker(f))$

On the other hand suppose we have surjections on the level of stalks $f^\#_\mathfrak{p}:A_{\mathfrak{p}}\to B_\mathfrak{p}$, where $\mathfrak{p}$ is prime in $A$, and $B_\mathfrak{p}$ denotes the localization of $B$ at the multiplicatively closed subset $f(A\backslash \mathfrak{p})$. But then by [[Atiyah Localization#^191764]] we have that $f:A\to B$ is surjective.
`\end{proof}`

>[!lem] Closed Immersion Auxillary Lemma
>Let $f:X\to \mathsf{Spec}(A)$ be a map of schemes which is a homeomorphism onto a closed subset and surjective on the level of sheaves. Then there exists an affine open cover of $\mathsf{Spec}(A) = \bigcup_{i \in I}D(a_i)$ in terms of basic open sets, $a_i \in A$, such that for each $i \in I$ there exists an ideal $I_i \subseteq A_{a_i}$ such that $f^{-1}(D(a_i)) \cong \mathsf{Spec}(A_{a_i}/I_i)$.

^a1af70

`\begin{proof}`
Suppose $f:X\to \mathsf{Spec}(A)$ is a closed immersion. Since $f(X)$ is a closed subset of $\mathsf{Spec}(A)$, there exists an ideal $I \subseteq A$ such that $f(X) = V(I) = \{\mathfrak{p} \in \mathsf{Spec}(A):I \subseteq \mathfrak{p}\}$. Consider an affine open cover $X = \bigcup_{i \in I}U_i$, where $U_i \cong \mathsf{Spec}(A_i)$. Fix $i \in I$. Then by assumption $f(U_i)$ is open in the closed subset $f(X) = V(I)$ of $\mathsf{Spec}(A)$. Let $f(U_i) = \bigcup_{j \in J_i}D(a_{i,j}+I)$ be an open cover by basic opens in $V(I)\cong \mathsf{Spec}(A/I)$ where $a_{i,j} \in A$. Note that $D(a_{i,j}+I) = D(a_{i,j})\cap V(I)$.

Since $U_i \cong \mathsf{Spec}(A_i)$, the restriction $f\vert_{U_i}:U_i\to f(X)\cong \mathsf{Spec}(A/I)$ is a map of affine schemes. Thus, as the inclusion of affine schemes into schemes is fully faithful, we have a cring homomorphism $f_i:A/I\to A_i$ which represents $f\vert_{U_i}$. Recall that
$$\mathsf{Spec}(f_i)^{-1}(D(a_{i,j}+I)) = D(f_i(a_{i,j}+I))$$
so by the isomorphism $U_i\cong \mathsf{Spec}(A_i)$, it follows that $f^{-1}(D(a_{i,j}+I))$ is an affine open subscheme of $U_i$ for each $j \in J_i$. 

Since being a homeomorphism onto a closed subset, or giving an epimorphism on the level of structure sheaves, are both local for each $a_{i,j}$, $f\vert_{f^{-1}(D(a_{i,j}+I))}:f^{-1}(D(a_{i,j}+I))\to D(a_{i,j}+I)$ is a homeomorphism onto a closed subset with epimorphism on the level of structure sheaves. Then by [[Closed Subschemes and Immersions#^6ab1a3]] since $f^{-1}(D(a_{i,j}+I))$ is an affine scheme, it follows that there exists exists an ideal $I_{i,j} \subseteq (A/I)_{a_{i,j}+I}$ such that $f^{-1}(D(a_{i,j}+I)) \cong \mathsf{Spec}((A/I)_{a_{i,j}+I}/I_{i,j})$.

Finally, since $f(X)$ is closed in $\mathsf{Spec}(A)$ we can cover $\mathsf{Spec}(A)\backslash f(X)$ by basic open affine subsets that do not intersect $f(X)$. Then for any such $D(a'_i) \subseteq \mathsf{Spec}(A)\backslash f(X)$, $f^{-1}(D(a'_i)) = \emptyset$, which is the spectrum of the zero ring. In other words, for any such open affine covering of $\mathsf{Spec}(A)\backslash f(X)$, together with the open covering by $D(a_{i,j})$ of $f(X)$, we have that the hypotheses hold, completing the proof.
`\end{proof}`

>[!lem] Closed Immersion Characterization
>Let $f:X\to Y$ be a map of schemes. Then $f$ is a homeomorphism onto a closed subset of $Y$ and epic on structure sheaves if and only if there exists an open affine cover of $Y = \bigcup_{i \in I}U_i$ such that $U_i \cong \mathsf{Spec}(A_i)$ and there exists $I_i \subseteq A_i$ for which $f^{-1}(U_i)\cong \mathsf{Spec}(A_i/I_i)$.

^7a90ce

`\begin{proof}`
Let $f:X\to Y$ be a map of schemes. As commented previously the if direction holds. Now, suppose $f$ is a homeomorphism onto a closed subset and epic on structure sheaves. Let $Y = \bigcup_{k \in K}V_k$ where $V_k \cong \mathsf{Spec}(A_k)$ be an open affine cover of $Y$. Then $X = \bigcup_{k \in K}f^{-1}(V_k)$ is an open cover of $X$. 

Note that each $f\vert_{f^{-1}(V_k)}:f^{-1}(V_k)\to V_k$ is a homeomorphism onto a closed subset and epic on structure sheaves, with $V_k$ affine. Thus, by [[Closed Subschemes and Immersions#^a1af70]] it follows that there exists a cover of $V_k = \bigcup_{j \in J_k}U_{j,k}$ by open affine subschemes, $U_{j,k} \cong \mathsf{Spec}(A_{j,k})$, such that there exist ideals $I_{j,k} \subseteq A_{j,k}$ with $f^{-1}(U_{j,k}) \cong \mathsf{Spec}(A_{j,k}/I_{j,k})$. But as the $V_k$ are open in $Y$, so are the $U_{j,k}$, so $Y = \bigcup_{k \in K}\bigcup_{j \in J_k}U_k$ is an open affine cover of $Y$ satisfying the claim. 
`\end{proof}`

Note that closed immersions contain isomorphisms and are closed under composition. In addition, closed immersions are preserved under base change, as we now show.

>[!lem] Closed Immersion Affine Base Change
>If $\mathsf{Spec}(g):\mathsf{Spec}(D)\to \mathsf{Spec}(A)$ is a closed immersion of affine schemes, and $\mathsf{Spec}(f):\mathsf{Spec}(B)\to \mathsf{Spec}(A)$ is any other map of affine schemes, then the pullback of $\mathsf{Spec}(g)$ along $\mathsf{Spec}(f)$ is a closed immersion of affine schemes.

^771482

`\begin{proof}`
Since pullbacks of affine schemes are computed by pushforwards in the category $\mathsf{CRing}$, it is sufficient to work with the pushout diagram. Observe that for the maps given in the lemma statement, the pushout of crings is 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7BD%5Cotimes_AB%7D%20%26%20B%20%5C%5C%0A%20%20%20%20%09%7BD%7D%20%26%20A%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D2-2%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-2%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_2%7D%22'%2C%20from%3D1-2%2C%20to%3D1-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_1%7D%22%2C%20from%3D2-1%2C%20to%3D1-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{D\otimes_AB} &amp; B \\
    	{D} &amp; A
    	\arrow[&quot;g&quot;, from=2-2, to=2-1]
    	\arrow[&quot;f&quot;', from=2-2, to=1-2]
    	\arrow[&quot;{p_2}&quot;', from=1-2, to=1-1]
    	\arrow[&quot;{p_1}&quot;, from=2-1, to=1-1]
    	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=2-2]
    \end{tikzcd}
" /></p>
Note $g$ is surjective. Now, let $\sum_{i =1}^nd_i\otimes b_i \in D\otimes_AB$ be an arbitrary element of the tensor. For each $1 \leq i \leq n$ there exists $a_i \in A$ such that $g(a_i) = d_i$. Then by definition of $p_2$ we have that 
$$p_2\left(\sum_{i=1}^nf(a_i)b_i\right)= \sum_{i=1}^n1\otimes f(a_i)b_i = \sum_{i=1}^ng(a_i)\otimes b_i = \sum_{i=1}^nd_i\otimes b_i$$
sing the bilinearity of the tensor product with respect to the $A$-algebra structures of $B$ and $D$. Thus, $p_2$ is surjective, and hence $\mathsf{Spec}(p_2)$ is a closed immersion.
`\end{proof}`

>[!proposition] Closed Immersion Closed Under Base Change
>The pullback of a closed immersion along any map of schemes is again a closed immersion.

^42a50b

`\begin{proof}`
Let $f:X\to Z$ be a closed immersion of schemes and let $g:Y\to Z$ be an arbitrary map of schemes. We form the pullback in schemes to obtain the commuting square
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7BX%5Ctimes_ZY%7D%20%26%20Y%20%5C%5C%0A%20%20%20%20%09X%20%26%20Z%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_2%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_1%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{X\times_ZY} &amp; Y \\
    	X &amp; Z
    	\arrow[&quot;f&quot;', from=2-1, to=2-2]
    	\arrow[&quot;g&quot;, from=1-2, to=2-2]
    	\arrow[&quot;{p_2}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;{p_1}&quot;', from=1-1, to=2-1]
    	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=2-2]
    \end{tikzcd}
" /></p>
We claim that $p_2:X\times_ZY\to Y$ is a closed immersion of schemes. 

Let $Z = \bigcup_{i \in I}W_i$ be an open affine cover of $Z$ such that $f^{-1}(W_i)$ is an open affine subscheme of $X$ for each $i\in I$, which exists since $f$ is a closed immersion. Note that $f\vert_{f^{-1}(W_i)}:f^{-1}(W_i)\to W_i$ is a closed immersion for each $i \in I$. For each $i \in I$, let $g^{-1}(W_i) = \bigcup_{k \in K_i}V_{i,k}$ be an open affine cover of $g^{-1}(W_i)$. Using [[Closed Subschemes and Immersions#^771482]] we have the pullback for each $i \in I$ and $k \in K_i$,
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7Bp_1%5E%7B-1%7D(f%5E%7B-1%7D(W_i))%5Ccap%20p_2%5E%7B-1%7D(V_%7Bi%2Ck%7D)%7D%20%26%20V_%7Bi%2Ck%7D%20%5C%5C%0A%20%20%20%20%09f%5E%7B-1%7D(W_i)%20%26%20W_i%0A%20%20%20%20%09%5Carrow%5B%22f%5Cvert_%7Bf%5E%7B-1%7D(W_i)%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22g%5Cvert_%7BV_%7Bi%2Ck%7D%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_2%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp_1%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{p_1^{-1}(f^{-1}(W_i))\cap p_2^{-1}(V_{i,k})} &amp; V_{i,k} \\
    	f^{-1}(W_i) &amp; W_i
    	\arrow[&quot;f\vert_{f^{-1}(W_i)}&quot;', from=2-1, to=2-2]
    	\arrow[&quot;g\vert_{V_{i,k}}&quot;, from=1-2, to=2-2]
    	\arrow[&quot;{p_2}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;{p_1}&quot;', from=1-1, to=2-1]
    	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=2-2]
    \end{tikzcd}
" /></p>
with the horizontal map $p_1^{-1}(f^{-1}(W_i))\cap p_2^{-1}(V_{i,k}) \to V_{i,k}$ being a closed immersion, where $p_1^{-1}(f^{-1}(W_i))\cap p_2^{-1}(V_{i,k})$ is an affine open in $X\times_ZY$ since the pullback of affine schemes is affine. Note that as $f\circ p_1 = g\circ p_2$ and $g(V_{i,k}) \subseteq W_i$, $p_2^{-1}(V_{i,k}) \subseteq (g\circ p_2)^{-1}(W_i) = (f\circ p_1)^{-1}(W_i) = p_1^{-1}(f^{-1}(W_i))$. Hence, we have that $p_1^{-1}(f^{-1}(W_i))\cap p_2^{-1}(V_{i,k}) = p_2^{-1}(V_{i,k})$, which implies that by the above work $p_2\vert_{p_2^{-1}(V_{i,k})}:p_2^{-1}(V_{i,k})\to V_{i,k}$ is a closed immersion between affine schemes. But now $Y = \bigcup_{i \in I}\bigcup_{k \in K_i}V_{i,k}$ is an affine open cover of $Y$, so as being a closed immersion is affine local on the target we have that $p_2:X\times_ZY\to Y$ is a closed immersion, as desired.
`\end{proof}`
Next we show that closed immersions satisfy an additional property on top of being composable.

>[!proposition] Closed Immersions are Left-factor Closed
>Let $X,Y,Z$ be schemes and let $f:X\to Y$ and $g:Y\to Z$ be maps of schemes. If $g$ is a closed immersion and $g\circ f$ is a closed immersion then $f$ is a closed immersion.

^4164ff

`\begin{proof}`
First, $g:Y\to Z$ and $g\circ f:X\to Z$ are homeomorphisms onto a closed subspace of $Z$. Since $g\circ f$ is a homeomorphism onto its image, we must have that $f$ is injective. Further, $g(f(X))$ is a closed subset of $Z$, so $g^{-1}(g(f(X))) = f(X)$ must be a closed subset of $Y$. Finally, if $U \subseteq X$ is an open subset, $g(f(U))$ is open in $g(f(X)) \subseteq g(Y)$. It follows that $f(U)$ must be open in $f(X)$ as $g$ is a homeomorphism onto its image, so $f$ is also a homeomorphism onto its image in $Y$.

To show $f$ is a closed immersion it is sufficient to show that $f^\#_x:\mathcal{O}_{Y,f(x)}\to \mathcal{O}_{X,x}$ is surjective for every $x \in X$. But $g\circ f$ is a closed immersion by assumption, so for every $x \in X$, $(g\circ f)^\#_x:\mathcal{O}_{Z,g(f(x))}\to \mathcal{O}_{X,x}$ is surjective. Now, again by uniqueness of the map on stalks we have a commutative diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7B%5Cmathcal%7BO%7D_%7BZ%2Cg(f(x))%7D%7D%20%26%26%20%7B%5Cmathcal%7BO%7D_%7BX%2Cx%7D%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7B%5Cmathcal%7BO%7D_%7BY%2Cf(x)%7D%7D%0A%20%20%20%20%09%5Carrow%5B%22%7B(g%5Ccirc%20f)%5E%5C%23_x%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E%5C%23_x%7D%22'%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bg%5E%5C%23_%7Bf(x)%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{\mathcal{O}_{Z,g(f(x))}} &amp;&amp; {\mathcal{O}_{X,x}} \\
    	&amp; {\mathcal{O}_{Y,f(x)}}
    	\arrow[&quot;{(g\circ f)^\#_x}&quot;, from=1-1, to=1-3]
    	\arrow[&quot;{f^\#_x}&quot;', from=2-2, to=1-3]
    	\arrow[&quot;{g^\#_{f(x)}}&quot;', from=1-1, to=2-2]
    \end{tikzcd}
" /></p>
so  $(g\circ f)^\#_x = f^\#_x\circ g^\#_{f(x)}$. By the surjectivity of the composite cring homomorphism it follows that $f^\#_x$ must also be surjective.
`\end{proof}`

## Ideal Sheaf

Another very important classification of closed immersions comes from the introduction of what is known as the **ideal sheaf**.

>[!def] Ideal Sheaf
>An **ideal sheaf** on a space $Y$ is a sub-$\mathcal{O}_Y$-module $\mathscr{I}$ of $\mathcal{O}_Y$.

A closed immersion $\pi:X\hookrightarrow Y$ determines an ideal sheaf on $Y$, namely the kernel $\mathscr{I}_{X/Y}$ of the map of $\mathcal{O}_Y$-modules
$$\mathcal{O}_Y\to \pi_*\mathcal{O}_X$$
From our previous work we have an exact sequence of $\mathcal{O}_Y$-modules
$$0\to \mathscr{I}_{X/Y}\to \mathcal{O}_Y\to \pi_*\mathcal{O}_X\to 0$$
For each affine open subset $\mathsf{Spec}(B)$ of $Y$, $\mathsf{Spec}(B)\hookrightarrow Y$ determines an ideal $I(B) \subseteq B$, and varying over the base of affine opens we have an $\mathcal{O}$-module over the base, which extends to a $\mathcal{O}_Y$-module on $Y$, and the cokernel of $\mathscr{I}\hookrightarrow \mathcal{O}_Y$ is $\pi_*\mathcal{O}_X$. 

Not every sheaf of ideals yields a closed subscheme, so we must be careful. For example, if $\mathscr{I}_{X/Y}$ is the kernel sheaf, and $U = \mathsf{Spec}(B)$ is an affine open subscheme of $Y$, then we have the exact sequence
$$0\to I(B)\to \mathcal{O}_Y(U)\to \mathcal{O}_X(\pi^{-1}(U))$$
Then 
$$0\to I(B)_f\to \mathcal{O}_Y(U)_f\to \mathcal{O}_X(\pi^{-1}(U))_{\pi^\#f}$$
is the same exact sequence for $I(B_f)$, and so $I(B_f) \cong I(B)_f$, which is not true in general for ideal sheaves. In general if $\mathscr{I}$ is an ideal sheaf of $\mathcal{O}_Y$, then for $s \in \mathscr{I}(U)$ we have a natural map $\mathscr{I}(U)_s\to \mathscr{I}(U_s)$ induced by the natural map $\mathcal{O}_Y(U)_s\to \mathcal{O}_Y(U_s)$, which need not be an isomorphism. We now show that this is really the only restriction.

>[!proposition] Kernel Ideal Sheaf Classification
>If $\mathscr{I}$ is an ideal sheaf on $Y$ such that for every affine open subset $\mathsf{Spec}(B)$ and each $f \in B$ the restriction $B\to B_f$ induces an isomorphism $I(B_f)\cong I(B)_f$, then there exists a unique closed subscheme $X\hookrightarrow Y$ such that $\mathscr{I} = \mathscr{I}_{X/Y}$.

`\begin{proof}`
**TBD**
`\end{proof}`

>[!def] Vanishing Scheme
>Let $Y$ be a scheme and $S\subseteq \Gamma(Y,\mathcal{O}_Y)$. Define the closed subscheme **cut out by $S$**, or **vanishing scheme of $S$**, $V(S)$, to be the closed subscheme determined by the ideal sheaf $\mathscr{I}$ given on an affine open $\mathsf{Spec}(B)$ by $\mathscr{I}(\mathsf{Spec}(B)) = B/\langle \text{res}_{Y,\mathsf{Spec}(B)}S\rangle$.

## Locally Closed Embeddings



#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024