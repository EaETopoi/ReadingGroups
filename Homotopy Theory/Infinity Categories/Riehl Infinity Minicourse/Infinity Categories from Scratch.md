---
date: 2024-05-17T14:02:00
tags:
  - InfinityCategories
  - Homotopy
  - Minicourse
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

The aim of this course is to give a precise account to the theory of infinity categories, paralleling the theory of ordinary categories. We begin with a schematic definition. An $(\infty,1)$-category is a category **weakly enriched** in $\infty$-groupoids. On the other hand, a model is an explicit mathematical object which realizes this schematic idea. A few examples of such models are as follows:

- Quasicategories (aka weak Kan complexes)
- Complete Segal spaces
- Segal categories
- Naturally marked simplicial sets

The quasi-categorical model, in a project initiated by Andre Joyal and continued by Lurie, has been expanded on to realize a number of the concepts of category theory in infinity categories. A primary question at this point is does it matter which model we use? The challenge is that the basic definitions in quasi-categories don't fully exist in a non-schematic way in other ways.

Moving forward, the term $\infty$-category will refer to any of the above stated models. 

Dr. Riehl in this minicourse approaches $\infty$-category theory in a "model independent way", which is to say we give and work with definitions that are stated generally enough that all the cases in each model are just special cases. Further, all theorems that are proved will apply to any of the given models. The theory Riehl develops will also be compatible with that of Joyal and Lurie, which uses quasi-categories. Riehl's development will also be invariant under change of models of $(\infty,1)$-categories, which is to say that we will have certain **change of model functors** such that if we ask the question "will a given functor have an adjoint" the answer will be the same in any model. Finally, the synthetic approach Riehl takes ensures that the theory and proofs is as simple as possible.


## A Look Into the Future

Each type/model/axiomatic system for $\infty$-categories comes with a notion of **$\infty$-functor** between $\infty$-categories. As a consequence of the axiomatization, we will also be provided with **$\infty$-natural transformations**. 

Recall that in ordinary category theory we have categories, functors between categories, and natural transformations between functors, which assemble into a strict $2$-category $\mathsf{Cat}_2$. We will show by the end of the lecture that $\infty$-categories, $\infty$-functors, and $\infty$-natural transformations, will also give a 2-category called the **homotopy $2$-category**. This homotopy 2-category will consist of the following data
- $\infty$-categories $A,B$ as objects,
- $\infty$-functors $F:A\to B$ as morphisms (or 1-cells)
- $\infty$-natural transformations $\eta:F\Rightarrow G:A\to B$ as 2-cells.
Note that from the structure of a 2-category we should be able to compose 2-cells, i.e. $\infty$-natural transformations, vertically and horizontally. In particular, for fixed $\infty$-categories $A,B$, we obtain a 1-category $\infty\mathsf{Fun}(A,B)$ of $\infty$-functors and $\infty$-natural transformations between them. More generally, we can consider **composition by pasting** when discussing vertical and horizontal composites simultaneously, where the middle/4-interchange law gives us unique composites of valid pasting diagrams.

With this notions assumed, we can immediately start defining classical categorical notions such as adjunctions.

>[!def] Adjunction
>An **adjunction** between $\infty$-categories $A$ and $B$ is a pair of functors $F:A\to B$ and $G:B\to A$ together with a pair of $2$-cells $\eta:1_A\Rightarrow G\circ F$ and $\epsilon:F\circ G\Rightarrow 1_B$ satisfying the triangle equalities
>$$(\epsilon*F)\circ (F*\eta) = 1_{F}\;\; (G*\epsilon)\circ (\eta*G)=1_{G}$$
>(Add pastings) We call $F$ a **left-adjoint** and $G$ a **right-adjoint**, and write $F\dashv G$.

From this definition our results for classical category theory immediately follows. For example, we obtain composition of adjunctions.

