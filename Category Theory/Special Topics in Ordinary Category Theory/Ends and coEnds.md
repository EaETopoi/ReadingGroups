---
date: 2024-05-19T14:30:00
tags:
  - CategoryTheory
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
These notes aim to provide intuition and motivation for the study of ends and coends, and their associated calculi. Throughout we will provide a number of examples of ends and coends, realizing them as limits and colimits of particular kinds, and showing a Fubini-like result for them. Much of these notes follows the approach in[^1].  

## (co)Wedges and (co)Ends
Ends and coends, like limits and colimits, are special kinds of universal objects in a category associated with some appropriate diagram. Before we can discuss ends and coends it is important to introduce the notion of **dinaturality**.

>[!def] Dinaturality
>A **dinatural transformation** $\alpha$ between bifunctors $F,G:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ is a collection of maps $\alpha_C:F(C,C)\to G(C,C)$ such that for any map $f:C\to C'$ in $\mathcal{C}$, the following hexagon commutes:
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20%7BF(C%2CC)%7D%20%26%20%7BG(C%2CC)%7D%20%5C%5C%0A%09%7BF(C'%2CC)%7D%20%26%26%26%20%7BG(C%2CC')%7D%20%5C%5C%0A%09%26%20%7BF(C'%2CC')%7D%20%26%20%7BG(C'%2CC')%7D%0A%09%5Carrow%5B%22%7B%5Calpha_C%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7BG(1_C%2Cf)%7D%22%2C%20from%3D1-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7BF(f%2C1_C)%7D%22%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7BF(1_%7BC'%7D%2Cf)%7D%22'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7BC'%7D%7D%22'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BG(f%2C1_%7BC'%7D)%7D%22'%2C%20from%3D3-3%2C%20to%3D2-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	&amp; {F(C,C)} &amp; {G(C,C)} \\	{F(C',C)} &amp;&amp;&amp; {G(C,C')} \\	&amp; {F(C',C')} &amp; {G(C',C')}	\arrow[&quot;{\alpha_C}&quot;, from=1-2, to=1-3]	\arrow[&quot;{G(1_C,f)}&quot;, from=1-3, to=2-4]	\arrow[&quot;{F(f,1_C)}&quot;, from=2-1, to=1-2]	\arrow[&quot;{F(1_{C'},f)}&quot;', from=2-1, to=3-2]	\arrow[&quot;{\alpha_{C'}}&quot;', from=3-2, to=3-3]	\arrow[&quot;{G(f,1_{C'})}&quot;', from=3-3, to=2-4]\end{tikzcd}" /></p>

More generally, when considering functors of multiple variables, we can consider transformations which are natural in certain variables and dinatural in others.

In most cases we will be considering special kinds of di-natural transformations where $G$ or $F$ are constant bifunctors. This leads to the definition of a (co)wedge for a given bifunctor.

>[!def] (co)Wedges
>A **(co)wedge** for a bifunctor $F:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ is an object $\omega$ of $\mathcal{D}$ together with a dinatural transformation $\alpha:\Delta_\omega\xrightarrow{..}F$ (resp. $\alpha:F\xrightarrow{..}\Delta_\omega$).

A **(co)end** for a bifunctor $F:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$, if it exists, is then a universal (co)wedge in the sense that all other (co)wedges factor uniquely through it. Explicitly, as with limits and colimits, we can consider a functor $\mathsf{(co)Wedge}_F:(\mathcal{D})\mathcal{D}^{op}\to \mathsf{Set}$ sending an object of $\mathcal{D}$ to the set of (co)wedges under it, and sending a map pre(post)-composition depending on if it is the wedge or cowedge functor. Then a (co)end is exactly a representation of the functors, $\mathsf{Wedge}_F \cong \mathcal{D}(-,\omega)$ (resp. $\mathsf{coWedge}_F\cong \mathcal{D}(\omega,-)$).

Usually we write the end of a bifunctor $F:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ as $\int_{c:\mathcal{C}}F(c,c)$ while we write the co-end as $\int^{c:\mathcal{C}}F(c,c)$. Let's go to our first example now to start illuminating the concept.

>[!example] Natural Transformations
>Let $F,G:\mathcal{C}\to \mathcal{D}$ be functors between locally small categories (i.e. $\mathsf{Set}$-enriched). Then we have a bifunctor $\mathcal{D}(F-,G-):\mathcal{C}^{op}\times \mathcal{C}\to \mathsf{Set}$. This bifunctor has an end, which is given by the set of natural transformations, $\mathsf{Nat}(F,G)$, between the functors. To see this note that our dinatural transformation is given by projection
>$$\begin{CD}\mathsf{Nat}(F,G) @>>> \mathcal{D}(Fc,Gc) \\ @VVV @VVGf\circ -V \\ \mathcal{D}(Fc',Gc') @> -\circ Ff>> \mathcal{D}(Fc,Gc')\end{CD}$$
>where $f:c\to c'$. The squares commute by naturality, and for any other function in set a wedge exactly corresponds to a collection of maps satisfying the naturality constraint.

Using our notation above we can write this example as $\mathsf{Nat}(F,G) \cong \int_{c:\mathcal{C}}\mathcal{D}(Fc,Gc)$. In general, we can realize ends as limits of a certain category called the **twisted arrow category**. Explicitly, for a category $\mathcal{C}$ its twisted arrow category $\mathcal{C}^{tw}$ is the category with arrows $f:c\to c'$ as objects, and morphisms commuting squares
$$\begin{CD}c @<h<< d \\ @VfVV @VVgV \\ c' @>>k> d'\end{CD}$$
where the domain is $f$ and the codomain is $g$. The twisted arrow category comes naturally equipped with a forgetful functor $\pi_{tw}:\mathcal{C}^{tw}\to \mathcal{C}^{op}\times \mathcal{C}$ sending a map $f:c\to c'$ to the pair $(c,c')$. ^be4441

>[!proposition] Ends as Limits
>Let $F:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ be a bifunctor. Then the end of $F$ is naturally isomorphic to the limit of the functor $F\circ \pi_{tw}:\mathcal{C}^{tw}\to \mathcal{D}$, and one exists if and only if the other exists.

^d3d04f

`\begin{proof}`
Let $F:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$. To prove the claim it suffices to show that a wedge for $F$ is the same as a cone over $F\circ \pi_{tw}$. To begin, let $E$ be an wedge of $F$. Then for each $f:c\to c'$ we have a map $E\to F(c,c')$ which is the diagonal of the square
$$\begin{CD}E @>\omega_c>> F(c,c) \\ @V\omega_{c'}VV @VVF(1_c,f)V \\ F(c',c') @>>F(f,1_{c'})> F(c,c') \end{CD}$$
If $(p,q)$ is a map in the twisted arrow category from $f:c\to c'$ to $g:d\to d'$ (so $p:d\to c$ and $q:c'\to d'$), then we have the commutative diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09E%20%26%26%26%26%20%7BF(d%2Cd)%7D%20%5C%5C%0A%09%26%26%20%7BF(c%2Cc)%7D%20%26%20%7BF(d%2Cc)%7D%20%5C%5C%0A%09%26%20%7BF(c'%2Cc')%7D%20%26%20%7BF(c%2Cc')%7D%20%26%20%7BF(d%2Cc')%7D%20%5C%5C%0A%09%26%20%7BF(c'%2Cd')%7D%20%26%20%7BF(c%2Cd')%7D%20%5C%5C%0A%09%7BF(d'%2Cd')%7D%20%26%26%26%26%20%7BF(d%2Cd')%7D%0A%09%5Carrow%5B%22%7B%5Comega_d%7D%22%2C%20from%3D1-1%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%7B%5Comega_c%7D%22%2C%20from%3D1-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7B%5Comega_%7Bc'%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7B%5Comega_%7Bd'%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D5-1%5D%0A%09%5Carrow%5B%22%7BF(1_c%2Cp)%7D%22%2C%20from%3D1-5%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7BF(1_d%2Cg)%7D%22%2C%20from%3D1-5%2C%20to%3D5-5%5D%0A%09%5Carrow%5B%22%7BF(p%2C1_c)%7D%22%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7BF(1_c%2Cf)%7D%22'%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF(1_d%2Cf)%7D%22%2C%20from%3D2-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7BF(f%2C1_%7Bc'%7D)%7D%22%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF(1_%7Bc'%7D%2Cq)%7D%22'%2C%20from%3D3-2%2C%20to%3D4-2%5D%0A%09%5Carrow%5B%22%7BF(p%2C1_%7Bc'%7D)%7D%22%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7BF(1_c%2Cq)%7D%22'%2C%20from%3D3-3%2C%20to%3D4-3%5D%0A%09%5Carrow%5B%22%7BF(p%2Cq)%7D%22%2C%20from%3D3-3%2C%20to%3D5-5%5D%0A%09%5Carrow%5B%22%7BF(1_d%2Cq)%7D%22%2C%20from%3D3-4%2C%20to%3D5-5%5D%0A%09%5Carrow%5B%22%7BF(f%2C1_%7Bd'%7D)%7D%22'%2C%20from%3D4-2%2C%20to%3D4-3%5D%0A%09%5Carrow%5B%22%7BF(p%2C1_%7Bd'%7D)%7D%22'%2C%20from%3D4-3%2C%20to%3D5-5%5D%0A%09%5Carrow%5B%22%7BF(q%2C1_%7Bd'%7D)%7D%22'%2C%20from%3D5-1%2C%20to%3D4-2%5D%0A%09%5Carrow%5B%22%7BF(g%2C1_%7Bd'%7D)%7D%22'%2C%20from%3D5-1%2C%20to%3D5-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	E &amp;&amp;&amp;&amp; {F(d,d)} \\
	&amp;&amp; {F(c,c)} &amp; {F(d,c)} \\
	&amp; {F(c',c')} &amp; {F(c,c')} &amp; {F(d,c')} \\
	&amp; {F(c',d')} &amp; {F(c,d')} \\
	{F(d',d')} &amp;&amp;&amp;&amp; {F(d,d')}
	\arrow[&quot;{\omega_d}&quot;, from=1-1, to=1-5]
	\arrow[&quot;{\omega_c}&quot;, from=1-1, to=2-3]
	\arrow[&quot;{\omega_{c'}}&quot;', from=1-1, to=3-2]
	\arrow[&quot;{\omega_{d'}}&quot;', from=1-1, to=5-1]
	\arrow[&quot;{F(1_c,p)}&quot;, from=1-5, to=2-4]
	\arrow[&quot;{F(1_d,g)}&quot;, from=1-5, to=5-5]
	\arrow[&quot;{F(p,1_c)}&quot;, from=2-3, to=2-4]
	\arrow[&quot;{F(1_c,f)}&quot;', from=2-3, to=3-3]
	\arrow[&quot;{F(1_d,f)}&quot;, from=2-4, to=3-4]
	\arrow[&quot;{F(f,1_{c'})}&quot;, from=3-2, to=3-3]
	\arrow[&quot;{F(1_{c'},q)}&quot;', from=3-2, to=4-2]
	\arrow[&quot;{F(p,1_{c'})}&quot;, from=3-3, to=3-4]
	\arrow[&quot;{F(1_c,q)}&quot;', from=3-3, to=4-3]
	\arrow[&quot;{F(p,q)}&quot;, from=3-3, to=5-5]
	\arrow[&quot;{F(1_d,q)}&quot;, from=3-4, to=5-5]
	\arrow[&quot;{F(f,1_{d'})}&quot;', from=4-2, to=4-3]
	\arrow[&quot;{F(p,1_{d'})}&quot;', from=4-3, to=5-5]
	\arrow[&quot;{F(q,1_{d'})}&quot;', from=5-1, to=4-2]
	\arrow[&quot;{F(g,1_{d'})}&quot;', from=5-1, to=5-5]
\end{tikzcd}
" /></p>
where every interior square commutes by either dinaturality or functoriality, and so the outer square commutes, which is the cone condition. 

Conversely, let $E$ be a cone over $F\circ \pi_{tw}$. Then for each $c \in \mathcal{C}$ we have a map $\alpha_{1_c}:E\to F(c,c)$. If $f:c\to c'$, then the diagram 
$$\begin{CD}E @>\alpha_{1_c}>>F(c,c) \\ @V\alpha_{1_{c'}}VV @VVF(1_c,f)V \\ F(c',c') @>>F(f,1_{c'})> F(c,c')\end{CD}$$
commutes since $$F(1_c,f)\circ \alpha_{1_c} = \alpha_f = F(f,1_{c'})\circ \alpha_{1_{c'}}$$
due to the fact that $E$ is a cone. Thus, we see that the two are equivalent, proving the claim.
`\end{proof}`
By duality we also see that coends are colimits, where we take the dual twisted arrow category for our diagrams. We then obtain the following immediate corollary:

>[!corollary] Existence of (co)Ends
>If $\mathcal{D}$ is small-complete and $\mathcal{C}$ is a small category, then any bifunctor $F:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ has a (co)end in $\mathcal{D}$.

Conversely, we can also realize all limits as ends by pre-composing with the projection $\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{C}$. As with (co)limits we obtain notions of functors preserving, creating, or reflecting (co)ends. Further, by [[Ends and coEnds#^d3d04f|Proposition 4]] all functors that preserve (co)limits also preserve (co)ends, so in particular the hom functors do. 

Although they are equivalent, there are a number of important heuristic and computational reasons for working with (co)ends in certain scenarios rather than (co)limits. For instance, the language of coends lends itself to defining generalizations of tensor products seen in module theory. In particular, the tensor of two modules over a ring can be realized as a special kind of coend, and in general the cowedge diagram condition can be thought of as the ability to pass an action between either variable of the bifunctor without affecting the result. For instance, let $\mathcal{V}$ be a monoidal category with tensor $\otimes$. If $T:\mathcal{D}^{op}\to \mathcal{V}$ and $S:\mathcal{D}\to \mathcal{V}$, we can define their tensor product (when it exists) to be the co-end of the bifunctor $T\otimes S:\mathcal{D}^{op}\times \mathcal{D}\to \mathcal{V}$. 

### Properties of (co)Ends

We now will prove some useful properties of (co)Ends, which by the observations at the end of the previous section will also extend to properties of (co)limits. First, we show that the construction of ends is functorial. This relies on the fact that a dinatural transformation composed with a natural transformation is again dinatural. Indeed, let $F,G,H:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ be bifunctors with dinatural transformation $\alpha:F\xrightarrow{..}G$ and natural transformation $\beta:G\Rightarrow H$. Then we can obtain a dinatural transformation $\beta\alpha:F\xrightarrow{..}H$ by composing pointwise. Indeed, for any $f:c\to c'$ in $\mathcal{C}$, we obtain the commuting diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20%7BF(c%2Cc)%7D%20%26%20%7BG(c%2Cc)%7D%20%26%20%7BH(c%2Cc)%7D%20%5C%5C%0A%09%7BF(c'%2Cc)%7D%20%26%26%26%20%7BG(c%2Cc')%7D%20%26%20%7BH(c%2Cc')%7D%20%5C%5C%0A%09%26%20%7BF(c'%2Cc')%7D%20%26%20%7BG(c'%2Cc')%7D%20%26%20%7BH(c'%2Cc')%7D%0A%09%5Carrow%5B%22%7B%5Calpha_c%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cbeta_%7Bc%2Cc%7D%7D%22%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%7BG(1_c%2Cf)%7D%22'%2C%20from%3D1-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7BH(1_c%2Cf)%7D%22%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%09%5Carrow%5B%22%7BF(f%2C1_c)%7D%22%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7BF(1_%7Bc'%7D%2Cf)%7D%22'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7B%5Cbeta_%7Bc%2Cc'%7D%7D%22'%2C%20from%3D2-4%2C%20to%3D2-5%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7Bc'%7D%7D%22'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BG(f%2C1_%7Bc'%7D)%7D%22%2C%20from%3D3-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7B%5Cbeta_%7Bc'%2Cc'%7D%7D%22'%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%7BH(f%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D3-4%2C%20to%3D2-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; {F(c,c)} &amp; {G(c,c)} &amp; {H(c,c)} \\
	{F(c',c)} &amp;&amp;&amp; {G(c,c')} &amp; {H(c,c')} \\
	&amp; {F(c',c')} &amp; {G(c',c')} &amp; {H(c',c')}
	\arrow[&quot;{\alpha_c}&quot;, from=1-2, to=1-3]
	\arrow[&quot;{\beta_{c,c}}&quot;, from=1-3, to=1-4]
	\arrow[&quot;{G(1_c,f)}&quot;', from=1-3, to=2-4]
	\arrow[&quot;{H(1_c,f)}&quot;, from=1-4, to=2-5]
	\arrow[&quot;{F(f,1_c)}&quot;, from=2-1, to=1-2]
	\arrow[&quot;{F(1_{c'},f)}&quot;', from=2-1, to=3-2]
	\arrow[&quot;{\beta_{c,c'}}&quot;', from=2-4, to=2-5]
	\arrow[&quot;{\alpha_{c'}}&quot;', from=3-2, to=3-3]
	\arrow[&quot;{G(f,1_{c'})}&quot;, from=3-3, to=2-4]
	\arrow[&quot;{\beta_{c',c'}}&quot;', from=3-3, to=3-4]
	\arrow[&quot;{H(f,1_{c'})}&quot;', from=3-4, to=2-5]
\end{tikzcd}
" /></p>


>[!proposition] Functorial Ends
>If $\gamma:F\Rightarrow G$ is a natural transformation between bifunctors $F,G:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ which both have ends, then there exists a unique map between their ends such that for any $c\in\mathcal{C}$ the diagram
>$$\begin{CD}\int_{c:\mathcal{C}}F(c,c) @>\omega_c^F>> F(c,c) \\ @V\int_{c:\mathcal{C}}\gamma_{c,c}VV @VV\gamma_{c,c}V \\ \int_{c:\mathcal{C}}G(c,c) @>>\omega_c^G> G(c,c) \end{CD}$$

^75a659

`\begin{proof}`
From the remark proceeding the Proposition $\gamma$ and $\omega^F$ compose to show that $\int_{c:\mathcal{C}}F(c,c)$ is naturally a wedge over $G$. But by the universal property of the end this implies that we have our desired unique map, as in the statement of the proposition. Uniqueness implies that this assignment is functorial in $\gamma$.
`\end{proof}`
Using [[Ends and coEnds#^75a659|Proposition 6]] we can introduce the concept of (co)ends with parameters. 

>[!theorem] Parameter Theorem for Ends
>Let $T:\mathcal{B}\times \mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ be a functor such that for every $b\in\mathcal{B}$ the functor $T(b,-,-)$ has an end $\omega_b$. Then the ends assemble into a unique functor $E:\mathcal{B}\to \mathcal{D}$ such that the wedge maps combine to give a transformation natural in $\mathcal{B}$.
>

^c13d5c

`\begin{proof}`
Note that each arrow $f:b\to b'$ defines a natural transformation $T(b,-,-)\to T(b',-,-)$, so by [[Ends and coEnds#^75a659|Proposition 6]] we obtain corresponding maps on ends, which we use to define the value of $E$ at $f$. By the remark at the end of the proof this is indeed a functorial assignment. Further, the desired naturality is the commutativity of the square in [[Ends and coEnds#^75a659|Proposition 6]]. 
`\end{proof}`
Using currying we can realize the functor $E$ in [[Ends and coEnds#^c13d5c|Theorem 7]] as the end of the curried functor $T^\#:\mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}^{\mathcal{B}}$. 

### Fubini-like Theorem for (co)Ends

^0fb563

We now move to showing that (co)Ends satisfy a useful fubini-like theorem, which is immensely powerful in computations. 

>[!proposition] Fubini-like Theorem for (co)Ends
>Let $F:\mathcal{B}^{op}\times \mathcal{B}\times \mathcal{C}^{op}\times \mathcal{C}\to \mathcal{D}$ be a functor such that for each $b,b' \in \mathcal{B}$ the end of $F(b,b',-,-)$ exists, so by [[Ends and coEnds#^c13d5c|Theorem 7]] they form a bifunctor $\int_{c:\mathcal{C}}F(-,-,c,c):\mathcal{B}^{op}\times \mathcal{B}\to \mathcal{D}$. Regarding $F$ as a bifunctor $F:(\mathcal{B}\times \mathcal{C})^{op}\times (\mathcal{B}\times \mathcal{C})\to \mathcal{D}$, we have that the double end of $F$ exists if and only if the end of $\int_{c:\mathcal{C}}F(-,-,c,c)$ exists, and there is an isomorphism 
>$$\theta:\int_{(b,c):\mathcal{B}\times \mathcal{C}}F(b,c,b,c) \cong \int_{b:\mathcal{B}}\left[\int_{c:\mathcal{C}}F(b,b,c,c)\right]$$

^60fafc

`\begin{proof}`
Let $\omega_{b,b'}:\int_{c:\mathcal{C}}F(b,b',c,c)\to F(b,b',-,-)$ denote the family of wedges which are natural in $b$ and $b'$. As in our proof of [[Ends and coEnds#^d3d04f|Proposition 4]] we show that a wedge for one side is the same as a wedge for the other.

On the left a wedge is an object $E$ of $\mathcal{D}$ together with a transformation $\xi:E\xrightarrow{..}F$ dinatural in the pair $(b,c) \in \mathcal{B}\times \mathcal{C}$. As a special case for any fixed $b \in \mathcal{B}$ and any $f:c\to c'$, we have a commuting square
$$\begin{CD}E @>\xi_{(b,c)}>> F(b,c,b,c) \\ @V\xi_{(b,c')}VV @VVF(1_b,1_c,1_b,f)V \\ F(b,c',b,c') @>>F(1_b,f,1_b,1_{c'})> F(b,c,b,c') \end{CD}$$
which implies that we obtain a unique map $\zeta_b:E\to \int_{c:\mathcal{C}}F(b,b,c,c)$. Then for $g:b\to b'$ we have the square
$$\begin{CD}E @>\zeta_b>> \int_{c:\mathcal{C}}F(b,b,c,c) \\ @V\zeta_{b'}VV @VV\int_{c:\mathcal{C}}F(1_b,g,1_c,1_c)V \\ \int_{c:\mathcal{C}}F(b',b',c,c) @>>\int_{c:\mathcal{C}}F(g,1_{b'},c,c)> \int_{c:\mathcal{C}}F(b,b',c,c) \end{CD}$$
which commutes since the lower and upper map are induced by the diagonal maps of the diagrams
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09E%20%26%20%7BF(b%2Cc%2Cb%2Cc)%7D%20%26%20%7BF(b%2Cc%2Cb'%2Cc)%7D%20%5C%5C%0A%09%7BF(b%2Cc'%2Cb%2Cc')%7D%20%26%20%7BF(b%2Cc%2Cb%2Cc')%7D%20%5C%5C%0A%09%7BF(b%2Cc'%2Cb'%2Cc')%7D%20%26%26%20%7BF(b%2Cc%2Cb'%2Cc')%7D%0A%09%5Carrow%5B%22%7B%5Cxi_%7B(b%2Cc)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B%5Cxi_%7B(b%2Cc')%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7BF(1_b%2C1_c%2Cg%2Cc)%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7BF(1_b%2C1_c%2C1_b%2Cf)%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7BF(1_b%2C1_c%2C1_%7Bb'%7D%2Cf)%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF(1_b%2Cf%2C1_b%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7BF(1_b%2C1_%7Bc'%7D%2Cg%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7BF(1_b%2C1_c%2Cg%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF(1_b%2Cf%2C1_%7Bb'%7D%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	E &amp; {F(b,c,b,c)} &amp; {F(b,c,b',c)} \\
	{F(b,c',b,c')} &amp; {F(b,c,b,c')} \\
	{F(b,c',b',c')} &amp;&amp; {F(b,c,b',c')}
	\arrow[&quot;{\xi_{(b,c)}}&quot;, from=1-1, to=1-2]
	\arrow[&quot;{\xi_{(b,c')}}&quot;', from=1-1, to=2-1]
	\arrow[&quot;{F(1_b,1_c,g,c)}&quot;, from=1-2, to=1-3]
	\arrow[&quot;{F(1_b,1_c,1_b,f)}&quot;, from=1-2, to=2-2]
	\arrow[&quot;{F(1_b,1_c,1_{b'},f)}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{F(1_b,f,1_b,1_{c'})}&quot;', from=2-1, to=2-2]
	\arrow[&quot;{F(1_b,1_{c'},g,1_{c'})}&quot;', from=2-1, to=3-1]
	\arrow[&quot;{F(1_b,1_c,g,1_{c'})}&quot;', from=2-2, to=3-3]
	\arrow[&quot;{F(1_b,f,1_{b'},1_{c'})}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>
and 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09E%20%26%20%7BF(b'%2Cc%2Cb'%2Cc)%7D%20%26%20%7BF(b%2Cc%2Cb'%2Cc)%7D%20%5C%5C%0A%09%7BF(b'%2Cc'%2Cb'%2Cc')%7D%20%26%20%7BF(b'%2Cc%2Cb'%2Cc')%7D%20%5C%5C%0A%09%7BF(b%2Cc'%2Cb'%2Cc')%7D%20%26%26%20%7BF(b%2Cc%2Cb'%2Cc')%7D%0A%09%5Carrow%5B%22%7B%5Cxi_%7B(b'%2Cc)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B%5Cxi_%7B(b'%2Cc')%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7BF(g%2C1_c%2C1_%7Bb'%7D%2Cc)%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7BF(1_%7Bb'%7D%2C1_c%2C1_%7Bb'%7D%2Cf)%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7BF(1_b%2C1_c%2C1_%7Bb'%7D%2Cf)%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF(1_%7Bb'%7D%2Cf%2C1_%7Bb'%7D%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7BF(g%2C1_%7Bc'%7D%2C1_%7Bb'%7D%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7BF(g%2C1_c%2C1_%7Bb'%7D%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF(1_b%2Cf%2C1_%7Bb'%7D%2C1_%7Bc'%7D)%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	E &amp; {F(b',c,b',c)} &amp; {F(b,c,b',c)} \\
	{F(b',c',b',c')} &amp; {F(b',c,b',c')} \\
	{F(b,c',b',c')} &amp;&amp; {F(b,c,b',c')}
	\arrow[&quot;{\xi_{(b',c)}}&quot;, from=1-1, to=1-2]
	\arrow[&quot;{\xi_{(b',c')}}&quot;', from=1-1, to=2-1]
	\arrow[&quot;{F(g,1_c,1_{b'},c)}&quot;, from=1-2, to=1-3]
	\arrow[&quot;{F(1_{b'},1_c,1_{b'},f)}&quot;, from=1-2, to=2-2]
	\arrow[&quot;{F(1_b,1_c,1_{b'},f)}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{F(1_{b'},f,1_{b'},1_{c'})}&quot;', from=2-1, to=2-2]
	\arrow[&quot;{F(g,1_{c'},1_{b'},1_{c'})}&quot;', from=2-1, to=3-1]
	\arrow[&quot;{F(g,1_c,1_{b'},1_{c'})}&quot;', from=2-2, to=3-3]
	\arrow[&quot;{F(1_b,f,1_{b'},1_{c'})}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>
respectively, which are equal, as we can, for example, can compare the top route in both using functoriality of $F$ and dinaturality of $\xi$.

For the other direction, suppose $E$ in $\mathcal{D}$ is a wedge of the right hand side, and hence comes with maps $\xi_b:E\to \int_{c:\mathcal{C}}F(b,b,c,c)$ for every $b \in \mathcal{B}$, which are dinatural in $b$. Composing the dinatural transformation $\xi$ with the natural transformation $\omega$ gives the wedge structure on $E$ over $F$ viewed as a bifunctor $(\mathcal{B}\times \mathcal{C})^{op}\times (\mathcal{B}\times \mathcal{C})\to \mathcal{D}$. This completes the proof.
`\end{proof}`
As an immediate corollary we get that we can permute iterated ends, as long as at least one (and hence all) of them exists.

## (co)Yoneda Lemma from (co)Ends

In this section we formulate the Yoneda lemma in terms of (co)ends and show that it has a dual version, often called the coYoneda lemma. Recall that for a locally small category $\mathcal{C}$, the yoneda Lemma states that for any presheaf $F:\mathcal{C}^{op}\to \mathsf{Set}$ we have an isomorphism
$$F(c) \cong \mathsf{Nat}(y^c,F)$$
which is natural in $F$ and $c\in \mathcal{C}$, where here $y^c = \mathcal{C}(-,c)$ is the image of $c$ under the yoneda embedding. From the [[Ends and coEnds#^be4441|example]] of $\mathsf{Nat}$ as a co-end this natural isomorphism becomes
$$F(c) \cong \int_{c\:\mathcal{C}}\mathsf{Set}(\mathcal{C}(c',c),F(c'))$$
which is sometimes called **Yoneda reduction**. The co-yoneda lemma is obtained by dualizing the end construction.

>[!proposition] coYoneda lemma
>For $F:\mathcal{C}^{op}\to \mathsf{Set}$ a pre-sheaf on a locally small category, we have an isomorphism
>$$F(c) \cong \int^{c':\mathcal{C}}\mathcal{C}(c,c')\times F(c')$$
>which is natural in $c \in \mathcal{C}$.

^d2333d

`\begin{proof}`
We can prove this claim using the yoneda embedding itself and the commutivity of homs with colimits in the first variable. Indeed, we have the following chain of isomorphisms for any presheaf $G:\mathcal{C}^{op}\to \mathsf{Set}$, natural in $G$:
$$
\begin{align*}
\mathsf{Nat}\left(\int^{c':\mathcal{C}}\mathcal{C}(-,c')\times F(c'),G\right) &\cong \int_{c':\mathcal{C}}\mathsf{Nat}(\mathcal{C}(-,c')\times F(c'),G) \\
&\cong \int_{c':\mathcal{C}}\int_{c:\mathcal{C}}\mathsf{Set}(\mathcal{C}(c,c')\times F(c'),G(c)) \\
&\cong \int_{c':\mathcal{C}}\int_{c:\mathcal{C}}\mathsf{Set}(F(c'),\mathsf{Set}(\mathcal{C}(c,c'),G(c))) \\
&\cong \int_{c':\mathcal{C}}\mathsf{Set}\left(F(c'),\int_{c:\mathcal{C}}\mathsf{Set}(\mathcal{C}(c,c'),G(c))\right) \\ 
&\cong \int_{c':\mathcal{C}}\mathsf{Set}(F(c'),G(c')) \tag{by Yoneda} \\
&\cong \mathsf{Nat}(F,G)
\end{align*}
$$
so by the yoneda embedding we obtain the desired natural isomorphism. This sequence of calculations illustrates the power of (co)end calculus. 
`\end{proof}`

#### References

[^1]: Mac Lane, S. (1978). Categories for the Working Mathematician (Vol. 5). New York, NY: Springer. https://doi.org/10.1007/978-1-4757-4721-8 ([Zotero Link](zotero://select/items/1_XFKT4GXC))