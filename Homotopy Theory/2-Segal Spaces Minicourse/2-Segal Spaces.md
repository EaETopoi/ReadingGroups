---
date: 2024-05-16T09:19:00
tags:
  - 2Segal
  - Homotopy
  - Minicourse
  - Simplicial
type: Notes
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

In this note we are continuing our discussion of 2-Segal objects, moving from 1-Segal and 2-Segal sets to 1-Segal and 2-Segal spaces. We will begin by introducing 2-Segal spaces and 2-Segal objects a little more generally. We will also discuss how 2-Segal objects arise from **Waldhausen's $S_\bullet$-construction**.
## Simplicial Spaces

We consider simplicial spaces as either objects $X:\Delta^{op}\to \mathbf{SSets}$ or $X:\Delta^{op}\to \mathbf{Top}$. To define **1-Segal spaces** we want the maps $X_n\to X_1\times_{X_0}^h\cdots \times_{X_0}^hX_1$ to be weak-equivalences for all $n \geq 2$, where the pullbacks are **homotopy limits**. Note that this is a weakening of the 2-Segality condition given in [[2-Segal Sets]]. These should correspond to **simplicial/topological categories** up to homotopy, consisting of spaces of objects and morphisms.

Next, going to **2-Segal spaces** we ask that the maps $X_n\to X_2\times_{X_1}^h\cdots \times_{X_1}^hX_2$ be weak equivalences for all $n \geq 3$, and each triangulation of a cyclically labeled triangulation of a regular $n$-gon. For example, we can recall the inclusion (square with 1-3 diagonal to 3-simplex) given by the map 
$$
X_{3}\xrightarrow{(d_{0},d_{2})}X_{2}\times_{X_{1}^h}X_{2}
$$
These give **simplicial/topological multivalued categories** up to homotopy. We can define these more general.

>[!Definition]
>A **2-Segal object** is a simplicial object $X:\Delta^{op}\to \mathcal{C}$ into a sufficiently nice category (e.g. model category, $(\infty,1)$-category with limits), having the desired maps being weak equivalences.

## Model Structures

We can consider a natural model structure where the underlying category is simplicial spaces, the injective (=Reedy) model structure is levelwise weak equivalences/cofibrations of spaces (in some references we can take a projective model structure). The **left Bousfield localization** with respect 
- $\mathcal{G}(n)\hookrightarrow \Delta[n]$ for $n \geq 2$, giving fibrant objects being 1-Segal
- $\mathcal{J}\hookrightarrow \Delta[n]$ for $n \geq 3$ + triangulation, giving fibration objects being 2-Segal.

## The $S_\bullet$-Construction

One of the most classical inputs for algebraic K-theory is that of an **exact category**, which can be thought of as a category where short exact sequences make sense (e.g. all abelian categories are exact categories).

>[!def|A.1] Grothendieck group
>For $\mathcal{C}$ exact, we define the Grothendieck group for $\mathcal{C}$ to be $$K_{0}(\mathcal{C}) = \mathbb{Z}\langle[\mathbb{Ob}(\mathcal{C})]/\langle [C]=[B]+[D] \text{ for } 0\to B \hookrightarrow C\twoheadrightarrow D\to 0\rangle$$

To define higher algebraic $K$-Groups one approach uses the following features of an exact category (these also hold in "**proto-exact categories**"):
- The category is pointed: has a zero object $*$
- Classes $\mathcal{M}$ of **admissible monomorphisms** ($\hookrightarrow$) containing $*\hookrightarrow A$ for all objects $A$, and $\mathcal{E}$ of **admissible epimorphisms** ($\twoheadrightarrow$) containing $A\twoheadrightarrow *$ for all $A$, and both closed under composition and containing all isomorphisms
- A commutative square <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20B%20%5C%5C%0A%09C%20%26%20D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; B \\
	C &amp; D
	\arrow[hook, from=1-1, to=1-2]
	\arrow[two heads, from=1-1, to=2-1]
	\arrow[two heads, from=1-2, to=2-2]
	\arrow[hook, from=2-1, to=2-2]
\end{tikzcd}
			" /></p> is cartesian if and only if it is cocartesian (called bicartesian). 
