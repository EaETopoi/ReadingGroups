---
date: 2024-07-11T14:09:00
tags:
  - Operads
  - Homotopy
  - CategoryTheory
  - SummerSchool
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

These notes follow the minicourse by Michael Ching (Amherst College) on operads during the 2024 PCMI Undergraduate Faculty Program. The purpose of the minicourse is to introduce the basic theory of operads and their appearances across mathematics.

**Slogan:** Operads are gadgets which encode certain types of algebraic structure

This slogan is quite vague, but will be a guiding principle for our investigation of operads. Let us witness this through a simple, and classical example, of monoids.

>[!example] Monoids
>The structure of a monoid is given by an underlying set, $M$, a binary operation $*:M\times M\to M$, and a specified element $e \in M$, under the relations describing associativity and left and right unity. A monoid is a type of algebraic structure, and so we should be able to encode it as an operad $\underline{\text{Mon}}$.

>[!example] Lie Algebras
>The structure of a lie algebra, over a field $k$, consists of a $k$-vector space $V$, a binary operation
>$$[,]:V\otimes_kV\to V$$
>satisfying anti-symmetry $[x,y] = -[y,x]$ (or equivalently, $[x,x] = 0$, which works better if $\text{char}(k) = 2$), and the Jacobian condition $[[x,y],z] + [[y,z],x]+[[z,x],y] = 0$ for all $x,y,z \in V$. This will be encoded by an operad $\underline{\mathsf{Lie}}$.

>[!example] Loop Spaces
>If $X$ is a topological space (with basepoint), we have the topological **loop space** $$\Omega X := \underline{\mathsf{Top}_*}(S^1,X)$$
>with compact open topology. There is an operad $E_1$, or $A_\infty$, which encodes the "structure" of a loop space in some precise way.

Although these are great examples of ways operads can be used to encode algebraic structure, it turns out that not all structures can be encoded in this way. For example, the structure of groups cannot be encoded as operads cannot account for inverses.

More general ways to encode these types of structures is
1. **Algebraic/Lawvere theories**
2. **Monads**

Another example, from combinatorics now, is the **Motzkin word**, which is a finite sequence of natural numbers, which later we will see forms an operad.

In addition to those describe above, operads can also encode the following structures over a commutative ring $R$:
1. $\mathsf{As}$: operad of associative $R$-algebras
2. $\mathsf{Com}$: operad of commutative $R$-algebras.
3. $\mathsf{Lie}$: operad of Lie-algebras over $R$
4. $\mathsf{Pois}$: operad of Poisson algebras over $R$

For some of these algebraic operads we have a kind of **Koszul duality**, where $\mathsf{As}$ and $\mathsf{Pois}$ are self-dual, while $\mathsf{Com}$ and $\mathsf{Lie}$ are dual.
### Operad Cohomology

We can define cohomology over an operad $P$ with respect to an object $A$ with structure encoded by the operad $P$, namely a $P$-algebra. We refer to this cohomology as $H^*_P(A)$.

For example, if $P = \mathsf{As}$ this is **Hochschild cohomology**, if $P = \mathsf{Com}$ this is **Andre-Quillen cohomology**, and $P = \mathsf{Lie}$ gives the **Chevalley-Eilenberg cohomology**.

### $A_\infty$-spaces (Stasheff, 1963)

