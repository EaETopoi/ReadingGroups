---
date: 2024-05-23T11:51:00
tags:
  - CategoryTheory
  - Homotopy
  - FiberedCategories
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

As evidenced by the prevalence of relative schemes and integral models in algebraic and arithmetic geometry, a tool of central importance is that of base-change. However, base-change is an operation that exists on slice categories in a far greater level of generality than geometric categories, like the category of relative schemes over some base.

In this section we will prove that if a category has pullbacks, then it has a notion of base-change between slice categories. Additionally, we will prove that base change always has a left-adjoint, and that in the case of categories such as Grothendieck topoi which have exponential objects, the base change also has a right-adjoint. 

## Cartesian Lifts and Fibered Categories

We will begin by constructing base-change functors out of the theory of fibered categories[^1] To begin we must define the notion of a cartesian lift.

>[!def] (Strong) Cartesian Lifts
>Let $p:\mathcal{E}\to \mathcal{B}$ be a functor. A **(strong) cartesian lift** of an arrow $f:B\to B'$ in $\mathcal{B}$ is an arrow $f^*_X:f^*X\to X$ in $\mathcal{E}$ above $f$ such that for any $g:Y\to X$ in $\mathcal{E}$ and any filling $h:p(Y)\to B$ of the triangle in $\mathcal{B}$, we have a unique filling of the triangle in $\mathcal{E}$:
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09Y%20%5C%5C%0A%20%20%20%20%09%7Bf%5E*X%7D%20%26%20X%20%5C%5C%0A%20%20%20%20%09%7Bp(Y)%7D%20%5C%5C%0A%20%20%20%20%09B%20%26%20%7BB'%7D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D4-1%2C%20to%3D4-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp(g)%7D%22%2C%20from%3D3-1%2C%20to%3D4-2%5D%0A%20%20%20%20%09%5Carrow%5B%22h%22'%2C%20from%3D3-1%2C%20to%3D4-1%5D%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists!%5Cwidetilde%7Bh%7D%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5Bdotted%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]    	Y \\    	{f^*X} &amp; X \\    	{p(Y)} \\    	B &amp; {B'}    	\arrow[&quot;f&quot;', from=4-1, to=4-2]    	\arrow[&quot;{p(g)}&quot;, from=3-1, to=4-2]    	\arrow[&quot;h&quot;', from=3-1, to=4-1]    	\arrow[&quot;g&quot;, from=1-1, to=2-2]    	\arrow[&quot;{f^*_X}&quot;', from=2-1, to=2-2]    	\arrow[&quot;{\exists!\widetilde{h}}&quot;', dashed, from=1-1, to=2-1]    	\arrow[dotted, from=2-1, to=3-1]    \end{tikzcd}" /></p>

Moving forward we drop the adjective **strong** and just refer to them as **cartesian lifts**. Cartesian lifts now let us characterize fibrations of categories.

>[!def] Fibered Categories
>A **fibration** of categories is a functor $p:\mathcal{E}\to \mathcal{B}$ such that for every $f:B\to B'$ in $\mathcal{B}$, and every $X \in p^{-1}(B')$, there exists a cartesian lift of $f$ with codomain $X$, $f^*_X:f^*X\to X$.
>
>An **opfibration** of categories is a functor $p:\mathcal{E}\to \mathcal{B}$ such that for every $f:B\to B'$ in $\mathcal{B}$, and every $X \in p^{-1}(B)$, there exists an **opcartesian lift** of $f$ with domain $X$, $f_{!,X}:X\to f_!X$.

One of the many reasons for studying fibrations, also known as fibered categories, is that they provide a sensible way of producing functors between fibers above objects in the base category $\mathcal{B}$. Here, the fiber $p^{-1}(B)$ above an object $B \in \mathcal{B}_0$ is the subcategory of $\mathcal{E}$ consisting of objects $X \in \mathcal{E}_0$ such that $p(X) = B$ and arrows $f:X\to Y$ between such objects such that $p(f) = 1_B$.


Provided we have a choice of cartesian lift above each arrow $f:B\to B'$ in $\mathcal{B}$ and each $X \in p^{-1}(B')_0$, these cartesian lifts provide base-change functors between the fibers. Classically a choice of cartesian lifts for a fibration is called a **cleavage**.

