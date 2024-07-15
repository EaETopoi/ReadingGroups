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
>
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
>A fibration $p:\mathcal{E}\to \mathcal{B}$ is an opfibration if and only if all basechange functors $f^*:p^{-1}(B)\to p^{-1}(A)$, for $f:A\to B$, have left adjoints.

`\begin{proof}`
Let $f:A\to B$ be a map in $\mathcal{B}$. Note that by the classification of cartesian lifts applied to identity fillings, we have a natural bijection between maps $Y\to X$ in $\mathcal{E}$ lying over $f$ and maps $Y\to f^*X$ in $p^{-1}(A)$. On the other hand, the dual property for opcartesian lifts gives a bijection between maps $Y\to X$ over $f$ and maps $f_!Y\to X$ in $p^{-1}(B)$. In other words, we have the natural bijection
$$p^{-1}(B)(f_!Y,X)\cong p^{-1}(B)(Y,f^*X)$$
so the existence of opcartesian lifts is equivalent to the existence of right adjoints, and vice-versa if we start with an opfibration.
`\end{proof}`

### The Standard Fibration

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


### Properties of Fibrations

We now collect a number of important properties satisfied by arbitrary (cloven) fibrations, beginning with a uniqueness result on cartesian lifts.

>[!lemma] Uniqueness of Cartesian Lifts
>Let $p:\mathcal{E}\to \mathcal{B}$ be a fibration. If $f:A\to B$ is a map in $\mathcal{B}$ and $X \in p^{-1}(B)_0$, then any two cartesian lifts $g$ and $h$ of $f$ based at $X$ are uniquely isomorphic in $p^{-1}(A) /X$.

^9bd130

`\begin{proof}`
Let $g:g^*X\to X$ and $h:h^*X\to X$ be two cartesian lifts of $f:A\to B$ based at $X$. Using the identity triangle corresponding to a degenerate triangle we obtain unique maps $\varphi:h^*X\to g^*X$ and $\psi:g^*X\to h^*X$ lying above the identity such that $h\circ \psi = g$ and $h = g\circ \varphi$. Further, uniqueness says that $\varphi = \psi^{-1}$. Thus, $g$ and $h$ are uniquely isomorphic in the slice $p^{-1}(A)/X$.
`\end{proof}`

Next, we show that cartesian lifts are preserved under composition, and so form a wide subcategory of $\mathcal{E}$, for $p:\mathcal{E}\to \mathcal{B}$ a fibration.

>[!lemma] Composition of Cartesian Lifts
>Let $p:\mathcal{E}\to \mathcal{B}$ be a fibration and let $f:A\to B,g:B\to C$ be maps in $\mathcal{B}$.  If $Z \in p^{-1}(C)_0$, and $h:g^*Z\to Z$ and $k:f^*g^*Z\to g^*Z$ are cartesian lifts of $g$ and $f$, respectively, then $h\circ k$ is a cartesian lift of $g\circ f$.

^2f75ef