- Further, any corner <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20B%20%5C%5C%0A%09C%20%26%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; B \\
	C &amp;
	\arrow[hook, from=1-1, to=1-2]
	\arrow[two heads, from=1-1, to=2-1]
\end{tikzcd}
" /></p>and any<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20B%20%5C%5C%0A%09C%20%26%20D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; B \\
	C &amp; D
	\arrow[two heads, from=1-2, to=2-2]
	\arrow[hook, from=2-1, to=2-2]
\end{tikzcd}
" /></p> can be completed to a bicartesian square as above, essentially uniquely.

>[!example]
>- $R$-modules with usual monomorphisms and epimorphisms
>- Pointed sets (finite) with $\mathcal{M} =$ injections and $\mathcal{E} =$ surjections with singleton pre-images over non-basepoints


>[!rmk] Waldhausen's $S_\bullet$-construction for a proto-exact category
>Let $\mathcal{C}$ be a proto-exact category:
>- Let $S_0(\mathcal{C}) =$ groupoid of zero objects of $\mathcal{C}$
>- Let $S_1(\mathcal{C})=$ groupoid of diagrams of the form <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B*%7D%20%26%20%7Ba_%7B01%7D%7D%20%5C%5C%0A%09%26%20%7B*%7D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{*} &amp; {a_{01}} \\&amp; {*}\arrow[hook, from=1-1, to=1-2]\arrow[two heads, from=1-2, to=2-2]\end{tikzcd}" /></p> encoding objects
>- Let $S_2(\mathcal{C})=$ groupoid of diagrams <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B*%7D%20%26%20%7Ba_%7B01%7D%7D%20%26%20%7Ba_%7B02%7D%7D%20%5C%5C%0A%09%26%20%7B*%7D%20%26%20%7Ba_%7B12%7D%7D%20%5C%5C%0A%09%26%26%20%7B*%7D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{*} &amp; {a_{01}} &amp; {a_{02}} \\&amp; {*} &amp; {a_{12}} \\&amp;&amp; {*}\arrow[hook, from=1-1, to=1-2]\arrow[hook, from=1-2, to=1-3]\arrow[two heads, from=1-2, to=2-2]\arrow[two heads, from=1-3, to=2-3]\arrow[hook, from=2-2, to=2-3]\arrow[two heads, from=2-3, to=3-3]\end{tikzcd}" /></p> with square bicartesian, which model "short exact sequences"
>- Let $S_n(\mathcal{C})=$groupoid of diagrams
><p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B*%7D%20%26%20%7Ba_%7B01%7D%7D%20%26%20%7Ba_%7B02%7D%7D%20%26%20%5Ccdots%20%26%20%7Ba_%7B0n%7D%7D%20%5C%5C%0A%09%26%20%7B*%7D%20%26%20%7Ba_%7B12%7D%7D%20%26%20%5Ccdots%20%26%20%7Ba_%7B1n%7D%7D%20%5C%5C%0A%09%26%26%20%7B*%7D%20%26%20%5Ccdots%20%26%20%5Cvdots%20%5C%5C%0A%09%26%26%26%26%20%7Ba_%7B(n-1)n%7D%7D%20%5C%5C%0A%09%26%26%26%26%20%7B*%7D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-5%2C%20to%3D2-5%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-4%2C%20to%3D2-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-5%2C%20to%3D3-5%5D%0A%09%5Carrow%5Bhook%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bhook%2C%20from%3D3-4%2C%20to%3D3-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D3-5%2C%20to%3D4-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D4-5%2C%20to%3D5-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{*} &amp; {a_{01}} &amp; {a_{02}} &amp; \cdots &amp; {a_{0n}} \\&amp; {*} &amp; {a_{12}} &amp; \cdots &amp; {a_{1n}} \\&amp;&amp; {*} &amp; \cdots &amp; \vdots \\&amp;&amp;&amp;&amp; {a_{(n-1)n}} \\&amp;&amp;&amp;&amp; {*}\arrow[hook, from=1-1, to=1-2]\arrow[hook, from=1-2, to=1-3]\arrow[two heads, from=1-2, to=2-2]\arrow[hook, from=1-3, to=1-4]\arrow[two heads, from=1-3, to=2-3]\arrow[hook, from=1-4, to=1-5]\arrow[two heads, from=1-5, to=2-5]\arrow[hook, from=2-2, to=2-3]\arrow[hook, from=2-3, to=2-4]\arrow[two heads, from=2-3, to=3-3]\arrow[hook, from=2-4, to=2-5]\arrow[two heads, from=2-5, to=3-5]\arrow[hook, from=3-3, to=3-4]\arrow[hook, from=3-4, to=3-5]\arrow[two heads, from=3-5, to=4-5]\arrow[two heads, from=4-5, to=5-5]\end{tikzcd}" /></p>
>with all squares bicartesian
>Then $S_\bullet(\mathcal{C})$ is a simplicial groupoid: 
>- face maps $d_i$ removes everything with index $i$
>- degeneracy maps $s_i$ repeat entries with identity maps