Let $Y$ be a topological space together with a continuous binary operation $*:Y\times Y\to Y$. Further, suppose we have a *interval of $3$-ary operations*, namely a continuous map
$$[0,1]\times Y^3\to Y$$
which provides a homotopy between the composites $(x,y,z)\mapsto x*(y*z)$ and $(x,y,z)\mapsto (x*y)*z$. We can also have higher homotopies of $n$-ary operations. For example, in the case of $n = 4$ let $K_4$ be the pentagon and $K_4\times Y^4\to Y$ is a kind of homotopy that has the following geometric form going between different composites

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%26%20%7B(xy)(zw)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B((xy)z)w%7D%20%26%26%26%26%20%7Bx(y(zw))%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%20%7B(x(yz))w%7D%20%26%26%20%7Bx((yz)w)%7D%0A%09%5Carrow%5Bno%20head%2C%20from%3D1-3%2C%20to%3D3-5%5D%0A%09%5Carrow%5Bno%20head%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bno%20head%2C%20from%3D3-1%2C%20to%3D5-2%5D%0A%09%5Carrow%5Bno%20head%2C%20from%3D5-2%2C%20to%3D5-4%5D%0A%09%5Carrow%5Bno%20head%2C%20from%3D5-4%2C%20to%3D3-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp;&amp; {(xy)(zw)} \\
	\\
	{((xy)z)w} &amp;&amp;&amp;&amp; {x(y(zw))} \\
	\\
	&amp; {(x(yz))w} &amp;&amp; {x((yz)w)}
	\arrow[no head, from=1-3, to=3-5]
	\arrow[no head, from=3-1, to=1-3]
	\arrow[no head, from=3-1, to=5-2]
	\arrow[no head, from=5-2, to=5-4]
	\arrow[no head, from=5-4, to=3-5]
\end{tikzcd}
" /></p>

where the homotopy fills the pentagon. In general, we ask for a homotopy
$$K_n\times Y^n\to Y$$
where $K_n$ is some topological $m(n)$-gon, where $m(n)$ is the number of ways we can associate $n$-elements into pairs.

This data defines the structure of an operad. 

>[!example] Loop Space
>The loop space $\Omega X$ is an $A_\infty$-space where $\Omega X\times \Omega X\to \Omega X$ is composition of loops, $[0,1]\times (\Omega X)^3\to \Omega X$ is the associator homotopy for $3$ elements, and the higher such associators are given similarly.

## $\mathsf{Set}$-operads

### Commutative Monoids

A view of commutative monoids that will be helpful for the translation to operads is the following: A commutative monoid $(A,*,e)$ can be thought of as monoids where there is exactly **one** way to multiply any finite sequence of elements, 
$$m_n:A^n\to A;\;m_n(x_1,\dots,x_n) = x_1*\cdots *x_n$$
>[!def] Commutative Monoid Def 2
>A commutative monoid is a set $A$ together with, for all $n\geq 0$, a map $m_n:A^n\to A$ such that
>1. $m_1 = \text{id}_A$
>2. $m_n\circ \sigma^* = m_n$ for any $\sigma \in \Sigma_n$
>3. For any $n_1,...,n_k \geq 0$, $$m_k(m_{n_1}(x_1^1,\dots,x_{n_1}^1),\dots,m_{n_k}(x_1^k, \dots,x_{n_k}^k))=m_{n_1+\cdots +n_k}(x_1^1, \dots, x_{n_1}^1, \dots, x_1^k, \dots, x_{n_k}^k)$$

### Monoids

>[!def] Monoid Def 2
>A monoid is a set $A$ together with, for each $n\geq 0,\sigma \in \Sigma_n$, an operation $$m_\sigma:A^n\to A$$
>such that
>1. $m_1 = \text{id}_A$ where $1 \in \Sigma_1$ is the identity permutation
>2. for all $\sigma,\tau \in \Sigma_n$, $$m_\sigma(x_{\tau^{-1}(1)},...,x_{\tau^{-1}(n)}) = m_{\sigma\tau}(x_1,\dots,x_n)$$
>3. For $\sigma \in \Sigma_k$, and $\tau_i \in \Sigma_{n_i}$, $1\leq i \leq k$, we have $$m_\sigma(m_{\tau_1}(x_1^1,\dots,x_{n_1}^1),\dots,m_{\tau_k}(x_1^k, \dots,x_{n_k}^k))=m_{\sigma\circ (\tau_1,\dots,\tau_k)}(x_1^1, \dots, x_{n_1}^1, \dots, x_1^k, \dots, x_{n_k}^k)$$