`\begin{proof}`
First, consider a commuting triangle

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bp(X)%7D%20%5C%5C%0A%09A%20%26%20B%20%26%20C%0A%09%5Carrow%5B%22%5Cell%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7Bp(u)%7D%22%2C%20from%3D1-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22g%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{p(X)} \\
	A &amp; B &amp; C
	\arrow[&quot;\ell&quot;', from=1-1, to=2-1]
	\arrow[&quot;{p(u)}&quot;, from=1-1, to=2-3]
	\arrow[&quot;f&quot;', from=2-1, to=2-2]
	\arrow[&quot;g&quot;', from=2-2, to=2-3]
\end{tikzcd}
" /></p>

where $u:X\to Z$ is a map in $\mathcal{E}$. Since $h:g^*Z\to Z$ is a cartesian lift we have a unique $r:X\to g^*Z$ such that $p(r) = f\circ \ell:p(X)\to B$ and $h\circ r = u$. This gives a new diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bp(X)%7D%20%5C%5C%0A%09A%20%26%20B%20%26%26%26%20C%0A%09%5Carrow%5B%22%5Cell%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7Bp(r)%7D%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Bp(u)%7D%22%2C%20from%3D1-1%2C%20to%3D2-5%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22g%22'%2C%20from%3D2-2%2C%20to%3D2-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{p(X)} \\
	A &amp; B &amp;&amp;&amp; C
	\arrow[&quot;\ell&quot;', from=1-1, to=2-1]
	\arrow[&quot;{p(r)}&quot;, from=1-1, to=2-2]
	\arrow[&quot;{p(u)}&quot;, from=1-1, to=2-5]
	\arrow[&quot;f&quot;', from=2-1, to=2-2]
	\arrow[&quot;g&quot;', from=2-2, to=2-5]
\end{tikzcd}
" /></p>

Then, since $k:f^*g^*Z\to g^*Z$ is a cartesian lift, there exists a unique $s:X\to f^*g^*Z$ such that $p(s) = \ell$ and $k\circ s = r$. If $s':X\to f^*g^*Z$ is another map such that $p(s')=\ell$ and $h\circ k\circ s' = u$, then $p(k\circ s') = f\circ \ell$, so by uniqueness $k\circ s' = r$, and hence $s' = s$.
`\end{proof}`

An important equivalent characterization of cartesian lifts can be given. Let $p:\mathcal{E}\to \mathcal{B}$ be a functor, and let $f:B\to B'$ be a map in $\mathcal{B}$ with $B' = p(X)$ for some $X \in \mathcal{E}$. Suppose $f^*_X:f^*X\to X$ is a cartesian lift of $f$. What does this mean? We want to witness $f^*_X$ as some kind of universal map into $X$. Note that the filling problems we are interested in are those of the form 

<p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09Y%20%5C%5C%0A%20%20%20%20%09%7Bf%5E*X%7D%20%26%20X%20%5C%5C%0A%20%20%20%20%09%7Bp(Y)%7D%20%5C%5C%0A%20%20%20%20%09B%20%26%20%7BB'%7D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D4-1%2C%20to%3D4-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bp(g)%7D%22%2C%20from%3D3-1%2C%20to%3D4-2%5D%0A%20%20%20%20%09%5Carrow%5B%22h%22'%2C%20from%3D3-1%2C%20to%3D4-1%5D%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists!%5Cwidetilde%7Bh%7D%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5Bdotted%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]    	Y \\    	{f^*X} &amp; X \\    	{p(Y)} \\    	B &amp; {B'}    	\arrow[&quot;f&quot;', from=4-1, to=4-2]    	\arrow[&quot;{p(g)}&quot;, from=3-1, to=4-2]    	\arrow[&quot;h&quot;', from=3-1, to=4-1]    	\arrow[&quot;g&quot;, from=1-1, to=2-2]    	\arrow[&quot;{f^*_X}&quot;', from=2-1, to=2-2]    	\arrow[&quot;{\exists!\widetilde{h}}&quot;', dashed, from=1-1, to=2-1]    	\arrow[dotted, from=2-1, to=3-1]    \end{tikzcd}" /></p>

The existence and uniqueness of $\widetilde{h}$ says that we want a bijection between the set of morphism $\widetilde{h}:Y\to f^*X$ and those morphisms $h:p(Y)\to B$ such that $f\circ p(\widetilde{h}) = f\circ h$. Note that since $f = p(f^*_X)$, we can speak of this property independent of $f$, and so speak of **strong cartesian morphisms**, relative to $p$, in $\mathcal{E}$. Then the above reformulation is exactly the statement that a morphism $f:e\to e'$ in $\mathcal{E}$ is strong cartesian relative to $p$ if it induces an isomorphism
$$\text{Map}_\mathcal{E}(d,e)\to \text{Map}_\mathcal{E}(d,e')\times_{\text{Map}_\mathcal{B}(p(d),p(e'))}\text{Map}_\mathcal{B}(p(d),p(e))$$
given by $\varphi\mapsto (f\circ \varphi,p(\varphi))$, where the pullback on the right fits in the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ctext%7BMap%7D_%5Cmathcal%7BE%7D(d%2Ce)%7D%20%5C%5C%0A%09%26%20%7B%5Ctext%7BMap%7D_%5Cmathcal%7BE%7D(d%2Ce')%5Ctimes_%7B%5Ctext%7BMap%7D_%5Cmathcal%7BB%7D(p(d)%2Cp(e'))%7D%5Ctext%7BMap%7D_%5Cmathcal%7BB%7D(p(d)%2Cp(e))%7D%20%26%26%20%7B%5Ctext%7BMap%7D_%5Cmathcal%7BB%7D(p(d)%2Cp(e))%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%20%7B%5Ctext%7BMap%7D_%5Cmathcal%7BE%7D(d%2Ce')%7D%20%26%26%20%7B%5Ctext%7BMap%7D_%5Cmathcal%7BB%7D(p(d)%2Cp(e'))%7D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22p%22%2C%20bend%20left%20%3D%2010%2C%20from%3D1-1%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7Bf%5Ccirc-%7D%22'%2C%20bend%20right%20%3D%2010%2C%20from%3D1-1%2C%20to%3D4-2%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D4-2%5D%0A%09%5Carrow%5B%22%7Bp(f)%5Ccirc-%7D%22%2C%20from%3D2-4%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22p%22'%2C%20from%3D4-2%2C%20to%3D4-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\text{Map}_\mathcal{E}(d,e)} \\
	&amp; {\text{Map}_\mathcal{E}(d,e')\times_{\text{Map}_\mathcal{B}(p(d),p(e'))}\text{Map}_\mathcal{B}(p(d),p(e))} &amp;&amp; {\text{Map}_\mathcal{B}(p(d),p(e))} \\
	\\
	&amp; {\text{Map}_\mathcal{E}(d,e')} &amp;&amp; {\text{Map}_\mathcal{B}(p(d),p(e'))}
	\arrow[dashed, from=1-1, to=2-2]
	\arrow[&quot;p&quot;, bend left = 10, from=1-1, to=2-4]
	\arrow[&quot;{f\circ-}&quot;', bend right = 10, from=1-1, to=4-2]
	\arrow[from=2-2, to=2-4]
	\arrow[from=2-2, to=4-2]
	\arrow[&quot;{p(f)\circ-}&quot;, from=2-4, to=4-4]
	\arrow[&quot;p&quot;', from=4-2, to=4-4]
\end{tikzcd}
" /></p>

This classification is much more suitable to generalization.

## Grothendieck Construction and Pseudo-Functors

In this section we show that the data of a **cloven fibration** (i.e. a fibration $F:\mathcal{E}\to \mathcal{B}$ with a choice of cleavage) is equivalent to a pseudo-functor $\Phi_F:\mathcal{B}^{op}\to \mathsf{Cat}$ via the Grothendieck construction, where $\mathcal{B}^{op}$ is viewed as a discrete $2$-category. Let us begin by recalling the definition of a pseudo-functor between (weak) 2-categories.

>[!def] Lax Functor
>Let $\mathcal{A}$ and $\mathcal{B}$ be bicategories. A **lax functor** $F:\mathcal{A}\to \mathcal{B}$ consists of the following data:
>1. A map on one cells $F:\mathcal{A}_0\to \mathcal{B}_0$
>2. For every $A,A' \in \mathcal{A}_0$, a functor
>   $$F:\mathcal{A}(A,A')\to \mathcal{B}(FA,FA')$$
>3. For $A,A',A'' \in \mathcal{A}_0$, natural transformation $F^2:F_{A',A''}\circ_\mathcal{B}F_{A,A'}\Rightarrow F_{A,A''}(-\circ_\mathcal{A}-)$ 
>4. For $A \in \mathcal{A}_0$, a natural transformation $F^0:\text{id}_{F(X)}\Rightarrow F(\text{id}_X)$, viewed as functors $\mathbb{1}\to \mathcal{B}(FX,FX)$, which consists exactly of a $2$-cell $\text{id}_{F(X)}\to F(\text{id}_X)$ in $\mathcal{B}(FX,FX)$.
>
>such that $F$ satisfies an associativity coherence diagram, relative to the associators for $\mathcal{A}$ and $\mathcal{B}$, as well as left and right unity coherence diagrams.

>[!def] Pseudo-functor
>Let $\mathcal{A}$ and $\mathcal{B}$ be bicategories. A **pseudofunctor**, $F:\mathcal{A}\to \mathcal{B}$, is a lax functor with $F^0$ and $F^2$ invertible.

For our case, we are considering pseudofunctors $F:\mathcal{A}\to \mathcal{B}$ where $\mathcal{A}$ is discrete. This means that $F$ consists of an assignment on objects and an assignment on $1$-cells such that for $f:A\to A',g:A'\to A''$ in $\mathcal{A}$, $F(g)\circ F(f) \cong F(g\circ f)$ in $\mathcal{B}(FA,FA'')$, and $\text{id}_{FA}\cong F(\text{id}_A)$ in $\mathcal{B}(FA,FA)$, where naturality becomes the diagrams

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BF(g)%5Ccirc%20F(f)%7D%20%26%26%20%7BF(g)%5Ccirc%20F(f)%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%20%7BF(g%5Ccirc%20f)%7D%0A%09%5Carrow%5B%22%7B%5Ctext%7Bid%7D_%7BF(g)%7D%5Ccirc%20%5Ctext%7Bid%7D_%7BF(f)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7BF%5E2%7D%22'%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7BF%5E2%7D%22%2C%20from%3D1-3%2C%20to%3D3-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{F(g)\circ F(f)} &amp;&amp; {F(g)\circ F(f)} \\
	\\
	&amp; {F(g\circ f)}
	\arrow[&quot;{\text{id}_{F(g)}\circ \text{id}_{F(f)}}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{F^2}&quot;', from=1-1, to=3-2]
	\arrow[&quot;{F^2}&quot;, from=1-3, to=3-2]
\end{tikzcd}
" /></p>

If in addition $\mathcal{B}$ is a (strict) $2$-category this naturality diagram also becomes trivial, and the coherence diagrams become

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BF(h)%5Ccirc%20F(g)%5Ccirc%20F(f)%7D%20%26%26%20%7BF(h)%5Ccirc%20F(g%5Ccirc%20f)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7BF(h%5Ccirc%20g)%5Ccirc%20F(f)%7D%20%26%26%20%7BF(h%5Ccirc%20g%5Ccirc%20f)%7D%0A%09%5Carrow%5B%22%7B1_%7BFh%7D*F%5E2%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7BF%5E2*1_%7BFf%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7BF%5E2%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF%5E2%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{F(h)\circ F(g)\circ F(f)} &amp;&amp; {F(h)\circ F(g\circ f)} \\
	\\
	{F(h\circ g)\circ F(f)} &amp;&amp; {F(h\circ g\circ f)}
	\arrow[&quot;{1_{Fh}*F^2}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{F^2*1_{Ff}}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{F^2}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{F^2}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

and

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BF1_Y%5Ccirc%20Ff%7D%20%26%26%20Ff%20%26%26%20%7BFf%5Ccirc%20F1_X%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%26%20Ff%0A%09%5Carrow%5B%22%7BF%5E2%7D%22'%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF%5E0*1_%7BFf%7D%7D%22'%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%7B1_%7BFf%7D*F%5E0%7D%22%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7BF%5E2%7D%22%2C%20from%3D1-5%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{F1_Y\circ Ff} &amp;&amp; Ff &amp;&amp; {Ff\circ F1_X} \\
	\\
	&amp;&amp; Ff
	\arrow[&quot;{F^2}&quot;', from=1-1, to=3-3]
	\arrow[&quot;{F^0*1_{Ff}}&quot;', from=1-3, to=1-1]
	\arrow[&quot;{1_{Ff}*F^0}&quot;, from=1-3, to=1-5]
	\arrow[Rightarrow, no head, from=1-3, to=3-3]
	\arrow[&quot;{F^2}&quot;, from=1-5, to=3-3]
\end{tikzcd}
" /></p>

Therefore, a pseudofunctor of the form $F:\mathcal{B}\to \mathsf{Cat}$, for instance, where $\mathcal{B}$ is a $1$-category viewed as a discrete $2$-category, is an assignment of the objects in $\mathcal{B}$ to categories and the morphisms to functors such that $F(g)\circ F(f)\cong F(g\circ f)$ for any composable maps $g$ and $f$ in $\mathcal{B}$, with this isomorphism satisfying the specified coherence diagrams.


Recall that we have already seen in [[Basic Fibered Categories#^9803ab]] that if $p:\mathcal{E}\to \mathcal{B}$ is a cloven fibration, then we have an assignment $X \in \mathcal{B}\mapsto p^{-1}(X)$ and $f:X\to Y$ in $\mathcal{B}$ going to a functor $f^*:p^{-1}(Y)\to p^{-1}(X)$. Thus, we almost have all we need to show that we get a pseudo-functor $p^*:\mathcal{B}^{op}\to \mathsf{Cat}$. It remains only to show that for $f:X\to Y, g:Y\to Z$ in $\mathcal{B}$, $f^*g^*\cong (gf)^*$, naturally.

>[!lemma] Coherent Functoriality Isomorphism
>Let $p:\mathcal{E}\to \mathcal{B}$ be a cloven fibration. Let $f:X\to Y,g:Y\to Z$ be maps in $\mathcal{B}$. Then we have a natural isomorphism $$f^*g^* \cong (gf)^*$$

^280c14

`\begin{proof}`
We shall define the natural isomorphism using a uniqueness argument from cartesian lifts before showing naturality. Note $f^*g^*,(gf)^*:p^{-1}(Z)\to p^{-1}(X)$. If $C \in p^{-1}(Z)$, then by [[Basic Fibered Categories#^2f75ef]] we have that $f^*g^*C\to g^*C\to C$ and $(gf)^*C\to C$ are both cartesian lifts of $gf:X\to Z$ in $\mathcal{B}$. Thus, by [[Basic Fibered Categories#^9bd130]] we have a unique isomorphism $\varphi_C:f^*g^*C\to (gf)^*C$ in the slice category such that $p(\varphi_C) = \text{id}_X$. This $\varphi:f^*g^*\Rightarrow (gf)^*$ will be our natural transformation. It remains to show naturality.

For naturality let $k:C'\to C$ in $p^{-1}(Z)$. Then we can consider the paired lifting diagrams

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bf%5E*g%5E*C'%7D%20%26%20%7Bg%5E*C'%7D%20%26%20%7BC'%7D%20%5C%5C%0A%09%26%20%7Bf%5E*g%5E*C%7D%20%26%20%7Bg%5E*C%7D%20%26%20C%20%26%20X%20%26%20Y%20%26%20Z%20%5C%5C%0A%09%7B(gf)%5E*C'%7D%20%26%26%20%7BC'%7D%20%5C%5C%0A%09%26%20%7B(gf)%5E*C%7D%20%26%26%20C%20%26%26%26%20X%20%26%20Y%20%26%20Z%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7Bf%5E*g%5E*k%7D%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi_%7BC'%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bg%5E*k%7D%22'%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22k%22%2C%20from%3D1-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5BRightarrow%2C%20dashed%2C%20no%20head%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi_C%7D%22%7Bpos%3D0.3%7D%2C%20from%3D2-2%2C%20to%3D4-2%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-4%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D2-5%2C%20to%3D4-7%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D2-6%2C%20to%3D2-7%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-6%2C%20to%3D4-8%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-7%2C%20to%3D4-9%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B(gf)%5E*k%7D%22'%2C%20from%3D3-1%2C%20to%3D4-2%5D%0A%09%5Carrow%5B%22k%22%2C%20from%3D3-3%2C%20to%3D4-4%5D%0A%09%5Carrow%5Bfrom%3D4-2%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D4-7%2C%20to%3D4-8%5D%0A%09%5Carrow%5B%22g%22'%2C%20from%3D4-8%2C%20to%3D4-9%5D%0A%09%5Carrow%5Bshorten%20%3C%3D13pt%2C%20shorten%20%3E%3D13pt%2C%20squiggly%2C%20tail%20reversed%2C%20from%3D0%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{f^*g^*C'} &amp; {g^*C'} &amp; {C'} \\
	&amp; {f^*g^*C} &amp; {g^*C} &amp; C &amp; X &amp; Y &amp; Z \\
	{(gf)^*C'} &amp;&amp; {C'} \\
	&amp; {(gf)^*C} &amp;&amp; C &amp;&amp;&amp; X &amp; Y &amp; Z
	\arrow[from=1-1, to=1-2]
	\arrow[&quot;{f^*g^*k}&quot;', from=1-1, to=2-2]
	\arrow[&quot;{\varphi_{C'}}&quot;', from=1-1, to=3-1]
	\arrow[from=1-2, to=1-3]
	\arrow[&quot;{g^*k}&quot;', from=1-2, to=2-3]
	\arrow[&quot;k&quot;, from=1-3, to=2-4]
	\arrow[Rightarrow, dashed, no head, from=1-3, to=3-3]
	\arrow[from=2-2, to=2-3]
	\arrow[&quot;{\varphi_C}&quot;{pos=0.3}, from=2-2, to=4-2]
	\arrow[from=2-3, to=2-4]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=2-4, to=4-4]
	\arrow[&quot;f&quot;, from=2-5, to=2-6]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=2-5, to=4-7]
	\arrow[&quot;g&quot;, from=2-6, to=2-7]
	\arrow[Rightarrow, no head, from=2-6, to=4-8]
	\arrow[Rightarrow, no head, from=2-7, to=4-9]
	\arrow[dashed, from=3-1, to=3-3]
	\arrow[&quot;{(gf)^*k}&quot;', from=3-1, to=4-2]
	\arrow[&quot;k&quot;, from=3-3, to=4-4]
	\arrow[from=4-2, to=4-4]
	\arrow[&quot;f&quot;', from=4-7, to=4-8]
	\arrow[&quot;g&quot;', from=4-8, to=4-9]
	\arrow[shorten &lt;=13pt, shorten &gt;=13pt, squiggly, tail reversed, from=0, to=1]
\end{tikzcd}
" /></p>

We show that $\varphi_C\circ f^*g^*k = (gf)^*k\circ \varphi_{C'}$ by showing that they are the unique lift for the same diagram. Let $\ell_{g,C}:g^*C\to C$ denote the cartesian lift above $g$ in the above diagram, and similarly for the other lifts. Then we have that $\varphi_C\circ f^*g^*k$ and  $(gf)^*k\circ \varphi_{C'}$ lie above the identity, and
$$\ell_{gf,C}\circ \varphi_C\circ f^*g^*k = \ell_{g,C}\circ \ell_{f,g^*C}\circ f^*g^*k = k\circ \ell_{g,C'}\circ \ell_{f,g^*C'}$$
and
$$\ell_{gf,C}\circ (gf)^*k\circ \varphi_{C'} = k\circ \ell_{gf,C'}\circ \varphi_{C'}= k \circ \ell_{g,C'}\circ \ell_{f,g^*C'}$$
so both maps are the desired unique lift of the identity making the appropriate diagrams commute. This completes the proof
`\end{proof}`

With [[Basic Fibered Categories#^280c14]] in hand, it remains to show the unity and associator coherency diagrams. We show the left unity diagram and the associator diagram. Let $f:X\to Y,g:Y\to Z$ and $h:Z\to W$ be maps in $\mathcal{B}$. First, for the left unity diagram, let $\varphi_C:1_Y^*f^*C\to f^*C$ be the isomorphism given in [[Basic Fibered Categories#^9bd130]] for $C$ lying above $Y$, and similarly, let $\psi_{f^*C}:f^*C\to 1_Y^*f^*C$ be the isomorphism, also coming from [[Basic Fibered Categories#^9bd130]] applied now to the lifting of identities. Consider the lifting diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20%7B1_Y%5E*f%5E*C%7D%20%26%20%7Bf%5E*C%7D%20%26%20C%20%26%20X%20%26%20Y%20%5C%5C%0A%09%7Bf%5E*C%7D%20%26%26%20C%20%5C%5C%0A%09%26%20%7Bf%5E*C%7D%20%26%26%20C%20%26%26%26%20X%20%26%20Y%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi_C%7D%22%7Bpos%3D0.3%7D%2C%20from%3D1-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-5%2C%20to%3D1-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D3-7%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-6%2C%20to%3D3-8%5D%0A%09%5Carrow%5B%22%7B%5Cpsi_%7Bf%5E*C%7D%7D%22%2C%20dashed%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7B1_%7Bf%5E*C%7D%7D%22'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7B1_C%7D%22%2C%20from%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%7B1_C%7D%22%2C%20from%3D2-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bfrom%3D3-2%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D3-7%2C%20to%3D3-8%5D%0A%09%5Carrow%5Bshorten%20%3C%3D13pt%2C%20shorten%20%3E%3D13pt%2C%20squiggly%2C%20tail%20reversed%2C%20from%3D0%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; {1_Y^*f^*C} &amp; {f^*C} &amp; C &amp; X &amp; Y \\
	{f^*C} &amp;&amp; C \\
	&amp; {f^*C} &amp;&amp; C &amp;&amp;&amp; X &amp; Y
	\arrow[from=1-2, to=1-3]
	\arrow[&quot;{\varphi_C}&quot;{pos=0.3}, from=1-2, to=3-2]
	\arrow[from=1-3, to=1-4]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=3-4]
	\arrow[&quot;f&quot;, from=1-5, to=1-6]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-5, to=3-7]
	\arrow[Rightarrow, no head, from=1-6, to=3-8]
	\arrow[&quot;{\psi_{f^*C}}&quot;, dashed, from=2-1, to=1-2]
	\arrow[dashed, from=2-1, to=2-3]
	\arrow[&quot;{1_{f^*C}}&quot;', from=2-1, to=3-2]
	\arrow[&quot;{1_C}&quot;, from=2-3, to=1-4]
	\arrow[&quot;{1_C}&quot;, from=2-3, to=3-4]
	\arrow[from=3-2, to=3-4]
	\arrow[&quot;f&quot;', from=3-7, to=3-8]
	\arrow[shorten &lt;=13pt, shorten &gt;=13pt, squiggly, tail reversed, from=0, to=1]
\end{tikzcd}
" /></p>

where we have used that fact that $f^*$ is functorial, from [[Basic Fibered Categories#^9803ab]], to write $f^*1_C = 1_{f^*C}$. To show the diagram commutes it suffices to compute the following:
$$\ell_{f,C}\circ \varphi_C\circ \psi_{f^*C} = \ell_{f,C}\circ \ell_{1_Y,f^*C}\circ \psi_{f^*C} = \ell_{f,C}$$
and so by uniqueness $\varphi_c \circ \psi_{f^*C} = 1_{f^*C}$. Next, for the associator diagram adding superscripts on the $\varphi$'s to indicate the isomorphisms, we consider the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bf%5E*g%5E*h%5E*C%7D%20%26%20%7Bg%5E*h%5E*C%7D%20%26%20%7Bh%5E*C%7D%20%26%20C%20%5C%5C%0A%09%26%20%7B(gf)%5E*h%5E*C%7D%20%26%20%7Bh%5E*C%7D%20%26%26%20C%20%5C%5C%0A%09%7Bf%5E*(hg)%5E*C%7D%20%26%26%20%7B(hg)%5E*C%7D%20%26%20C%20%5C%5C%0A%09%26%20%7B(hgf)%5E*C%7D%20%26%26%26%20C%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi%5E%7Bf%2Cg%7D_%7Bh%5E*C%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Bf%5E*%5Cvarphi%5E%7Bg%2Ch%7D_%7BC%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi%5E%7Bg%2Ch%7D_C%7D%22%2C%20dashed%2C%20from%3D1-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%09%5Carrow%5BRightarrow%2C%20dashed%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi%5E%7Bgf%2Ch%7D_C%7D%22%7Bpos%3D0.3%7D%2C%20from%3D2-2%2C%20to%3D4-2%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D2-5%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-5%2C%20to%3D4-5%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi%5E%7Bf%2Chg%7D_C%7D%22'%2C%20from%3D3-1%2C%20to%3D4-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D3-4%2C%20to%3D4-5%5D%0A%09%5Carrow%5Bfrom%3D4-2%2C%20to%3D4-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{f^*g^*h^*C} &amp; {g^*h^*C} &amp; {h^*C} &amp; C \\
	&amp; {(gf)^*h^*C} &amp; {h^*C} &amp;&amp; C \\
	{f^*(hg)^*C} &amp;&amp; {(hg)^*C} &amp; C \\
	&amp; {(hgf)^*C} &amp;&amp;&amp; C
	\arrow[from=1-1, to=1-2]
	\arrow[&quot;{\varphi^{f,g}_{h^*C}}&quot;', from=1-1, to=2-2]
	\arrow[&quot;{f^*\varphi^{g,h}_{C}}&quot;', from=1-1, to=3-1]
	\arrow[from=1-2, to=1-3]
	\arrow[&quot;{\varphi^{g,h}_C}&quot;, dashed, from=1-2, to=3-3]
	\arrow[from=1-3, to=1-4]
	\arrow[Rightarrow, no head, from=1-3, to=2-3]
	\arrow[Rightarrow, no head, from=1-4, to=2-5]
	\arrow[Rightarrow, dashed, no head, from=1-4, to=3-4]
	\arrow[from=2-2, to=2-3]
	\arrow[&quot;{\varphi^{gf,h}_C}&quot;{pos=0.3}, from=2-2, to=4-2]
	\arrow[from=2-3, to=2-5]
	\arrow[Rightarrow, no head, from=2-5, to=4-5]
	\arrow[dashed, from=3-1, to=3-3]
	\arrow[&quot;{\varphi^{f,hg}_C}&quot;', from=3-1, to=4-2]
	\arrow[dashed, from=3-3, to=3-4]
	\arrow[Rightarrow, no head, from=3-4, to=4-5]
	\arrow[from=4-2, to=4-5]
\end{tikzcd}
" /></p>

where our goal is for the left most face to commute. However, this is equivalent, by the universal lifting property of cartesian lifts, to showing that the maps to the bottom right $C$ are equal in representing a filling. To do this we compute
$$\ell_{hgf,C}\circ \varphi_C^{gf,h}\circ \varphi^{f,g}_{h^*C} = \ell_{h,C}\circ \ell_{gf,h^*C}\circ \varphi_{h^*C}^{f,g} = \ell_{h,c}\circ \ell_{g,h^*C}\circ \ell_{f,g^*h^*C}$$
and
$$\ell_{hgf,C}\circ \varphi_C^{f,hg}\circ f^*\varphi_C^{g,h} = \ell_{hg,C}\circ \ell_{f,hg^*C}\circ f^*\varphi_C^{g,h} = \ell_{hg,C}\circ \varphi_C^{g,h}\circ \ell_{f,g^*h^*C} = \ell_{h,c}\circ \ell_{g,h^*C}\circ \ell_{f,g^*h^*C}$$
so both give our needed lift. 

Thus, the associator diagram holds, and we find a pseudo-functor $p^*:\mathcal{B}^{op}\to \mathsf{Cat}$. In order to proceed in the opposite direction let us recall the procedure for the Grothendieck construction.

From the philosophy of universal bundles we represent the Grothendieck construction as a pullback of the universal functor $\mathsf{Cat}_{*,\ell}\to \mathsf{Cat}$. First, $\mathsf{Cat}_{*,\ell}$ is the lax slice bicategory of $\mathsf{Cat}$ under the terminal category. Let us recall the notion of a lax slice of a bicategory.

>[!def] Lax-Slice of a Bicategory
>Let $\mathcal{B}$ be a bicategory and $B \in \mathcal{B}$ an object. The **lax slice $2$-category** $B//\mathcal{B}$ is the bicategory with
>1. $1$-morphisms $a:B\to A$ as objects in $\mathcal{B}$
>2. $1$-cells between objects $a:B\to A$ and $c:B\to C$ given by a pair of a 1-morphism $f:A\to C$ and a $2$-cell $\phi:fa\Rightarrow c$ 
>3. $2$-cells from $(f,\phi)$ to $(g,\psi)$ given by two cells $\xi:f\Rightarrow g$ such that $\phi = \psi\cdot (\xi a)$.
>
>Composition is given as in $\mathcal{B}$ for $1$-cells and $2$-cells. If $\mathcal{B}$ is strict, so is the slice.

From this definition we see that $\mathsf{Cat}_{*,\ell}$ is the category with objects pairs $(\mathcal{C},C)$ of a category and a specified object, $1$-cells $(F,f):(\mathcal{C},C)\to (\mathcal{D},D)$ pairs of functors $F:\mathcal{C}\to \mathcal{D}$ and morphisms $f:FC\to D$, and $2$-cells $\alpha:(F,f)\Rightarrow (G,g)$ natural transformations $\alpha:F\Rightarrow G$ such that $f = g\circ \alpha_C:F(C)\to G(C)\to D$. We have a natural forgetful functor $\mathsf{Cat}_{*,\ell}\to \mathsf{Cat}$, which we call the universal bundle. Then if $F:\mathcal{C}\to \mathsf{Cat}$ is a pseudofunctor, its Grothendieck construction is the category given by the (strict) $2$-pullback of $F$ along the universal bundle. Explicitly, $\int_\mathcal{C}F$ is the category with
1. $0$-cells are pairs $(C,a)$ for $C \in \mathcal{C}$ and $a \in F(C)$
2. $1$-cells are pairs $(f,\phi):(C,a)\to (D,b)$, with $f:C\to D$ and $\phi:F(f)(a)\to b$ 
3. $2$-cells are identities
To see that this is a **strict $2$-pullback**, suppose we have another 2-category $\mathcal{D}$ with projections $\mathcal{D}\to \mathcal{C}$ and $\mathcal{D}\to\mathsf{Cat}_{*,\ell}$ making the square commute. Then the above data tells us how to specify the unique map $\mathcal{D}\to \int_\mathcal{C}F$. The composition of $1$-cells in $\int_\mathcal{C}F$ is given on $(f,\phi):(A,a)\to (B,b)$ and $(g,\psi):(B,b)\to (C,c)$ by
$$(gf,\psi\circ F(g)(\phi)\circ (F^2)^{-1}):(A,a)\to (C,c),\;\psi\circ F(g)(\phi)\circ (F^2)^{-1}: F(gf)(a)\to F(g)F(f)(a)\to F(g)(b)\to c$$
The identity $1$-cells in $\int_\mathcal{C}F$ are the pairs $(\text{id}_C,(\Phi^0_c)^{-1}):(C,c)\to (C,c)$. Then to say that this is associative and unital it suffices to show that for $(f,\phi):(A,a)\to (B,b),(g,\psi):(B,b)\to (C,c)$, and $(h,\rho):(C,c)\to (D,d)$, we have 
$$\phi\circ F(f)((\Phi^0)_a^{-1})\circ (F^2)^{-1}_{\text{id}_A,f} = \phi$$
by the right unity axiom for a pseudofunctor, and
$$(\Phi^0)_b^{-1}\circ F(\text{id}_B)(\phi)\circ (F^2)^{-1}_{f,\text{id}_B} = \phi\circ (\Phi^0)^{-1}_{F(f)(a)}\circ (F^2)^{-1}_{f,\text{id}_B} = \phi$$
using naturality and the left unity axiom. For associativity, denoting the composition by $\odot$, observe that
$$
\begin{align}
(\rho\odot \psi) \odot \phi &= (\rho\circ F(h)(\psi)\circ (F^2)^{-1}_{g,h})\odot \phi \\ 
&= (\rho\circ F(h)(\psi)\circ (F^2)^{-1}_{g,h})\circ F(hg)(\phi)\circ (F^2)^{-1}_{f,hg}  \\
&= \rho\circ F(h)(\psi)\circ F(h)F(g)(\phi)\circ (F^2)^{-1}_{g,h}\circ (F^2)^{-1}_{f,hg}  \\
&= \rho\circ F(h)(\psi)\circ F(h)F(g)(\phi)\circ (F^2)^{-1}_{g,h}\circ (F^2)^{-1}_{gf,h}  \\
&=\rho\circ F(h)(\psi\odot\phi)\circ (F^2)^{-1}_{gf,h}  \\
&= \rho \odot (\psi \odot \phi)
\end{align}
$$
using the associativity coherency diagram for the pseudofunctor as well as naturality.

In the case $F:\mathcal{C}^{op}\to \mathsf{Cat}$, we instead pullback $\mathcal{C}\to \mathsf{Cat}^{op}$ along the universal $\mathsf{Cat}$-cobundle, $(\mathsf{Cat}_{*,c})^{op}\to \mathsf{Cat}^{op}$, where $\mathsf{Cat}_{*,c}$ is the **co-lax $2$-slice category**. Now, I claim that for any such pseudofunctor, the resulting projection from the Grothendieck construction is a fibration.

>[!proposition] Grothendieck Construction Gives Fibrations
>Let $F:\mathcal{C}^{op}\to \mathsf{Cat}$ be a pseudofunctor. Then $\pi_0:\int_\mathcal{C}F\to \mathcal{C}$ is a fibration.

^79c208

`\begin{proof}`
Let $f:A\to B$ be a map in $\mathcal{C}$, and let $(B,b) \in \int_\mathcal{C}F$, so $b \in F(B)$. Now, let $(g,\phi):(C,c)\to (B,b)$ be a map in $\int_\mathcal{C}F$, so $g:C\to B$ and $\phi:c\to F(g)(b)$. Finally, let $h:C\to A$ such that $f\circ h = g$. Now, we want to construct a $a \in F(A)$ and $\rho:a\to F(f)(b)$ such that there is a unique $\psi:c\to F(h)(a)$ in $F(C)$ for which $F^2\circ F(h)(\rho)\circ \psi = \phi$. 

Take $a := F(f)(b)$ and $\rho = \text{id}_a$. Then we need only show there is a unique $\psi$ such that $F^2\circ \psi = \phi$. But $F$ is a pseudo-functor, so this just is $\psi = (F^2)^{-1}\circ \phi$.
`\end{proof}`

Note that in the proof of [[Basic Fibered Categories#^79c208]] we constructed an explicit cartesian lift. This implies that a pseudo-functor doesn't just induce a fibration, it induces a naturally cloven fibration. A similar result to [[Basic Fibered Categories#^79c208]] is that the pullback of a fibration along any functor is again a fibration.

>[!proposition] Base-Change of Fibrations
>Let $p:\mathcal{E}\to \mathcal{B}$ be a fibration and let $F:\mathcal{A}\to \mathcal{B}$ be any other functor. Then $\pi_1:\mathcal{E}\times_\mathcal{B}\mathcal{A}\to \mathcal{A}$ is a fibration.

`\begin{proof}`
First, we have a model of the pullback $\mathcal{E}\times_\mathcal{B}\mathcal{A}$ in $\mathsf{Cat}$ given by the subcategory of $\mathcal{E}\times \mathcal{A}$ consisting of pairs $(e,a)$ with $p(e) = F(a)$ as well as maps $(f,g):(e,a)\to (e',a')$ such that $F(f) = p(g)$.

Now, let $f:a\to b$ be a map in $\mathcal{A}$, with lift of the codomain $(e,b) \in \mathcal{E}\times_\mathcal{B}\mathcal{A}$. Note $F(f):F(a)\to F(b)$ is a map in $\mathcal{B}$ with a codomain lift $e$. Since $p$ is a fibration we have a cartesian lift $\rho:F(f)^*e\to e$ lying above $F(f)$. Now, let $(g,h):(x,c)\to (e,b)$ be a map in the pullback, and suppose $k:c\to a$ in $\mathcal{A}$ such that $f\circ k = h$.  Then we have that $F(f)\circ F(k) = F(h)$, where $F(h) = p(g)$ is the image of a map under $p$. Since $\rho$ is a cartesian lift of $F(f)$, we have a unique $\alpha:x\to F(f)^*e$ lying above $F(k)$ such that $\rho\circ \alpha = g$. It follows that $(\alpha,k):(x,c)\to (F(f)^*e,a)$ is a map in the pullback making our desired diagram commute. Further, since $\alpha$ is unique and fully determines the map, the pair $(\alpha,k)$ is unique.
`\end{proof}`
We now wish to show that this procedure of grothendieck constructions and basechange pseudofunctors gives a suitable kind of equivalence between a category of pseudo-functors and a category of fibrations.

>[!lemma] Equivalence of Fibration and Grothendieck Construction of Fiber Pseudofunctor
>Let $p:\mathcal{E}\to \mathcal{B}$ be a cloven fibration, and let $\Phi_p:\mathcal{B}^{op}\to \mathsf{Cat}$ be the associated pseudofunctor for fibers. Then there is a unique isomorphism of categories $\int_\mathcal{B}\Phi_p\cong \mathcal{E}$ over $\mathcal{B}$ preserving cleavages and acting as identities on fibers.

^50f2b1

`\begin{proof}`
Define a functor $\alpha:\int_\mathcal{B}\Phi_p\to \mathcal{E}$ by sending a pair $(B,b)$ of an object $B \in \mathcal{B}$ and an element $b \in \Phi_p(b) = p^{-1}(b)$, to $b$. Send a map $(f,\phi):(B,b)\to (C,c)$, where $f:B\to C$ is in $\mathcal{B}$ and $\phi:b\to \Phi_p(f)(c)$, or $\phi:b\to f^*c$, to $\ell_{f,c}\circ \phi$, where $\ell_{f,c}:f^*c\to c$ is the cartesian lift over $f:B\to C$ in the cleavage of $p$. Note that if $(1_B,\varphi_{b}^{1_b}):(B,b)\to (B,b)$ is the identity map, with $\varphi_b^{1_b}:b\to 1_b^*b$ being the unique isomorphism over the identity such that $\ell_{1_b,b}\circ \varphi_b^{1_b} = 1_b$. Thus, $\alpha$ sends identities to identities.

If $(f,\phi):(A,a)\to (B,b)$ and $(g,\psi):(B,b)\to (C,c)$ are maps, whose composite is $(g\circ f,\varphi_c^{f,g}\circ f^*\psi\circ \phi):(A,a)\to (C,c)$ where $\varphi_c^{f,g}\circ f^*\psi\circ \phi:a\to f^*b\to f^*g^*c\to (gf)^*c$. Then observe that
$$\ell_{gf,c}\circ \varphi_c^{f,g}\circ f^*\psi\circ \phi = \ell_{g,c}\circ \ell_{f,g^*c}\circ f^*\psi\circ \phi = (\ell_{g,c}\circ \psi)\circ(\ell_{f,b}\circ \phi)$$
where the first equality uses the construction of the isomorphism $\varphi_{c}^{f,g}$, and the second uses the action of $f^*$ on arrows, all of which are surmised from the commuting diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09a%20%5C%5C%0A%09%26%20%7Bf%5E*b%7D%20%26%26%20b%20%5C%5C%0A%09%26%26%20%7Bf%5E*g%5E*c%7D%20%26%26%20%7Bg%5E*c%7D%20%26%26%20c%20%5C%5C%0A%09%5C%5C%0A%09%26%26%20%7B(gf)%5E*c%7D%20%26%26%26%26%20c%0A%09%5Carrow%5B%22%5Cphi%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bf%2Cb%7D%7D%22%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7Bf%5E*%5Cpsi%7D%22'%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Cpsi%22%2C%20from%3D2-4%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bf%2Cg%5E*c%7D%7D%22%2C%20from%3D3-3%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi_c%5E%7Bf%2Cg%7D%7D%22'%2C%20from%3D3-3%2C%20to%3D5-3%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bg%2Cc%7D%7D%22%2C%20from%3D3-5%2C%20to%3D3-7%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D3-7%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bgf%2Cc%7D%7D%22'%2C%20from%3D5-3%2C%20to%3D5-7%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	a \\
	&amp; {f^*b} &amp;&amp; b \\
	&amp;&amp; {f^*g^*c} &amp;&amp; {g^*c} &amp;&amp; c \\
	\\
	&amp;&amp; {(gf)^*c} &amp;&amp;&amp;&amp; c
	\arrow[&quot;\phi&quot;', from=1-1, to=2-2]
	\arrow[&quot;{\ell_{f,b}}&quot;, from=2-2, to=2-4]
	\arrow[&quot;{f^*\psi}&quot;', from=2-2, to=3-3]
	\arrow[&quot;\psi&quot;, from=2-4, to=3-5]
	\arrow[&quot;{\ell_{f,g^*c}}&quot;, from=3-3, to=3-5]
	\arrow[&quot;{\varphi_c^{f,g}}&quot;', from=3-3, to=5-3]
	\arrow[&quot;{\ell_{g,c}}&quot;, from=3-5, to=3-7]
	\arrow[Rightarrow, no head, from=3-7, to=5-7]
	\arrow[&quot;{\ell_{gf,c}}&quot;', from=5-3, to=5-7]
\end{tikzcd}
" /></p>

Now, we define a functor $\beta:\mathcal{E}\to \int_\mathcal{B}\Phi_p$ by sending an object $e \in \mathcal{E}$ to the pair $(p(e),e)$, and sending a morphism $f:e\to e'$ to the pair $(p(f),\phi_f):(p(e),e)\to (p(e'),e')$ where $\phi_f:e\to p(f)^*e'$ is the unique filling in the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09e%20%26%26%20%7Be'%7D%20%5C%5C%0A%09%26%20%7Bp(f)%5E*e'%7D%20%26%26%20%7Be'%7D%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B!%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bp(f)%2Ce'%7D%7D%22'%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	e &amp;&amp; {e'} \\
	&amp; {p(f)^*e'} &amp;&amp; {e'}
	\arrow[&quot;f&quot;, from=1-1, to=1-3]
	\arrow[&quot;{!}&quot;', dashed, from=1-1, to=2-2]
	\arrow[Rightarrow, no head, from=1-3, to=2-4]
	\arrow[&quot;{\ell_{p(f),e'}}&quot;', from=2-2, to=2-4]
\end{tikzcd}
" /></p>

lying over $\text{id}_{p(e)}:p(e)\to p(e)$. Note that if $f$ is the identity, $\text{id}_e:e\to e$, then the filling is exactly the isomorphism $\varphi_{e}^{1_{p(e)}}:e\to 1_{p(e)}^*e$, which means the pair $(1_{p(e)},\varphi_e^{1_{p(e)}})$ is exactly the appropriate identity in the Grothendieck construction.

Now, suppose $f:e\to e'$ and $g:e'\to e''$ are morphisms in $\mathcal{E}$. Then $gf$ is sent to $(p(gf),\phi_{gf})$ for $\phi_{gf}:e\to p(gf)^*e''$ and on the other hand
$$(p(g),\phi_g)\circ (p(f),\phi_f) = (p(g)p(f),\varphi_{e''}^{p(f),p(g)}\circ f^*\phi_g\circ \phi_f)$$
Thus, to show functoriality it remains to show that $\varphi_{e''}^{p(f),p(g)}\circ f^*\phi_g\circ \phi_f$ is our desired lift over the identity. For this we can use the commutative diagram
 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09e%20%26%26%20%7Be'%7D%20%5C%5C%0A%09%26%20%7Bp(f)%5E*e'%7D%20%26%26%20%7Be'%7D%20%26%26%20%7Be''%7D%20%5C%5C%0A%09%26%26%20%7Bp(f)%5E*p(g)%5E*e''%7D%20%26%26%20%7Bp(g)%5E*e''%7D%20%26%26%20%7Be''%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%26%20%7Bp(gf)%5E*e''%7D%20%26%26%26%26%20%7Be''%7D%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cphi_f%7D%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bp(f)%2Ce'%7D%7D%22%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7Bf%5E*%5Cphi_g%7D%22'%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D2-4%2C%20to%3D2-6%5D%0A%09%5Carrow%5B%22%7B%5Cphi_g%7D%22%2C%20from%3D2-4%2C%20to%3D3-5%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-6%2C%20to%3D3-7%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bp(f)%2Cp(g)%5E*e''%7D%7D%22%2C%20from%3D3-3%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22%7B%5Cvarphi_%7Be''%7D%5E%7Bp(f)%2Cp(g)%7D%7D%22'%2C%20from%3D3-3%2C%20to%3D5-3%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bp(g)%2Ce''%7D%7D%22%2C%20from%3D3-5%2C%20to%3D3-7%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D3-7%2C%20to%3D5-7%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bp(gf)%2Ce''%7D%7D%22'%2C%20from%3D5-3%2C%20to%3D5-7%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	e &amp;&amp; {e'} \\
	&amp; {p(f)^*e'} &amp;&amp; {e'} &amp;&amp; {e''} \\
	&amp;&amp; {p(f)^*p(g)^*e''} &amp;&amp; {p(g)^*e''} &amp;&amp; {e''} \\
	\\
	&amp;&amp; {p(gf)^*e''} &amp;&amp;&amp;&amp; {e''}
	\arrow[&quot;f&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\phi_f}&quot;', from=1-1, to=2-2]
	\arrow[Rightarrow, no head, from=1-3, to=2-4]
	\arrow[&quot;{\ell_{p(f),e'}}&quot;, from=2-2, to=2-4]
	\arrow[&quot;{f^*\phi_g}&quot;', from=2-2, to=3-3]
	\arrow[&quot;g&quot;, from=2-4, to=2-6]
	\arrow[&quot;{\phi_g}&quot;, from=2-4, to=3-5]
	\arrow[Rightarrow, no head, from=2-6, to=3-7]
	\arrow[&quot;{\ell_{p(f),p(g)^*e''}}&quot;, from=3-3, to=3-5]
	\arrow[&quot;{\varphi_{e''}^{p(f),p(g)}}&quot;', from=3-3, to=5-3]
	\arrow[&quot;{\ell_{p(g),e''}}&quot;, from=3-5, to=3-7]
	\arrow[Rightarrow, no head, from=3-7, to=5-7]
	\arrow[&quot;{\ell_{p(gf),e''}}&quot;', from=5-3, to=5-7]
\end{tikzcd}
" /></p>

to compute
$$\ell_{p(gf),e''}\circ \varphi_{e''}^{p(f),p(g)}\circ f^*\phi_g\circ \phi_f = g\circ f$$
as desired. Thus, $\beta$ is functorial.

Observe that $\alpha\circ \beta(e) = \alpha((p(e),e)) = e$, and $\alpha\circ \beta(f) = \alpha((p(f),\phi_f)) = \ell_{p(f),e'}\circ \phi_f = f$, so $\alpha\circ \beta = \text{id}_\mathcal{E}$. On the other hand, $\beta \circ \alpha(B,b) = \beta(b) = (p(b),b) = (B,b)$, and for $(f,\phi):(B,b)\to (C,c)$, with $\phi:b\to f^*c$, $\beta\circ \alpha(f,\phi)=\beta(\ell_{f,c}\circ \phi)$. Note $\phi$ lives in $p^{-1}(B)$, so $p(\phi) = \text{id}_B$, and hence $\beta(\ell_{f,c}\circ \phi)$ is the unique filling of the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09b%20%26%20%7Bf%5E*c%7D%20%26%20c%20%5C%5C%0A%09%26%20%7Bf%5E*c%7D%20%26%26%20c%0A%09%5Carrow%5B%22%5Cphi%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cphi%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bf%2Cc%7D%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7B%5Cell_%7Bf%2Cc%7D%7D%22'%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	b &amp; {f^*c} &amp; c \\
	&amp; {f^*c} &amp;&amp; c
	\arrow[&quot;\phi&quot;, from=1-1, to=1-2]
	\arrow[&quot;\phi&quot;', from=1-1, to=2-2]
	\arrow[&quot;{\ell_{f,c}}&quot;, from=1-2, to=1-3]
	\arrow[Rightarrow, no head, from=1-3, to=2-4]
	\arrow[&quot;{\ell_{f,c}}&quot;', from=2-2, to=2-4]
\end{tikzcd}
" /></p>

which is exactly $\phi$. Thus $\beta \circ \alpha = \text{id}_{\int_\mathcal{B}\Phi_p}$. Further, by construction $\beta$ and $\alpha$ are morphisms over $\mathcal{B}$. The above arguments also show that $\beta$ sends a cartesian lift $\ell_{f,c}:f^*c\to c$ in the cleavage for $\mathcal{E}$ to the pair $(f,\text{id}_{f^*c}):(p(f^*c),f^*c))\to (p(c),c)$, which from the proof of [[Basic Fibered Categories#^79c208]] is a cartesian lift in the induced cleavage on $\int_\mathcal{B}\Phi_p$. On the other hand, $\alpha$ sends such a $(f,\text{id}_{f^*c}):(B,f^*c)\to (C,c)$ to $\ell_{f,c}:f^*c\to c$. Therefore, the isomorphism preserves cleavages.
`\end{proof}`

For the dual of [[Basic Fibered Categories#^50f2b1]], we have the following result

>[!lemma] Psuedofunctor Associated with the Grothendieck Construction
>Let $\Phi:\mathcal{B}^{op}\to \mathsf{Cat}$ be a pseudo-functor. Then if $\pi_0:\int_\mathcal{B}\Phi\to \mathcal{B}$ is the Grothendieck construction of $\Phi$, there is a unique strict $2$-natural isomorphism $\Phi\cong \Phi_{\pi_0}$.

`\begin{proof}`
First, recall that $\Phi_{\pi_0}:\mathcal{B}^{op}\to \mathsf{Cat}$ is the pseudo-functor given by sending an object $B \in \mathcal{B}$ to the fiber category $\pi_0^{-1}(B)$, and sending a morphism $f:B\to B'$ to the pullback functor $f^*:\pi_0^{-1}(B')\to \pi_0^{-1}(B)$. Let us continue expanding these definitions. First, $\pi_0^{-1}(B)$ is the category with objects pairs $(B,b)$ where $b \in \Phi(B)$. Thus, on objects $\pi_0^{-1}(B)$ agrees with $\Phi(B)$. A morphism in $\pi_0^{-1}(B)$ is a map $(\text{id}_B,\phi):(B,b)\to (B,b')$, where $\phi:b\to \Phi(\text{id}_B)(b')$ is in $\Phi(B)$. Further, the composite of $\phi:b\to \Phi(\text{id}_B)(b')$ and $\psi:b'\to \Phi(\text{id}_B)(b'')$ is $\Phi^2\circ \Phi(\text{id}_B)(\psi)\circ \phi$. 

Now, the pullback functor $f^*:\pi_0^{-1}(B')\to \pi_0^{-1}(B)$ sends an object $(B',b')$ to $(B,\Phi(f)(b'))$, and sends a morphism $(\text{id}_{B'},\phi):(B',b')\to (B',b'')$ to $(\text{id}_B,\Phi^0\circ \Phi^2\circ\Phi(f)(\phi)):(B,\Phi(f)(b'))\to (B,\Phi(f)(b''))$.

We define the natural isomorphism $\alpha^\Phi:\Phi\Rightarrow \Phi_{\pi_0}$ as follows. If $B \in \mathcal{B}$, $\alpha^\Phi_B:\Phi(B)\to \Phi_{\pi_0}(B)$ is the functor that on objects maps $b\mapsto (B,b)$, and on arrows maps $f:b\to b'$ to $(\text{id}_B,\Phi^0_{b'}\circ f):(B,b)\to (B,b')$. If $f$ is an identity, $\text{id}_b:b\to b$, then $(\text{id}_B,\Phi^0_b):(B,b)\to (B,b)$ is exactly the identity in $\pi_0^{-1}(B)$. If $f:b\to b'$ and $g:b'\to b''$, then
$$\Phi_{b''}^0\circ g\circ f = \Phi(\text{id}_B)(g)\circ \Phi_{b'}^0\circ f = \Phi^2_{\text{id}_B,\text{id}_B}\circ \Phi(\text{id}_B)\Phi^0_{b''}\circ \Phi(\text{id}_B)(g)\circ \Phi_{b'}^0\circ f = \Phi^2\circ \Phi(\text{id}_B)(\Phi^0_{b''}\circ g)\circ \Phi^0_{b'}\circ f$$
which proves functoriality. To show naturality let $k:B\to B'$ in $\mathcal{B}$. Then consider the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CPhi(B')%7D%20%26%26%20%7B%5CPhi(B)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CPhi_%7B%5Cpi_0%7D(B')%7D%20%26%26%20%7B%5CPhi_%7B%5Cpi_0%7D(B)%7D%0A%09%5Carrow%5B%22%7B%5CPhi(k)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Calpha%5E%5CPhi_%7BB'%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Calpha%5E%5CPhi_B%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5CPhi_%7B%5Cpi_0%7D(k)%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Phi(B')} &amp;&amp; {\Phi(B)} \\
	\\
	{\Phi_{\pi_0}(B')} &amp;&amp; {\Phi_{\pi_0}(B)}
	\arrow[&quot;{\Phi(k)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\alpha^\Phi_{B'}}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{\alpha^\Phi_B}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\Phi_{\pi_0}(k)}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

On objects have a commuting square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bb'%7D%20%26%26%20%7B%5CPhi(k)(b')%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B(B'%2Cb')%7D%20%26%26%20%7B(B%2C%5CPhi(k)(b'))%7D%0A%09%5Carrow%5B%22%7B%5CPhi(k)%7D%22%2C%20maps%20to%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Calpha%5E%5CPhi_%7BB'%7D%7D%22'%2C%20maps%20to%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Calpha%5E%5CPhi_B%7D%22%2C%20maps%20to%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5CPhi_%7B%5Cpi_0%7D(k)%7D%22'%2C%20maps%20to%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{b'} &amp;&amp; {\Phi(k)(b')} \\
	\\
	{(B',b')} &amp;&amp; {(B,\Phi(k)(b'))}
	\arrow[&quot;{\Phi(k)}&quot;, maps to, from=1-1, to=1-3]
	\arrow[&quot;{\alpha^\Phi_{B'}}&quot;', maps to, from=1-1, to=3-1]
	\arrow[&quot;{\alpha^\Phi_B}&quot;, maps to, from=1-3, to=3-3]
	\arrow[&quot;{\Phi_{\pi_0}(k)}&quot;', maps to, from=3-1, to=3-3]
\end{tikzcd}
" /></p>

and on morphisms $f:b'\to b''$ in $\Phi(B')$, we have a square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09f%20%26%26%20%7B%5CPhi(k)(f)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B(%5Ctext%7Bid%7D_%7BB'%7D%2C%5CPhi%5E0_%7Bb''%7D%5Ccirc%20f)%7D%20%26%26%20%7B(%5Ctext%7Bid%7D_B%2C%5CPhi%5E0_%7B%5CPhi(k)(b'')%7D%5Ccirc%20%5CPhi(k)(f))%7D%0A%09%5Carrow%5B%22%7B%5CPhi(k)%7D%22%2C%20maps%20to%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Calpha%5E%5CPhi_%7BB'%7D%7D%22'%2C%20maps%20to%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Calpha%5E%5CPhi_B%7D%22%2C%20maps%20to%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5CPhi_%7B%5Cpi_0%7D(k)%7D%22'%2C%20maps%20to%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	f &amp;&amp; {\Phi(k)(f)} \\
	\\
	{(\text{id}_{B'},\Phi^0_{b''}\circ f)} &amp;&amp; {(\text{id}_B,\Phi^0_{\Phi(k)(b'')}\circ \Phi(k)(f))}
	\arrow[&quot;{\Phi(k)}&quot;, maps to, from=1-1, to=1-3]
	\arrow[&quot;{\alpha^\Phi_{B'}}&quot;', maps to, from=1-1, to=3-1]
	\arrow[&quot;{\alpha^\Phi_B}&quot;, maps to, from=1-3, to=3-3]
	\arrow[&quot;{\Phi_{\pi_0}(k)}&quot;', maps to, from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where $\Phi^0\circ \Phi^2\circ \Phi(k)(\Phi^0_{b''}) = \Phi^0$, by the right unity axiom for the pseudofunctor, so this square also commutes. Finally, for $B \in \mathcal{B}$, we define $\beta^\Phi_B:\Phi_{\pi_0}(B)\to \Phi(B)$ given by $(B,b)\mapsto b$, and $(\text{id}_B,\phi):(B,b)\to (B,b')$ maps to $(\Phi^0)^{-1}\circ \phi:b\to \Phi(\text{id}_B)b'\to b'$, which is functorial by a dual argument to functoriality of $\alpha^\Phi_B$, and evidently is inverse to $\alpha_B^\Phi$, so $\alpha^\Phi$ is our desired natural isomorphism.
`\end{proof}`

Note that in the above proofs, if either the pseudo-functors, or equivalently the fiber categories, landed in a full subcategory $\mathfrak{C} \subseteq \mathsf{Cat}$ we would have a correspondence between $\mathfrak{C}$ valued pseudofunctors and categories fibered over $\mathfrak{C}$.

>[!corollary] Equivalence of Theories
>If $\mathfrak{C}$ is a full subcategory of $\mathsf{Cat}$, then we have a correspondence between pseudo-functors $\Phi:\mathcal{B}^{op}\to \mathfrak{C}$ and fibered categories $p:\mathcal{E}\to \mathcal{B}$ where $p^{-1}(B) \in \mathfrak{C}$ for each $B \in \mathcal{B}$.

We summarize this in a more categorical flavour.

>[!theorem] Equivalence of Theories via a Strict 2-Equivalence of Strict 2-Categories
>Let $\mathcal{B}$ be a category. Then we have a strict $2$-equivalence of the strict $2$-category $\text{Bicat}^{ps}(\mathcal{B}^{op},\mathsf{Cat})$ of pseudofunctors, strong transformations, and modifications, and the strict $2$-category $\mathsf{ClovFib}(\mathcal{B})$ of cloven fibrations, $p:\mathcal{E}\to \mathcal{B}$, cleavage preserving functors $F:\mathcal{E}\to \mathcal{D}$ in the slice category $\mathsf{Cat}/\mathcal{B}$, and natural transformations between cleavage preserving functors.

`\begin{proof}`
We write $\int_\mathcal{B}:\text{Bicat}^{ps}(\mathcal{B}^{op},\mathsf{Cat})\to \mathsf{ClovFib}(\mathcal{B})$ for the strict $2$-functor that sends a pseudofunctor $\Phi:\mathcal{B}^{op}\to \mathsf{Cat}$ to its Grothendieck construction $\pi_0^\Phi:\int_\mathcal{B}\Phi\to \mathcal{B}$, a strong transformation $\alpha:\Phi\Rightarrow \Psi$ of pseudo-functors **TBD**
`\end{proof}`
### Example with Sites

Let us now interpret some of our results in a more algebro-geometric context. Let $(\mathcal{C},J)$ be a site. We can give, for each $C \in \mathcal{C}$, the slice category $\mathcal{C}/C$ a Grothendieck topology $J/C$, where covering sieves in $J/C$ are precisely those sieves which generate covering sieves in $J$ once the morphisms to $C$ are forgotten.

We can define a pseudofunctor $\Phi:\mathcal{C}^{op}\to \mathsf{Cat}$ by sending objects $C \in \mathcal{C}$ to the sheaf category of their slice, $\mathsf{Sh}(\mathcal{C}/C,J/C)$, and morphisms $f:C\to C'$ to the functor $f^*:\mathsf{Sh}(\mathcal{C}/C',J/C')\to \mathsf{Sh}(\mathcal{C}/C,J/C)$ given by sending a sheaf $P:(\mathcal{C}/C')^{op}\to \mathsf{Set}$ to the sheaf $f^*P:(\mathcal{C}/C)^{op}\to \mathsf{Set}$ given by
$$f^*P(A\to C) = P(A\to C\xrightarrow{f} C')$$
on objects and $f^*P(\varphi) = P(f\circ \varphi)$ on morphisms (this is just pre-composition by $f_*^{op}:(\mathcal{C}/C)^{op}\to (\mathcal{C}/C')^{op}$). For a natural transformation $\alpha:P\Rightarrow Q$ between sheaves, $f^*\alpha:f^*P\Rightarrow f^*Q$ is given by $f^*\alpha_{B} = \alpha_{f_*(B)}$.

This shows, in fact, that $\Phi$ is a strict $2$-functor, so in particular a pseudofunctor. Then we obtain an associated fibred category $\pi_0:\int_\mathcal{C}\Phi\to \mathcal{C}$ where $\int_\mathcal{C}\Phi$ has as objects pairs $(C,\mathscr{F})$ of an object $C \in \mathcal{C}$ and a $J/C$ sheaf $\mathscr{F}:(\mathcal{C}/C)^{op}\to \mathsf{Set}$, and as morphisms pairs $(f,\phi):(C,\mathscr{F})\to (D,\mathscr{G})$ of a morphism $f:C\to D$ in $\mathcal{C}$ and a natural transformation $\phi:\mathscr{F}\to f^*\mathscr{G}$. 

Thus, any site $(\mathcal{C},J)$ is naturally fibred in sheaf topoi induced by the site. Further, we can think of $\int_\mathcal{C}\Phi$ as a category of generalized "ringed spaces" in the sense that objects are objects equipped with structure sheaves, and morphisms are those analogous from the theory of ringed spaces.


### Sheaves as Categories Fibred in Groupoids

^9afa40

Now, let $(\mathcal{C},J)$ be a site, and let $\mathscr{F}:\mathcal{C}^{op}\to \mathsf{Set}$ be a sheaf on this site. Note that we can embed $\mathsf{Set}\hookrightarrow \mathsf{Cat}$ as the full subcategory of discrete categories, which are of course trivially groupoids. Then $\mathscr{F}:\mathcal{C}^{op}\to \mathsf{Cat}$ is a pseudo-functor, since it is a strict $2$-functor, and hence we can associate to the sheaf a cloven fibration $\pi_0:\int_\mathcal{C}\mathscr{F}\to \mathcal{C}$.

Here objects of $\int_\mathcal{C}\mathscr{F}$ are pairs $(C,s)$ of an object $C \in \mathcal{C}$ and a section $s \in \mathscr{F}(C)$. A morphism is a pair $(f,\phi):(C,s)\to (D,t)$ consisting of a map $f:C\to D$ in $\mathcal{C}$, and a map $\phi:s\to \mathscr{F}(t)$. But $\mathscr{F}$ is a functor valued in discrete categories, so the only such map is the identity, and hence a morphism is a map $f:C\to D$ such that $\mathscr{F}(t) = s$, which we can view as a kind of restriction. Note that the fiber over an object $C$ is the discrete category $\mathscr{F}(C)$. Since $\mathscr{F}$ is a sheaf, this fiber category is "equivalent", in some sense, to some category obtained by gluing the discrete categories associated with an open cover. This leads us to the observation that a sheaf is a **discrete stack**, a concept which we explore and formalize in [[Descent via Fibered Categories and Stacks]].

#### References

[^1]: Categorical Logic and Type Theory. (n.d.). https://www.cs.ru.nl/B.Jacobs/CLT/bookinfo.html. Accessed 23 May 2024
[^2]: Shulman, M. A. (2009, January 9). Framed bicategories and monoidal fibrations. arXiv. https://doi.org/10.48550/arXiv.0706.1286