Taking the **nerve levelwise** gives a simplicial space (also $S_\bullet(\mathcal{C})$) whose diagonal/geometric realization is a space $|S_\bullet(\mathcal{C})|$. One can check that $\pi_1|S_\bullet(\mathcal{C})| \cong K_0(\mathcal{C})$ if $\mathcal{C}$ is an exact category. So, we can define the **$K$-theory space** of $\mathcal{C}$ to be $K(\mathcal{C}) = \Omega|S_\bullet(\mathcal{C})|$ (the loop space of the realization of the levelwise nerve of the $S_\bullet$-construction) and the $K$-groups, 
$$K_{i}(\mathcal{C}) = \pi_{i}K(\mathcal{C}) = \pi_{{i+1}}|S_{\bullet}(\mathcal{C})|$$

>[!theorem] Dyckerhoff-Kapranov, Galvez-Carnillo-Kock-Tonks
>Taking the simplicial nerve, $S_\bullet(\mathcal{C})$ is a 2-Segal space

The **idea** of the construction can be summarized by the following example: Consider $(d_0,d_2):S_3(\mathcal{C})\to S_2(\mathcal{C})\times_{S_1(\mathcal{C})}^hS_2(\mathcal{C})$ which can be represented by the diagram

<p align="left"><img align="left" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B*%7D%20%26%20%7Ba_%7B01%7D%7D%20%26%20%7Ba_%7B02%7D%7D%20%26%20%7Ba_%7B03%7D%7D%20%5C%5C%0A%09%26%20%7B*%7D%20%26%20%7Ba_%7B12%7D%7D%20%26%20%7Ba_%7B13%7D%7D%20%5C%5C%0A%09%26%26%20%7B*%7D%20%26%20%7Ba_%7B23%7D%7D%20%5C%5C%0A%09%26%26%26%20%7B*%7D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-4%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bhook%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D3-4%2C%20to%3D4-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{*} &amp; {a_{01}} &amp; {a_{02}} &amp; {a_{03}} \\
	&amp; {*} &amp; {a_{12}} &amp; {a_{13}} \\
	&amp;&amp; {*} &amp; {a_{23}} \\
	&amp;&amp;&amp; {*}
	\arrow[hook, from=1-1, to=1-2]
	\arrow[hook, from=1-2, to=1-3]
	\arrow[two heads, from=1-2, to=2-2]
	\arrow[hook, from=1-3, to=1-4]
	\arrow[two heads, from=1-3, to=2-3]
	\arrow[two heads, from=1-4, to=2-4]
	\arrow[hook, from=2-2, to=2-3]
	\arrow[hook, from=2-3, to=2-4]
	\arrow[two heads, from=2-3, to=3-3]
	\arrow[two heads, from=2-4, to=3-4]
	\arrow[hook, from=3-3, to=3-4]
	\arrow[two heads, from=3-4, to=4-4]