>[!def] Monoid Def 3
>A monoid is a set $A$ together with, for all $n\geq 0$, a map $m_n:A^n\to A$ such that
>1. $m_1 = \text{id}_A$
>2. For any $n_1,...,n_k \geq 0$, $$m_k(m_{n_1}(x_1^1,\dots,x_{n_1}^1),\dots,m_{n_k}(x_1^k, \dots,x_{n_k}^k))=m_{n_1+\cdots +n_k}(x_1^1, \dots, x_{n_1}^1, \dots, x_1^k, \dots, x_{n_k}^k)$$

These two definitions of monoids relate to two different kinds of operads, namely symmetric and non-symmetric operads.

>[!example] Magma
>A magma can be described as a set $A$ with a unary operation, $m_1:A\to A$, the identity, a binary operation $m_2:A^2\to A$, two $3$-ary operations, based on different associates. In general, we have $m(n)$ $n$-ary operations indexed by planar binary rooted trees with $n$ leaves which correspond to binary associates of brackets for lists of $n$ elements.
>
>such that
>1. $m_1 = \text{id}_A$
>2. for a tree $T$ with $k$-leaves, and $u_i$, $1\leq i \leq k$, a tree with $n_i$ leaves,
>$$m_T(m_{u_1}(-),\cdots,m_{u_k}(-)) = m_{T\cdot(u_1,\dots,u_k)}(-,\cdots,-)$$ where $T\cdot(u_1,...,u_k)$ is obtained by **"grafting" trees**.

### Non-Symmetric, $\mathsf{Set}$-, Monochromatic Operads

We now begin giving explicit definitions of basic operads.

>[!def] $\mathsf{Set}$-Operads
>A **$\mathsf{Set}$-operad** $P$ consists of:
>1. A set $P(n)$, for each $n\geq 0$
>2. A specified element $\iota \in P(1)$
>3. For each finite sequence $n_1,...,n_k \geq 0$, a function $$\mu_{n_1,\dots,n_k}:P(k)\times P(n_1)\times \cdots \times P(n_k)\to P(n_1+\cdots+n_k)$$
>$$(\alpha,\beta_1,\dots,\beta_k) = \alpha(\beta_1,\dots,\beta_k)$$
>such that
>1. $\iota(\alpha) = \alpha = \alpha(\iota,...,\iota)$ for any $\alpha \in P(k)$, where the left is given by applying $\mu_k:P(1)\times P(k)\to P(k)$ and the right is given by applying $\mu_{1,...,1}:P(k)\times P(1)\times \cdots \times P(1)\to P(k)$.
>2. For $\alpha \in P(k)$, $\beta_i \in P(n_i)$, $1 \leq i \leq k$, and $\gamma_i^j \in P(m_{i,j})$ for $1 \leq j \leq k$, $1 \leq i \leq n_j$, we have
>   $$\alpha(\beta_1(\gamma_1^1,\dots,\gamma_{n_1}^1), \dots,\beta_k(\gamma_1^k, \dots,\gamma_{n_k}^k)) = [\alpha(\beta_1,\dots,\beta_k)](\gamma_1^1,\dots\dots,\gamma_{n_k}^k)$$
>which live in $P\left(\sum_{j=1}^k\sum_{i=1}^{n_i}m_{i,j}\right)$.