>[!proposition] Adjunction Composite
>Adjunctions compose, which is to say 
><p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20B%20%26%20C%20%26%20A%20%26%20C%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22F%22%2C%20shift%20left%3D2%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22G%22%2C%20shift%20left%3D2%2C%20from%3D1-2%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7BF'%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7BG'%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-3%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Ccong%22%7Bdescription%7D%2C%20draw%3Dnone%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D4%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7BF'%5Ccirc%20F%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D5%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7BG%5Ccirc%20G'%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-5%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D2%2C%20to%3D3%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D4%2C%20to%3D5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]A &amp; B &amp; C &amp; A &amp; C\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;F&quot;, shift left=2from=1-1, to=1-2]\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;G&quot;, shift left=2, from=1-2, to=1-1]\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{F'}&quot;, shift left=2, from=1-2, to=1-3]\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, &quot;{G'}&quot;, shift left=2, from=1-3, to=1-2]\arrow[&quot;\cong&quot;{description}, draw=none, from=1-3, to=1-4]\arrow[&quot;&quot;{name=4, anchor=center, inner sep=0}, &quot;{F'\circ F}&quot;, shift left=2, from=1-4, to=1-5]\arrow[&quot;&quot;{name=5, anchor=center, inner sep=0}, &quot;{G\circ G'}&quot;, shift left=2, from=1-5, to=1-4]\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=2, to=3]\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=4, to=5]\end{tikzcd}" /></p>