\end{tikzcd}"/>  <img align="right" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%5Ctextcolor%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%7B*%7D%20%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%7Ba_%7B01%7D%7D%20%26%20%7Ba_%7B02%7D%7D%20%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%7Ba_%7B03%7D%7D%20%5C%5C%0A%09%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%7B*%7D%20%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%7Ba_%7B12%7D%7D%20%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%7Ba_%7B13%7D%7D%20%5C%5C%0A%09%26%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%7B*%7D%20%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%7Ba_%7B23%7D%7D%20%5C%5C%0A%09%26%26%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%7B*%7D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%2C%20hook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%2C%20bend%20left%3D30%2C%20hook%2C%20from%3D1-2%2C%20to%3D1-4%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%2C%20two%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%2C%20two%20heads%2C%20from%3D1-4%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%2C%20hook%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%2C%20bend%20left%3D30%2C%20hook%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%2C%20hook%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%2C%20two%20heads%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%2C%20two%20heads%2C%20from%3D2-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%2C%20hook%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C92%3Bgreen%2C214%3Bblue%2C214%7D%2C%20two%20heads%2C%20from%3D3-4%2C%20to%3D4-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	\textcolor{rgb,255:red,214;green,92;blue,92}{*} &amp; \textcolor{rgb,255:red,214;green,92;blue,92}{a_{01}} &amp; {a_{02}} &amp; \textcolor{rgb,255:red,214;green,92;blue,92}{a_{03}} \\
	&amp; \textcolor{rgb,255:red,92;green,214;blue,214}{*} &amp; \textcolor{rgb,255:red,92;green,214;blue,214}{a_{12}} &amp; \textcolor{rgb,255:red,92;green,214;blue,214}{a_{13}} \\
	&amp;&amp; \textcolor{rgb,255:red,92;green,214;blue,214}{*} &amp; \textcolor{rgb,255:red,92;green,214;blue,214}{a_{23}} \\
	&amp;&amp;&amp; \textcolor{rgb,255:red,92;green,214;blue,214}{*}
	\arrow[color={rgb,255:red,214;green,92;blue,92}, hook, from=1-1, to=1-2]
	\arrow[hook, from=1-2, to=1-3]
	\arrow[color={rgb,255:red,214;green,92;blue,92}, bend left=30, hook, from=1-2, to=1-4]
	\arrow[color={rgb,255:red,214;green,92;blue,92}, two heads, from=1-2, to=2-2]
	\arrow[hook, from=1-3, to=1-4]
	\arrow[two heads, from=1-3, to=2-3]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-3, to=2-4]
	\arrow[color={rgb,255:red,214;green,92;blue,92}, two heads, from=1-4, to=2-4]
	\arrow[color={rgb,255:red,92;green,214;blue,214}, hook, from=2-2, to=2-3]
	\arrow[color={rgb,255:red,214;green,92;blue,92}, bend left=30, hook, from=2-2, to=2-4]
	\arrow[color={rgb,255:red,92;green,214;blue,214}, hook, from=2-3, to=2-4]
	\arrow[color={rgb,255:red,92;green,214;blue,214}, two heads, from=2-3, to=3-3]
	\arrow[color={rgb,255:red,92;green,214;blue,214}, two heads, from=2-4, to=3-4]
	\arrow[color={rgb,255:red,92;green,214;blue,214}, hook, from=3-3, to=3-4]
	\arrow[color={rgb,255:red,92;green,214;blue,214}, two heads, from=3-4, to=4-4]
\end{tikzcd}
" /></p>

However, this construction is not 1-Segal in general. For example, consider the 1-Segal condition $S_2(\mathcal{C})\to S_1(\mathcal{C}) \times_{S_0(\mathcal{C})}^hS_1(\mathcal{C})$ which to be a weak equivalence would need a unique filling in the following diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B*%7D%20%26%20%7Ba_%7B01%7D%7D%20%26%20%5Ctextcolor%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%7B%3F%7D%20%5C%5C%0A%09%26%20%7B*%7D%20%26%20%7Ba_%7B12%7D%7D%20%5C%5C%0A%09%26%26%20%7B*%7D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%2C%20dashed%2C%20hook%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bcolor%3D%7Brgb%2C255%3Ared%2C214%3Bgreen%2C92%3Bblue%2C92%7D%2C%20dashed%2C%20two%20heads%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{*} &amp; {a_{01}} &amp; \textcolor{rgb,255:red,214;green,92;blue,92}{?} \\
	&amp; {*} &amp; {a_{12}} \\
	&amp;&amp; {*}
	\arrow[hook, from=1-1, to=1-2]
	\arrow[color={rgb,255:red,214;green,92;blue,92}, dashed, hook, from=1-2, to=1-3]
	\arrow[two heads, from=1-2, to=2-2]
	\arrow[color={rgb,255:red,214;green,92;blue,92}, dashed, two heads, from=1-3, to=2-3]
	\arrow[hook, from=2-2, to=2-3]
	\arrow[two heads, from=2-3, to=3-3]