This last condition in the definition of an operad corresponds to a commuting square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%5Cbegin%7Barray%7D%7Bc%7D%20P(k)%5Ctimes%20%5Cleft(P(n_1)%5Ctimes%5Cleft(%5Cbegin%7Barray%7D%7Bc%7D%20P(m_%7B1%2C1%7D)%20%5C%5C%20P(m_%7B2%2C1%7D)%20%5C%5C%20%5Cvdots%20%5C%5C%20P(m_%7Bn_1%2C1%7D)%20%5Cend%7Barray%7D%5Cright)%5Cright)%5Ctimes%20%5Ccdots%20%5Ctimes%20%5Cleft(P(n_k)%5Ctimes%5Cleft(%5Cbegin%7Barray%7D%7Bc%7D%20P(m_%7B1%2Ck%7D)%20%5C%5C%20P(m_%7B2%2Ck%7D)%20%5C%5C%20%5Cvdots%20%5C%5C%20P(m_%7Bn_k%2Ck%7D)%20%5Cend%7Barray%7D%5Cright)%5Cright)%20%5Cend%7Barray%7D%20%26%26%20%7BP(k)%5Ctimes%20P(m_%7B1%2C1%7D%2B%5Ccdots%20%2Bm_%7Bn_1%2C1%7D)%5Ctimes%20%5Ccdots%20%5Ctimes%20P(m_%7B1%2Ck%7D%2B%5Ccdots%20%2Bm_%7Bn_k%2Ck%7D)%7D%20%5C%5C%0A%09%5C%5C%0A%09%5Cbegin%7Barray%7D%7Bc%7D%20P(n_1%2B%5Ccdots%2Bn_k)%5Ctimes%20%5Cleft(%5Cbegin%7Barray%7D%7Bc%7D%20P(m_%7B1%2C1%7D)%20%5C%5C%20P(m_%7B2%2C1%7D)%20%5C%5C%20%5Cvdots%20%5C%5C%20P(m_%7Bn_1%2C1%7D)%20%5Cend%7Barray%7D%5Cright)%5Ctimes%20%5Ccdots%20%5Ctimes%20%5Cleft(%5Cbegin%7Barray%7D%7Bc%7D%20P(m_%7B1%2Ck%7D)%20%5C%5C%20P(m_%7B2%2Ck%7D)%20%5C%5C%20%5Cvdots%20%5C%5C%20P(m_%7Bn_k%2Ck%7D)%20%5Cend%7Barray%7D%5Cright)%20%5Cend%7Barray%7D%20%26%26%20%7BP(m_%7B1%2C1%7D%2B%5Ccdots%2Bm_%7Bn_k%2Ck%7D)%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	\begin{array}{c} P(k)\times \left(P(n_1)\times\left(\begin{array}{c} P(m_{1,1}) \\ P(m_{2,1}) \\ \vdots \\ P(m_{n_1,1}) \end{array}\right)\right)\times \cdots \times \left(P(n_k)\times\left(\begin{array}{c} P(m_{1,k}) \\ P(m_{2,k}) \\ \vdots \\ P(m_{n_k,k}) \end{array}\right)\right) \end{array} &amp;&amp; {P(k)\times P(m_{1,1}+\cdots +m_{n_1,1})\times \cdots \times P(m_{1,k}+\cdots +m_{n_k,k})} \\
	\\
	\begin{array}{c} P(n_1+\cdots+n_k)\times \left(\begin{array}{c} P(m_{1,1}) \\ P(m_{2,1}) \\ \vdots \\ P(m_{n_1,1}) \end{array}\right)\times \cdots \times \left(\begin{array}{c} P(m_{1,k}) \\ P(m_{2,k}) \\ \vdots \\ P(m_{n_k,k}) \end{array}\right) \end{array} &amp;&amp; {P(m_{1,1}+\cdots+m_{n_k,k})}
	\arrow[from=1-1, to=1-3]
	\arrow[from=1-1, to=3-1]
	\arrow[from=1-3, to=3-3]
	\arrow[from=3-1, to=3-3]
\end{tikzcd}
" /></p>

