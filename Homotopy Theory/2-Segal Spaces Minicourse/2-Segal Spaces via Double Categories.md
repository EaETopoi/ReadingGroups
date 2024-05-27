---
date: 2024-05-21T09:31:00
tags:
  - 2Segal
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

In this notes we continue off from [[2-Segal Spaces]] by returning to the $S_\bullet$-construction before going into a discussion on **Hall algebras**. In [[2-Segal Spaces#The $S_ bullet$-Construction]] we also talked about generalizing the input for the $S_\bullet$-construction in the discrete context.

## Generalizing $S_\bullet$

Recall that $S_n(\mathcal{C})$, classically, gives a groupoid of diagrams of the form
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B*%7D%20%26%20%7Ba_%7B01%7D%7D%20%26%20%7Ba_%7B02%7D%7D%20%26%20%5Ccdots%20%26%20%7Ba_%7B0n%7D%7D%20%5C%5C%0A%09%26%20%7B*%7D%20%26%20%7Ba_%7B12%7D%7D%20%26%20%5Ccdots%20%26%20%7Ba_%7B1n%7D%7D%20%5C%5C%0A%09%26%26%20%7B*%7D%20%26%20%5Ccdots%20%26%20%5Cvdots%20%5C%5C%0A%09%26%26%26%26%20%7Ba_%7B(n-1)n%7D%7D%20%5C%5C%0A%09%26%26%26%26%20%7B*%7D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-5%2C%20to%3D2-5%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-4%2C%20to%3D2-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D2-5%2C%20to%3D3-5%5D%0A%09%5Carrow%5Bhook%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bhook%2C%20from%3D3-4%2C%20to%3D3-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D3-5%2C%20to%3D4-5%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D4-5%2C%20to%3D5-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{*} &amp; {a_{01}} &amp; {a_{02}} &amp; \cdots &amp; {a_{0n}} \\&amp; {*} &amp; {a_{12}} &amp; \cdots &amp; {a_{1n}} \\&amp;&amp; {*} &amp; \cdots &amp; \vdots \\&amp;&amp;&amp;&amp; {a_{(n-1)n}} \\&amp;&amp;&amp;&amp; {*}\arrow[hook, from=1-1, to=1-2]\arrow[hook, from=1-2, to=1-3]\arrow[two heads, from=1-2, to=2-2]\arrow[hook, from=1-3, to=1-4]\arrow[two heads, from=1-3, to=2-3]\arrow[hook, from=1-4, to=1-5]\arrow[two heads, from=1-5, to=2-5]\arrow[hook, from=2-2, to=2-3]\arrow[hook, from=2-3, to=2-4]\arrow[two heads, from=2-3, to=3-3]\arrow[hook, from=2-4, to=2-5]\arrow[two heads, from=2-5, to=3-5]\arrow[hook, from=3-3, to=3-4]\arrow[hook, from=3-4, to=3-5]\arrow[two heads, from=3-5, to=4-5]\arrow[two heads, from=4-5, to=5-5]\end{tikzcd}" /></p>
where horizontal arrows are admissible monomorphisms in some category and vertical morphisms are admissible epimorphisms in that same category, with all squares being bicartesian.

Last time we began considering these diagrams as living in an augmented stable double category. However, we only treated the discrete case, so how can we go to a homotopy version? Well, we can replace our double categories by objects known as **double (1-)Segal space**, $X:\Delta^{op}\times \Delta^{op}\to \mathsf{SSets}$ that is a **Segal** space in each variable, which we think of as a "double category up to homotopy".

Recall that the **stability** condition on a double category ensured that we could complete any corner <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20B%20%5C%5C%0A%09C%20%26%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; B \\
	C &amp;
	\arrow[hook, from=1-1, to=1-2]
	\arrow[two heads, from=1-1, to=2-1]
\end{tikzcd}
" /></p>and any <p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20B%20%5C%5C%0A%09C%20%26%20D%0A%09%5Carrow%5Btwo%20heads%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; B \\
	C &amp; D
	\arrow[two heads, from=1-2, to=2-2]
	\arrow[hook, from=2-1, to=2-2]
\end{tikzcd}
" /></p> 
to a unique square. Now, instead we ask that these corners determine a square up to homotopy/up to a contractible space of choices. Recall we also had the pointed condition, which said that we had an object $*$
 that is initial for the horizontal category and terminal for the vertical category. Going to spaces of such objects, and spaces of maps to/from other objects, we replace the uniqueness requirements by the statement that the space of maps to these objects are contractible. Similarly we can make a homotopy condition out of the augmentation condition.


We now organize this data as follows.

>[!def]
>Let $\Sigma$ be the category which is obtained by adjoining  a terminal object $[-1]$ to $\mathbb{\Delta}\times \mathbb{\Delta}$. Then a **homotopy double category** is a functor $\Sigma^{op}\to \mathsf{SSets}$.

We then have the following result:

>[!theorem] B.-Osorno-Ozornova-Rovelli-Scheimbauer
>1. There is a model structure on $\mathsf{SSets}^{\Sigma^{op}}$ with fibrant objects the augmented stable double Segal spaces.
>2. The $S_\bullet$-construction defines the right adjoint of a **Quillen equivalence** between it and the 2-Segal space model structure.
>3. In (proto-)exact (quasi-)categories, this $S_\bullet$-construction recovers the classical/known versions.

**Related work:** There is current work on CGW categories and their variants defined by Campbell-Zakharevich, with variants done by Sarazola-Shapiro, also form a general input for $K$-theory constructions. Current work in progress by B.-Shapiro-Zakharevich goes into showing that CGW categories can be understood as pointed stable double Segal spaces, which is known, but it is attempted to determine what kind of subcategory this forms.


## Hall Algebras

Throughout let $\mathcal{A}$ denote an abelian category with $|\mathcal{A}(A,B)|$, and $|\text{Ext}^1(A,B)|$ finite for all objects $A$ and $B$ (i.e. $\mathcal{A}$ is **finitary**). Then we can associate a Hall algebra to $\mathcal{A}$.

>[!def] Hall Algebras
>The **Hall Algebra** $\mathscr{H}(\mathcal{A})$ is define as a vector space (over some field $\mathbb{k}$) with basis isomorphism classes of objects in $\mathcal{A}$, and multiplication given on basis elements by
>$$[A]\cdot[B] = \sum_{[C]}g_{AB}^C[C]$$
>where $g_{AB}^C = \frac{|\{0\to A\to C\to B\to 0\}|}{|\text{Aut}(A)||\text{Aut}(B)|}$.

This definition gives an associative unital algebra, with unit $[0]$.

>[!example]
>Let $\mathfrak{g}$ be a Lie algebra of type $A$, $D$, or $E$. It has an associated **simply laced Dynkin diagram** (i.e. a graph) which after specifying an orientation on each edge gives a quiver $Q$. 
>
>Let $\mathcal{A}$ be the category of representations of the quiver $Q$ over $\mathbb{F}_q$, a finite field (this is the category of functors from $Q$ to $\mathsf{Vect}_{\mathbb{F}_q}$, after completing $Q$ to a category). This forms a finitary abelian category, and hence gives a Hall algebra $\mathscr{H}(Q)$. This Hall algebra has a close relationship with the **quantum group** associated with the Lie algebra, $U_q(\mathfrak{g})$ (Ringel-Green).

Okay, this is interesting, but how are they connected to 2-Segal spaces and 2-Segality? Well some of the origins of 2-Segal spaces came from finding origins of Hall algebras.

Rcall $\mathcal{A}$ is a finitary abelian category, so in particular it is an exact category. Then $S_\bullet(\mathcal{A})$ is a 2-Segal groupoid/space with $S_0(\mathcal{A})$ is the groupoid of $0$ objects, $S_1(\mathcal{A})$ is the groupoid with connected components corresponding to isomorphism classes of objects, and $S_2(\mathcal{A})$ is the groupoid of short exact sequences (and higher extensions for higher $S_n(\mathcal{A})$). Recall that "composition" is defined via the span
$$S_1(\mathcal{A})\times_{S_0(\mathcal{A})}S_1(\mathcal{A})\xleftarrow{(d_2,d_0)}S_2(\mathcal{A})\xrightarrow{d_1}S_1(\mathcal{A})$$
where the left map sends a SES $0\to A\to C\to B\to 0$ to the pair $(A,B)$, and the right map sends it to $C$. Then since $\mathcal{A}$ is finitary, the left map has finite fibers.

For a field $\mathbb{k}$, take finitely-supported functions $\pi_0S_1(\mathcal{A})\to \mathbb{k}$, which defines a $\mathbb{k}$-vector space. We define a multiplication on this vector space using the composition above. Explicitly
$$\mathbb{k}^{\pi_0S_1(\mathcal{A})}_{fin}\times \mathbb{k}^{\pi_0S_1(\mathcal{A})}_{fin} \cong \mathbb{k}^{\pi_0S_1(\mathcal{A})\times \pi_0S_1(\mathcal{A})}_{fin}\xrightarrow{(d_2,d_0)^*}\mathbb{k}^{\pi_0S_2(\mathcal{A})}_{fin}\xrightarrow{(d_1)_!}\mathbb{k}^{\pi_0S_1(\mathcal{A})}$$
where the pullbacks and push-forwards exist by our finitary assumptions. Explicitly, on an element of $f$ on the left, we obtain a map that sends $[C]$ to 
$$\sum_{[S],d_1(S)=[C]}f(d_2,d_0)(S)$$
where the sum is over isomorphism classes of short exact sequences. If $f = (\mathbb{1}_{[A]},\mathbb{1}_{[B]})$, we get $$\sum_{[C]}\sum_{[0\to A\to C\to B\to 0]}\mathbb{1}_{[C]} = \sum_{[C]}g_{AB}^C\mathbb{1}_{[C]}$$
recovering the previous definition.

We can perform this same kind of construction for sufficiently finitary 2-Segal objects $X$ with $X_0 = *$ (if this assumption is dropped you get a $\mathbb{k}$-linear category with object set $X_0$).

>[!def] Hall Algebra for a 2-Segal set
>Let $K$ be a reduced 2-Segal set (i.e. $K_0 = *$), and let $\mathbb{k}$ be a field. The Hall algebra $\mathscr{H}_\mathbb{k}(K)$ is defined as the $\mathbb{k}$-vector space of finitely supported functions $K_1\to \mathbb{k}$, and multiplication given by $\mathbb{1}_a*\mathbb{1}_b = \sum_cg_{ab}^c\mathbb{1}_c$, where $\mathbb{1}_a$ denotes the characteristic function for $a$ and $g_{ab}^c$ is the number of $2$-simplices $z \in K_2$ such that $d_0(z) = b, d_1(z) = c$, and $d_2(z) = a$.

We can recover the previous classical example using isomorphism classes in $2$-Segal groupoids. We can also recover other variants of Hall algebras, for example derived or motivic (Dyckerhoff-Kapranov Higher Segals). You can also retain more structure to get a Hall $(\infty,2)$-category.

>[!example]
>Let $M$ be a partial monoid. Then $\mathscr{H}(M)$ is the algebra which, as a vector space, is spanned by elements of $M$, and multiplication on characteristic elements given by
>$$\mathbb{1}_m*\mathbb{1}_n = \left\{\begin{array}{cc} m\cdot n & \text{if } m,n \in M_2 \\ 0 & \text{otherwise} \end{array}\right.$$
>In this case composition is unique, when it exists, so there are no longer sums or interesting coefficients.

>[!example]
>Let $\mathcal{G}$ be a finite graph. We can define an associated simplicial set $X_\mathcal{G}=: X$ where 
>- $X_0 = \{\emptyset\}$, 
>- $X_1 = \{\text{subgraphs of }\mathcal{G}\}$ 
>- $X_n = \{$subgraphs $H$ of $\mathcal{G}$ equipped with an ordered partition into $n$ possibly empty subsets$\}$ 
>The face maps $X_2\to X_1$, $d_0$ and $d_2$, remove the least (in ordering) or greatest subgraph, respectively, with $d_1$ merging the subgraphs. The degeneracy maps $X_1\to X_2$ add an empty set.

^b6bbe5