\end{tikzcd}
" /></p>

which in the algebraic world comes down to not all extensions splitting.

>[!rmk] 
>Waldhausen originally defined this construction for Waldhausen categories, or more generally categories with cofibrations. In this setting we only have one type of morphism, $\hookrightarrow$, and certain pushout conditions. In this setting we would no longer necessarily be able to have 2-Segal spaces, as defined previously, due to the lack of pullbacks. We do, however, always get "half" the structure: "**left/lower 2-Segal**" (by **Tanner Carawan**).

This leads to an important question.
**Q. What is the most general input for $S_\bullet$ for which the output is 2-Segal?** 
Let's return to our input data and look for possible generalizations. For simplicity, we will take an $S_\bullet$ that is discrete moving forward: we take sets of diagrams in the above form, where now $S_\bullet(\mathcal{C})$ is a simplicial set. What do we need?
-  Need "horizontal" ($\hookrightarrow$) and "vertical" ($\twoheadrightarrow$) morphisms that assemble into squares. (This approaches the data of a **double category**, or a category internal to categories) In particular, this means that we no longer require that both types of morphisms live in the same type of ambient category. 
- Since "bicartesian squares" no longer make sense in the setting of a general double category, instead we replace them by a **stability** condition which says that for any "span" or "cospan" for an arrow in each direction, we can uniquely determine a square in the double category.
- To get a zero object we ask that our double category is **pointed**, which says that we have an object $*$ that is initial in the horizontal category and terminal in the vertical category.

These requirements give a **reduced** 2-Segal set $K$, $K_0 = *$.

More generally, we can consider an **augmentation** subset $A$ of objects such that for any object $X$ we have a unique $a$ and a unique horizontal map from $a$ to $X$ and a unique $b$ and a unique vertical map from $X$ to $b$, where $a,b \in A$.

>[!theorem] B-Osorno-Ozornova-Rovelli-Scheimbauer
>The discrete $S_\bullet$-construction defines an equivalence of categories between augmented stable double categories and $2$-Segal sets.

The inverse functor $P$ takes a 2-Segal set $K$ to the double category $P(K)$ 
- Object set: $K_1$ (aumentation: $K_0$)
- Horizontal morphisms: $K_2$
- Vertical Morphisms: $K_2$ (different structure than horizontal morphisms)
- Squares: $K_3$ 

Lets consider the [[2-Segal Sets#^59fe58]] example in this context.

>[!example] Partial Monoid
>Let $M$ be a partial monoid with composable pairs $M_2 \subseteq M\times M$. Recall when we thought of this as a 2-Segal set, $M_2$ was the set of 2-simplexes. Then a pair $(a,b) \in M_2$ as a vertical morphisms is thought of as $a\bullet b\twoheadrightarrow b$, while as a horizontal morphism is thought of as a morphism $a\hookrightarrow a\bullet b$. 
>
>We think of a 3-simplex $(a,b,c) \in M_3$ (i.e. a composable triple) as corresponding to a square <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Ba%5Cbullet%20b%7D%20%26%20%7B(a%5Cbullet%20b)%5Cbullet%20c%3Da%5Cbullet(b%5Cbullet%20c)%7D%20%5C%5C%0A%09b%20%26%20%7Bb%5Cbullet%20c%7D%0A%09%5Carrow%5B%22%7B%5Cbullet%20c%7D%22%2C%20hook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22a%5Cbullet%22'%2C%20two%20heads%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22a%5Cbullet%22%2C%20two%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Cbullet%20c%7D%22'%2C%20hook%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{a\bullet b} &amp; {(a\bullet b)\bullet c=a\bullet(b\bullet c)} \\b &amp; {b\bullet c}\arrow[&quot;{\bullet c}&quot;, hook, from=1-1, to=1-2]\arrow[&quot;a\bullet&quot;', two heads, from=1-1, to=2-1]\arrow[&quot;a\bullet&quot;, two heads, from=1-2, to=2-2]\arrow[&quot;{\bullet c}&quot;', hook, from=2-1, to=2-2]\end{tikzcd}" /></p>
>and associativity gives stability.

We will continue our generalization of the $S_\bullet$-construction in [[2-Segal Spaces via Double Categories]].