`\begin{proof}`
To prove the claim we must provide the appropriate unit and co-unit satisfying the triangle identities for the adjunction. We will provide the necessary diagram in one such case:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%26%26%20A%20%5C%5C%0A%09%26%20B%20%26%26%20B%20%26%26%20B%20%5C%5C%0A%09%26%26%20C%20%26%26%26%26%20C%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7BF'%7D%22'%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22G%22'%2C%20from%3D2-4%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-4%2C%20to%3D2-6%5D%0A%09%5Carrow%5B%22%7BF'%7D%22%2C%20from%3D2-6%2C%20to%3D3-7%5D%0A%09%5Carrow%5B%22%7BG'%7D%22'%2C%20from%3D3-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3-3%2C%20to%3D3-7%5D%0A%09%5Carrow%5B%22%5Ceta%22%2C%20shorten%20%3C%3D4pt%2C%20shorten%20%3E%3D4pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3E%3D3pt%2C%20Rightarrow%2C%20from%3D1-5%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%7B%5Ceta'%7D%22%2C%20shorten%20%3C%3D3pt%2C%20Rightarrow%2C%20from%3D1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon'%7D%22%2C%20shorten%20%3C%3D4pt%2C%20shorten%20%3E%3D4pt%2C%20Rightarrow%2C%20from%3D2%2C%20to%3D3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp;&amp;&amp; A \\
	&amp; B &amp;&amp; B &amp;&amp; B \\
	&amp;&amp; C &amp;&amp;&amp;&amp; C
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-1, to=1-5]
	\arrow[&quot;F&quot;', from=1-1, to=2-2]
	\arrow[&quot;F&quot;, from=1-5, to=2-6]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=2-2, to=2-4]
	\arrow[&quot;{F'}&quot;', from=2-2, to=3-3]
	\arrow[&quot;G&quot;', from=2-4, to=1-5]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=2-4, to=2-6]
	\arrow[&quot;{F'}&quot;, from=2-6, to=3-7]
	\arrow[&quot;{G'}&quot;', from=3-3, to=2-4]
	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, Rightarrow, no head, from=3-3, to=3-7]
	\arrow[&quot;\eta&quot;, shorten &lt;=4pt, shorten &gt;=4pt, Rightarrow, from=0, to=1]
	\arrow[&quot;\epsilon&quot;, shorten &gt;=3pt, Rightarrow, from=1-5, to=2]
	\arrow[&quot;{\eta'}&quot;, shorten &lt;=3pt, Rightarrow, from=1, to=3-3]
	\arrow[&quot;{\epsilon'}&quot;, shorten &lt;=4pt, shorten &gt;=4pt, Rightarrow, from=2, to=3]
\end{tikzcd}
" /></p>
where by interchange and the triangle identities for the individual adjunctions this diagram gives the identity natural transformation on $F'\circ F$. The other triangle identity is similar.
`\end{proof}`

Continuing we can define equivalences of $\infty$-categories.

>[!def] Equivalence
>An **equivalence** between $\infty$-categories $A$ and $B$ is a pair of functors $F:A\to B$ and $G:B\to A$ together with $\infty$-natural isomorphisms $\eta:1_A\Rightarrow G\circ F$ and $\eta:F\circ G\Rightarrow 1_B$.

>[!exercise]
>Any equivalence, in the sense just defined, can be promoted to an adjoint equivalence by changing one of the 2-cell isomorphisms.

`\begin{proof}`
Let $A$ and $B$ be objects of a $2$-category $\mathcal{C}$, and let $F:A\to B$ and $G:B\to A$ be maps forming an equivalence via 2-cell isomorphisms $\eta:1_A\Rightarrow G\circ F$ and $\epsilon:F\circ G\Rightarrow 1_B$. We wish to adjust one of these 2-cell isomorphisms to give an adjoint equivalence. For this we fix $\eta$ and define a new $\epsilon'$. To see how $\epsilon':F\circ G\Rightarrow 1_{B}$ must be defined, note that it must be a 2-cell isomorphism and we must have that 
$$(\epsilon'*F) \circ (F*\eta) = 1_{F}\;\;(G*\epsilon')\circ (\eta*G) = 1_{G}$$
Since $\eta$ is a natural isomorphism we have that $\epsilon'_F =  F\eta^{-1}$ and $G\epsilon' = \eta_G^{-1}$. We define $\epsilon'$ to be given by the pasting diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20B%20%5C%5C%0A%09%5C%5C%0A%09%26%20A%20%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%26%20B%0A%09%5Carrow%5B%22G%22%2C%20from%3D1-2%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-2%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3-2%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D3-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22G%22'%2C%20from%3D4-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22'%2C%20shorten%20%3E%3D9pt%2C%20Rightarrow%2C%20from%3D1-2%2C%20to%3D0%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3C%3D4pt%2C%20shorten%20%3E%3D4pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D2pt%2C%20Rightarrow%2C%20from%3D1%2C%20to%3D3-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; B \\
	\\
	&amp; A &amp;&amp; A \\
	B &amp;&amp;&amp;&amp; B
	\arrow[&quot;G&quot;, from=1-2, to=3-4]
	\arrow[&quot;F&quot;', from=3-2, to=1-2]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=3-2, to=3-4]
	\arrow[&quot;F&quot;, from=3-4, to=4-5]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=1-2]
	\arrow[&quot;G&quot;', from=4-1, to=3-2]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=4-5]
	\arrow[&quot;{\eta^{-1}}&quot;', shorten &gt;=9pt, Rightarrow, from=1-2, to=0]
	\arrow[&quot;\epsilon&quot;, shorten &lt;=4pt, shorten &gt;=4pt, Rightarrow, from=0, to=2]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=2pt, Rightarrow, from=1, to=3-2]
\end{tikzcd}
" /></p>
Note that this is a 2-cell isomorphism as it is a composite of 2-cell isomorphisms. First, to see the identity $(G*\epsilon')\circ (\eta*G)=1_G$ we check the pasting diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09B%20%26%26%26%20A%20%26%26%20A%20%5C%5C%0A%09%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%26%20B%0A%09%5Carrow%5B%22G%22%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-4%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D2-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3C%3D10pt%2C%20shorten%20%3E%3D10pt%2C%20Rightarrow%2C%20from%3D2-3%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22G%22'%2C%20from%3D3-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D3-1%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22G%22'%2C%20from%3D3-5%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22'%2C%20shorten%20%3E%3D14pt%2C%20Rightarrow%2C%20from%3D1-1%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Ceta%22%2C%20shorten%20%3C%3D7pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22'%2C%20shorten%20%3C%3D11pt%2C%20Rightarrow%2C%20from%3D2%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	B &amp;&amp;&amp; A &amp;&amp; A \\
	&amp;&amp; A \\
	B &amp;&amp;&amp;&amp; B
	\arrow[&quot;G&quot;, from=1-1, to=1-4]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=1-6]
	\arrow[&quot;F&quot;, from=1-4, to=3-5]
	\arrow[&quot;F&quot;, from=2-3, to=1-1]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=2-3, to=1-4]
	\arrow[&quot;\epsilon&quot;, shorten &lt;=10pt, shorten &gt;=10pt, Rightarrow, from=2-3, to=3-5]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=3-1, to=1-1]
	\arrow[&quot;G&quot;', from=3-1, to=2-3]
	\arrow[Rightarrow, no head, from=3-1, to=3-5]
	\arrow[&quot;G&quot;', from=3-5, to=1-6]
	\arrow[&quot;{\eta^{-1}}&quot;', shorten &gt;=14pt, Rightarrow, from=1-1, to=1]
	\arrow[&quot;\eta&quot;, shorten &lt;=7pt, Rightarrow, from=0, to=3-5]
	\arrow[&quot;{\epsilon^{-1}}&quot;', shorten &lt;=11pt, Rightarrow, from=2, to=2-3]
\end{tikzcd}
" /></p>
Note that using interchange and some input and removal of identities, this pasting diagram can be written as 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09B%20%26%26%26%20A%20%26%26%20A%20%5C%5C%0A%09%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%26%20B%0A%09%5Carrow%5B%22G%22%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22%5Ceta%22%2C%20shorten%20%3C%3D8pt%2C%20Rightarrow%2C%20from%3D1-4%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D2-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D2-3%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22G%22'%2C%20from%3D3-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3-1%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22G%22'%2C%20from%3D3-5%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22'%2C%20shorten%20%3E%3D14pt%2C%20Rightarrow%2C%20from%3D1-1%2C%20to%3D0%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3C%3D3pt%2C%20shorten%20%3E%3D3pt%2C%20Rightarrow%2C%20from%3D2-3%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22'%2C%20shorten%20%3C%3D11pt%2C%20Rightarrow%2C%20from%3D1%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	B &amp;&amp;&amp; A &amp;&amp; A \\
	&amp;&amp; A \\
	B &amp;&amp;&amp;&amp; B
	\arrow[&quot;G&quot;, from=1-1, to=1-4]
	\arrow[Rightarrow, no head, from=1-4, to=1-6]
	\arrow[&quot;\eta&quot;, shorten &lt;=8pt, Rightarrow, from=1-4, to=3-5]
	\arrow[&quot;F&quot;, from=2-3, to=1-1]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=2-3, to=1-4]
	\arrow[&quot;F&quot;, from=2-3, to=3-5]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=3-1, to=1-1]
	\arrow[&quot;G&quot;', from=3-1, to=2-3]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=3-1, to=3-5]
	\arrow[&quot;G&quot;', from=3-5, to=1-6]
	\arrow[&quot;{\eta^{-1}}&quot;', shorten &gt;=14pt, Rightarrow, from=1-1, to=0]
	\arrow[&quot;\epsilon&quot;, shorten &lt;=3pt, shorten &gt;=3pt, Rightarrow, from=2-3, to=2]
	\arrow[&quot;{\epsilon^{-1}}&quot;', shorten &lt;=11pt, Rightarrow, from=1, to=2-3]
\end{tikzcd}
" /></p>
and now we can cancel the $\eta\circ \eta^{-1}$ term using interchange. This reduces the diagram to
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09B%20%26%20A%20%26%20B%20%5C%5C%0A%09%26%20B%0A%09%5Carrow%5B%22G%22'%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20bend%20left%20%3D%2050%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22'%2C%20shorten%20%3C%3D2pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3C%3D2pt%2C%20shorten%20%3E%3D2pt%2C%20Rightarrow%2C%20from%3D1-2%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	B &amp; A &amp; B \\
	&amp; B
	\arrow[&quot;G&quot;', from=1-1, to=1-2]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, bend left = 50, Rightarrow, no head, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-1, to=2-2]
	\arrow[&quot;F&quot;, from=1-2, to=1-3]
	\arrow[&quot;F&quot;, from=1-2, to=2-2]
	\arrow[Rightarrow, no head, from=2-2, to=1-3]
	\arrow[&quot;{\epsilon^{-1}}&quot;', shorten &lt;=2pt, Rightarrow, from=0, to=1-2]
	\arrow[&quot;\epsilon&quot;, shorten &lt;=2pt, shorten &gt;=2pt, Rightarrow, from=1-2, to=1]
\end{tikzcd}
" /></p>
which then simplifies to the identity on $F$, as desired. To get the second inequality we use [[Infinity Categories from Scratch#^18c328|Lemma 4]], which also completes the proof.
`\end{proof}`

>[!lemma] Weak Adjoint Equivalence
>If $(F,G,\eta,\epsilon):A\to B$ is an equivalence in a 2-category, then it is an adjoint equivalence if and only if it satisfies one of the triangle identities.

`\begin{proof}`
By duality it suffices to prove that if $(F,G,\eta,\epsilon)$ is an equivalence and $(G*\epsilon)\circ (\eta*G) = 1_G$, then $(\epsilon*F)\circ (F*\eta) = 1_F$. Note that we also have the inverse of the triangle identity, since we are dealing with equivalences, which is $(\eta^{-1}*G)\circ (G*\epsilon^{-1})=1_G$. Now, we proceed by arguing through a chain of equalities of pasting diagrams. First, using our identities we can insert the inverse triangle inequality diagram in the middle of the $(\epsilon*F)\circ (F*\eta)$ pasting:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%20A%20%5C%5C%0A%09%26%20B%20%5C%5C%0A%09%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%20B%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D1-1%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-3%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3-3%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-3%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22%5Ceta%22'%2C%20shorten%20%3C%3D13pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D5pt%2C%20Rightarrow%2C%20from%3D2-2%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3E%3D4pt%2C%20Rightarrow%2C%20from%3D3-3%2C%20to%3D3%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D8pt%2C%20Rightarrow%2C%20from%3D2%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp; A \\
	&amp; B \\
	&amp;&amp; A \\
	B &amp;&amp;&amp; B
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-1, to=1-3]
	\arrow[&quot;F&quot;', from=1-1, to=4-1]
	\arrow[&quot;F&quot;, from=1-3, to=4-4]
	\arrow[&quot;G&quot;, from=2-2, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=3-3, to=1-3]
	\arrow[&quot;F&quot;', from=3-3, to=2-2]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=2-2]
	\arrow[&quot;G&quot;, from=4-1, to=3-3]
	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=4-4]
	\arrow[&quot;\eta&quot;', shorten &lt;=13pt, Rightarrow, from=0, to=4-1]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=5pt, Rightarrow, from=2-2, to=1]
	\arrow[&quot;\epsilon&quot;, shorten &gt;=4pt, Rightarrow, from=3-3, to=3]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=8pt, Rightarrow, from=2, to=3-3]
\end{tikzcd}
" /></p>
Next, we can extend the bottom left by an identity and $\epsilon,\epsilon^{-1}$ pair to obtain
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%26%20A%20%5C%5C%0A%09%26%26%20B%20%5C%5C%0A%09%26%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%26%20B%20%26%20A%20%26%20B%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D1-1%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-4%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-1%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-5%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D4%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20bend%20left%20%3D%2060%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-5%2C%20to%3D4-7%5D%0A%09%5Carrow%5B%22%22%7Bname%3D5%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20bend%20right%20%3D%2060%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-5%2C%20to%3D4-7%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D4-6%2C%20to%3D4-7%5D%0A%09%5Carrow%5B%22%5Ceta%22'%2C%20shorten%20%3C%3D9pt%2C%20shorten%20%3E%3D9pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D5pt%2C%20Rightarrow%2C%20from%3D2-3%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D11pt%2C%20Rightarrow%2C%20from%3D2%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20Rightarrow%2C%20from%3D3-4%2C%20to%3D3%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D2pt%2C%20Rightarrow%2C%20from%3D4%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3E%3D2pt%2C%20Rightarrow%2C%20from%3D4-6%2C%20to%3D5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp;&amp; A \\
	&amp;&amp; B \\
	&amp;&amp;&amp; A \\
	B &amp;&amp;&amp;&amp; B &amp; A &amp; B
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-1, to=1-4]
	\arrow[&quot;F&quot;', from=1-1, to=4-1]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=3-4]
	\arrow[&quot;F&quot;, from=1-4, to=4-5]
	\arrow[&quot;G&quot;, from=2-3, to=1-4]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=2-3, to=4-1]
	\arrow[&quot;F&quot;', from=3-4, to=2-3]
	\arrow[&quot;G&quot;, from=4-1, to=3-4]
	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=4-5]
	\arrow[&quot;G&quot;, from=4-5, to=4-6]
	\arrow[&quot;&quot;{name=4, anchor=center, inner sep=0}, bend left = 60, Rightarrow, no head, from=4-5, to=4-7]
	\arrow[&quot;&quot;{name=5, anchor=center, inner sep=0}, bend right = 60, Rightarrow, no head, from=4-5, to=4-7]
	\arrow[&quot;F&quot;, from=4-6, to=4-7]
	\arrow[&quot;\eta&quot;', shorten &lt;=9pt, shorten &gt;=9pt, Rightarrow, from=0, to=2]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=5pt, Rightarrow, from=2-3, to=1]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=11pt, Rightarrow, from=2, to=3-4]
	\arrow[&quot;\epsilon&quot;, Rightarrow, from=3-4, to=3]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=2pt, Rightarrow, from=4, to=4-6]
	\arrow[&quot;\epsilon&quot;, shorten &gt;=2pt, Rightarrow, from=4-6, to=5]
\end{tikzcd}
" /></p>
With this substitution we now have an $G\circ F$ pair where we can insert an $\eta,\eta^{-1}$ pair
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%26%20A%20%5C%5C%0A%09%26%26%20B%20%26%26%26%26%20B%20%5C%5C%0A%09%26%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%26%20B%20%26%20A%20%5C%5C%0A%09%26%26%26%26%26%26%20B%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D1-1%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-4%2C%20to%3D2-7%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-7%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D4%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-7%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-4%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-1%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D5%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-5%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D6%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20bend%20right%20%3D%2050%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-5%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D4-6%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22%5Ceta%22'%2C%20shorten%20%3C%3D9pt%2C%20shorten%20%3E%3D9pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D3%5D%0A%09%5Carrow%5B%22%5Ceta%22%2C%20shorten%20%3C%3D7pt%2C%20Rightarrow%2C%20from%3D2%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D5pt%2C%20Rightarrow%2C%20from%3D2-3%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D11pt%2C%20Rightarrow%2C%20from%3D3%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D10pt%2C%20Rightarrow%2C%20from%3D4%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D8pt%2C%20Rightarrow%2C%20from%3D2-7%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20Rightarrow%2C%20from%3D3-4%2C%20to%3D5%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3E%3D5pt%2C%20Rightarrow%2C%20from%3D4-6%2C%20to%3D6%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp;&amp; A \\
	&amp;&amp; B &amp;&amp;&amp;&amp; B \\
	&amp;&amp;&amp; A \\
	B &amp;&amp;&amp;&amp; B &amp; A \\
	&amp;&amp;&amp;&amp;&amp;&amp; B
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-1, to=1-4]
	\arrow[&quot;F&quot;', from=1-1, to=4-1]
	\arrow[&quot;F&quot;, from=1-4, to=2-7]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=3-4]
	\arrow[&quot;F&quot;, from=1-4, to=4-5]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=4-6]
	\arrow[&quot;G&quot;, from=2-3, to=1-4]
	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, Rightarrow, no head, from=2-3, to=4-1]
	\arrow[&quot;G&quot;, from=2-7, to=4-6]
	\arrow[&quot;&quot;{name=4, anchor=center, inner sep=0}, Rightarrow, no head, from=2-7, to=5-7]
	\arrow[&quot;F&quot;', from=3-4, to=2-3]
	\arrow[&quot;G&quot;, from=4-1, to=3-4]
	\arrow[&quot;&quot;{name=5, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=4-5]
	\arrow[&quot;G&quot;, from=4-5, to=4-6]
	\arrow[&quot;&quot;{name=6, anchor=center, inner sep=0}, bend right = 50, Rightarrow, no head, from=4-5, to=5-7]
	\arrow[&quot;F&quot;, from=4-6, to=5-7]
	\arrow[&quot;\eta&quot;', shorten &lt;=9pt, shorten &gt;=9pt, Rightarrow, from=0, to=3]
	\arrow[&quot;\eta&quot;, shorten &lt;=7pt, Rightarrow, from=2, to=4-5]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=5pt, Rightarrow, from=2-3, to=1]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=11pt, Rightarrow, from=3, to=3-4]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=10pt, Rightarrow, from=4, to=4-6]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=8pt, Rightarrow, from=2-7, to=2]
	\arrow[&quot;\epsilon&quot;, Rightarrow, from=3-4, to=5]
	\arrow[&quot;\epsilon&quot;, shorten &gt;=5pt, Rightarrow, from=4-6, to=6]
\end{tikzcd}
" /></p>
Using the interchange law we can re-arrange our middle $\eta$ so that it can cancel with the middle $\eta^{-1}$ in the following diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%26%20A%20%5C%5C%0A%09%26%26%20B%20%26%26%26%26%20B%20%5C%5C%0A%09%26%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%26%20B%20%26%20A%20%5C%5C%0A%09%26%26%26%26%26%26%20B%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D1-1%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-4%2C%20to%3D2-7%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%5Ceta%22%2C%20shorten%20%3C%3D12pt%2C%20Rightarrow%2C%20from%3D1-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-7%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D4%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-7%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-4%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-1%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D5%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-5%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D6%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20bend%20right%20%3D%2060%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-5%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D4-6%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22%5Ceta%22'%2C%20shorten%20%3C%3D9pt%2C%20shorten%20%3E%3D9pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D3%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D5pt%2C%20Rightarrow%2C%20from%3D2-3%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D11pt%2C%20Rightarrow%2C%20from%3D3%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D10pt%2C%20Rightarrow%2C%20from%3D4%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D8pt%2C%20Rightarrow%2C%20from%3D2-7%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20Rightarrow%2C%20from%3D3-4%2C%20to%3D5%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3E%3D5pt%2C%20Rightarrow%2C%20from%3D4-6%2C%20to%3D6%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp;&amp; A \\
	&amp;&amp; B &amp;&amp;&amp;&amp; B \\
	&amp;&amp;&amp; A \\
	B &amp;&amp;&amp;&amp; B &amp; A \\
	&amp;&amp;&amp;&amp;&amp;&amp; B
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-1, to=1-4]
	\arrow[&quot;F&quot;', from=1-1, to=4-1]
	\arrow[&quot;F&quot;, from=1-4, to=2-7]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=3-4]
	\arrow[&quot;\eta&quot;, shorten &lt;=12pt, Rightarrow, from=1-4, to=4-5]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=4-6]
	\arrow[&quot;G&quot;, from=2-3, to=1-4]
	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, Rightarrow, no head, from=2-3, to=4-1]
	\arrow[&quot;G&quot;, from=2-7, to=4-6]
	\arrow[&quot;&quot;{name=4, anchor=center, inner sep=0}, Rightarrow, no head, from=2-7, to=5-7]
	\arrow[&quot;F&quot;', from=3-4, to=2-3]
	\arrow[&quot;F&quot;', from=3-4, to=4-5]
	\arrow[&quot;G&quot;, from=4-1, to=3-4]
	\arrow[&quot;&quot;{name=5, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=4-5]
	\arrow[&quot;G&quot;, from=4-5, to=4-6]
	\arrow[&quot;&quot;{name=6, anchor=center, inner sep=0}, bend right = 60, Rightarrow, no head, from=4-5, to=5-7]
	\arrow[&quot;F&quot;, from=4-6, to=5-7]
	\arrow[&quot;\eta&quot;', shorten &lt;=9pt, shorten &gt;=9pt, Rightarrow, from=0, to=3]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=5pt, Rightarrow, from=2-3, to=1]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=11pt, Rightarrow, from=3, to=3-4]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=10pt, Rightarrow, from=4, to=4-6]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=8pt, Rightarrow, from=2-7, to=2]
	\arrow[&quot;\epsilon&quot;, Rightarrow, from=3-4, to=5]
	\arrow[&quot;\epsilon&quot;, shorten &gt;=5pt, Rightarrow, from=4-6, to=6]
\end{tikzcd}
" /></p>
This puts our diagram in a position to cancel the middle $\epsilon,\epsilon^{-1}$ pair in
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%26%20A%20%5C%5C%0A%09%26%26%20B%20%26%26%26%26%20B%20%5C%5C%0A%09%26%26%26%20A%20%5C%5C%0A%09B%20%26%26%26%26%20B%20%26%20A%20%5C%5C%0A%09%26%26%26%26%26%26%20B%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D1-1%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-4%2C%20to%3D2-7%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D2-7%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-7%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-4%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D3-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-1%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D4%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-1%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D4-5%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D5%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20bend%20right%20%3D%2060%2C%20Rightarrow%2C%20no%20head%2C%20from%3D4-5%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D4-6%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22%5Ceta%22'%2C%20shorten%20%3C%3D9pt%2C%20shorten%20%3E%3D9pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D11pt%2C%20Rightarrow%2C%20from%3D2%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D5pt%2C%20Rightarrow%2C%20from%3D3%2C%20to%3D4-6%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D11pt%2C%20Rightarrow%2C%20from%3D2-7%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20Rightarrow%2C%20from%3D3-4%2C%20to%3D4%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3E%3D5pt%2C%20Rightarrow%2C%20from%3D4-6%2C%20to%3D5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp;&amp; A \\
	&amp;&amp; B &amp;&amp;&amp;&amp; B \\
	&amp;&amp;&amp; A \\
	B &amp;&amp;&amp;&amp; B &amp; A \\
	&amp;&amp;&amp;&amp;&amp;&amp; B
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-1, to=1-4]
	\arrow[&quot;F&quot;', from=1-1, to=4-1]
	\arrow[&quot;F&quot;, from=1-4, to=2-7]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=4-6]
	\arrow[&quot;G&quot;, from=2-3, to=1-4]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=2-3, to=4-1]
	\arrow[&quot;G&quot;, from=2-7, to=4-6]
	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, Rightarrow, no head, from=2-7, to=5-7]
	\arrow[&quot;F&quot;', from=3-4, to=2-3]
	\arrow[&quot;F&quot;', from=3-4, to=4-5]
	\arrow[&quot;G&quot;, from=4-1, to=3-4]
	\arrow[&quot;&quot;{name=4, anchor=center, inner sep=0}, Rightarrow, no head, from=4-1, to=4-5]
	\arrow[&quot;G&quot;, from=4-5, to=4-6]
	\arrow[&quot;&quot;{name=5, anchor=center, inner sep=0}, bend right = 60, Rightarrow, no head, from=4-5, to=5-7]
	\arrow[&quot;F&quot;, from=4-6, to=5-7]
	\arrow[&quot;\eta&quot;', shorten &lt;=9pt, shorten &gt;=9pt, Rightarrow, from=0, to=2]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=11pt, Rightarrow, from=2, to=3-4]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=5pt, Rightarrow, from=3, to=4-6]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=11pt, Rightarrow, from=2-7, to=1]
	\arrow[&quot;\epsilon&quot;, Rightarrow, from=3-4, to=4]
	\arrow[&quot;\epsilon&quot;, shorten &gt;=5pt, Rightarrow, from=4-6, to=5]
\end{tikzcd}
" /></p>
After cancelling these terms we can re-arrange/remove identity cells to obtain
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20A%20%26%26%26%20B%20%5C%5C%0A%09%5C%5C%0A%09B%20%26%26%26%20A%20%5C%5C%0A%09%26%26%26%26%20B%0A%09%5Carrow%5B%22F%22%2C%20from%3D1-2%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D1-2%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-2%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D1-5%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22G%22%2C%20from%3D3-1%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3-1%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22F%22%2C%20from%3D3-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5B%22%5Ceta%22%2C%20shorten%20%3C%3D11pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon%5E%7B-1%7D%7D%22%2C%20shorten%20%3C%3D5pt%2C%20Rightarrow%2C%20from%3D1%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7B%5Ceta%5E%7B-1%7D%7D%22%2C%20shorten%20%3E%3D11pt%2C%20Rightarrow%2C%20from%3D1-5%2C%20to%3D0%5D%0A%09%5Carrow%5B%22%5Cepsilon%22%2C%20shorten%20%3E%3D8pt%2C%20Rightarrow%2C%20from%3D3-4%2C%20to%3D2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; A &amp;&amp;&amp; B \\
	\\
	B &amp;&amp;&amp; A \\
	&amp;&amp;&amp;&amp; B
	\arrow[&quot;F&quot;, from=1-2, to=1-5]
	\arrow[&quot;F&quot;', from=1-2, to=3-1]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-2, to=3-4]
	\arrow[&quot;G&quot;, from=1-5, to=3-4]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-5, to=4-5]
	\arrow[&quot;G&quot;, from=3-1, to=3-4]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, Rightarrow, no head, from=3-1, to=4-5]
	\arrow[&quot;F&quot;, from=3-4, to=4-5]
	\arrow[&quot;\eta&quot;, shorten &lt;=11pt, Rightarrow, from=0, to=3-1]
	\arrow[&quot;{\epsilon^{-1}}&quot;, shorten &lt;=5pt, Rightarrow, from=1, to=3-4]
	\arrow[&quot;{\eta^{-1}}&quot;, shorten &gt;=11pt, Rightarrow, from=1-5, to=0]
	\arrow[&quot;\epsilon&quot;, shorten &gt;=8pt, Rightarrow, from=3-4, to=2]
\end{tikzcd}
" /></p>
which reduces to the identity on $F$ after using the interchange law to cancel again.
`\end{proof}`



