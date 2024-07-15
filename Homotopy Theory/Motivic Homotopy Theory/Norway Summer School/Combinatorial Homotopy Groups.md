---
date: 2024-07-07T09:59:00
tags:
  - Homotopy
  - Simplicial
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

In this note we discuss the combinatorial perspective on homotopy groups for simplicial sets, following the work in[^1].


## Homotopies and Fibrant Objects

Note that in the standard model structure on $\mathsf{sSet}$, the fibrant objects are precisely the Kan complexes. Since the homotopy relation is an equivalence relation for quasi-categories, by [[Introduction to Quasi-Categories#^cbf6e4]], and since Kan complexes are quasi-categories, we have a simple description of the path-components $\pi_0$ for fibrant objects in the simplicial sets category.

Due to this, we have a nice combinatorial description of fundamental groups for fibrant objects.

>[!def] Homotopy Groups for Fibrant Objects
>Let $X \in \mathsf{sSet}_*$ be a fibrant object. Then we define its $n$th homotopy group to be $$\pi_nX := \pi_0\underline{\mathsf{sSet}_*}(S^q,X)$$

We start by showing that $\pi_nX$, as defined above, has a natural group structure. Namely, if $f:\Delta^n\to X$ and $g:\Delta^n\to X$ are representatives of elements in the $n$th homotopy groups, and $x:*\to X$ is the point of the pointed simplicial set $X$, then we can define their composite by taking an extension of the inner horn $(x_n,...,x_n,f,-,g)$ to obtain a $\sigma:\Delta^{n+1}\to X$, and then defining the composite to be $d_n\sigma$. 

To see that this is well-defined, up to homotopy, suppose $h_{n-1}$ is a homotopy, relative to $\partial\Delta^n$, from $f$ to some $f'$, and let $h_{n+1}$ be a homotopy, relative to $\partial\Delta^n$, from $g$ to some $g'$. Suppose $\sigma'$ is obtained from $f'$ and $g'$, and let 
$$\partial\sigma = (x_n , \dots, x_n,f,d_n^{n+1}\sigma,h),\;\;\;\partial\sigma' = (x_n, \dots, x_n,f',d_n^{n+1}\sigma',h')$$
We now have a map
$$(\Delta^{n+1}\times \partial\Delta^1)\cup(\Lambda_n^{n+1}\times \Delta^1)\to X$$
determined by the data of $(\sigma,\sigma')$ for the left part of the union, and the data $(x_n,...,x_n,h_{n-1},-,h_{n+1})$ for the second part. Since $X$ is a Kan complex, and hence a quasi-category, and the inclusion of the left-simplex above into $\Delta^{n+1}\times \Delta^1$ is an inner anodyne morphism by an extension of [[Introduction to Quasi-Categories#^ef92d0]], we have an extension $\omega:\Delta^{n+1}\times \Delta^1\to X$. It follows that the composite 
$$\Delta^n\times \Delta^1\xrightarrow{d_n^{n+1}\times 1}\Delta^{n+1}\times \Delta^1\xrightarrow{\omega}X$$
gives our desired homotopy from $d_n^{n+1}\sigma$ to $d_n^{n+1}\sigma'$ relative to the boundary $\partial\Delta^n$.

We show these are groups (in a separate note we prove that for $n\geq 2$ the homotopy groups are abelian). Note that if $x_n:\Delta^n\to \Delta^0\xrightarrow{x}X$ is the constant path, and $f:\Delta^n\to X$ is any other path, we have that the horn $(x_n,...,x_n,x_n,-,f)$ has a filling $(x_n,...,x_n,x_n,f,f)$, given by $s^n_n(f)$. Similarly, $(x_n,...,x_n,f,-,x_n)$ has a filling $(x_n,...,x_n,f,f,x_n)$ given by $s_{n-1}^n(f)$. Further, by the above argument for  any $f$, left and right multiplication is bijective since a homotopy of the composite gives a homotopy of the domain map. In particular, this implies that every element has an inverse, and so it remains to show associativity.

Let $f,g,h:\Delta^n\to X$ be three maps representing paths. Let $\omega_{n-1}$ witness the composite of $f$ and $g$, let $\omega_{n+1}$ witness the composite of $d_n^{n+1}\omega_{n-1}$ and $h$, and let $\omega_{n+2}$ witness the composite of $g$ and $h$.

We then have an inner horn $\Lambda_n^{n+2}\to X$ determined by $(x_n,...,x_n,\omega_{n-1},-,\omega_{n+1},\omega_{n+2})$, which we can extend to a map $\omega:\Delta^{n+2}\to X$. Note that the boundary of $d_n^{n+2}\omega$ is given by the tuple $(x_n,...,x_n,f,d_n^{n+1}\omega_{n+1},d_n^{n+1}\omega_{n+2})$. We can then compute
$$
\begin{align*}
([f][g])[h] &= [d_n^{n+1}\omega_{n-1}][h] \\
&= [d_n^{n+1}\omega_{n+1}] \\
&= [d_n^{n+1}d_n^{n+2}\omega] \\
&= [f][d_n^{n+1}\omega_{n+2}] \\
&= [f]([g][h])
\end{align*}
$$

This combinatorial construction agrees with our previous topological one.

>[!lemma] Combinatorial Homotopy Group vs. Topological Homotopy Group
>Let $X \in \mathsf{sSet}_*$ be a fibrant object. Then there is a natural isomorphism $\pi_nX\cong \pi_n|X|$ for all $n \geq 0$.

`\begin{proof}[Proof Idea.]`
Note that the unit $X\to \text{Sing}_\bullet(|X|)$ is a weak homotopy equivalence by the topological definition of the simplicial homotopy groups. Since $X$ is a fibrant object (i.e. a Kan complex), the **Whitehead Theorem** implies that the unit $X\to \text{Sing}_\bullet(|X|)$ is a homotopy equivalence. This implies that the map
$$\underline{\mathsf{sSet}_*}(S^n,X)\to \underline{\mathsf{sSet}_*}(S^n,\text{Sing}_\bullet(|X|)\cong \text{Sing}_\bullet(|X|^{|S^n|})$$
is a homotopy equivalence. It follows that they have the same $\pi_0$, completing the sketch.
`\end{proof}`

### Fiber Sequence

An important object in the study of higher homotopy groups is the fiber sequence. Suppose $p:X\to Y$ is a Kan fibration of simplicial sets and let $y:\Delta^0\to Y$ be a point. Let $F = y\times_YX$ be the fiber of $p$ above $y$, and let $x:\Delta^0\to F$ be a point in the fiber, giving a point in $X$ and turning the maps into pointed maps. Given a representative $f:\Delta^n\to Y$ of an element in $\pi_n(Y,y)$ we have a diagram, with filling (since $p$ is a Kan fibration),

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_0%5En%7D%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%7D%20%26%26%20Y%0A%09%5Carrow%5B%22%7B(-%2Cx%2C...%2Cx)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Csigma%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_0^n} &amp;&amp; X \\
	\\
	{\Delta^n} &amp;&amp; Y
	\arrow[&quot;{(-,x,...,x)}&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[&quot;\sigma&quot;, dashed, from=3-1, to=1-3]
	\arrow[&quot;f&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

The element $d_0^n\sigma$ factors through $F$, and the homotopy class $[d_0^n\sigma] \in \pi_{n-1}(F,x)$ is independent of the lift $\sigma$ or the representative $f$ of the homotopy class $[f]$. This induces a map
$$\partial:\pi_n(Y,y)\to \pi_{n-1}(F,x)$$
called the **boundary map**.

>[!lem] Characterization of Representatives of the point
>Let $f:\Delta^n\to X$ represent an element of $\pi_n(X,x)$. Then $[f] = e$, the identity element, if and only if there is an $(n+1)$-simplex $\omega$ of $X$ such that $\partial\omega = (x,...,x,\alpha)$

`\begin{proof}`
The lemma follows from the uniqueness of composite of maps and the fact that $\pi_n(X,x)$ is a group.
`\end{proof}`

>[!lem] Fiber  Sequence
>1. The boundary map $\partial:\pi_n(Y,y)\to \pi_{n-1}(F,x)$ is a group homomorphism for $n > 1$
>2. The sequence
>   
>   <p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%5Ccdots%20%26%20%7B%5Cpi_n(F%2Cx)%7D%20%26%20%7B%5Cpi_n(X%2Cx)%7D%20%26%20%7B%5Cpi_n(Y%2Cy)%7D%20%26%20%7B%5Cpi_%7Bn-1%7D(F%2Cx)%7D%20%5C%5C%0A%09%26%20%5Ccdots%20%26%20%7B%5Cpi_1(Y%2Cy)%7D%20%26%20%7B%5Cpi_0(F%2Cx)%7D%20%26%20%7B%5Cpi_0(X%2Cx)%7D%20%26%20%7B%5Cpi_0(Y%2Cy)%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7Bi_*%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bp_*%7D%22%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%5Cpartial%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%09%5Carrow%5Bfrom%3D1-5%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Bp_*%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%5Cpartial%22'%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7Bi_*%7D%22'%2C%20from%3D2-4%2C%20to%3D2-5%5D%0A%09%5Carrow%5B%22%7Bp_*%7D%22'%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	\cdots &amp; {\pi_n(F,x)} &amp; {\pi_n(X,x)} &amp; {\pi_n(Y,y)} &amp; {\pi_{n-1}(F,x)} \\	&amp; \cdots &amp; {\pi_1(Y,y)} &amp; {\pi_0(F,x)} &amp; {\pi_0(X,x)} &amp; {\pi_0(Y,y)}	\arrow[from=1-1, to=1-2]	\arrow[&quot;{i_*}&quot;, from=1-2, to=1-3]	\arrow[&quot;{p_*}&quot;, from=1-3, to=1-4]	\arrow[&quot;\partial&quot;, from=1-4, to=1-5]	\arrow[from=1-5, to=2-2]	\arrow[&quot;{p_*}&quot;', from=2-2, to=2-3]	\arrow[&quot;\partial&quot;', from=2-3, to=2-4]	\arrow[&quot;{i_*}&quot;', from=2-4, to=2-5]	\arrow[&quot;{p_*}&quot;', from=2-5, to=2-6]\end{tikzcd}" /></p>

`\begin{proof}`
For **(1)**, suppose $n \geq 2$, and that we have diagrams

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_0%5En%7D%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%7D%20%26%26%20Y%0A%09%5Carrow%5B%22%7B(-%2Cx%2C...%2Cx)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Csigma_i%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22f_i%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_0^n} &amp;&amp; X \\
	\\
	{\Delta^n} &amp;&amp; Y
	\arrow[&quot;{(-,x,...,x)}&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[&quot;\sigma_i&quot;, dashed, from=3-1, to=1-3]
	\arrow[&quot;f_i&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

for $i = n-1,n,n+1$, and where the $f_i$ represent elements of $\pi_n(Y,y)$. Suppose we have an $(n+1)$-simplex $\omega$ with $\partial\omega = (x,...,x,\alpha_{n-1},\alpha_n,\alpha_{n+1})$, which witnesses $[\alpha_{n-1}][\alpha_{n+1}]=[\alpha_n]$. Then we have a diagram, and lift,

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_0%5E%7Bn%2B1%7D%7D%20%26%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5E%7Bn%2B1%7D%7D%20%26%26%26%20Y%0A%09%5Carrow%5B%22%7B(-%2Cy%2C...%2Cy%2C%5Csigma_%7Bn-1%7D%2C%5Csigma_n%2C%5Csigma_%7Bn%2B1%7D)%7D%22%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22%5Cgamma%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%5Comega%22'%2C%20from%3D3-1%2C%20to%3D3-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_0^{n+1}} &amp;&amp;&amp; X \\
	\\
	{\Delta^{n+1}} &amp;&amp;&amp; Y
	\arrow[&quot;{(-,y,...,y,\sigma_{n-1},\sigma_n,\sigma_{n+1})}&quot;, from=1-1, to=1-4]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-4, to=3-4]
	\arrow[&quot;\gamma&quot;, dashed, from=3-1, to=1-4]
	\arrow[&quot;\omega&quot;', from=3-1, to=3-4]
\end{tikzcd}
" /></p>


so that
$$\partial(d_0^{n+1}\gamma) = (x, \dots,x,d_0^n\sigma_{n-1},d_0^n\sigma_n,d_0^n\sigma_{n+1})$$
so $[d_0^n\sigma_n] = [d_0^n\sigma_{n-1}][d_0^n\sigma_{n+1}]$, which proves that $\partial$ is a group homomorphism for $n \geq 2$.

For **(2)** we first show that the sequence
$$\pi_n(X,x)\xrightarrow{p_*}\pi_n(Y,y)\xrightarrow{\partial}\pi_{n-1}(F,x)$$
is exact. Note that if $f:\Delta^n\to X$ represents an element of $\pi_n(X,x)$, then we have the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_0%5En%7D%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%7D%20%26%26%20Y%0A%09%5Carrow%5B%22%7B(-%2Cx%2C...%2Cx)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22f%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22p%5Ccirc%20f%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_0^n} &amp;&amp; X \\
	\\
	{\Delta^n} &amp;&amp; Y
	\arrow[&quot;{(-,x,...,x)}&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[&quot;f&quot;, dashed, from=3-1, to=1-3]
	\arrow[&quot;p\circ f&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where $d_0^nf = x$. This shows that $\partial\circ p_*$ is trivial. Now, suppose $\gamma:\Delta^n\to Y$ represents an element of $\pi_n(Y,y)$ such that there exists a diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_0%5En%7D%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%7D%20%26%26%20Y%0A%09%5Carrow%5B%22%7B(-%2Cx%2C...%2Cx)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Comega%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%5Cgamma%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_0^n} &amp;&amp; X \\
	\\
	{\Delta^n} &amp;&amp; Y
	\arrow[&quot;{(-,x,...,x)}&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[&quot;\omega&quot;, dashed, from=3-1, to=1-3]
	\arrow[&quot;\gamma&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where $[d_0^n\omega] = e$. Then we have a homotopy $h_0:\Delta^{n-1}\times \Delta^1\to F$ from $d_0^n\omega$ to $x$ relative to $\partial\Delta^{n-1}$. 

Now, we obtain a map $(\Delta^n\times \Lambda_0^1)\cup(\partial\Delta^n)$ **TBC**


#### References

[^1]: Dundas, B. I., Levine, M., Østvær, P. A., Röndigs, O., & Voevodsky, V. (Eds.). (2007). Motivic Homotopy Theory. Berlin, Heidelberg: Springer. https://doi.org/10.1007/978-3-540-45897-5