>[!proposition] Base Change
>Let $p:\mathcal{E}\to \mathcal{B}$ be a fibration with a cleavage. Then each $f:A\to B$ in $\mathcal{B}$ induces a functor $f^*:p^{-1}(B)\to p^{-1}(A)$.

^9803ab

`\begin{proof}`
Fix $f:A\to B$ in $\mathcal{B}$. For each $X \in p^{-1}(B)_0$ we have a specified cartesian lift $f^*_X:f^*X\to X$, where $f^*X$ lies above $A$. We define $f^*:p^{-1}(B)\to p^{-1}(A)$ on objects by $f^*(X) := \text{dom}(f^*_X)$. Next, let $g:Y\to X$ be a map in $p^{-1}(B)$. By the defining property of a cartesian lift we obtain a unique filling above the identity:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7Bf%5E*Y%7D%20%26%20Y%20%26%26%20A%20%26%20B%20%5C%5C%0A%20%20%20%20%09%26%20%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_Y%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22g%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists%20!f%5E*g%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5Bshorten%20%3C%3D19pt%2C%20shorten%20%3E%3D19pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D0%2C%20to%3D1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{f^*Y} &amp; Y &amp;&amp; A &amp; B \\
    	&amp; {f^*X} &amp; X &amp;&amp; A &amp; B
    	\arrow[&quot;{f^*_Y}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;g&quot;, from=1-2, to=2-3]
    	\arrow[&quot;{f^*_X}&quot;', from=2-2, to=2-3]
    	\arrow[&quot;{\exists !f^*g}&quot;', dashed, from=1-1, to=2-2]
    	\arrow[&quot;f&quot;, from=1-4, to=1-5]
    	\arrow[Rightarrow, no head, from=1-5, to=2-6]
    	\arrow[&quot;f&quot;', from=2-5, to=2-6]
    	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=2-5]
    	\arrow[shorten &lt;=19pt, shorten &gt;=19pt, dotted, tail reversed, from=0, to=1]
    \end{tikzcd}
" /></p>
We define $f^*(g)$ to be this unique filling. By uniqueness, $f^*1_X = 1_{f^*X}$ since it fills the diagram:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%20%5C%5C%0A%20%20%20%20%09%26%20%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5Bshorten%20%3C%3D13pt%2C%20shorten%20%3E%3D13pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D0%2C%20to%3D1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{f^*X} &amp; X &amp;&amp; A &amp; B \\
    	&amp; {f^*X} &amp; X &amp;&amp; A &amp; B
    	\arrow[&quot;{f^*_X}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-2, to=2-3]
    	\arrow[&quot;{f^*_X}&quot;', from=2-2, to=2-3]
    	\arrow[&quot;f&quot;, from=1-4, to=1-5]
    	\arrow[Rightarrow, no head, from=1-5, to=2-6]
    	\arrow[&quot;f&quot;', from=2-5, to=2-6]
    	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=2-5]
    	\arrow[Rightarrow, no head, from=1-1, to=2-2]
    	\arrow[shorten &lt;=13pt, shorten &gt;=13pt, dotted, tail reversed, from=0, to=1]
    \end{tikzcd}
" /></p>
Finally, if $h:Z\to Y$ is another map in the fiber $p^{-1}(B)$, then we have the composite diagram:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bf%5E*Z%7D%20%26%20Z%20%26%26%20A%20%26%20B%20%5C%5C%0A%09%26%20%7Bf%5E*Y%7D%20%26%20Y%20%26%26%20A%20%26%20B%20%5C%5C%0A%09%26%26%20%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_Y%7D%22%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D2-3%2C%20to%3D3-4%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists%20!f%5E*g%7D%22'%2C%20dashed%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-6%2C%20to%3D3-7%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D3-6%2C%20to%3D3-7%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-5%2C%20to%3D3-6%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_Z%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22h%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists!f%5E*h%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%20%20%20%20%09%5Carrow%5Bshorten%20%3C%3D14pt%2C%20shorten%20%3E%3D14pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D2-3%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists%20!f%5E*(g%5Ccirc%20h)%7D%22'%2C%20bend%20right%20%3D%2060%2C%20dashed%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{f^*Z} &amp; Z &amp;&amp; A &amp; B \\
	&amp; {f^*Y} &amp; Y &amp;&amp; A &amp; B \\
	&amp;&amp; {f^*X} &amp; X &amp;&amp; A &amp; B
    	\arrow[&quot;{f^*_Y}&quot;, from=2-2, to=2-3]
    	\arrow[&quot;g&quot;, from=2-3, to=3-4]
    	\arrow[&quot;{f^*_X}&quot;', from=3-3, to=3-4]
    	\arrow[&quot;{\exists !f^*g}&quot;', dashed, from=2-2, to=3-3]
    	\arrow[&quot;f&quot;, from=2-5, to=2-6]
    	\arrow[Rightarrow, no head, from=2-6, to=3-7]
    	\arrow[&quot;f&quot;', from=3-6, to=3-7]
    	\arrow[Rightarrow, no head, from=2-5, to=3-6]
    	\arrow[&quot;{f^*_Z}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;h&quot;, from=1-2, to=2-3]
    	\arrow[&quot;{\exists!f^*h}&quot;', dashed, from=1-1, to=2-2]
    	\arrow[&quot;f&quot;, from=1-4, to=1-5]
    	\arrow[shorten &lt;=14pt, shorten &gt;=14pt, dotted, tail reversed, from=2-3, to=2-5]
    	\arrow[Rightarrow, no head, from=1-5, to=2-6]
    	\arrow[Rightarrow, no head, from=1-4, to=2-5]
    	\arrow[&quot;{\exists !f^*(g\circ h)}&quot;', bend right = 60, dashed, from=1-1, to=3-3]
    \end{tikzcd}
" /></p>
where by uniqueness of the filling $f^*(g\circ h) = f^*g\circ f^*h$. Thus $f^*:p^{-1}(B)\to p^{-1}(A)$ is a functor.
`\end{proof}`

The primary example of interest for us is called the standard fibration. For a category $\mathcal{C}$, we always have a category $\mathcal{C}^2$ which has arrows, $f:A\to B$, as objects, and commutative squares between arrows
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20B%20%5C%5C%0A%09X%20%26%20Y%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22g%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22k%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; B \\
	X &amp; Y
	\arrow[&quot;f&quot;, from=1-1, to=1-2]
	\arrow[&quot;h&quot;', from=1-1, to=2-1]
	\arrow[&quot;g&quot;', from=2-1, to=2-2]
	\arrow[&quot;k&quot;, from=1-2, to=2-2]
\end{tikzcd}
" /></p>
as maps. Additionally, we have a natural projection functor $\pi_1:\mathcal{C}^2\to \mathcal{C}$ given by sending arrows to their codomains and squares to the maps between codomains on the right edge of the square. 

When $\mathcal{C}$ has pullbacks the functor $\pi_1$ is a fibration of categories, where the cartesian lifts are pullback squares. Indeed, going through our definition of a cartesian arrow we obtain that a filling corresponds to the closing of a wedge, where the closing map is the unique one induced by the pullback
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20X%20%26%26%20M%20%5C%5C%0A%09Y%20%26%20A%20%26%20N%20%5C%5C%0A%09B%20%26%20M%20%26%26%20Y%20%26%26%20B%0A%09%5Carrow%5B%22g%22'%7Bpos%3D0.2%7D%2C%20dashed%2C%20from%3D2-2%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22k%22'%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22h%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-2%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22k%22'%2C%20from%3D3-4%2C%20to%3D3-6%5D%0A%09%5Carrow%5B%22s%22%2C%20from%3D2-3%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%5Cell%22%2C%20from%3D3-2%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22r%22'%2C%20from%3D2-3%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Cell%22%2C%20from%3D1-4%2C%20to%3D3-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22t%22'%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22t%22'%7Bpos%3D0.2%7D%2C%20from%3D3-2%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7B%5Cexists!%5Cwidetilde%7Bt%7D%7D%22'%2C%20dashed%2C%20from%3D2-3%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1-2%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bshorten%20%3E%3D12pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D2-3%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; X &amp;&amp; M \\
	Y &amp; A &amp; N \\
	B &amp; M &amp;&amp; Y &amp;&amp; B
	\arrow[&quot;g&quot;'{pos=0.2}, dashed, from=2-2, to=3-1]
	\arrow[&quot;k&quot;', from=2-1, to=3-1]
	\arrow[&quot;h&quot;, from=1-2, to=2-2]
	\arrow[&quot;f&quot;', from=1-2, to=2-1]
	\arrow[&quot;k&quot;', from=3-4, to=3-6]
	\arrow[&quot;s&quot;, from=2-3, to=3-2]
	\arrow[&quot;\ell&quot;, from=3-2, to=3-1]
	\arrow[&quot;r&quot;', from=2-3, to=2-2]
	\arrow[&quot;\ell&quot;, from=1-4, to=3-6]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;t&quot;', from=1-4, to=3-4]
	\arrow[&quot;t&quot;'{pos=0.2}, from=3-2, to=2-1]
	\arrow[&quot;{\exists!\widetilde{t}}&quot;', dashed, from=2-3, to=1-2]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=-90}, draw=none, from=1-2, to=3-1]
	\arrow[shorten &gt;=12pt, dotted, tail reversed, from=2-3, to=0]
\end{tikzcd}
" /></p>
A cleavage is simply a choice of pullback for each diagram. Then for $C \in \mathcal{C}_0$, the fiber category $\pi_1^{-1}(C)$ is isomorphic to the slice category $\mathcal{C}/C$. It follows that given a cleavage for $\pi_1$, [[Basic Fibered Categories#^9803ab]] implies that we have well-defined base-change functors $f^*:\mathcal{C}/B\to \mathcal{C}/A$ for $f:A\to B$ in $\mathcal{C}$ induced by pullback.


Dually to all of the definitions and results so far we have a notion of opfibrations of categories where we consider opcartesian lifts which have the dual property. Given an opfibration $p:\mathcal{E}\to \mathcal{B}$ with opcleavage we denote the induced functor on fibers for a map $f:A\to B$ by $f_!:p^{-1}(A)\to p^{-1}(B)$. We will now show that a fibration is also an opfibration, and vice-versa, if and only if its pullback functors have left-adjoints[^2].

>[!proposition] Fibration v Opfibration
>A fibration $p:\mathcal{E}\to \mathcal{B}$ is an opfibration if and only if all pullback functors $f^*:p^{-1}(B)\to p^{-1}(A)$, for $f:A\to B$, have left adjoints.

`\begin{proof}`
Let $f:A\to B$ be a map in $\mathcal{B}$. Note that by the classification of cartesian lifts applied to identity fillings, we have a natural bijection between maps $Y\to X$ in $\mathcal{E}$ lying over $f$ and maps $Y\to f^*X$ in $p^{-1}(A)$. On the other hand, the dual property for opcartesian lifts gives a bijection between maps $Y\to X$ over $f$ and maps $f_!Y\to X$ in $p^{-1}(B)$. In other words, we have the natural bijection
$$p^{-1}(B)(f_!Y,X)\cong p^{-1}(B)(Y,f^*X)$$
so the existence of opcartesian lifts is equivalent to the existence of right adjoints, and vice-versa if we start with an opfibration.
`\end{proof}`

The standard fibration $\pi_1:\mathcal{C}^2\to \mathcal{C}$ has left-adjoints for all of its base-change functors, and so itself is also an opfibration. Indeed, given $f:A\to B$, the left adjoint to $f^*$, $f_!:\mathcal{C}/A\to \mathcal{C}/B$ is given by post-composition. Indeed, the universal property of the pullback tells us that the two-dashed maps in the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BA%5Ctimes_BX%7D%20%26%26%20Y%20%5C%5C%0A%09A%20%26%20X%20%5C%5C%0A%09%26%20B%0A%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D1-3%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-3%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{A\times_BX} &amp;&amp; Y \\
	A &amp; X \\
	&amp; B
	\arrow[&quot;f&quot;', from=2-1, to=3-2]
	\arrow[&quot;g&quot;, from=2-2, to=3-2]
	\arrow[&quot;h&quot;', from=1-3, to=2-1]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-1, to=2-2]
	\arrow[dashed, from=1-3, to=2-2]
	\arrow[dashed, from=1-3, to=1-1]
\end{tikzcd}
" /></p>
are equivalent, so having one immediately implies having the other. 


Thus, $f_!\dashv f^*$, so in this context $f^*$ always preserves limits since it has a left adjoint. In order to obtain a geometric morphism, however, we still need a right adjoint for $f^*$. This doesn't exist in general, but as we will now show, it will for Grothendieck topoi, since the standard fibration has right adjoints for its base-change functors if the base category is locally cartesian closed.

>[!def] Cartesian Closed
>A category $\mathcal{C}$ with finite products is said to be **cartesian closed** if for every object $C \in \mathcal{C}$, the product functor $-\times C:\mathcal{C}\to \mathcal{C}$ has a right adjoint, $(-)^C$.  
>
>$\mathcal{C}$ is said to be **locally cartesian closed** if for every $C \in \mathcal{C}_0$, $\mathcal{C}/C$ is cartesian closed.

With locally cartesian closedness we can now construct right adjoints for base-change functors.

>[!proposition] Right Adjoint to Base Change
>Let $\mathcal{C}$ be a locally cartesian closed category with pullbacks. Then the base-change functors for the standard fibration $\pi_1:\mathcal{C}^2\to \mathcal{C}$ have right adjoints.

`\begin{proof}`
Let $f:A\to B$, and let $f^*:\mathcal{C}/B\to \mathcal{C}/A$ be its base-change functor. For a right adjoint $f_*:\mathcal{C}/A\to \mathcal{C}/B$ we must have a natural correspondence between the dashed maps in the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7Bf%5E*X%7D%20%26%26%20Y%20%5C%5C%0A%20%20%20%20%09A%20%26%20X%20%26%26%20%7Bf_*Y%7D%20%5C%5C%0A%20%20%20%20%09%26%20B%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5B%22h%22'%2C%20from%3D1-3%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf_*h%7D%22%2C%20from%3D2-4%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5Bdashed%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{f^*X} &amp;&amp; Y \\
    	A &amp; X &amp;&amp; {f_*Y} \\
    	&amp; B
    	\arrow[&quot;f&quot;', from=2-1, to=3-2]
    	\arrow[&quot;g&quot;, from=2-2, to=3-2]
    	\arrow[&quot;h&quot;', from=1-3, to=2-1]
    	\arrow[from=1-1, to=2-1]
    	\arrow[from=1-1, to=2-2]
    	\arrow[dashed, from=1-1, to=1-3]
    	\arrow[&quot;{f_*h}&quot;, from=2-4, to=3-2]
    	\arrow[dashed, from=2-2, to=2-4]
    \end{tikzcd}
" /></p>
Note that products in a slice category are exactly pullbacks. Then since $\mathcal{C}/B$ is cartesian closed, the equivalence between the arrows in the diagram is exactly given by the exponential adjunction, where $f_*h:f_*Y\to B$ is exactly the exponential functor, $(-)^A$, associated with $f:A\to B$ applied to $f\circ h:Y\to B$.
`\end{proof}`

Therefore for any cartesian closed category with pullbacks, $\mathcal{C}$, and in particular any Grothendieck topoi, we have for each $f:A\to B$ in $\mathcal{C}$ a triple adjunction

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BC%7D%2FB%7D%20%26%26%20%7B%5Cmathcal%7BC%7D%2FA%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf%5E*%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_!%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%7D%22%2C%20bend%20left%20%3D%2060%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{C}/B} &amp;&amp; {\mathcal{C}/A}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f^*}&quot;, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{f_!}&quot;', bend right = 60, from=1-3, to=1-1]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{f_*}&quot;, bend left = 60, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=2]
\end{tikzcd}
" /></p>
which in the case of Grothendieck topoi gives our desired geometric morphisms associated with base-change.



#### References

[^1]: Categorical Logic and Type Theory. (n.d.). https://www.cs.ru.nl/B.Jacobs/CLT/bookinfo.html. Accessed 23 May 2024
[^2]: Shulman, M. A. (2009, January 9). Framed bicategories and monoidal fibrations. arXiv. https://doi.org/10.48550/arXiv.0706.1286