>[!example]
>0. Sets with no structure: Take $P(n) = \emptyset$ for $n \geq 1$ and $P(1) = \{\iota\}$.
>1. Sets with a chosen element: $P(0) = \{e\}$, $P(1) = \{\iota\}$, $P(n) = \emptyset$ for $n \geq 2$
>2. Monoids: $P(n) = \{m_n\}$ for all $n \geq 0$, $\iota = m_1$, (the axioms give operad conditions)
>3. Magmas: $P(n) = \{$planar binary rooted trees with $n$-leaves, $\iota \in P(1)$ being the tree represented by a line, and $P(k)\times P(n_1)\times \cdots \times P(n_k)\to P(n_1+\cdots +n_k)$ is given by **grafting trees**.
>4. Motzkin words: 
>5. Diassociative monoids (set with two associative binary operations satisfying some conditions)


#### Partial Composition Maps for Operads

We can provide an alternative approach to our previous definition of operads using a notion of partial composition. Throughout, let $P$ be an operad. Take $\alpha \in P(k)$ and $\beta \in P(n)$, and let $1 \leq j \leq k$. Then we can define 
$$\alpha\circ_j\beta = \alpha(\iota,\cdots,\iota,\beta,\iota, \cdots,\iota) \in P(k+n-1)$$
so we get
$$\circ_j:P(k)\times P(n)\to P(k+n-1)$$
which we refer to as **partial composition maps**. If $P$ is not an operad over a concrete category, such as an operad over some monoidal category, we can define 
$$\circ_j:P(k)\otimes P(n)\to P(k+n-1)$$
in terms of certain commutative diagrams. In either case, we can define operads, instead of using the previous complex multiple variable composition using these partial composition maps, and their successive composites.

Using this partial composition perspective we can more easily describe morphisms of operads, giving us a categorical structure for operads.

>[!def] Morphisms of Operads
>An **operad morphism** $\phi:P\to Q$ is a collection of functions $\phi_n:P(n)\to Q(n)$ such that
>1. $\phi_1(\iota_P) = \iota_Q$
>2. $\phi_k(\alpha)\circ_j\phi_n(\beta) = \phi_{k+n-1}(\alpha\circ_j\beta)$ for $1 \leq j \leq k$ and $\alpha \in P(k),\beta \in P(n)$


>[!example]
>Consider $\phi:\underline{\mathsf{SemiGrp}}\to \underline{\mathsf{Mon}}$ where $\phi_0:\emptyset\to \{*\}$, and $\phi_n:\{*\}\to \{*\}$ for all $n > 0$.

In fact, considering the example above the operad $\underline{\mathsf{Mon}}$ is the terminal object in the category of $\mathsf{Set}$-operads.

### Algebras Over an Operad

From our slogan, operads encode algebraic structure, but how do we implement these structures? This is done using algebras over operads.
## Theory of Operads
### Operads of $G$-Sets

Throughout, let $G$ be a monoid and let $P$ be the operad with 
$P(1) = G$, $P(n) = \emptyset$ for $n \neq 1$, $\iota = e_G \in P(1)$, and 
$$P(1)\times P(1)\xrightarrow{\mu_1}P(1)$$
with $\mu_1 = \cdot_G$. In this way, we can identify monoids with operads where $P(n) = \emptyset$ for $n \neq 1$. In fact, for any operad, $P(1)$ will be a monoid.

For this operad, $P$-algebras are precisely $G$-sets. 

#### Transfer of Structure Between Operads


One thing we would like to do with morphisms between operads is to perform a kind of **base-change**, or **structure-transfer**, between algebras in one operad and algebras in a second operad.

>[!def] Transfer of Structure
>Let $\phi:P\to Q$ be an operad morphism, and let $A$ be a $Q$-algebra. Define a $P$-algebra with the same underlying set $A$ such that
>$$m_n^P(\alpha,x_1,\dots,x_n) := m_n^Q(\phi(\alpha),x_1,\dots,x_n)$$
>which is a pullback.

>[!example]
>Any monoid has a $P$ algebra structure for any operad $P$, since the operad of monoids is final in the category of $\mathsf{Set}$-operads. Applying this pullback of $\mathbb{N}$ under $+$ is a **Motz**-algebra, where $m\star n = m+n$, and $[\ell,m,n] = \ell+m+n$.



#### References