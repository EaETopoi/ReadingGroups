---
date: 2024-05-19T14:28:00
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

These notes aim to provide intuition for, and a number of examples of, Kan extensions and their prolific use in category theory. We begin with recalling the definitions of Kan extensions and pointwise Kan extensions before doing some computations and giving information on certain  (co)end formulas using results from [[Ends and coEnds]]. 

## Basics of Kan Extensions

Kan extensions can be thought to arise from the desire to answer a natural and prolific question in mathematics: if we have some relation of structures, i.e. a functor $F:\mathcal{A}\to \mathcal{C}$, such that $\mathcal{A}$ exists as a sub-object of some other structure, via $K:\mathcal{A}\to \mathcal{B}$, can we extend $F$ along $K$ in a way which is suitably universal? Another motivation for the study of Kan extensions comes from wanting to study the left and right adjoints of functors of the form $\mathcal{A}^K:\mathcal{A}^\mathcal{C}\to \mathcal{A}^\mathcal{B}$ for a category $\mathcal{A}$ and a functor $K:\mathcal{B}\to \mathcal{C}$.

>[!def] Kan Extensions
>Given functors $F:\mathcal{A}\to \mathcal{E}$ and $K:\mathcal{A}\to \mathcal{D}$, the **left Kan extension** of $F$ along $K$ is a functor $H:\mathcal{D}\to \mathcal{E}$ together with a natural transformation $\alpha:F\Rightarrow H\circ K$ such that for any other functor $G:\mathcal{D}\to \mathcal{E}$ with natural transformation $\beta:F\Rightarrow G\circ K$, there exists a unique natural transformation $\overline{\beta}:H\Rightarrow K$ such that $(\overline{\beta}*G)\circ \alpha = \beta$, which is to say
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BA%7D%7D%20%26%26%20%7B%5Cmathcal%7BE%7D%7D%20%26%20%7B%5Cmathcal%7BA%7D%7D%20%26%26%20%7B%5Cmathcal%7BE%7D%7D%20%5C%5C%0A%09%26%20%7B%5Cmathcal%7BD%7D%7D%20%26%26%26%20%7B%5Cmathcal%7BD%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22F%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22K%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22F%22%2C%20from%3D1-4%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22K%22'%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%09%5Carrow%5B%22%22%7Bname%3D3%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22G%22'%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D4%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22H%22%2C%20from%3D2-5%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D5%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22G%22'%2C%20bend%20right%20%3D%2070%2C%20from%3D2-5%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22%5Cbeta%22'%2C%20shorten%20%3C%3D3pt%2C%20Rightarrow%2C%20from%3D0%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Calpha%22'%2C%20shorten%20%3C%3D3pt%2C%20Rightarrow%2C%20from%3D1%2C%20to%3D2-5%5D%0A%09%5Carrow%5Bshorten%20%3C%3D26pt%2C%20shorten%20%3E%3D26pt%2C%20Rightarrow%2C%20no%20head%2C%20from%3D3%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%7B!%5Coverline%7B%5Cbeta%7D%7D%22%2C%20shorten%20%3C%3D4pt%2C%20shorten%20%3E%3D4pt%2C%20Rightarrow%2C%20from%3D4%2C%20to%3D5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathcal{A}} &amp;&amp; {\mathcal{E}} &amp; {\mathcal{A}} &amp;&amp; {\mathcal{E}} \\	&amp; {\mathcal{D}} &amp;&amp;&amp; {\mathcal{D}}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;F&quot;, from=1-1, to=1-3]	\arrow[&quot;K&quot;', from=1-1, to=2-2]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;F&quot;, from=1-4, to=1-6]	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;K&quot;', from=1-4, to=2-5]	\arrow[&quot;&quot;{name=3, anchor=center, inner sep=0}, &quot;G&quot;', from=2-2, to=1-3]	\arrow[&quot;&quot;{name=4, anchor=center, inner sep=0}, &quot;H&quot;, from=2-5, to=1-6]	\arrow[&quot;&quot;{name=5, anchor=center, inner sep=0}, &quot;G&quot;', bend right = 70, from=2-5, to=1-6]	\arrow[&quot;\beta&quot;', shorten &lt;=3pt, Rightarrow, from=0, to=2-2]	\arrow[&quot;\alpha&quot;', shorten &lt;=3pt, Rightarrow, from=1, to=2-5]	\arrow[shorten &lt;=26pt, shorten &gt;=26pt, Rightarrow, no head, from=3, to=2]	\arrow[&quot;{!\overline{\beta}}&quot;, shorten &lt;=4pt, shorten &gt;=4pt, Rightarrow, from=4, to=5]\end{tikzcd}" /></p>
>
>Dually, the **right Kan extension** of $F$ along $K$ is a functor $H:\mathcal{D}\to \mathcal{E}$ together with a natural transformation $\alpha:H\circ K\Rightarrow F$ such that for any functor $G:\mathcal{D}\to \mathcal{E}$ with natural transformation $\beta:G\circ K\Rightarrow F$ we have a unique natural transformation $\overline{\beta}:G\Rightarrow H$ such that $\alpha \circ (\overline{\beta}*G) = \beta$.

Suppose given functors $F:\mathcal{A}\to \mathcal{E}$ and $K:\mathcal{A}\to \mathcal{D}$ we had such a (left) extension $G:\mathcal{D}\to \mathcal{E}$. Then the natural transformation $\beta:F\Rightarrow G\circ K$ implies that for every $f:Ka\to d$  in $\mathcal{D}$ we have a map $F(a)\xrightarrow{\beta_a} G(K(a))\xrightarrow{G(f)}G(d)$, and together these maps give $G(d)$ the structure of a cocone under the functors $(K\downarrow d)\xrightarrow{\pi_0}\mathcal{A}\xrightarrow{F}\mathcal{E}$. Thus, to obtain a universal such extension a natural place to look is to take the colimit of this diagram. We now show that when the desired colimits exist such a construction indeed gives the left Kan extension of $F$ along $K$ (a dual approach using limits gives the right Kan extension).

>[!proposition] Left Kan Extension as Colimit
>Let $F:\mathcal{A}\to \mathcal{E}$ and $K:\mathcal{A}\to \mathcal{D}$ be functors such that for any $d \in \mathcal{D}$, the composite $(K\downarrow d)\xrightarrow{\pi_0}\mathcal{A}\xrightarrow{F}\mathcal{E}$ has a colimit in $\mathcal{E}$. Then the functor $L:\mathcal{D}\to \mathcal{E}$ defined by sending an object of $\mathcal{D}$ to this limit define a functor with the limiting cone giving a natural transformation $\alpha:F\Rightarrow L\circ K$ which is universal.

^42a123

`\begin{proof}`
For each $d \in \mathcal{D}$, let $\lambda_d:F\circ \pi_0^d\Rightarrow \Delta_{L(d)}$ denote the limit cocone. Then, for $g:d\to d'$ in $\mathcal{D}$, we have a unique map $L(g):L(d)\to L(d')$ given by the universal property of the colimit applied to the cone $\lambda_{d'}*(K\downarrow g)$, where $(K\downarrow g):(K\downarrow d)\to (K\downarrow d')$ is given by post-composition, and we use the fact that $\pi_0^d = \pi_0^{d'}\circ (K\downarrow g)$. Explicitly, this says that $L(g)$ is the unique map such that for any $f:Ka\to d$, the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BF(a)%7D%20%26%20%7BL(d)%7D%20%5C%5C%0A%09%26%20%7BL(d')%7D%0A%09%5Carrow%5B%22%7B(%5Clambda_d)_f%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B(%5Clambda_%7Bd'%7D)_%7Bg%5Ccirc%20f%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7BL(g)%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{F(a)} &amp; {L(d)} \\
	&amp; {L(d')}
	\arrow[&quot;{(\lambda_d)_f}&quot;, from=1-1, to=1-2]
	\arrow[&quot;{(\lambda_{d'})_{g\circ f}}&quot;', from=1-1, to=2-2]
	\arrow[&quot;{L(g)}&quot;, from=1-2, to=2-2]
\end{tikzcd}
" /></p>
commutes. By uniqueness $L$ is functorial with this assignment.

Note that we have for each $a \in \mathcal{A}$ the natural transformation $\lambda_{Ka}:F\circ \pi_0^{Ka}\Rightarrow \Delta_{L(K(a))}$. Then we define $\alpha:F\Rightarrow L\circ K$ by $\alpha_a:= (\lambda_{Ka})_{1_{Ka}}:F(a)\to L(K(a))$. Note this is natural in $a$ since for $g:a\to a'$ in $\mathcal{A}$ we obtain the commuting square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BF(a)%7D%20%26%26%20%7BF(a')%7D%20%5C%5C%0A%09%5C%5C%0A%09%7BL(K(a))%7D%20%26%26%20%7BL(K(a'))%7D%0A%09%5Carrow%5B%22%7BF(g)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B(%5Clambda_%7BKa%7D)_%7B1_%7BKa%7D%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B(%5Clambda_%7BKa'%7D)_%7BK(g)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B(%5Clambda_%7BKa'%7D)_%7B1_%7BKa'%7D%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BL(K(g))%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{F(a)} &amp;&amp; {F(a')} \\
	\\
	{L(K(a))} &amp;&amp; {L(K(a'))}
	\arrow[&quot;{F(g)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{(\lambda_{Ka})_{1_{Ka}}}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{(\lambda_{Ka'})_{K(g)}}&quot;, from=1-1, to=3-3]
	\arrow[&quot;{(\lambda_{Ka'})_{1_{Ka'}}}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{L(K(g))}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where the upper triangle commutes by naturality of $\lambda_{Ka'}$ and the lower triangle commutes by definition of $L(K(g))$. 

Finally, to see that this pair $(L,\alpha)$ is the left Kan extension of $F$ along $K$, let $G:\mathcal{D}\to \mathcal{E}$ be another functor together with a natural transformation $\beta:F\Rightarrow G\circ K$. As discussed prior to the proposition, this natural transformation gives $G(d)$ for each $d \in \mathcal{D}$, the structure of a cocone under $F\circ \pi_0^d$. Thus, for each $d \in \mathcal{D}$ we have a unique map $\overline{\beta}_d:L(d)\to G(d)$ such that for each $f:Ka\to d$ in $(K\downarrow d)$, $\overline{\beta}_d\circ (\lambda_d)_f = G(f)\circ \beta_a$. In particular, $(\overline{\beta}*K)\circ \alpha = \beta$. Note that $\overline{\beta}$ is natural since for any $g:d\to d'$, and any $f:Ka\to d$, we can form the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BF(a)%7D%20%26%20%7BL(d)%7D%20%26%20%7BL(d')%7D%20%5C%5C%0A%09%7BG(K(a))%7D%20%26%20%7BG(d)%7D%20%26%20%7BG(d')%7D%0A%09%5Carrow%5B%22%7B(%5Clambda_d)_f%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B(%5Clambda_%7Bd'%7D)_%7Bg%5Ccirc%20f%7D%7D%22%2C%20bend%20left%20%3D%2040%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cbeta_a%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7BL(g)%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Coverline%7B%5Cbeta%7D_d%7D%22'%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Coverline%7B%5Cbeta%7D_%7Bd'%7D%7D%22%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7BG(f)%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7BG(g%5Ccirc%20f)%7D%22'%2C%20bend%20right%20%3D%2040%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7BG(g)%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{F(a)} &amp; {L(d)} &amp; {L(d')} \\
	{G(K(a))} &amp; {G(d)} &amp; {G(d')}
	\arrow[&quot;{(\lambda_d)_f}&quot;, from=1-1, to=1-2]
	\arrow[&quot;{(\lambda_{d'})_{g\circ f}}&quot;, bend left = 40, from=1-1, to=1-3]
	\arrow[&quot;{\beta_a}&quot;', from=1-1, to=2-1]
	\arrow[&quot;{L(g)}&quot;, from=1-2, to=1-3]
	\arrow[&quot;{\overline{\beta}_d}&quot;', from=1-2, to=2-2]
	\arrow[&quot;{\overline{\beta}_{d'}}&quot;, from=1-3, to=2-3]
	\arrow[&quot;{G(f)}&quot;', from=2-1, to=2-2]
	\arrow[&quot;{G(g\circ f)}&quot;', bend right = 40, from=2-1, to=2-3]
	\arrow[&quot;{G(g)}&quot;', from=2-2, to=2-3]
\end{tikzcd}
" /></p>
where the left square and outer rectangle commute by construction of $\overline{\beta}$. Thus, the right hand square commutes upon pre-composition by $(\lambda_d)_f$ for all $f:Ka\to d$ in $(K\downarrow d)$. But, $\lambda_d$ is a co-limiting cone, so by uniqueness the right square commutes as well, and hence $\overline{\beta}$ is natural.

It remains to show that $\overline{\beta}$ is unique. Let $\gamma:L\Rightarrow G$ be another natural isomorphism such that $\gamma_{Ka}\circ (\lambda_{Ka})_{1_{Ka}} =\beta_a$. Then for any $f:Ka\to d$ in $(K\downarrow d)$ we can use the previous commuting diagram with $\overline{\beta}$ replaced by $\gamma$ to compute 
$$\gamma_d\circ (\lambda_d)_f = \gamma_d\circ L(f)\circ (\lambda_{Ka})_{1_{Ka}} = G(f)\circ \gamma_{Ka}\circ (\lambda_{Ka})_{1_{Ka}} = G(f) \circ \beta_a$$
but this is the equality that uniquely defines $\overline{\beta}$, so $\gamma = \overline{\beta}$, as desired.
`\end{proof}`

We obtain the following immediate corollary.

>[!corollary] Existence of Left Kan Extensions
>If $F:\mathcal{A}\to \mathcal{E}$ is a functor where $\mathcal{E}$ is co-complete and $\mathcal{A}$ is small, then $F$ has a left Kan extension along any $K:\mathcal{A}\to \mathcal{D}$. In particular, $\mathcal{E}^K$ has a left adjoint.

^8ae769

The only non-trivial part of this corollary is that $\mathcal{E}^K$ has left adjoint. However, this follows from the observation that a left adjoint to $\mathcal{E}^K:\mathcal{E}^\mathcal{D}\to \mathcal{E}^\mathcal{A}$ is a functor $\text{Lan}_K:\mathcal{E}^\mathcal{A}\to \mathcal{E}^\mathcal{D}$ such for any $F:\mathcal{A}\to \mathcal{E}$ and any $G:\mathcal{D}\to \mathcal{E}$ we have a natural bijection
$$\mathcal{E}^\mathcal{D}(\text{Lan}_K(F),G) \cong \mathcal{E}^\mathcal{A}(F,\mathcal{E}^K(G))$$
which is precisely the universal property of the left Kan extension. Note that as in the general case for universal property constructions of functor, $\text{Lan}_K$ indeed defines such a functor when all such left Kan extensions exist. Further, when $\mathcal{A}$ is small and $\mathcal{E}$ is (co)complete (for example $\mathcal{E} = \mathsf{Set}$), then we have a pair of adjunctions
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BE%7D%5E%5Cmathcal%7BD%7D%7D%20%26%26%20%7B%5Cmathcal%7BE%7D%5E%5Cmathcal%7BA%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathcal%7BE%7D%5EK%7D%22'%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ctext%7BRan%7D_K%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ctext%7BLan%7D_K%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D2%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{E}^\mathcal{D}} &amp;&amp; {\mathcal{E}^\mathcal{A}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathcal{E}^K}&quot;', from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\text{Ran}_K}&quot;', bend right = 60, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{\text{Lan}_K}&quot;', bend right = 60, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=2, to=0]
\end{tikzcd}
" /></p>
When extending along an embedding (i.e. a fully-faithful functor) our Kan extensions truly extend the functor of interest up to natural isomorphism.

>[!corollary] Extending along Fully-Faithful Functors
>Let $F:\mathcal{A}\to \mathcal{E}$ and $K:\mathcal{A}\to \mathcal{D}$ be functors such that for any $d \in \mathcal{D}$, the composite $(K\downarrow d)\xrightarrow{\pi_0}\mathcal{A}\xrightarrow{F}\mathcal{E}$ has a colimit in $\mathcal{E}$. If $K$ is fully-faithful then universal natural transformation $\alpha:F\Rightarrow L\circ K$ factoring through the left Kan extension of $F$ along $K$ is a natural isomorphism.

^90826e

`\begin{proof}`
Recall that $L\circ K(a)$ is given as the colimit of the composite $(K\downarrow Ka)\xrightarrow{\pi_0}\mathcal{A}\xrightarrow{F}\mathcal{E}$. Since $K$ is fully faithful every object $f:Ka'\to Ka$ in the comma category $(K\downarrow Ka)$ can be written uniquely as $Kh:Ka'\to Ka$ for some map $h:a'\to a$ in $\mathcal{A}$. Then the identity $1_{Ka}:Ka\to Ka$ is terminal in $(K\downarrow Ka)$. It follows that the colimit can be obtained by evaluating at this terminal object, which is precisely $F(a)$, so $L\circ K\cong F$.
`\end{proof}`

[[Kan Extensions#^90826e|Corollary 4]] implies that when $K$ is in fact the inclusion of a full-subcategory, we can take $\alpha = 1_F$. 

### (co)End Formulas

We can now combine our work in [[Ends and coEnds]] with our current work on Kan extensions by realizing Kan extensions as certain (co)Ends, provided some assumptions on our domain and codomain categories. In this section we will treat right Kan extensions since the last section was carried out for left Kan extensions (though by duality we obtain results for the other from proofs for one). 

>[!theorem] Kan Extensions as Ends
>Let $F:\mathcal{A}\to \mathcal{E}$ and $K:\mathcal{A}\to \mathcal{D}$ such that for each $a,a' \in \mathcal{A}$ and each $d \in \mathcal{D}$, the power $F(a)^{\mathcal{D}(d,Ka')}$ exists in $\mathcal{A}$ (explicitly $F(a)^{\mathcal{D}(d,Ka')} = \prod_{g \in \mathcal{D}(d,Ka')}F(a)$), then $F$ has a right Kan extension $R$ along $K$ if for each $d \in \mathcal{D}$ the following end exists and $R$ is given on objects by this end:
>$$Rd = \int_{a:\mathcal{A}}F(a)^{\mathcal{D}(d,Ka)}$$
>

^79496e

`\begin{proof}`
By [[Ends and coEnds#^c13d5c]] we can view the right hand side as a functor $\int_{a:\mathcal{A}}F(a)^{\mathcal{D}(-,Ka)}:\mathcal{D}\to \mathcal{E}$. Observe that for $G:\mathcal{D}\to \mathcal{E}$ we have natural isomorphisms
$$\mathcal{E}(G\circ Ka,Fa)\cong \mathsf{Nat}(\mathcal{D}(-,Ka),\mathcal{E}(G-,Fa))\cong \int_{d:\mathcal{D}}\mathsf{Ens}(\mathcal{D}(d,Ka),\mathcal{E}(Gd,Fa))$$
where $\mathsf{Ens}$ is a sufficiently large full subcategory of $\mathsf{Set}$[^1]. With this in mind we can make the following chain of natural isomorphisms using a combination of continuity of Hom, the expression of $\mathsf{Nat}$ as an end, the universal property of powers, and [[Ends and coEnds#^60fafc]]:
$$
\begin{align*}
\mathsf{Nat}(G,R) &\cong \int_{d:\mathcal{D}}\mathcal{E}(Gd,Rd) \\
&\cong \int_{d:\mathcal{D}}\int_{a:\mathcal{A}}\mathcal{E}(Gd,F(a)^{\mathcal{D}(d,Ka)}) \\
&\cong \int_{d:\mathcal{D}}\int_{a:\mathcal{A}}\mathsf{Ens}(\mathcal{D}(d,Ka),\mathcal{E}(Gd,Fa)) \\
&\cong \int_{a:\mathcal{A}}\int_{d:\mathcal{D}}\mathsf{Ens}(\mathcal{D}(d,Ka),\mathcal{E}(Gd,Fa)) \\
&\cong \int_{a:\mathcal{A}}\mathcal{E}(GKa,Fa) \\
&\cong \mathsf{Nat}(GK,F)
\end{align*}
$$
as desired, where we can use Fubini since both ends exist. Further, $\mathsf{Ens}$ must be a sufficiently large category of sets in order to contain all hom sets for $\mathcal{D}$ and $\mathcal{E}$ and all sets of natural transformations.

To obtain the co-unit of the Kan extension we replace $G$ by $R$ and trace the identities through the chain of isomorphisms, where for each $d \in \mathcal{D}$, $\omega_d$ denotes the wedge associated with $Rd$.:
$$1_R\mapsto \int_{d:\mathcal{D}}1_{R(d)}\mapsto \int_{d:\mathcal{D}}\int_{a:\mathcal{A}}(\omega_d)_a \mapsto \int_{a:\mathcal{A}}\int_{d:\mathcal{D}}(\omega_d)_a^\# \mapsto \omega^\#$$
where $\omega^\#:GK\Rightarrow F$ is the natural transformation given at $a \in \mathcal{A}$ by $\omega_a^\#:GK(a)\to F(a)$ which is $\pi_{1_{Ka}}\circ (\omega_{Ka})_a$. 
`\end{proof}`
## Pointwise Kan Extensions

Although Kan extensions on their own satisfy a number of interesting properties, in general they are not the truly useful notion. The reason for this is that general Kan extensions are not always preserved by representable functors, where the following characterizes what we mean when we say a functor preserves a Kan extension.

>[!def] Preservation of Kan Extensions
>We say a functor $G:\mathcal{E}\to \mathcal{C}$ preserves the left Kan extension of $F:\mathcal{A}\to \mathcal{E}$ along $K:\mathcal{A}\to \mathcal{D}$, $(\text{Lan}_KF,\eta)$, if $(G\circ \text{Lan}_KF,G*\eta)$ is a left Kan extension of $G\circ F:\mathcal{A}\to \mathcal{C}$ (vice-versa for right Kan extensions).

For example, left (resp. right) adjoints preserve all left (resp. right) Kan extensions.

>[!theorem] Adjoints Preserve Kan Extensions
>If $F:\mathcal{A}\to \mathcal{E}$ has a left Kan extension along $K:\mathcal{A}\to \mathcal{D}$, $(\text{Lan}_KF,\eta)$, and if $G:\mathcal{E}\to \mathcal{C}$ is a left adjoint, then $G$ preserves the left Kan extension of $F$ along $K$.

`\begin{proof}`
Let $R$ be the right adjoint of $G$. Then for $S:\mathcal{D}\to \mathcal{C}$ we have a sequence of natural isomorphisms
$$\mathcal{C}^\mathcal{A}(G\circ F,S\circ K) \cong \mathcal{E}^\mathcal{A}(F,R\circ S\circ K) \cong \mathcal{E}^\mathcal{D}(\text{Lan}_KF,R\circ S) \cong \mathcal{C}^\mathcal{D}(G\circ \text{Lan}_KF,S)$$
Let $\iota:1_{\mathcal{E}}\Rightarrow R\circ G$ denote the unit of the adjunction and let $\epsilon:G\circ R\Rightarrow 1_{\mathcal{C}}$ denote the co-unit of the adjunction. Then plugging in $G\circ \text{Lan}_KF$ for $S$ and tracing the identity along the natural isomorphisms (from right to left) we have that the unit of the left Kan extension is
$$1_{G\text{Lan}_KF}\mapsto \iota_{\text{Lan}_KF}\mapsto (\iota_{\text{Lan}_KF}*K)\circ \eta \mapsto \epsilon_{G\text{Lan}_KF\circ K}\circ G\iota_{\text{Lan}_KF\circ K}\circ (G*\eta)=G*\eta$$
this completes the proof.
`\end{proof}`
Note that when $\mathcal{E}$ has all copowers for $e \in \mathcal{E}$, $\mathcal{E}(e,-):\mathcal{E}\to \mathsf{Set}$ has a left adjoint given by the co-power. Thus, in this case $\mathcal{E}(e,-)$ preserves right Kan extensions. However, this need not always be the case. The type of Kan extensions which are preserved by all representable functors are called **pointwise Kan extensions**.

>[!def] Pointwise Kan Extension
>Let $F:\mathcal{A}\to \mathcal{E}$ and $K:\mathcal{A}\to \mathcal{D}$ be functors with $\mathcal{E}$ locally small (i.e. enriched in $\mathsf{Set}$). Then a right Kan extension of $F$ is a right Kan extension which is preserved by all representable functors $\mathcal{E}(e,-)$. A left Kan extension of $F$ is a left Kan extension whose opposite is preserved by all representable functors $\mathcal{E}^{op}(e,-) = \mathcal{E}(-,e)$. 

It turns out that pointwise Kan extensions are exactly those as computed in [[Kan Extensions#^42a123|Proposition 2]].

>[!theorem] Pointwise Kan Extensions
>A functor $F:\mathcal{A}\to \mathcal{E}$ into a locally small category has a pointwise left Kan extension along $K:\mathcal{A}\to \mathcal{D}$ if and only if the colimits in [[Kan Extensions#^42a123|Proposition 2]] exist, and in which case the left Kan extension is given in terms of them.

`\begin{proof}`
If the colimits exist, then as proven in [[Kan Extensions#^42a123|Proposition 2]] they define a left Kan extension $(L,\eta)$ for $F$ along $K$. Further, for any $e \in \mathcal{E}$ we have that 
$$
\begin{align*}
\mathcal{E}^{op}(e,Ld) \cong \lim_{\xrightarrow[(f:Ka\to d)\in (K\downarrow d)]{}}\mathcal{E}^{op}(e,F(a)) =\lim_{\xrightarrow[(f:d\to Ka)\in (d\downarrow K)_{\mathcal{D}^{op}}]{}}\mathcal{E}^{op}(e,F)\circ \pi_0^d(f)
\end{align*}
$$
and so by the dual to [[Kan Extensions#^42a123|Proposition 2]] we have that $(\mathcal{E}^{op}(e,L^{op}),\mathcal{E}^{op}(e,\eta^{op}))$ is a right Kan extension of $\mathcal{E}^{op}(e,F^{op})$ along $K^{op}$, and so $L$ is by definition a pointwise left Kan extension.

Conversely, suppose $(L,\eta)$ is a pointwise left Kan extension of $F$ along $K$. Then by assumption for any $e \in \mathcal{E}$,  $(\mathcal{E}^{op}(e,L^{op}),\mathcal{E}^{op}(e,\eta^{op}))$ is a right Kan extension of $\mathcal{E}^{op}(e,F^{op})$ along $K^{op}$. Then we have that 
$$\mathcal{E}^{op}(e,L^{op}(d)) \cong \mathsf{Set}^{\mathcal{D}^{op}}(\mathcal{D}^{op}(d,-),\mathcal{E}^{op}(e,L^{op}-))\cong \mathsf{Set}^{\mathcal{A}^{op}}(\mathcal{D}^{op}(d,K^{op}-),\mathcal{E}^{op}(e,F^{op}-))$$
using Yoneda followed by the definition of a right Kan extension. Note that an element of the right hand side assigns for every $f:d\to K^{op}a$ in $\mathcal{D}^{op}$ an element $g:e\to F^{op}a$ in a way that is natural in $g$. This is precisely the data of a cone of $(d\downarrow K^{op})\xrightarrow{\pi_1^d}\mathcal{A}^{op}\xrightarrow{F^{op}}\mathcal{E}^{op}$ under $e$, so applying this observation on the right we find 
$$\mathcal{E}^{op}(e,L^{op}(d))\cong \mathsf{Cone}(e, F^{op}\circ \pi_1^d)$$
Removing all $op$'s this is equivalent to
$$\mathcal{E}(L(d),e)\cong \mathsf{coCone}(F\circ \pi_0^d,e)$$
which is natural in $e$. Thus, this says that the co-cones are representable, and that $L(d)$ is the desired colimit.
`\end{proof}`

### All Concepts are Kan Extensions





#### References

[^1]: See the discussion in Mac Lane, S. (1978). Categories for the Working Mathematician (Vol. 5). New York, NY: Springer. https://doi.org/10.1007/978-1-4757-4721-8 for more details.