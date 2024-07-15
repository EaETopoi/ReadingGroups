---
date: 2024-06-26T00:10:00
tags:
  - InfinityCategories
  - CategoryTheory
  - HigherCategories
  - Simplicial
  - Homotopy
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

In this note we begin to introduce the basic theory of quasi-categories following [Kerodon](https://kerodon.net/)[^1]. The definition of quasi-categories will be that of simplicial sets satisfying certain lifting properties, extending that of spaces in [[Topological Spaces to Simplicial Sets]] and that of categories in [[Categories and Simplicial Sets]]. Namely, we have the following generalization:

>[!def] Quasi-categories
>A **quasi-category** is a simplicial set $S_\bullet$ satisfying the following:
>- Every inner horn in $S_\bullet$ extends (not necessarily uniquely) to an $n$-simplex in $S_\bullet$

^c9ac7c

We sometimes refer to the condition in [[Introduction to Quasi-Categories#^c9ac7c]] as the **weak Kan extension condition**, introduced by Boardman and Vogt with quasi-categories being under the name of **weak Kan complexes**. The **quasi-category** terminology is due to Joyal who developed much of the foundational theory, while more recent developments by Lurie has popularized the term **$\infty$-categories**.

Note that every Kan complex and every nerve of a category is a quasi-category. Note that since the condition for a quasi-category is defined in terms of a lifting criterion for maps into the simplicial set, products of quasi-categories are again quasi-categories.

On the other hand, coproducts are also quasi-categories, although this is more subtle and uses the theory of connectedness of simplicial sets in [[Topological Spaces to Simplicial Sets#^427e97]].

## Basic Properties of Quasi-Categories

If $\mathcal{C} := S_\bullet$ is a quasi-category, an **object** of $\mathcal{C}$ refers to a $0$-simplex $x \in S_0$. On the other hand, a **morphism** of $\mathcal{C}$ is a $1$-simplex $\sigma:x\to y$ in $S_1$, where $d_0^1\sigma = y$ and $d_1^1\sigma = x$. Further, for any object $x$, the degenerate $1$-simplex $s_0^0(x)$ can be identified as the **identity morphism of $x$**, $1_x$ or $\text{id}_x$. If $\mathcal{C}$ is $N_\bullet(\mathcal{D})$ for some ordinary category $\mathcal{D}$, then these notions coincide with those in $\mathcal{D}$.

On the other hand, if $\mathcal{C} = \text{Sing}_\bullet(X)$ for a topological space $X$, the objects correspond to points, the morphisms correspond to continuous paths, and the identity morphism corresponds to the constant path.

### Opposite Quasi-category

As with ordinary categories, we can take the **opposite quasi-category**. To perform this construction first let $\text{Lin}$ denote the category of finite linearly ordered sets with non-decreasing functions as morphisms. Note that $\mathbb{\Delta}$ is a full subcategory of $\text{Lin}$. Then for an object $I$ in $\text{Lin}$, we have a natural opposite object $I^{op}$ obtained by reversing the linear order. This defines a functor $(-)^{op}:\text{Lin}\to \text{Lin}$ which is an involution (and so in particular an automorphism of $\text{Lin}$). Although $\mathbb{\Delta}$ is not stable under this involution, we have a unique functor $\text{Op}:\mathbb{\Delta}\to \mathbb{\Delta}$ which is compatible with $(-)^{op}$ up to an isomorphism.

In particular, $\text{Op}$ is an identity on objects functor such that for $\alpha:[m]\to [n]$, $\text{Op}(\alpha):[m]\to [n]$ is given by $\text{Op}(\alpha)(i) = n-\alpha(m-i)$. Note that if $i \leq j$, $m-j\leq m-i$ so $\alpha(m-j)\leq \alpha(m-i)$ and
$$\text{Op}(\alpha)(i) = n-\alpha(m-i)\leq n-\alpha(m-j)=\text{Op}(\alpha)(j)$$
so this functor is well-defined and evidently functorial. Observe that $[n]^{op} = \{0 > 1 > \cdots > n\}$, so we have the isomorphism $[n]^{op}\to [n]$ given by sending $i$ to $n-i$. This isomorphism gives a natural isomorphism $(-)^{op}\circ \iota \Rightarrow \iota\circ \text{Op}$ since for any $\alpha:[m]\to [n]$ and any $i \in [m]$, one direction maps $i\mapsto \alpha(i)\mapsto n-\alpha(i)$, while the other maps $i\mapsto m-i\mapsto n-\alpha(m-(m-i)) = n-\alpha(i)$.

>[!def] Opposite Simplicial Set
>Let $S_\bullet:\mathbb{\Delta}^{op}\to \mathsf{Set}$ be a simplicial set. Then we define its opposite, $S_\bullet^{op}$, as the composite $$\mathbb{\Delta}^{op}\xrightarrow{Op}\mathbb{\Delta}^{op}\xrightarrow{S_\bullet}\mathsf{Set}$$

Note that if $S_\bullet$ is a simplicial set, $S_n^{op} = S_n$, and for $f:[m]\to [n]$, $S_\bullet^{op}(f) = S_\bullet(\text{Op}(f))$. Note that $\text{Op}(\delta^i_n)$ sends $0\leq j \leq n-1$ to $n-\delta^i_n(n-1-j)$, which if $n-1-j \leq i-1$ is $n-(n-1-j) = j+1$, and if $n-1-j \geq i$ is $n-(n-j) = j$. Equivalently, we have that if $j\geq n-i$ then $j\mapsto j+1$, and if $j < n-i$ then $j\mapsto j$. Thus, $\text{Op}(\delta^i_n) = \delta^{n-i}_n$. Similarly, $\text{Op}(\eta_n^i) = \eta_n^{n-i}$, so
$$S_\bullet^{op}(\delta_n^i) = S_\bullet(\delta_n^{n-i})\;\;\text{ and }\;\;S_\bullet^{op}(\eta_n^i) = S_\bullet(\eta_n^{n-i})$$

Now, consider a category $\mathcal{C}$ and its nerve $N_\bullet(\mathcal{C})$. Note that $N_\bullet(\mathcal{C}^{op})$ swaps the direction of the sequence of maps. Due to this we have a natural isomorphism $N_\bullet(\mathcal{C})^{op}\cong N_\bullet(\mathcal{C}^{op})$, so our definition of the opposite simplicial set is compatible with the notion of opposites of ordinary categories.

>[!rmk]
>We have a canonical isomorphism $\text{Sing}_\bullet(X)\cong \text{Sing}_\bullet(X)^{op}$ which sends a singular $n$-simplex $\sigma:|\Delta^n|\to X$ to the singular $n$-simplex obtained by pre-composing with the homeomorphism $r:|\Delta^n|\to |\Delta^n|$ given by $r(t_0,...,t_n) = (t_n,...,t_0)$. Note that $r$ corresponds to the isomorphism $[n]^{op}\cong [n]$ given by $r(i) = n-i$.

We now show that the opposite simplicial complex construction restricts to an involution on the category of quasi-categories.

>[!proposition] Opposite Quasi-Category
>If $\mathcal{C}$ is a quasi-category then so is $\mathcal{C}^{op}$.

`\begin{proof}`
Let $\sigma_0:\Lambda_i^n\to \mathcal{C}^{op}$ be an inner horn. Taking opposite simplicial sets we obtain a map $\sigma_0^{op}:(\Lambda_i^n)^{op}\to \mathcal{C}$. Observe that our previous work gives a unique isomorphism $(\Delta^n)^{op}\cong \Delta^n$ given by sending $f:[m]\to [n]$ to $\text{Op}(f):[m]\to [n]$, which is a map of simplicial sets since for any $g:[k]\to [m]$, $$\text{Op}((\Delta^n)^{op}(g)(f)) = \text{Op}(f\circ \text{Op}(g)) = \text{Op}(f)\circ g = (\Delta^n)(g)(\text{Op}(f))$$
as claimed. Further, this isomorphism carries $(\Lambda_i^n)^{op}$ to $\Lambda_{n-i}^n$, which is still an inner horn, so our map becomes $\sigma_0^{op}:\Lambda_{n-i}^n\to \mathcal{C}$, which has a lift $\sigma^{op}:\Delta^n\to \mathcal{C}$, and hence $\sigma^{op}:(\Delta^n)^{op}\to \mathcal{C}$, and applying $(-)^{op}$ again gives our desired lift $\sigma:\Delta^n\to \mathcal{C}^{op}$.
`\end{proof}`

Note that when interpreting $\mathcal{C}^{op}$ categorically, the objects of $\mathcal{C}^{op}$, i.e. its $0$-simplices, are the same as that of $\mathcal{C}$. On the other hand, a morphism $\sigma:\Delta^1\to \mathcal{C}^{op}$ from $x$ to $y$ satisfies $x = \sigma\cdot \text{Op}(d_1^1) = \sigma\cdot d_0^1$ and $y = \sigma\cdot \text{Op}(d_0^1) = \sigma\cdot d_1^1$. Thus, $\sigma$ corresponds to a morphism $\Delta^1\to \mathcal{C}$ from $y$ to $x$.

Note that an identical proof to that above also shows that Kan complexes are preserved by taking the opposite simplicial set.


### Homotopies in Quasi-Categories

Note that for any topological space $X$, $\text{Sing}_\bullet(X)$ is a Kan complex, and hence a quasi-category, with objects being points and a morphism between points $x,y \in X$ being a path $f:[0,1]\to X$ such that $f(0) = x$ and $f(1) = y$. In this setting we can discuss homotopy classes of paths, which is often preferred when studying objects such as the fundamental group $\pi_1(X,x)$.

We now generalize this to quasi-categories more broadly.

>[!def] Homotopies in Quasi-categories
>Let $\mathcal{C}$ be a quasi-category and let $f,g:c\to d$ be a pair of morphisms in $\mathcal{C}$ (i.e. $1$-simplices $f,g:\Delta^1\to \mathcal{C}$ with $d_0^1f,d_0^1g = d$ and $d_1^1f,d_1^1g = c$). A **homotopy from $f$ to $g$** is a $2$-simplex $\sigma$ of $\mathcal{C}$ satisfying $d_0^2(\sigma) = \text{id}_d$, $d_1^2(\sigma) = g$, and $d_2^2(\sigma) = f$. When such a homotopy exists we will say that $f$ and $g$ are **homotopic**.

Note that in an ordinary category all homotopies are trivial in the sense that two morphisms are homotopic if and only if they are equal. On the other hand, the above definition coincides with the notion of a path homotopy between $f,g:[0,1]\to X$ when dealing with the quasi-category of singular simplices in $X$. We can make this equivalence explicit using the homeomorphism $\pi:[0,1]\times [0,1]\to |\Delta^2|$, where $\pi(s,t) = (1-s,(1-t)s,ts)$.


The definition of homotopies in quasi-categories given above can be considered in any simplicial set. However, the importance of quasi-categories comes in the fact that in general this is not an equivalence relation on the set of morphisms with common domain and codomain, but it is when dealing with quasi-categories.

>[!proposition] Equivalence Relation for Quasi-categories
>Let $\mathcal{C}$ be a quasi-category with objects $x,y \in \mathcal{C}_0$. Let $E \subseteq \mathcal{C}_1$ denote the set of all morphisms $f:x\to y$ in $\mathcal{C}$. Then the relation of homotopy is an equivalence relation on $E$.

^cbf6e4

`\begin{proof}`
First let $f:x\to y$. Consider the degenerate $2$-simplex $f\cdot s_1^1$ which has face maps $f\cdot s_1^1\cdot d_0^2 = f\cdot d_0^1\cdot s_0^0 = y\cdot s_0^0 = \text{id}_y$, $f\cdot s_1^1\cdot d_1^2 = f$ and $f\cdot s_1^1\cdot d_2^2 = f$. Thus, $f\cdot s_1^1$ is a homotopy from $f$ to itself, so the relation $E$ is reflexive.

To prove symmetry and transitivity it suffices to show that for morphisms $f,g,h:x\to y$, if $f\sim g$ and $f\sim h$ then $g\sim h$. Now, let $\sigma_2,\sigma_3:\Delta^2\to\mathcal{C}$ be the $2$-simplices witnessing the homotopies from $f$ to $h$ and $f$ to $g$, respectively. Let $\sigma_0 = y\cdot s_0^0\cdot s_0^1$, which is the constant $2$-simplex with all boundaries $\text{id}_y$. Then the tuple $(\sigma_0,-,\sigma_2,\sigma_3)$ satisfies the necessary boundary conditions to determine a map of simplicial sets $\tau_0:\Lambda_1^3\to \mathcal{C}$, guaranteed by [[Topological Spaces to Simplicial Sets#^f48f55]]. Now, since $\mathcal{C}$ is a quasi-category and $\tau_0$ is an inner horn, we can extend to a $3$-simplex $\tau:\Delta^3\to \mathcal{C}$ such that the $2$-simplex $\tau\circ \delta^3_1$ has $\tau\circ \delta^3_1\circ \delta^2_0 = \text{id}_y$, $\tau\circ \delta^3_1\circ \delta^2_1 = h$, and $\tau\circ \delta_1^3\circ \delta_2^2 = g$, so $\tau\circ \delta_1^3$ is our desired homotopy.
`\end{proof}`

Now, how do homotopies play out in the opposite category?

>[!proposition] Homotopies in Opposite Category
>Let $\mathcal{C}$ be a quasi-category and let $f,g:x\to y$ be morphisms in $\mathcal{C}$. Then $f$ and $g$ are homotopic in $\mathcal{C}$ if and only if, when regarded as morphisms of the opposite quasi-category $\mathcal{C}^{op}$, they are homotopic. Hence, the following are equivalent:
>1. There exists a $2$-simplex $\sigma:\Delta^2\to \mathcal{C}$ such that $d_0^2(\sigma) = \text{id}_y$, $d_1^2(\sigma) = g$, and $d_2^2(\sigma) = f$.
>2. There exists a $2$-simplex $\tau:\Delta^2\to \mathcal{C}$ such that $d_0^2(\tau) = f$, $d_1^2(\tau) = g$, and $d_2^2(\tau) = \text{id}_x$.

^a46df9

`\begin{proof}`
First let us prove **(1)** implies **(2)**. Let $\sigma:\Delta^2\to \mathcal{C}$ be a homotopy from $f$ to $g$ in $\mathcal{C}$. Then we have a homotopy $\sigma_0:\Delta^2\to \mathcal{C}$ from $g$ to $f$, witnessing the symmetry of the relation. On the other hand, $s_1^1(g)$ denotes the homotopy from $g$ to itself, while $s_0^1(g)$ is the homotopy from $g$ to itself in $\mathcal{C}^{op}$. This data $(\sigma_0,s_1^1(g),-,s_0^1(g))$ determines an inner horn $\rho_0:\Lambda_2^3\to \mathcal{C}$. Since $\mathcal{C}$ is a quasi-category we can extend to a $3$-simplex $\rho:\Delta^3\to \mathcal{C}$, where the $2$-simplex $\rho\circ \delta_2^3$ is our desired homotopy from $f$ to $g$ in $\mathcal{C}^{op}$.

The reverse direction is symmetric since $\mathcal{C}$ is the opposite quasi-category of $\mathcal{C}^{op}$, since $\text{Op}$ is an involution.
`\end{proof}`

We can now recontextualize the notion of homotopy. To do this we should first understand the product simplicial set $\Delta^1\times \Delta^1$. I claim that this product is equivalent to the coproduct $\Delta^2\cup_{\Delta^1}\Delta^2$. From [[Quasi-Categories Preliminaries#^6fc0d8]] we have two non-degenerate $2$-simplices in $\Delta^1\times \Delta^1$, namely $\sigma_1=(001,011)$ and $\sigma_2=(011,001)$. Further, the non-degenerate $1$-simplices are $\{(01,00), (01,11), (00,01), (11,01), (01,01)\}$, which are all faces of $\sigma_1$ and $\sigma_2$. Finally, the non-degenerate $0$-simplices are $\{(0,0),(0,1),(1,0),(1,1)\}$, i.e. all the $0$-simplices are non-degenerate, as always. Further, pulling back along $\delta^2_1:\Delta^1\to \Delta^2$, both $2$-simplices become the $1$-simplex $\sigma_1\circ \delta_1^2 = (01,01) = \sigma_2\circ \delta_1^2$, so $\Delta^1\times \Delta^1$ is a candidate for the pushout of $\delta_1^2$ along itself.

Suppose we have $f:\Delta^2\to S_\bullet$ and $g:\Delta^2\to S_\bullet$ such that $f\circ \delta_1^2 = g\circ \delta_1^2$. Then define $h:\Delta^1\times \Delta^1\to S_\bullet$ by specifying $h((001,011)) = f(1_{[2]})$ and $h((011,001)) = g(1_{[2]})$. Since all faces, and faces of faces, of these 2-simplices are non-degenerate, it suffices to show that $h$ commutes with face maps by [[Quasi-Categories Preliminaries#^f585d6]]. Observe that this follows from the fact that $f\circ \delta_1^2 = g\circ \delta_1^2$. Thus, $h$ is uniquely defined, and so
$$\Delta^1\times \Delta^1\cong \Delta^2\cup_{\Delta^1}\Delta^2$$


>[!corollary] Symmetric Form of Homotopy
>Let $f,g:x\to y$ be morphisms in a quasi-category $\mathcal{C}$. Then $f$ and $g$ are homotopic if and only if there exists a map of simplicial sets $H:\Delta^1\times \Delta^1\to \mathcal{C}$ such that $H\vert_{\{0\}\times\Delta^1}=f$, $H\vert_{\{1\}\times\Delta^1} = g$, $H\vert_{\Delta^1\times\{0\}}=\text{id}_x$, and $H\vert_{\Delta^1\times\{1\}}=\text{id}_y$.

^ac0ab1

`\begin{proof}`
Suppose first that $\sigma$ is a homotopy from $f$ to $g$. Then we can obtain $H$ as the gluing of $\sigma$ with the homotopy from $g$ to itself in $\mathcal{C}^{op}$, using the fact that $\Delta^1\times \Delta^1\cong \Delta^2\cup_{\Delta^1}\Delta^2$.

On the other hand, suppose we have such a simplicial set $H:\Delta^1\times \Delta^1\to \mathcal{C}$. Then this determines a homotopy from $f$ to $h$ in $\mathcal{C}$ and a homotopy from $h$ to $g$ in $\mathcal{C}^{op}$, where $h$ is the morphism corresponding to the diagonal in $H$. By [[Introduction to Quasi-Categories#^a46df9]] and [[Introduction to Quasi-Categories#^cbf6e4]] we obtain a homotopy from $f$ to $g$, as desired.
`\end{proof}`


### Composition of Morphisms

Now that we understand how homotopies of morphisms play out in quasi-categories, we can begin introducing other notions we would want from categorical structures, such as composition.

>[!def] Composition in Quasi-Categories
>Let $\mathcal{C}$ be a quasi-category with morphisms $f:x\to y,g:y\to z$, and $h:x\to z$. We say that $h$ is **a composite** of $f$ and $g$ if there exists a $2$-simplex $\sigma$ of $\mathcal{C}$ such that $d_0^2(\sigma) = g$, $d_1^2(\sigma) = h$, and $d_2^2(\sigma) = f$. In this case we say the $2$-simplex $\sigma$ **witnesses $h$** as a composition of $f$ and $g$.

As we shall now show, due to the inner horn filling property quasi-categories always have composites, and these composites are defined up to homotopy.

>[!proposition] Existence and Uniqueness up to Homotopy of Composites
>Let $f:x\to y$ and $g:y\to z$ be morphisms in a quasi-category $\mathcal{C}$. Then:
>1. There exists a $h:x\to z$ witnessing the composition of $f$ and $g$
>2. If $h':x\to z$ is another map, then $h'$ witnesses the composition of $f$ and $g$ if and only if it is homotopic to $h$.

^972080

`\begin{proof}`
Property **(1)** follows from the fact that $f$ and $g$ determine an inner horn $\Lambda_1^2\to \mathcal{C}$, which extends to a $2$-simplex since $\mathcal{C}$ is a quasi-category.

Now, let $\sigma:\Delta^2\to \mathcal{C}$ be such that $d_0^2(\sigma) = g$, $d_1^2(\sigma) = h$, and $d_2^2(\sigma) = f$, and let $h':x\to z$ be another morphism. First suppose $\sigma':\Delta^2\to \mathcal{C}$ is a $2$-simplex witnessing the composite of $f$ and $g$ being $h'$. Then the triple $(s_1^1(g),-,\sigma',\sigma)$ defines an inner horn $\tau_0:\Lambda_1^3\to \mathcal{C}$, which when completed to a $3$-simplex, $\tau:\Delta^3\to \mathcal{C}$, witnesses the face $d_1^3(\tau)$ as a homotopy from $h$ to $h'$.

Conversely, suppose $\sigma'':\Delta^2\to \mathcal{C}$ is a homotopy from $h$ to $h'$. Then we can instead consider the inner horn $\rho_0:\Lambda_2^3\to \mathcal{C}$ given by the triple $(s_1^1(g),\sigma'',-,\sigma)$, in which case the face $d_2^3(\rho)$ of the extension witnesses $h'$ as a composition of $f$ and $g$.
`\end{proof}`

>[!example] Topological Composition
>Let $X$ be a topological space and let $f,g:[0,1]\to X$ be path such that $f(1) = g(0)$. Then they have a composite $g\star f$ in the quasi-category $\text{Sing}_\bullet(X)$ witnessed by (its adjoint) the continuous map
>$$\sigma:|\Delta^2|\to X,\;\;\;\sigma(t_0,t_1,t_2) = \left\{\begin{array}{cc} f(t_1+2t_2) & t_0 \geq t_2 \\ g(t_2-t_0) & t_0 \leq t_2 \end{array}\right.$$
>Note that this is just one of many homotopic composites.

We now show that composites of homotopic maps are themselves homotopic.

>[!proposition] Composites of Homotopic Maps
>Let $f,f':x\to y$ and $g,g':y\to z$ be homotopic in $\mathcal{C}$. Let $h$ be a composite of $f$ and $g$, and let $h'$ be a composite of $f'$ and $g'$. Then $h$ is homotopic to $h'$.

^53383c

`\begin{proof}`
We prove the claim by showing $h$ and $h'$ are homotopic to a common map $h''$, which witnesses the composition of $f$ and $g'$. Let $\sigma_3$ be the $2$-simplex for the composite $h$, $\sigma_2$ be for the composite $h''$, and $\sigma_0$ be the $2$-simplex for the homotopy from $g$ to $g'$. Then the triple $(\sigma_0,-,\sigma_2,\sigma_3)$ defines an inner horn $\tau_0:\Lambda_1^3\to \mathcal{C}$ which extends to a $3$-simplex $\tau$ with $d_1^3(\tau)$ being a $2$-simplex witnessing the homotopy from $h$ to $h''$. 

On the other hand, let $\sigma_0'$ be the composite for $h''$, let $\sigma_1'$ be the composite for $h'$, and let $\sigma_3'$ be the left-homotopy for $f$ with $f'$. Then the triple $(\sigma_0',\sigma_1',-,\sigma_3')$ determines an inner horn $\rho_0:\Lambda_2^3\to \mathcal{C}$ whose filling $\rho:\Delta^3\to \mathcal{C}$ has face $d_2^3(\rho)$ which gives a left-homotopy between $h''$ and $h'$, which is equivalent to a homotopy by [[Introduction to Quasi-Categories#^ac0ab1]].
`\end{proof}`

Finally, we show that composites of triples are defined up to homotopy.

>[!proposition] Composition is Associative up to Homotopy
>Let $f:x\to y$, $g:y\to z$, $h:z\to w$ be in $\mathcal{C}$. Let $K$ be a composite of $g$ and $f$, $L$ a composite of $h$ and $g$, and $L'$ a composite of $L$ and $f$. Then $L'$ is a composite of $K$ with $h$.

^76b2aa

`\begin{proof}`
Let $\sigma_0$ witness the composite $L$, $\sigma_2$ witness the composite $L'$, and $\sigma_3$ witness the composite $K$. Then the triple $(\sigma_0,-,\sigma_2,\sigma_3)$ determines an inner horn $\tau_0:\Lambda_1^3\to \mathcal{C}$ which extends to a $3$-simplex $\tau:\Delta^3\to \mathcal{C}$ such that $d_1^3(\tau)$ is a $2$-simplex witnessing $L'$ as a composite of $K$ with $h$.
`\end{proof}`

### The Homotopy Category of a Quasi-Category

Recall that for a topological space $X$ we have its fundamental groupoid, $\pi_{\leq 1}(X)$, which is an invariant of $X$ determined by its singular $n$-simplices for $n \leq 2$. This implies that we can think of this invariant as an invariant for $\text{Sing}_\bullet(X)$, which we now hope to extend to the case of quasi-categories.

Technically we already have this invariant on hand - it is our homotopy category. However, in general the homotopy category of a simplicial set is hard to describe, so in this section we see how it simplifies for quasi-categories.

We will now construct an explicit model for $h\mathcal{C}$, when $\mathcal{C}$ is a quasi-category, and show it satisfies the appropriate universal property. The objects of $h\mathcal{C}$ will be the zero simplices of $\mathcal{C}$, while the morphisms from $x$ to $y$ in $h\mathcal{C}$ will be homotopy classes of morphisms. From [[Introduction to Quasi-Categories#^53383c]] and the reflexivity of homotopies, we obtain a unique composition law such that $[g]\circ [f] = [h]$ whenever $h$ is a composition of $f$ and $g$, and this composition is unital. Associativity follows by [[Introduction to Quasi-Categories#^76b2aa]].

We have a natural map of simplicial sets $\mathcal{C}\to N_\bullet(h\mathcal{C})$ which is the identity on $0$-simplices, sends $1$-simplices to their homotopy classes, and sends $n$-simplices, for $n \geq 2$, sends an $n$-simplex $\sigma$ to the sequence of maps corresponding to the edges $[0,1],[1,2],...,[n-1,n]$ in the $n$-simplex. If $\mathcal{D}$ is any ordinary category, and $\mathcal{C}\to N_\bullet(\mathcal{D})$ is a map of simplicial sets, then it is determined by where it sends its $0$-simplices and $1$-simplices. Further, because it is a map of simplicial sets it must be "functorial" with respect to composition, and so uniquely determines a functor $h\mathcal{C}\to \mathcal{D}$.


Note that this construction generalizes the fundamental groupoid. Indeed, $h\text{Sing}_\bullet(X)$ for a topological space $X$ is exactly the fundamental groupoid $\pi_{\leq 1}(X)$.


### Isomorphisms in Quasi-categories

We now consider isomorphisms in infinity categories. Since we now have the homotopy category, $h\mathcal{C}$, at our disposal, this will make our work much simpler moving forward.

>[!def] Isomorphism
>Let $f:x\to y$ be a morphism in a quasi-category $\mathcal{C}$. We say that $f$ is an **isomorphism** if its homotopy class $[f]$ is an isomorphism in $h\mathcal{C}$.

Just like with isomorphisms in ordinary categories, isomorphisms in quasi-categories satisfy the $2$-$3$ property, so if $f:x\to y$ and $g:y\to z$ are morphisms in a quasi-category with composite $h$, then if any two of $f$, $g$, and $h$ are isomorphisms, then so is the third.

>[!def] Homotopy Inverse
>Let $f:x\to y$ be a map in quasi-category $\mathcal{C}$. If $g:y\to x$ is another map such that $\text{id}_x$ is a composite of $f$ and $g$, then $g$ is said to be a **left homotopy inverse** of $f$ and $f$ is said to be a **right homotopy inverse** of $g$.
>
>We say that $g$ is a **homotopy inverse** of $f$ if it is both a left and right homotopy inverse of $f$.

From usual calculations in ordinary categories, if $f$ admits a left homotopy inverse $g$ and a right homotopy inverse $h$, then $g$ and $h$ are homotopic, which follows from the calculation in $h\mathcal{C}$:
$$[g] = [g]\circ [\text{id}_y] = [g]\circ ([f]\circ [h]) = ([g]\circ [f])\circ [h] = [\text{id}_x]\circ [h] = [h]$$
It follows that $f$ is an isomorphism if and only if it admits left and right homotopy inverses.

We now show a first step in the process of arguing that Kan complexes play the role of groupoids in the setting of quasi-categories.

>[!proposition] All maps are Isomorphisms in Kan Complexes
>Let $\mathcal{C}$ be a Kan complex. Then every morphism in $\mathcal{C}$ is an isomorphism.

^331db6

`\begin{proof}`
Let $f:x\to y$ be a morphism in $\mathcal{C}$. Then $f$ determines an outer horn $(-,\text{id}_x,f):\Lambda_0^2\to \mathcal{C}$. Since $\mathcal{C}$ is a Kan complex this extends to a $2$-simplex $(g,\text{id}_x,f):\Delta^2\to \mathcal{C}$ which witnesses $g$ as a left homotopy inverse of $f$.

Similarly, the outer horn $(f,\text{id}_y,-):\Lambda_2^2\to \mathcal{C}$ extends to a $2$-simplex $(f,\text{id}_y,h):\Delta^2\to \mathcal{C}$ which witnesses $h$ as a right homotopy inverse of $f$, and so $f$ is an isomorphism.
`\end{proof}`

>[!rmk] Fundamental Groupoid of a Kan Complex
>If $\mathcal{C}$ is a Kan complex then [[Introduction to Quasi-Categories#^331db6]] implies that the homotopy category $h\mathcal{C}$ is a groupoid. Moving forward we will write $\pi_{\leq 1}(\mathcal{C}) := h\mathcal{C}$ for Kan complexes, and refer to the homotopy category as the **fundamental groupoid** of $\mathcal{C}$.

Observe that we quickly obtain the following isomorphism of sets:
$$\pi_0(\mathcal{C})\cong \pi_{\leq 1}(\mathcal{C})_0/\text{iso}$$
when $\mathcal{C}$ is a Kan complex.

## Functors of Quasi-Categories

In this section we introduce the equivalent notion of functors of quasi-categories. Recall that if $\mathcal{C}$ and $\mathcal{D}$ are ordinary categories, then since the Nerve functor $N_\bullet$ is fully-faithful, functors $F:\mathcal{C}\to \mathcal{D}$ are in bijection with morphisms of simplicial sets, $N_\bullet(\mathcal{C})\to N_\bullet(\mathcal{D})$. Thus, it is natural to take the following definition.

>[!def] Functors between quasi-categories
>Let $\mathcal{C}$ and $\mathcal{D}$ be quasi-categories. A **functor** from $\mathcal{C}$ to $\mathcal{D}$ is then a morphism of simplicial sets $F:\mathcal{C}\to \mathcal{D}$.

We will proceed through a number of standard constructions related to functors appearing in ordinary category theory. For example we will construct a quasi-category of functors which agrees with that for ordinary categories when restricted to nerves of categories.

This work will require certain digressions into the deeper theory of categorical lifting properties and the homotopy theory of simplicial sets.

### Examples of Functors

Let $\mathcal{C}$ be a quasi-category and let $\mathcal{D}$ be an ordinary category. Then we have a natural bijection
$$\mathsf{sSet}(\mathcal{C},N_\bullet(\mathcal{D}))\cong \mathsf{Cat}(h\mathcal{C},\mathcal{D})$$
which comes from the homotopy category-nerve adjunction. 

In general, if $\mathcal{C}$ and $\mathcal{D}$ are both quasi-categories and $F:\mathcal{C}\to \mathcal{D}$ is a functor, then $F$ assigns objects $x$, $0$-cells, to objects $F(x)$, and morphisms $f:x\to y$, $1$-cells, to morphisms $F(f):F(x)\to F(y)$ where the domain and codomain are respected since $F$ respects face and degeneracy maps. Similarly, if $x$ is an object of $\mathcal{C}$ and $\text{id}_x = s_0^0(x):x\to x$ is its associated identity morphism, then $F(\text{id}_x) = \text{id}_{F(x)}$. 

Finally, if $f:x\to y$ and $g:y\to z$ are morphisms in $\mathcal{C}$ with a composite $h$ which is witnessed by a $2$-simplex $\sigma:\Delta^2\to \mathcal{C}$, then $F(\sigma):\Delta^2\to\mathcal{C}$ witnesses $F(h)$ as a composite of $F(f)$ with $F(g)$.

>[!rmk] 
>Note that although functors between quasi-categories share a number of properties with functors between ordinary categories, it does not suffice to define functors of quasi-categories on objects and morphisms such that identities and composites are satisfied. Indeed, functors on quasi-categories must be defined on **all** simplicial dimensions. These higher dimensions are needed to encode composition "up to coherent homotopy", a concept we will expand on more in the future.
>
>For example, the higher dimensions also guarantee that a functor of quasi-categories carries homotopies to homotopies (viewed as $2$-simplices).


Note that the final statement in the above remark implies that functors of quasi-categories preserve left and right homotopy inverses of morphisms.

Let's now interpret these facts in the topological setting.

>[!example]
>Let $X$ be a topological space and $\mathcal{C}$ an ordinary category. A functor $F:\text{Sing}_\bullet(X)\to N_\bullet(\mathcal{C})$ assigns points to objects, continuous paths to morphisms, and $2$-simplexes to pairs of morphisms along with their composite. Further, since all $1$-cells are isomorphisms in $\text{Sing}_\bullet(X)$, $F$ sends all paths to isomorphisms in $\mathcal{C}$.
>
>Using the stronger definition of local systems as a family of compatible representations of the fundamental group of $X$, $\pi_1(X,x)$, it follows that functors $F:\text{Sing}_\bullet(X)\to N_\bullet(\mathcal{C})$ are equivalent to **$\mathcal{C}$-valued local systems** on $X$.

More generally, if $\mathcal{C}$ is a quasi-category, we can define **$\mathcal{C}$-valued local systems** on $X$ to be functors of quasi-categories $\text{Sing}_\bullet(X)\to \mathcal{C}$.

Note that just as for functors in nerves of ordinary categories, we have the following equivalence for a quasi-category $\mathcal{C}$ and a topological space $X$:
$$\mathsf{sSet}(\mathcal{C},\text{Sing}_\bullet(X))\cong \mathsf{Top}(|\mathcal{C}|,X)$$
using the geometric realization-singular simplicial set adjunction.


### Commutative Diagrams

Recall that in ordinary categories we can interpret functors as commutative diagrams in the codomain category indexed by the domain category. In this section we will investigate how far this idea extends to functors between quasi-categories.

>[!def] Diagrams in Quasi-categories
>A **diagram** in $\mathcal{C}$ indexed by a simplicial set $K$ is a map of simplicial sets $f:K\to \mathcal{C}$.

When $K\cong N_\bullet(I)$, we will refer to $f:K\to \mathcal{C}$ as an $I$-indexed diagram in $\mathcal{C}$. Note that in general the indexing simplicial set $K$ need **not** be a quasi-category.

If $K$ is a simplicial set of dimension $\leq 1$, i.e. a directed graph $\mathcal{G}$, then a diagram $K\to \mathcal{C}$ is equivalent to a collection $\{c_v\}_{v \in \text{Vert}(\mathcal{G})}$ of objects and a collection $\{f_e\}_{e \in \text{Edge}(\mathcal{G})}$ of morphisms.

>[!example]
>Let $K$ denote the boundary of the product $\Delta^1\times \Delta^1$, i.e. $$K = (\partial\Delta^1\times \Delta^1)\cup_{\partial\Delta^1\times \partial\Delta^1}(\Delta^1\times \partial\Delta^1)$$
>Then $K$ is a $1$-dimensional simplicial set with non-degenerate $1$-simplices $\{(01,00),(11,01),(00,01),(11,01)\}$ and non-degenerate $0$-simplices given by their faces. In other words, $K$ is the directed graph corresponding to a square with edges either going right or down.
>
>A $K$-indexed diagram in a quasi-category $\mathcal{C}$ can then be depicted pictorially as a square
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BC_%7B00%7D%7D%20%26%26%20%7BC_%7B01%7D%7D%20%5C%5C%0A%09%5C%5C%0A%09%7BC_%7B10%7D%7D%20%26%26%20%7BC_%7B11%7D%7D%0A%09%5Carrow%5B%22%7Bf_%7B(01%2C00)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bf_%7B(00%2C01)%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7Bf_%7B(11%2C01)%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bf_%7B(01%2C11)%7D%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{C_{00}} &amp;&amp; {C_{01}} \\	\\	{C_{10}} &amp;&amp; {C_{11}}	\arrow[&quot;{f_{(01,00)}}&quot;, from=1-1, to=1-3]	\arrow[&quot;{f_{(00,01)}}&quot;', from=1-1, to=3-1]	\arrow[&quot;{f_{(11,01)}}&quot;, from=1-3, to=3-3]	\arrow[&quot;{f_{(01,11)}}&quot;', from=3-1, to=3-3]\end{tikzcd}" /></p>

We now move to introducing the notion of **commutative diagrams** into the theory of quasi-categories.

>[!def] Commutative Diagram
>Let $K$ be a simplicial set of dimension $\leq 1$, which can be identified with a graph $\mathcal{G}$. Further, suppose for each $v,w \in \text{Vert}(\mathcal{G})$ there exists at most one edge $(v,w) \in \text{Edge}(\mathcal{G})$, and the graph $\mathcal{G}$ has no directed cycles.
>
>If $\mathcal{C}$ is an ordinary category, we say that a diagram $\sigma:K\to N_\bullet(\mathcal{C})$ is **commutative** if the following holds:
>- If $v,w$ are vertices in $\mathcal{G}$ which are joined by paths $v=v_0,v_1,...,v_m = w$ and $v=v_0',v_1',...,v_n' = w$, then we have an identity
>$$f_{v_m,v_{m-1}}\circ \cdots \circ f_{v_0,v_1} = f_{v_n',v_{n-1}'}\circ \cdots \circ f_{v_1',v_0'}$$

^5e6286

>[!proposition] Classification of Commutative Diagrams indexed by graphs
>Let $K$ be a simplicial set of dimension $\leq 1$ with graph $\mathcal{G}$ satisfying the hypotheses in [[Introduction to Quasi-Categories#^5e6286]] (except for the last one). Let $\mathcal{C}$ be an ordinary category and let $\sigma:K\to N_\bullet(\mathcal{C})$ be a diagram. Then the following hold:
>1. There is a natural partial order on $\text{Vert}(\mathcal{G})$ generated by the edges in $\mathcal{G}$.
>2. There is a unique monomorphism $K\hookrightarrow N_\bullet(\text{Vert}(\mathcal{G}))$, where we view $\text{Vert}(\mathcal{G})$ as a category with its poset structure.
>3. $\sigma$ extends to a map $\overline{\sigma}:N_\bullet(\text{Vert}(\mathcal{G}))\to N_\bullet(\mathcal{C})$, and hence a functor $\text{Vert}(\mathcal{G})\to \mathcal{C}$, if and only if $\sigma$ is **commutative**, and this extension is necessarily unique.

^ebc27e

`\begin{proof}`
**(1)** follows from our hypotheses that $\mathcal{G}$ has no directed loops. Since $K$ is of dimension $\leq 1$, we obtain an identity on vertices map $K\to N_\bullet(\text{Vert}(\mathcal{G}))$ by sending an edge $e:v\to w$ to the relation $v\leq w$ in $\text{Vert}(\mathcal{G})$. Since all vertices in $\mathcal{G}$ have at most one edge between them, this map is a monomorphism.

We can now identify $K$ with a sub-simplicial set of $N_\bullet(\text{Vert}(\mathcal{G}))$. Identifying $\sigma$ with the pair of objects, $\{C_v\}_{v \in \text{Vert}(\mathcal{G})}$, and morphisms, $\{f_{w,v}:C_v\to C_w\}_{(v,w) \in \text{Edge}(\mathcal{G})}$, if $\sigma$ extends to a simplicial map $\overline{\sigma}$, then since $\overline{\sigma}$ represents a functor of ordinary categories, and hence preserves composition, it satisfies the hypotheses for a commutative diagram. On the other hand, if $\sigma$ is commutative we can define $\overline{\sigma}$ by sending $v\leq w$ to $f_{v_n,v_{n-1}}\circ f_{v_{n-1},v_{n-2}}\circ \cdots \circ f_{v_1,v_0}$ for any sequence of edges $v=v_0\leq v_1\leq \cdots \leq v_n = w$.
`\end{proof}`

Note that in [[Introduction to Quasi-Categories#^ebc27e]], we can identify $\sigma:K\to N_\bullet(\mathcal{C})$ with $N_\bullet(\text{Path}[\mathcal{G}])\to N_\bullet(\mathcal{C})$, and so commutativity of $\sigma$ is equivalent to the requirement that $F:\text{Path}[\mathcal{G}]\to \mathcal{C}$ factors through the quotient functor $\text{Path}[G]\twoheadrightarrow \text{Vert}(\mathcal{G})$ (i.e. the value of $F$ on a path depends only on its endpoints).

>[!example] Commutative Squares
>Let $K = \partial(\Delta^1\times \Delta^1) = (\partial\Delta^1\times \Delta^1)\cup_{\partial\Delta^1\times\partial\Delta^1}(\Delta^1\times\partial\Delta^1)$ be as in our previous example. Then a diagram $\sigma:K\to N_\bullet(\mathcal{C})$, as in the diagram
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BC_%7B00%7D%7D%20%26%26%20%7BC_%7B01%7D%7D%20%5C%5C%0A%09%5C%5C%0A%09%7BC_%7B10%7D%7D%20%26%26%20%7BC_%7B11%7D%7D%0A%09%5Carrow%5B%22%7Bf_%7B(01%2C00)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bf_%7B(00%2C01)%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7Bf_%7B(11%2C01)%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bf_%7B(01%2C11)%7D%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{C_{00}} &amp;&amp; {C_{01}} \\	\\	{C_{10}} &amp;&amp; {C_{11}}	\arrow[&quot;{f_{(01,00)}}&quot;, from=1-1, to=1-3]	\arrow[&quot;{f_{(00,01)}}&quot;', from=1-1, to=3-1]	\arrow[&quot;{f_{(11,01)}}&quot;, from=1-3, to=3-3]	\arrow[&quot;{f_{(01,11)}}&quot;', from=3-1, to=3-3]\end{tikzcd}" /></p>
>
>is commutative if and only if $f_{(11,01)}\circ f_{(01,00)} = f_{(01,11)}\circ f_{(00,01)}$ in $\mathcal{C}$. [[Introduction to Quasi-Categories#^ebc27e]] implies that we obtain an extension $\overline{\sigma}:\Delta^1\times \Delta^1\to N_\bullet(\mathcal{C})$, or equivalently a functor of ordinary categories $[1]\times [1]\to \mathcal{C}$.

Part **(3)** of [[Introduction to Quasi-Categories#^ebc27e]] sadly does not hold in general for quasi-categories. For example, if $I$ is the partially ordered set $[1]\times [1]$ (with the product ordering), the simplicial set $N_\bullet(I)\cong \Delta^1\times \Delta^1$ has four vertices, five nondegenerate edges, and two nondegenerate $2$-simplices. An $I$-indexed diagram in a quasi-category $\mathcal{C}$ is then equivalent to

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BC_%7B00%7D%7D%20%26%26%26%20%7BC_%7B01%7D%7D%20%5C%5C%0A%09%26%26%20%5Csigma%20%5C%5C%0A%09%26%20%5Ctau%20%5C%5C%0A%09%7BC_%7B10%7D%7D%20%26%26%26%20%7BC_%7B11%7D%7D%0A%09%5Carrow%5B%22%7Bf_%7B(01%2C00)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%7Bf_%7B(00%2C01)%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D4-1%5D%0A%09%5Carrow%5B%22%7Bf_%7B(01%2C01)%7D%7D%22%2C%20from%3D1-1%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22%7Bf_%7B(11%2C01)%7D%7D%22%2C%20from%3D1-4%2C%20to%3D4-4%5D%0A%09%5Carrow%5B%22%7Bf_%7B(01%2C11)%7D%7D%22'%2C%20from%3D4-1%2C%20to%3D4-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{C_{00}} &amp;&amp;&amp; {C_{01}} \\
	&amp;&amp; \sigma \\
	&amp; \tau \\
	{C_{10}} &amp;&amp;&amp; {C_{11}}
	\arrow[&quot;{f_{(01,00)}}&quot;, from=1-1, to=1-4]
	\arrow[&quot;{f_{(00,01)}}&quot;', from=1-1, to=4-1]
	\arrow[&quot;{f_{(01,01)}}&quot;, from=1-1, to=4-4]
	\arrow[&quot;{f_{(11,01)}}&quot;, from=1-4, to=4-4]
	\arrow[&quot;{f_{(01,11)}}&quot;', from=4-1, to=4-4]
\end{tikzcd}
" /></p>

which is not usually determined by its restriction to the simplicial subset $K$, as it lacks the data of these two $2$-simplices and our diagonal map.

If $\sigma:K\to \mathcal{C}$ is such a diagram, we can compose with the unit to obtain a diagram $\sigma':K\to N_\bullet(h\mathcal{C})$. By [[Introduction to Quasi-Categories#^ebc27e]] we have that $\sigma'$ is commutative if and only if $[f_{(11,01)}]\circ [f_{(01,00)}] = [f_{(01,11)}] \circ [f_{(00,01)}]$. This is equivalent to the existence of $2$-simplices $\sigma$ and $\tau$ witnessing a common composite $f_{(01,01)}$ of $f_{(11,01)}$ with $f_{(01,00)}$, and of $f_{(01,11)}$ with $f_{(00,01)}$, which is exactly the data of an extension $\overline{\sigma}:\Delta^1\times \Delta^1\to \mathcal{C}$ since $\Delta^1\times\Delta^1 \cong \Delta^2\cup_{\Delta^1}\Delta^2$.

Note that this extension is in general **not** unique, since the boundary cells only determine the inner composite up to homotopy and do not fully determine the homotopies themselves either. Further, observe that in this case we were able to lift a functor of ordinary categories $I\to h\mathcal{C}$ to a functor of quasi-categories, $N_\bullet(I)\to \mathcal{C}$. However, this is **not** possible in general, even for poset categories. A simple example where this fails is $I = [1]\times [1]\times [1]$.

>[!example] Property versus Structure
>Note that in the case of ordinary characters, a diagram being commutative is a **property** of that underlying diagram, which it either does or doesn't posses. On the other hand, for a general quasi-category, the commutativity of a diagram is a **structure** which promotes a diagram to a commutative diagram, and this requires the specification of additional data to *witness* this commutativity.

### Quasi-Category of Functors

Recall that the category of simplicial sets is cartesian closed, where for $S$ and $T$ simplicial sets
$$T^S = \mathsf{sSet}(\Delta^n\times S,T)$$
Moving forward we will write $\text{Fun}(S,T)$ for this simplicial set, hinting to our later goal of showing that under certain hypotheses on $S$ and $T$ this construction yields a quasi-category.

The co-unit of the adjunction $\text{ev}:T^S\times S\to T$ sends an $n$-simplex $f$ of $T^S$ and an $n$-simplex $\sigma$ of $S$ to the $n$-simplex of $T$ given by the composite
$$\Delta^n\xrightarrow{\delta}\Delta^n\times \Delta^n\xrightarrow{\text{id}\times\sigma}\Delta^n\times S\xrightarrow{f}T$$
where $\delta$ is the diagonal map. We now show that this produces the right object for ordinary categories.

>[!proposition] Functor Simplex for Ordinary Categories
>If $\mathcal{C}$ and $\mathcal{D}$ are ordinary categories and $\text{ev}:\text{Fun}(\mathcal{C},\mathcal{D})\times \mathcal{C}\to \mathcal{D}$ denotes the evaluation functor, then the adjoint map of the composite
>$$N_\bullet(\text{Fun}(\mathcal{C},\mathcal{D}))\times N_\bullet(\mathcal{C})\cong N_\bullet(\text{Fun}(\mathcal{C},\mathcal{D})\times \mathcal{C})\xrightarrow{N_\bullet(\text{ev})}N_\bullet(\mathcal{D})$$
>is an isomorphism of simplicial sets.

^318eda

`\begin{proof}`
Note that the adjoint of the described composite is the map of simplicial sets $\rho:N_\bullet(\text{Fun}(\mathcal{C},\mathcal{D}))\to \text{Fun}(N_\bullet(\mathcal{C}),N_\bullet(\mathcal{D}))$ given on $n$-simplices by the composite of the following isomorphisms
$$
\begin{align*}
\mathsf{sSet}(\Delta^n,N_\bullet(\text{Fun}(\mathcal{C},\mathcal{D}))) &\cong \mathsf{Cat}([n],\text{Fun}(\mathcal{C},\mathcal{D})) \tag{nerve is ff}\\
&\cong \mathsf{Cat}([n]\times\mathcal{C},\mathcal{D}) \tag{adj.} \\
&\cong \mathsf{sSet}(N_\bullet([n]\times \mathcal{C}),N_\bullet(\mathcal{D})) \tag{nerve is ff} \\
&\cong \mathsf{sSet}(\Delta^n\times N_\bullet(\mathcal{C}),N_\bullet(\mathcal{D})) \tag{nerve pres. lims} \\
&\cong \mathsf{sSet}(\Delta^n,\text{Fun}(N_\bullet(\mathcal{C}),N_\bullet(\mathcal{D})))
\end{align*}
$$
completing the proof.
`\end{proof}`

Taking homotopy categories [[Introduction to Quasi-Categories#^318eda]] implies that
$$\text{Fun}(\mathcal{C},\mathcal{D})\cong h\text{Fun}(N_\bullet(\mathcal{C}),N_\bullet(\mathcal{D}))$$
We also obtain the following interesting corollaries for simplicial sets in general.

>[!corollary] Functor simplicial set into a nerve
>If $S$ is a simplicial set and $\mathcal{D}$ is an ordinary category then the adjoint of the composite
>$$N_\bullet(\text{Fun}(hS,\mathcal{D}))\times S\to N_\bullet(\text{Fun}(hS,\mathcal{D})\times hS)\to N_\bullet(\mathcal{D})$$
>induces an isomorphism of simplicial sets $\rho_S:N_\bullet(\text{Fun}(hS,\mathcal{D}))\cong \text{Fun}(S,N_\bullet(\mathcal{D}))$.

^c8ee2d

`\begin{proof}`
The assignment $S\mapsto \rho_S$ is part of a functor $\mathsf{sSet}^{op}\to \text{Arr}(\mathsf{sSet})$ that sends a map of simplicial sets $f:S\to T$ to the pair of maps $N_\bullet(y^f):N_\bullet(\text{Fun}(hT,\mathcal{D}))\to N_\bullet(\text{Fun}(hS,\mathcal{D}))$ and $\text{Fun}(f,N_\bullet(\mathcal{D})):\text{Fun}(T,N_\bullet(\mathcal{D}))\to \text{Fun}(S,N_\bullet(\mathcal{D}))$.  Note that $N_\bullet(\text{Fun}(h-,\mathcal{D}))$ and $\text{Fun}(-,N_\bullet(\mathcal{D}))$ send colimits to limits, since internal homs for closed monoidal categories send colimits to limits in the first variable. It follows that it suffices to prove the claim on a generating set of for the category of simplicial sets over colimits.

Thus, the claim holds by [[Introduction to Quasi-Categories#^318eda]] since all simplicial sets are colimits of standard simplices.
`\end{proof}`

>[!corollary] Homotopy Functor Commutes with Finite Products
>The homotopy functor $h:\mathsf{sSet}\to \mathsf{Cat}$ preserves finite products.

`\begin{proof}`
Note that the final object in $\mathsf{sSet}$ is the image of the final object in $\mathsf{Cat}$, so its homotopy functor is isomorphic to itself since the co-unit $h(N_\bullet(-))\to 1$ is an isomorphism. Thus $h$ preserves final objects. It remains to show that the canonical map $h(S\times T)\to hS\times hT$ for any simplicial sets $S$ and $T$ is an isomorphism. 

We can do this using the Yoneda embedding by showing that for any category $\mathcal{C}$ we obtain an isomorphism $\mathsf{Cat}(hS\times hT,\mathcal{C})\to \mathsf{Cat}(h(S\times T),\mathcal{C})$. Observe that we have a sequence of isomorphisms
$$
\begin{align*}
\mathsf{Cat}(hS\times hT,\mathcal{C}) &\cong \mathsf{Cat}(hS,\text{Fun}(hT,\mathcal{C})) \\
&\cong \mathsf{sSet}(S,N_\bullet(\text{Fun}(hT,\mathcal{C}))) \\
&\cong \mathsf{sSet}(S,\text{Fun}(T,N_\bullet(\mathcal{C}))) \\
&\cong \mathsf{sSet}(S\times T,N_\bullet(\mathcal{C})) \\ 
&\cong \mathsf{Cat}(h(S\times T),\mathcal{C})
\end{align*}
$$
where in the middle isomorphism we have used [[Introduction to Quasi-Categories#^c8ee2d]].
`\end{proof}`

Later we will show that when $\mathcal{D}$ is a quasi-category, and $S$ is any simplicial set, $\text{Fun}(S,\mathcal{D})$ is a quasi-category, so quasi-category form an exponential ideal in the category of simplicial sets.

>[!def] Quasi-Category of Functors
>If $\mathcal{C}$ and $\mathcal{D}$ are quasi-categories, we refer to $\text{Fun}(\mathcal{C},\mathcal{D})$ as the **quasi-category of functors from $\mathcal{C}$ to $\mathcal{D}$**.

Note that the objects of the quasi-category $\text{Fun}(\mathcal{C},\mathcal{D})$ are maps of simplicial sets $\Delta^0\times \mathcal{C}\to \mathcal{D}$, where $\Delta^0\times \mathcal{C}\cong \mathcal{C}$. Thus the objects of the quasi-category of functors are necessarily functors. Then we can define a **natural transformation** of functors $F,G:\mathcal{C}\to \mathcal{D}$ between quasi-categories to be a $1$-simplex in this quasi-category, namely a map of simplicial sets $u:\Delta^1\times \mathcal{C}\to \mathcal{D}$, such that $u\vert_{\{0\}\times \mathcal{C}} = F$ and $u\vert_{\{1\}\times \mathcal{C}} = G$.

## Lifting Properties, Homotopy, and Combinatorics

In this section we cover a number of digressions which are very important in the development of functors between quasi-categories and quasi-categories themselves more generally. We begin with a short aside on lifting properties in categories.

### Lifting Properties.

Throughout let $\mathcal{C}$ denote an ordinary category. We refer to a commuting square in $\mathcal{C}$ as a **lifting problem**, where the solution to such a problem is an anti-diagonal map which "lifts" the bottom map and creates two commuting triangles.

>[!def] Orthogonal Maps
>Let $f:A\to B$ and $g:X\to Y$ be maps in $\mathcal{C}$. We say $f$ is **weakly left orthogonal to $g$** (equivalently $g$ is **weakly right orthogonal to $f$**)if for each pair of morphisms $u:A\to X$ and $v:B\to Y$ making the square below commute, there is a lift (not necessarily unique) indicated by the dashed line
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09B%20%26%26%20Y%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	A &amp;&amp; X \\	\\	B &amp;&amp; Y	\arrow[&quot;u&quot;, from=1-1, to=1-3]	\arrow[&quot;f&quot;', from=1-1, to=3-1]	\arrow[&quot;g&quot;, from=1-3, to=3-3]	\arrow[dashed, from=3-1, to=1-3]	\arrow[&quot;v&quot;', from=3-1, to=3-3]\end{tikzcd}" /></p>
>
>In this case we write $f\perp_wg$.

If $\mathcal{A}$ and $\mathcal{B}$ are collections of arrows in $\mathcal{C}$, we say $\mathcal{A}$ is **weakly left orthogonal** to $\mathcal{B}$ (equivalently $\mathcal{B}$ is **weakly right orthogonal** to $\mathcal{A}$) if for all $f \in \mathcal{A}$ and all $g \in \mathcal{B}$, $f\perp_wg$. In this case we write $\mathcal{A}\perp_w\mathcal{B}$. When the lift is unique we drop the "weakly" prefix and just write $\perp$.

If $\mathcal{A}$ is a class of morphisms in $\mathcal{C}$, we will write $\mathcal{A}^\perp$ (resp. $\mathcal{A}^{\perp_w}$) for the maximal set of maps (resp. weakly) right orthogonal to $\mathcal{A}$, and ${^\perp}\mathcal{A}$ (resp. ${^{\perp_w}}\mathcal{A}$) for the maximal set of maps (resp. weakly) left orthogonal to $\mathcal{A}$. Note that $\mathcal{A}^{\perp}\subseteq \mathcal{A}^{\perp_w}$ and ${^{\perp}}\mathcal{A}\subseteq {^{\perp_w}}\mathcal{A}$. 

We now review a number of useful properties of these classes.

>[!proposition] Properties of Orthogonality of Maps
>Let $\mathcal{A}$ be a collection of maps in a category $\mathcal{C}$. Then the following hold:
>1. $\mathcal{A}^{\perp}$ (resp. ${^{\perp}}\mathcal{A}$) contains all isomorphisms
>2. $\mathcal{A}\cap \mathcal{A}^{\perp_w}\cap {^{\perp_w}}\mathcal{A} =$ the set of all isomorphisms
>3. $\mathcal{A}^{\perp}$ (resp. ${^{\perp}}\mathcal{A}$) and $\mathcal{A}^{\perp_w}$ (resp. ${^{\perp_w}}\mathcal{A}$) are closed under composition
>4. If $h\circ g \in \mathcal{A}^{\perp}$ (resp. ${^\perp}\mathcal{A}$) and $h$ is monic (resp. $g$ is epic) then $g$ (resp. $h$) is in $\mathcal{A}^{\perp}$ (resp. ${^\perp}\mathcal{A}$) (same for weak)
>5. If $h\circ g$ and $h$ are in $\mathcal{A}^{\perp}$ (resp. $h\circ g$ and $g$ in ${^\perp}\mathcal{A}$) then $g$ is in $\mathcal{A}^{\perp}$ (resp. $h$ is in ${^\perp}\mathcal{A}$)
>6. $\mathcal{A}^{\perp}$ and $\mathcal{A}^{\perp_w}$ (resp. ${^\perp}\mathcal{A}$ and ${^{\perp_w}}\mathcal{A}$) are closed under pullbacks (resp. pushouts)
>7. $\mathcal{A}^{\perp}$ and $\mathcal{A}^{\perp_w}$ (resp. ${^\perp}\mathcal{A}$ and ${^{\perp_w}}\mathcal{A}$) are closed under products (resp. coproducts)
>8. Every section is in $\mathcal{A}^{\perp}$, $\mathcal{A}^{\perp_w}$ (resp. every retraction is in ${^\perp}\mathcal{A}$, ${^{\perp_w}}\mathcal{A}$) if and only if for any pair of maps in  $\mathcal{A}^{\perp}$, $\mathcal{A}^{\perp_w}$ (resp. ${^\perp}\mathcal{A}$, ${^{\perp_w}}\mathcal{A}$), the equalizer is (resp. co-equalizer) is an $\mathcal{A}^{\perp}$, $\mathcal{A}^{\perp_w}$ (resp. ${^\perp}\mathcal{A}$, ${^{\perp_w}}\mathcal{A}$) map.
>9. $\mathcal{A}^{\perp}$, $\mathcal{A}^{\perp_w}$, ${^\perp}\mathcal{A}$, and ${^{\perp_w}}\mathcal{A}$ are closed under retractions in the arrow category
>10. $\mathcal{A}^{\perp}$ and $\mathcal{A}^{\perp_w}$ (resp. ${^\perp}\mathcal{A}$ and ${^{\perp_w}}\mathcal{A}$) are closed under transfinite cocomposition (resp. transfinite composition)

^193325

Before proving [[Introduction to Quasi-Categories#^193325]] let us first define transfinite composition and cocomposition formally and provide an example.

>[!def] Transfinite Composition
>Let $\alpha$ be an ordinal and let $\text{Ord}_{\leq \alpha} = \alpha \cup \{\alpha\} = \{\beta\in \text{Ord}:\beta \leq \alpha\}$ be the linearly ordered set of ordinals less than or equal to $\alpha$. Let $\mathcal{A}$ be a collection of morphisms in $\mathcal{C}$. 
>
>A morphism $f$ of $\mathcal{C}$ is said to be a **transfinite composition** of morphisms of $\mathcal{A}$ if there exists an ordinal $\alpha$ and a functor $F:\text{Ord}_{\leq \alpha}\to \mathcal{C}$ such that
>1.  for every limit ordinal $\lambda\leq \alpha$, $F\vert_{\text{Ord}_{\leq \lambda}}$ is a colimiting cone witnessing $C_\lambda$ as a colimit of the diagram $F\vert_{\text{Ord}_{<\lambda}}$ 
>2. For every ordinal $\beta < \alpha$, $F(\beta \leq \beta+1) \in \mathcal{A}$
>3. $f = F(0 \leq \alpha)$
>
>If $F$ is contravariant we refer to this as transfinite cocomposition.

We now proceed to the proof of our extended proposition.

`\begin{proof}[Proof of Properties of Orthogonality.]`
In most cases will only prove one of the claims, as the other follows by duality.

For **(1)** both claims are clear since we can go back obtain our (necessarily unique) diagonal map by going back along the appropriate isomorphism.

For **(2)** it suffices by duality to show that every morphism $f:A\to B$ which is in $\mathcal{A}$ and $\mathcal{A}^{\perp_w}$ is an isomorphism. However, this follows immediately by forming the lifting problem where $f$ is on either vertical edge and identities are on the horizontal edges of the square:

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%20A%20%5C%5C%0A%09%5C%5C%0A%09B%20%26%26%20B%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp; A \\
	\\
	B &amp;&amp; B
	\arrow[Rightarrow, no head, from=1-1, to=1-3]
	\arrow[&quot;f&quot;', from=1-1, to=3-1]
	\arrow[&quot;f&quot;, from=1-3, to=3-3]
	\arrow[dashed, from=3-1, to=1-3]
	\arrow[Rightarrow, no head, from=3-1, to=3-3]
\end{tikzcd}
" /></p>

For **(3)** let $g:X\to Y$ and $h:Y\to Z$ be in $\mathcal{A}^{\perp_w}$ (resp. $\mathcal{A}^{\perp}$). Then for any $f:A\to B$ in $\mathcal{A}$ observe that we obtain iterated lifts

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%20X%20%5C%5C%0A%09%26%26%20Y%20%5C%5C%0A%09B%20%26%26%20Z%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22h%22%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp; X \\
	&amp;&amp; Y \\
	B &amp;&amp; Z
	\arrow[&quot;u&quot;, from=1-1, to=1-3]
	\arrow[&quot;f&quot;', from=1-1, to=3-1]
	\arrow[&quot;g&quot;, from=1-3, to=2-3]
	\arrow[&quot;h&quot;, from=2-3, to=3-3]
	\arrow[dashed, from=3-1, to=1-3]
	\arrow[dashed, from=3-1, to=2-3]
	\arrow[&quot;v&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

first by viewing $g\circ u$ as the top arrow and then by considering the lifting problem of the resulting square. If $g$ and $h$ were in $\mathcal{A}^{\perp}$, this resulting lift would be unique.

For **(4)** we prove the weak case with $h\circ g$ in ${^{\perp_w}}\mathcal{A}$ and $g$ epic. Let $f:A\to B$ be in $\mathcal{A}$. Then in the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09X%20%5C%5C%0A%09%26%20Y%20%26%20A%20%5C%5C%0A%09%26%20Z%20%26%20B%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22u%22%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	X \\
	&amp; Y &amp; A \\
	&amp; Z &amp; B
	\arrow[&quot;g&quot;, from=1-1, to=2-2]
	\arrow[&quot;u&quot;, from=2-2, to=2-3]
	\arrow[&quot;h&quot;', from=2-2, to=3-2]
	\arrow[&quot;f&quot;, from=2-3, to=3-3]
	\arrow[&quot;v&quot;', from=3-2, to=3-3]
\end{tikzcd}
" /></p>

we obtain a map $k:Z\to A$ such that $f\circ k = v$ and $k\circ h \circ g = u\circ g$, which implies that $k\circ h = u$ since $g$ is epic.

For **(5)** we can form a similar diagram and obtain a similar map $k:Z\to A$. Then the lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09X%20%26%26%20A%20%5C%5C%0A%09%5C%5C%0A%09Y%20%26%20Z%20%26%20B%0A%09%5Carrow%5B%22%7Bu%5Ccirc%20g%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D3-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	X &amp;&amp; A \\
	\\
	Y &amp; Z &amp; B
	\arrow[&quot;{u\circ g}&quot;, from=1-1, to=1-3]
	\arrow[&quot;g&quot;, from=1-1, to=3-1]
	\arrow[&quot;f&quot;, from=1-3, to=3-3]
	\arrow[dashed, from=3-1, to=1-3]
	\arrow[&quot;h&quot;', from=3-1, to=3-2]
	\arrow[&quot;v&quot;', from=3-2, to=3-3]
\end{tikzcd}
" /></p>

has two solutions, namely $k\circ h$ and $u$. But since we are in the strong orthogonality case for **(5)** we have uniqueness of the lifts, so $k\circ h = u$, and again we find $h \in {^{\perp}}\mathcal{A}$.

For **(6)** let us consider the case of $\mathcal{A}^{\perp}$, so let $g:X\to Y$ be in $\mathcal{A}^{\perp}$, let $f:A\to B$ be in $\mathcal{A}$, and let $h:Z\to Y$ be an arbitrary morphism. Then consider the lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20D%20%26%20X%20%5C%5C%0A%09B%20%26%20Z%20%26%20Y%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7Bh'%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bg'%7D%22'%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; D &amp; X \\
	B &amp; Z &amp; Y
	\arrow[&quot;u&quot;, from=1-1, to=1-2]
	\arrow[&quot;f&quot;', from=1-1, to=2-1]
	\arrow[&quot;{h'}&quot;, from=1-2, to=1-3]
	\arrow[&quot;{g'}&quot;', from=1-2, to=2-2]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-2, to=2-3]
	\arrow[&quot;g&quot;, from=1-3, to=2-3]
	\arrow[dashed, from=2-1, to=1-3]
	\arrow[&quot;v&quot;', from=2-1, to=2-2]
	\arrow[&quot;h&quot;', from=2-2, to=2-3]
\end{tikzcd}
" /></p>

where the diagonal arrow exists since $f\perp g$. Then, by the universal property of the pullback we obtain an appropriate lift 

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20D%20%26%20X%20%5C%5C%0A%09B%20%26%20Z%20%26%20Y%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7Bh'%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bg'%7D%22'%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; D &amp; X \\
	B &amp; Z &amp; Y
	\arrow[&quot;u&quot;, from=1-1, to=1-2]
	\arrow[&quot;f&quot;', from=1-1, to=2-1]
	\arrow[&quot;{h'}&quot;, from=1-2, to=1-3]
	\arrow[&quot;{g'}&quot;', from=1-2, to=2-2]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-2, to=2-3]
	\arrow[&quot;g&quot;, from=1-3, to=2-3]
	\arrow[dashed, from=2-1, to=1-2]
	\arrow[dashed, from=2-1, to=1-3]
	\arrow[&quot;v&quot;', from=2-1, to=2-2]
	\arrow[&quot;h&quot;', from=2-2, to=2-3]
\end{tikzcd}
" /></p>

which is unique if the first lift is unique.

For **(7)** let $g:X\to Y$ and $h:Z\to W$ be in $^{\perp}\mathcal{A}$ and let $f:A\to B$ be in $\mathcal{A}$. Then the lifting problem we're interested in creates two lifting problems which can be solved individually

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20Z%20%5C%5C%0A%09X%20%26%26%20%7BX%5Camalg%20Z%7D%20%26%26%20A%20%5C%5C%0A%09Y%20%5C%5C%0A%09%26%20W%20%26%20%7BY%5Camalg%20W%7D%20%26%26%20B%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bdotted%2C%20from%3D1-2%2C%20to%3D4-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22v%22%2C%20from%3D2-3%2C%20to%3D2-5%5D%0A%09%5Carrow%5B%22%7Bg%5Camalg%20h%7D%22'%2C%20from%3D2-3%2C%20to%3D4-3%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D2-5%2C%20to%3D4-5%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D2-5%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D4-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D4-2%2C%20to%3D2-5%5D%0A%09%5Carrow%5Bfrom%3D4-2%2C%20to%3D4-3%5D%0A%09%5Carrow%5B%22u%22'%2C%20from%3D4-3%2C%20to%3D4-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp; Z \\
	X &amp;&amp; {X\amalg Z} &amp;&amp; A \\
	Y \\
	&amp; W &amp; {Y\amalg W} &amp;&amp; B
	\arrow[from=1-2, to=2-3]
	\arrow[dotted, from=1-2, to=4-2]
	\arrow[from=2-1, to=2-3]
	\arrow[from=2-1, to=3-1]
	\arrow[&quot;v&quot;, from=2-3, to=2-5]
	\arrow[&quot;{g\amalg h}&quot;', from=2-3, to=4-3]
	\arrow[&quot;f&quot;, from=2-5, to=4-5]
	\arrow[dashed, from=3-1, to=2-5]
	\arrow[from=3-1, to=4-3]
	\arrow[dashed, from=4-2, to=2-5]
	\arrow[from=4-2, to=4-3]
	\arrow[&quot;u&quot;', from=4-3, to=4-5]
\end{tikzcd}
" /></p>

solving the resulting coproduct lifting problem.

**(8)** follows immediately from **(6)** after observing that in any category if $f,g:X\to Y$ are parallel maps, there equalizer is given equivalently by the pullback 

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09D%20%26%26%20Y%20%5C%5C%0A%09%5C%5C%0A%09X%20%26%26%20%7BY%5Ctimes%20Y%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cpi_%7Bf%3Dg%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5CDelta%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20f%2Cg%5Crangle%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	D &amp;&amp; Y \\
	\\
	X &amp;&amp; {Y\times Y}
	\arrow[from=1-1, to=1-3]
	\arrow[&quot;{\pi_{f=g}}&quot;', from=1-1, to=3-1]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=3-3]
	\arrow[&quot;\Delta&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\langle f,g\rangle}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where the diagonal map is a section, and for any section $s:A\to B$ with retraction $r:B\to A$, $s$ is the equalizer of the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20B%20%26%20B%0A%09%5Carrow%5B%22s%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7Bs%5Ccirc%20r%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B1_B%7D%22'%2C%20shift%20right%3D2%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; B &amp; B
	\arrow[&quot;s&quot;, from=1-1, to=1-2]
	\arrow[&quot;{s\circ r}&quot;, shift left=2, from=1-2, to=1-3]
	\arrow[&quot;{1_B}&quot;', shift right=2, from=1-2, to=1-3]
\end{tikzcd}
" /></p>

For **(9)** we can proceed simultaneously. Let $g:X\to Y$ be in $\mathcal{A}^{\perp_w}$ or ${^{\perp_w}}\mathcal{A}$ and consider the section-retraction pair in the arrow category along with the lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20%7BX'%7D%20%26%20X%20%26%20%7BX'%7D%20%26%20A%20%5C%5C%0A%09B%20%26%20%7BY'%7D%20%26%20Y%20%26%20%7BY'%7D%20%26%20B%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22s%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bg'%7D%22'%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22r%22%2C%20from%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22g%22'%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7Bu'%7D%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%7Bg'%7D%22%2C%20from%3D1-4%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-5%2C%20to%3D2-5%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Bs'%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D2-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%7Br'%7D%22'%2C%20from%3D2-3%2C%20to%3D2-4%5D%0A%09%5Carrow%5B%22%7Bv'%7D%22'%2C%20from%3D2-4%2C%20to%3D2-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; {X'} &amp; X &amp; {X'} &amp; A \\
	B &amp; {Y'} &amp; Y &amp; {Y'} &amp; B
	\arrow[&quot;u&quot;, from=1-1, to=1-2]
	\arrow[&quot;f&quot;', from=1-1, to=2-1]
	\arrow[&quot;s&quot;, from=1-2, to=1-3]
	\arrow[&quot;{g'}&quot;', from=1-2, to=2-2]
	\arrow[&quot;r&quot;, from=1-3, to=1-4]
	\arrow[&quot;g&quot;', from=1-3, to=2-3]
	\arrow[&quot;{u'}&quot;, from=1-4, to=1-5]
	\arrow[&quot;{g'}&quot;, from=1-4, to=2-4]
	\arrow[&quot;f&quot;', from=1-5, to=2-5]
	\arrow[dashed, from=2-1, to=1-3]
	\arrow[&quot;v&quot;', from=2-1, to=2-2]
	\arrow[&quot;{s'}&quot;', from=2-2, to=2-3]
	\arrow[dashed, from=2-3, to=1-5]
	\arrow[&quot;{r'}&quot;', from=2-3, to=2-4]
	\arrow[&quot;{v'}&quot;', from=2-4, to=2-5]
\end{tikzcd}
" /></p>

Then if $k:B\to X$ is the left lift in the diagram, $g'\circ r\circ k = r'\circ s'\circ  v = v$ and $r\circ k\circ f = r\circ s \circ u = u$, so $r\circ k$ is our desired lift. On the other hand, if $k':Y\to A$ is the right lift in the diagram, then $k'\circ s'\circ g' = u'\circ r\circ s = u'$ and $f\circ k'\circ s' = v'\circ r'\circ s' = v'$, so $k'\circ s'$ is our desired lift.

Finally, we prove both cases for **(10)**. Let $f$ be a transfinite composition of morphisms in ${^{\perp_w}}\mathcal{A}$, which is witnessed by a functor $F:\text{Ord}_{\leq\alpha}\to \mathcal{C}$, for $\alpha$ an ordinal. Let $g:A\to B$ be in $\mathcal{A}$ and consider the lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BC_0%7D%20%26%20A%20%5C%5C%0A%09%7BC_%5Calpha%7D%20%26%20B%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{C_0} &amp; A \\
	{C_\alpha} &amp; B
	\arrow[&quot;u&quot;, from=1-1, to=1-2]
	\arrow[&quot;f&quot;', from=1-1, to=2-1]
	\arrow[&quot;g&quot;, from=1-2, to=2-2]
	\arrow[&quot;v&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

For each $\beta \leq \alpha$, we can re-write this lifting problem as a factored lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BC_0%7D%20%26%26%20A%20%5C%5C%0A%09%7BC_%5Cbeta%7D%20%5C%5C%0A%09%7BC_%5Calpha%7D%20%26%26%20B%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bf_%5Cbeta%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bu_%5Cbeta%7D%22'%2C%20dashed%2C%20from%3D2-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bf_%7B%5Calpha%2C%5Cbeta%7D%7D%22'%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{C_0} &amp;&amp; A \\
	{C_\beta} \\
	{C_\alpha} &amp;&amp; B
	\arrow[&quot;u&quot;, from=1-1, to=1-3]
	\arrow[&quot;{f_\beta}&quot;', from=1-1, to=2-1]
	\arrow[&quot;g&quot;, from=1-3, to=3-3]
	\arrow[&quot;{u_\beta}&quot;', dashed, from=2-1, to=1-3]
	\arrow[&quot;{f_{\alpha,\beta}}&quot;', from=2-1, to=3-1]
	\arrow[&quot;v&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

we construct the lifts $u_\beta:C_\beta\to A$ by transfinite induction on $\alpha$. First, by assumption $f_1 = f_{1,0}:C_0\to C_1$ is in ${^{\perp_w}}\mathcal{A}$, so we have such a lift $u_1$. Now, by induction suppose such lifts $\{u_\beta\}_{\beta < \gamma}$ exists, where in addition $u_{\delta} = u_\beta\circ f_{\delta,\beta}$ for any $\delta \leq \beta < \gamma$. If $\gamma$ is a successor ordinal, so $\gamma = \beta+1$ for some ordinal $\beta < \gamma$, then since $f_{\beta+1,\beta}$ is in ${^{\perp_w}}\mathcal{A}$, we obtain a lift $u_{\beta+1}:C_{\beta+1}\to A$ such that $u_{\beta} = u_{\beta+1}\circ f_{\beta+1,\beta}$, and $g\circ u_{\beta+1} = v\circ f_{\alpha,\beta+1}$.

On the other hand, suppose $\gamma$ is a limit ordinal. Then $C_\gamma = \text{colim}_{\beta < \gamma}C_\beta$ and by assumption the $u_\beta$, for $\beta < \gamma$, form a cone over $A$. Thus, we have a unique $u_\gamma:C_\gamma\to A$ such that $u_\beta = u_\gamma\circ f_{\gamma,\beta}$ for any $\beta < \gamma$. Additionally, the $g\circ u_\beta$ make $B$ a cone, and so by uniqueness $g\circ u_\gamma = v\circ f_{\alpha,\gamma}$.

By transfinite induction it follows that we obtain our desired lift $u_\alpha:C_\alpha\to A$. Taking ops everywhere we obtain the equivalent case for $\mathcal{A}^{\perp_w}$.
`\end{proof}`

>[!def] Saturated Set
>Let $\mathcal{C}$ be a category with small colimits and let $\mathcal{A}$ be a collection of morphisms in $\mathcal{C}$. We say $\mathcal{A}$ is **weakly saturated** if it is closed under pushouts, retracts in the arrow category, and transfinite composition.

It follows that for any class of morphisms $\mathcal{A}$, ${^\perp}\mathcal{A}$ and ${^{\perp_w}}\mathcal{A}$ are **weakly saturated**. Note that intersections of collections of morphisms which are weakly saturated are also weakly saturated, so every class of morphisms $\mathcal{A}_0$ has a smallest class of morphisms $\mathcal{A}$ containing it which is weakly saturated. It follows that $\mathcal{A} \subseteq {^{\perp_w}}(\mathcal{A}_0^{\perp_w})$, and if $\mathcal{A}_0$ is weakly left orthogonal to some class of maps $\mathcal{B} \subseteq \mathcal{A}_0^{\perp_w}$, then necessarily so is $\mathcal{A}$.

### Trivial Kan Fibrations

We now specialize our work on lifting properties to simplicial sets.

>[!def] Trivial Kan Fibration
>Let $q:X\to Y$ be a morphism of simplicial sets. Then $q$ is said to be a **trivial Kan fibration** if $\{q\}$ is weakly right orthogonal to the set $\{\partial\Delta^n\hookrightarrow \Delta^n\,:\,n\geq 0\}$.

Let $\mathcal{W} = \{\partial\Delta^n\hookrightarrow\Delta^n\,:\,n\geq 0\}^{\perp_w}$ denote the class of weakly right orthogonal maps to the simplex boundary inclusions, i.e. the collection of all trivial Kan fibrations. Then by [[Introduction to Quasi-Categories#^193325]] we have that $\mathcal{W}$ is closed under isomorphisms, composition, pullbacks, products, left composition by monics, retractions in the arrow category, and transfinite cocomposition. We now aim to obtain a simpler description of $\mathcal{W}$.

>[!proposition] Weakly Saturated Class of Morphisms Generated by Boundary Inclusions
>Let $\mathcal{M}$ be the class of all monomorphisms in $\mathsf{sSet}$ (i.e. pointwise injective maps). Then $\mathcal{M}$ is the weak saturation of $\{\partial\Delta^n\hookrightarrow \Delta^n\}_{n\geq 0}$.

`\begin{proof}`
We first show that $\mathcal{M}$ is weakly saturated before  showing it is the weak saturation of the set of boundary inclusions.

**Part (1)** First, recall that in any category, a morphism $f:A\to B$ is a monomorphism if and only if the square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20A%20%5C%5C%0A%09A%20%26%20B%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; A \\
	A &amp; B
	\arrow[Rightarrow, no head, from=1-1, to=1-2]
	\arrow[Rightarrow, no head, from=1-1, to=2-1]
	\arrow[&quot;f&quot;, from=1-2, to=2-2]
	\arrow[&quot;f&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

is a pullback. We must show $\mathcal{M}$ is closed under pushouts, retracts in the arrow category, and transfinite composition. In general pushouts do not preserve monics, but for sets, if we have a pushout

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%20C%20%5C%5C%0A%09B%20%26%20D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7Bf'%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Bg'%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D180%7D%2C%20draw%3Dnone%2C%20from%3D2-2%2C%20to%3D1-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp; C \\
	B &amp; D
	\arrow[&quot;g&quot;, from=1-1, to=1-2]
	\arrow[&quot;f&quot;', from=1-1, to=2-1]
	\arrow[&quot;{f'}&quot;, from=1-2, to=2-2]
	\arrow[&quot;{g'}&quot;', from=2-1, to=2-2]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=180}, draw=none, from=2-2, to=1-1]
\end{tikzcd}
" /></p>

where $f$ is injective. Then we have the concrete model for $D = B\amalg C/\sim$, where $\sim$ is generated by $f(a)\sim g(a)$ for $a \in A$. Now, suppose $c,c' \in C$ such that $c \sim c'$ in $D$. Then either $c = c'$, or we must have some $a \in A$ with $g(a) = c$, and $f(a)\sim c'$. Then there is some $a' \in A$ such that $f(a) = f(a')$, and $g(a') = c'$. But $f$ is injective so $a = a'$, and hence $c = c'$. Thus $f'$ will be injective. Therefore, since monics in $\mathsf{Set}$ are preserved by pushouts and since colimits in $\mathsf{sSet}$ are computed term-wise, monics in $\mathsf{sSet}$ are preserved by pushouts.

Now, suppose $f:A\to B$ is injective and suppose $g:C\to D$ is a retract of $f$, so that we have a diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09C%20%26%20A%20%26%20C%20%5C%5C%0A%09D%20%26%20B%20%26%20D%0A%09%5Carrow%5B%22s%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22g%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22r%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7Bs'%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Br'%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	C &amp; A &amp; C \\
	D &amp; B &amp; D
	\arrow[&quot;s&quot;, from=1-1, to=1-2]
	\arrow[&quot;g&quot;', from=1-1, to=2-1]
	\arrow[&quot;r&quot;, from=1-2, to=1-3]
	\arrow[&quot;f&quot;, from=1-2, to=2-2]
	\arrow[&quot;g&quot;, from=1-3, to=2-3]
	\arrow[&quot;{s'}&quot;', from=2-1, to=2-2]
	\arrow[&quot;{r'}&quot;', from=2-2, to=2-3]
\end{tikzcd}
" /></p>

Since $s'\circ g = f\circ s$ is monic it follows that $g$ is also monic, and hence monics in any category are closed under retracts in the arrow category.

Finally, we show $\mathcal{M}$ is closed under transfinite composition by transfinite induction. Let $\{f_{\beta+1,\beta}\}_{\beta < \alpha}$ be a collection of composable monics where $\alpha$ is an ordinal. If $\alpha = 1$ then the collection consists only of $f_{1,0}$, which is monic, so there is nothing to show. 

Now, suppose $f_{\beta,\delta}$ is monic or all $\delta \leq \beta < \alpha$. If $\alpha$ is a successor ordinal we have some $\beta < \alpha$ such that $\beta + 1 = \alpha$. Then for any $\delta \leq \beta$, $f_{\alpha,\delta} = f_{\beta+1,\beta}\circ f_{\beta,\delta}$ which is monic since the composite of two monics is monic.

On the other hand, suppose $\alpha$ is a limit ordinal, so $\text{colim}_{\beta < \alpha}C_\beta = C_\alpha$. Since monomorphisms are classified by finite limits, and finite limits commute with filtered colimits, it follows that the colimit $f_{\alpha,\delta}:C_\delta\to C_\alpha$ is a monomorphism.

**Part (2)** Note that $\mathcal{M}$ contains the set of all boundary maps, so it remains to show that it is the smallest such set that is weakly saturated. To do this, suppose $\mathcal{M}'$ is another such set and let $i:A\hookrightarrow B$ be a monomorphism. For $k \geq -1$, let $B(k) = \text{sk}_k(B)\cup i(A)$ in $B$. Then $i$ is the transfinite composition
$$A=B(-1)\hookrightarrow B(0)\hookrightarrow B(1)\hookrightarrow \cdots$$
Since $\mathcal{M}'$ is weakly saturated it suffices to show $B(k-1)\hookrightarrow B(k)$ is in $\mathcal{M}'$ for each $k \geq 0$. Now, we have the pushout square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ccoprod_%7B%5Csigma%20%5Cin%20B%5E%7Bnd%7D_k%5Cbackslash%20i(A_k)%7D%5Cpartial%5CDelta%5Ek%7D%20%26%26%20%7BB(k-1)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Ccoprod_%7B%5Csigma%20%5Cin%20B%5E%7Bnd%7D_k%5Cbackslash%20i(A_k)%7D%5CDelta%5Ek%7D%20%26%26%20%7BB(k)%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D180%7D%2C%20draw%3Dnone%2C%20from%3D3-3%2C%20to%3D1-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\coprod_{\sigma \in B^{nd}_k\backslash i(A_k)}\partial\Delta^k} &amp;&amp; {B(k-1)} \\
	\\
	{\coprod_{\sigma \in B^{nd}_k\backslash i(A_k)}\Delta^k} &amp;&amp; {B(k)}
	\arrow[from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[hook, from=1-3, to=3-3]
	\arrow[from=3-1, to=3-3]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=180}, draw=none, from=3-3, to=1-1]
\end{tikzcd}
" /></p>

Again, since $\mathcal{M}'$ is weakly saturated it suffices to show that the inclusion
$$j:\coprod_{\sigma \in B^{nd}_k\backslash i(A_k)}\partial\Delta^k\hookrightarrow\coprod_{\sigma \in B^{nd}_k\backslash i(A_k)}\Delta^k$$
is in $\mathcal{M}'$ by induction. By the axiom of choice we can choose a well-ordering on $B_k^{nd}\backslash i(A_k)$, and so write $j$ as a transfinite composition of morphisms
$$j_\sigma:\left(\coprod_{\tau\geq \sigma}\partial\Delta^k\right)\amalg\left(\coprod_{\tau< \sigma}\Delta^k\right)\hookrightarrow \left(\coprod_{\tau> \sigma}\partial\Delta^k\right)\amalg\left(\coprod_{\tau\leq \sigma}\Delta^k\right)$$
which is a pushout of the inclusion $\partial\Delta^k\hookrightarrow \Delta^k$.
`\end{proof}`

We can now provide a simple classification of trivial Kan fibration.

>[!corollary] Classification of Trivial Kan Fibrations
>Let $p:X\to Y$ be a map of simplicial sets. Then $p$ is a trivial Kan fibration if and only if $p$ is weakly right orthogonal to all monomorphisms of simplicial sets.

^26d07a

An easy consequence of [[Introduction to Quasi-Categories#^26d07a]] is that every trivial Kan fibration $p:X\to Y$ is a retraction (i.e. has a section) since we can form the lifting problem with left hand side $\emptyset\hookrightarrow Y$, top map the unique one, and bottom map the identity.

>[!corollary] Section of trivial Kan fibrations
>If $p:X\to Y$ is a trivial Kan fibration of simplicial sets, then $p$ admits a section. Further, if $s:Y\to X$ is a section of $p$, the composite $s\circ p:X\to X$ is **fiberwise homotopic to the identity**. In other words, we have a map of simplicial sets $h:\Delta^1\times X\to X$, which is identity upon projection onto $Y$, and such that $h\vert_{\{0\}\times X} = s\circ p$ and $h\vert_{\{1\}\times X} = \text{id}_X$.

`\begin{proof}`
The first part of the claim was argued above. Thus, let $s:Y\to X$ be such a section. We can then form the lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cpartial%5CDelta%5E1%5Ctimes%20X%7D%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5E1%5Ctimes%20X%7D%20%26%26%20Y%0A%09%5Carrow%5B%22%7Bs%5Ccirc%20p%5Camalg%20%5Ctext%7Bid%7D_X%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22h%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bp%5Ccirc%20%5Cpi_1%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\partial\Delta^1\times X} &amp;&amp; X \\
	\\
	{\Delta^1\times X} &amp;&amp; Y
	\arrow[&quot;{s\circ p\amalg \text{id}_X}&quot;, from=1-1, to=1-3]
	\arrow[hook', from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[&quot;h&quot;, dashed, from=3-1, to=1-3]
	\arrow[&quot;{p\circ \pi_1}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where we use the fact that $\partial\Delta^1 \cong \Delta^0\coprod\Delta^0$, and products distribute in $\mathsf{sSet}$, so $\partial\Delta^1\times X\cong X\coprod X$. Note the lift $h$ is our desired homotopy and exists by [[Introduction to Quasi-Categories#^26d07a]] since the left hand map is a monomorphism.
`\end{proof}`

We now investigate some interesting constructions on trivial Kan fibrations.

>[!corollary] Functor map for trivial Kan fibration
>Let $p:X\to Y$ be a trivial Kan fibration and let $i:A\to B$ be a monomorphism. Then the map
>$$\theta:\text{Fun}(B,X)\xrightarrow{(p\circ-,-\circ i)}\text{Fun}(B,Y)\times_{\text{Fun}(A,Y)}\text{Fun}(A,X)$$
>is a trivial Kan fibration.

`\begin{proof}`
We show the lifting problem has a solution when considering boundary maps. Thus, suppose $n \geq 0$ and that we have a lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cpartial%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7BFun%7D(B%2CX)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7BFun%7D(B%2CY)%5Ctimes_%7B%5Ctext%7BFun%7D(A%2CY)%7D%5Ctext%7BFun%7D(A%2CX)%7D%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%5Ctheta%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\partial\Delta^n} &amp;&amp; {\text{Fun}(B,X)} \\
	\\
	{\Delta^n} &amp;&amp; {\text{Fun}(B,Y)\times_{\text{Fun}(A,Y)}\text{Fun}(A,X)}
	\arrow[&quot;u&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;\theta&quot;, from=1-3, to=3-3]
	\arrow[&quot;v&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where $v = (f,g)$. Having a lift $k:\Delta^n\to \text{Fun}(B,X)$ is equivalent, using our adjunction, to having a map $k^\flat:\Delta^n\times B\to X$, where the equalities $(p\circ -)\circ k = f$, $(-\circ i)\circ k = g$, and $k\circ \iota_n = u$ become $p\circ k^\flat = f^\flat$, $k^\flat\circ i = g^\flat$, and $u^\flat = k^\flat \circ (\iota_n\times 1_B)$. In summary, after taking adjoints this lifting problem becomes equivalent to the lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B(%5Cpartial%5CDelta%5En%5Ctimes%20B)%5Ccoprod_%7B%5Cpartial%5CDelta%5En%5Ctimes%20A%7D(%5CDelta%5En%5Ctimes%20A)%7D%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%5Ctimes%20B%7D%20%26%26%20Y%0A%09%5Carrow%5B%22%7B(u%5E%5Cflat%2Cg%5E%5Cflat)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B(%5Ciota_n%5Ctimes%201_B)%5Camalg(1_%7B%5CDelta%5En%7D%5Ctimes%20i)%7D%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bf%5E%5Cflat%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{(\partial\Delta^n\times B)\coprod_{\partial\Delta^n\times A}(\Delta^n\times A)} &amp;&amp; X \\
	\\
	{\Delta^n\times B} &amp;&amp; Y
	\arrow[&quot;{(u^\flat,g^\flat)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{(\iota_n\times 1_B)\amalg(1_{\Delta^n}\times i)}&quot;', hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[&quot;{f^\flat}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

which has a solution by [[Introduction to Quasi-Categories#^26d07a]] since the left-hand map is a monomorphism.
`\end{proof}`

As a special case when $A = \emptyset$ we obtain the following corollary immediately:

>[!corollary] Postcomposition by a trivial Kan fibration is a trivial Kan fibration
>If $p:X\to Y$ is a trivial Kan fibration, then for every simplicial set $B$, the induced map $p\circ -:\text{Fun}(B,X)\to \text{Fun}(B,Y)$ is a trivial Kan fibration.

^fe96ec


An important piece of homotopy theory is the notion of being contractible, and this will be essential for our formalization of the statement that we have a "coherent space of homotopies".

>[!def] Contractible Kan complex
>If $X$ is a simplicial set, we say $X$ is a **contractible Kan complex** if the unique map $X\to \Delta^0$ is a trivial Kan fibration. 

Note that this definition is equivalent to the statement that every boundary map $\sigma_0:\partial\Delta^n\to X$ can be extended to an $n$-simplex $\sigma:\Delta^n\to X$, which geometrically signals that $X$ has no holes (i.e. should have trivial homotopy type).

>[!example]
>Let $X$ be a topological space. Then $\text{Sing}_\bullet(X)$ is a contractible Kan complex if and only if $X$ is **weakly contractible**, which is to say every continuous map $\sigma_0:S^{n-1}\to X$ is nullhomotopic, so $\pi_n(X,x) = \{*\}$ for all $n\geq 0$.

In addition to this wealth of examples from topology, for any trivial Kan fibration $p:X\to Y$, and any $0$-simplex $y$ of $Y$, the fiber $X\times_Y\{y\}$ is a contractible kan complex, since the map $X\times_Y\{y\}\to \{y\}\cong \Delta^0$ is the pullback of $p$, and so itself a trivial Kan fibration.

>[!proposition] Kan complexes and trivial Kan fibrations
>Let $p:X\to Y$ be a trivial Kan fibration of simplicial sets. Then
>1. If $X$ is a Kan complex so is $Y$
>2. If $X$ is a contractible Kan complex so is $Y$
>3. If $X$ is a quasi-category so is $Y$.

`\begin{proof}`
Let $n > 0$. Then for any $0\leq i \leq n$ and any $\Lambda_i^n\to Y$ we have a lift

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%5Cemptyset%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CLambda_i%5En%7D%20%26%26%20Y%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	\emptyset &amp;&amp; X \\
	\\
	{\Lambda_i^n} &amp;&amp; Y
	\arrow[from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[dashed, from=3-1, to=1-3]
	\arrow[from=3-1, to=3-3]
\end{tikzcd}
" /></p>

since $p$ is a trivial Kan fibration. If $\Lambda_i^n\to X$ has a filling $\Delta^n\to X$, then post-composing with $p$ gives a filling for $\Lambda_i^n\to Y$. This proves **(1)** and **(3)**. The same argument can be made with $\Lambda_i^n$ replaced by $\partial\Delta^n$, which will prove **(2)**.
`\end{proof}`

This allows us to obtain an equivalent description of contractible Kan complexes.

>[!corollary] Classification of contractible Kan complexes
>Let $X$ be a simplicial set. Then the following are equivalent:
>1. $X$ is a contractible Kan complex
>2. For every monomorphism $i:A\to B$ and every map $f_0:A\to X$, there exists a map $f:B\to X$ such that $f_0=f\circ i$.

This is an application of [[Introduction to Quasi-Categories#^26d07a]]. We immediately obtain the following:

>[!corollary] Contractible Kan Complexes are Kan Complexes
>If $X$ is a contractible Kan complex then it is a Kan complex, and so in particular a quasi-category.

Another important property of trivial Kan fibrations is that they are preserved under filtered colimits.

>[!proposition] Filtered Colimits of trivial Kan fibrations
>The class of trivial Kan fibrations, $\mathcal{W}$, is closed under filtered colimits in the arrow category.

^13abed

`\begin{proof}`
Let $F:I\to \text{Arr}(\mathsf{sSet})$ be a filtered diagram such that for all $i \in I$, $F(i) \in \mathcal{W}$. Note that since $\mathsf{sSet}$ is cocomplete the colimit, $g:X\to Y$, exists, and $X = \text{colim}(s\circ F)$ and $Y = \text{colim}(t\circ F)$ where $s$ and $t$ are the source and target functors. Now let $i:A\to B$ be a monomorphism, and consider a lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09A%20%26%26%20X%20%5C%5C%0A%09%5C%5C%0A%09B%20%26%26%20Y%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22i%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	A &amp;&amp; X \\
	\\
	B &amp;&amp; Y
	\arrow[&quot;u&quot;, from=1-1, to=1-3]
	\arrow[&quot;i&quot;', from=1-1, to=3-1]
	\arrow[&quot;g&quot;, from=1-3, to=3-3]
	\arrow[&quot;v&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

Note that for each $i \in I$, we obtain a restricted lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bu%5E%7B-1%7D(X_i)%7D%20%26%26%20%7BX_i%7D%20%26%20X%20%5C%5C%0A%09%5C%5C%0A%09%7Bv%5E%7B-1%7D(Y_i)%7D%20%26%26%20%7BY_i%7D%20%26%20Y%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bi%5Cvert_%7Bu%5E%7B-1%7D(X_i)%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5B%22%7Bg_i%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-3%2C%20to%3D3-4%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{u^{-1}(X_i)} &amp;&amp; {X_i} &amp; X \\
	\\
	{v^{-1}(Y_i)} &amp;&amp; {Y_i} &amp; Y
	\arrow[&quot;u&quot;, from=1-1, to=1-3]
	\arrow[&quot;{i\vert_{u^{-1}(X_i)}}&quot;', from=1-1, to=3-1]
	\arrow[from=1-3, to=1-4]
	\arrow[&quot;{g_i}&quot;, from=1-3, to=3-3]
	\arrow[&quot;g&quot;, from=1-4, to=3-4]
	\arrow[dashed, from=3-1, to=1-3]
	\arrow[&quot;v&quot;', from=3-1, to=3-3]
	\arrow[from=3-3, to=3-4]
\end{tikzcd}
" /></p>

which has a solution, say $f_i:v^{-1}(Y_i)\to X_i$, since the restriction of a monomorphism (i.e. a composite of two monomorphisms) is again a monomorphism. We want to glue these morphisms together. For this suppose $a \in v^{-1}(Y_i)\cap v^{-1}(Y_j)$. Then $g(f_i(a)) = g(f_j(a))$, which implies that we have some $k \in I$, with $i,j\leq k$ such that $r_k(g_i(f_i(a))) = r_k(g_j(f_j(a)))$ in $Y_k$.
**TBC/DO NOT KNOW**


### Contractible Space of Homotopies for Composition

Throughout let $\mathcal{C}$ be a quasi-category. In this section we aim to describe a partial uniqueness result for composites in $\mathcal{C}$. We know from [[Introduction to Quasi-Categories#^972080]] that composites are unique up to homotopy. In this section we endeavour to obtain a stronger result that the $2$-simplexes themselves which witness the composites are unique up to a **contractible space of choices**.

The following result will be proven later:

>[!thm] Classification of quasi-categories (due to Joyal)
>Let $S$ be a simplicial set. Then the following are equivalent:
>1. $S$ is a quasi-category
>2. the inclusion $\Lambda_1^2\hookrightarrow \Delta^2$ induces a trivial Kan fibration
>$$\text{Fun}(\Delta^2,S)\to \text{Fun}(\Lambda_1^2,S)$$

^d95c8b

As an immediate corollary we obtain the following:

>[!corollary] Contractible Space of Composites
>Let $f:x\to y$ and $g:y\to z$ be a composable pair of morphisms in a quasi-category $\mathcal{C}$. Let $(g,-,f):\Lambda_1^2\to \mathcal{C}$ be the associated inner horn. Then the fiber product
>$$\text{Fun}(\Delta^2,\mathcal{C})\times_{\text{Fun}(\Lambda_1^2,\mathcal{C})}\{(g,-,f)\}$$
>is a contractible Kan complex

where we have used the fact that for any trivial Kan fibration $p:X\to Y$, $X\times_Y\{y\}$ is a contractible Kan complex for any point $y$ in $Y$. Intuitively the fiber product $\text{Fun}(\Delta^2,\mathcal{C})\times_{\text{Fun}(\Lambda_1^2,\mathcal{C})}\{(g,-,f)\}$ represents the space of those $2$-simplexes which witness composites of $g$ and $f$, and so the corollary says that this space is (weakly) contractible.

[[Introduction to Quasi-Categories#^d95c8b]] also lets us finally show that functor simplicial sets are quasi-categories when the codomain is a quasi-category.

>[!thm] Quasi-categories are an exponentiable ideal
>Let $S$ be a simplicial set and let $\mathcal{D}$ be a quasi-category. Then $\mathcal{D}^S = \text{Fun}(S,\mathcal{D})$ is a quasi-category.

`\begin{proof}`
By [[Introduction to Quasi-Categories#^d95c8b]] it suffices to show that the restriction map
$$r:\text{Fun}(\Delta^2,\text{Fun}(S,\mathcal{D}))\to \text{Fun}(\Lambda_1^2,\text{Fun}(S,\mathcal{D}))$$
is a trivial Kan fibration. Since isomorphisms are trivial Kan fibrations, it suffices to show that the corresponding map

$$\text{Fun}(S,\text{Fun}(\Delta^2,\mathcal{D}))\to \text{Fun}(S,\text{Fun}(\Lambda_1^2,\mathcal{D}))$$

is a trivial Kan fibration, which follows by [[Introduction to Quasi-Categories#^fe96ec]] and [[Introduction to Quasi-Categories#^d95c8b]].
`\end{proof}`

Before proving [[Introduction to Quasi-Categories#^d95c8b]] we go on a brief digression.

#### Inner Anodyne Maps

>[!def] Inner Anodyne Map
>Let $f:A\to B$ be a map of simplicial sets. Then we say $f$ is **inner anodyne** if it belongs to the smallest weakly saturated class of morphisms containing all inner horn inclusions, $\Lambda_i^n\hookrightarrow \Delta^n$, for $0 < i < n$.

Note that since every inner horn inclusion is a monomorphism, the collection of inner anodyne maps must be contained in the collection of monomorphisms by minimality, since it is weakly saturated.

>[!claim] Inner Anodyne $\implies$ bijective on $0$-simplices
>If $f:A\to B$ is an inner anodyne map, then it is bijective on $0$-simplices.

`\begin{proof}`
Since $f$ is a monomorphism it is injective on $0$-simplices, so it suffices to show that it is surjective on $0$-simplices. Note that all inner horn inclusions are surjective on $0$-simplices, and that this property is preserved by pushouts, retracts in the arrow category, and filtered colimits, so in particular transfinite composition.
`\end{proof}`


>[!proposition] Quasi-category Classification in terms of Inner Anodyne Maps
>Let $S$ be a simplicial set. Then $S$ is a quasi-category if and only if for every inner anodyne map of simplicial sets $i:A\hookrightarrow B$, and every $f_0:A\to S$, there exists a map $f:B\to S$ such that $f_0= f\circ i$.

^4c6682

`\begin{proof}`
Note that the set of inner anodyne maps is contained in the weakly saturated class ${^{\perp_w}}(\{\Lambda_i^n\hookrightarrow \Delta^n\,:\,0 < i < n\}_{n\geq 2}^{\perp_w})$. Note that $\{\Lambda_i^n\hookrightarrow \Delta^n\,:\,0 < i < n\}_{n\geq 2}^{\perp_w}$ contains the map $S\to \Delta^0$ if and only if $S$ is a quasi-category. It follows that $S$ is a quasi-category if and only if $(A\hookrightarrow B)\perp_w(S\to \Delta^0)$ for any inner anodyne map $A\hookrightarrow B$.
`\end{proof}`

Replacing $\perp_w$ by $\perp$ in [[Introduction to Quasi-Categories#^4c6682]] we obtain the following corollary immediately:

>[!corollary] Nerve Classification in terms of Inner Anodyne Maps
>A simplicial set $S$ is a nerve of an ordinary category if and only if for every inner anodyne map of simplicial sets $i:A\hookrightarrow B$, and every $f_0:A\to S$, there exists a *unique* map $f:B\to S$ such that $f_0 = f\circ i$.

We need one more combinatorial result before we can prove our main claim.

>[!lem] Combinatorial Lemma for Quasi-Cateogry Classification (due to Joyal)
>1. If $i:A\hookrightarrow B$ is a monomorphism of simplicial sets, the induced map $$(B\times \Lambda_1^2)\bigcup_{A\times \Lambda_1^2}(A\times \Delta^2)\hookrightarrow B\times \Delta^2$$
>is inner anodyne
>2. The collection of inner anodyne maps is generated as a weakly saturated class by the inclusions $$(\Delta^m\times \Lambda_1^2)\bigcup_{\partial\Delta^m\times \Lambda_1^2}(\partial\Delta^m\times \Delta^2)\hookrightarrow \Delta^m\times \Delta^2$$
>for all $m \geq 0$

^ef92d0

`\begin{proof}`
Let $\mathcal{M}$ be the weakly saturated class generated by the maps in **(2)** and let $\mathcal{N}$ denote the collection of all maps $A\to B$ such that the corresponding map in **(1)** is in $\mathcal{M}$. Since products and colimits commute with colimits in $\mathsf{sSet}$ the fact that $\mathcal{M}$ is weakly saturated implies that so is $\mathcal{N}$. Note that by construction $\mathcal{N}$ contains all boundary inclusions, $\partial\Delta^m\hookrightarrow \Delta^m$, and since $\mathcal{N}$ is weakly saturated it follows that $\mathcal{N}$ contains all monomorphisms.

I claim that all inner anodyne maps are in $\mathcal{M}$. Since $\mathcal{M}$ is weakly saturated it suffices to show that all inner horn inclusions are in $\mathcal{M}$. Note that if $f:\Lambda_i^n\hookrightarrow \Delta^n$ is an inner horn inclusion belongs to $\mathcal{N}$ since it is a monomorphism. Thus the monomorphism
$$\overline{f}:(\Delta^n\times \Lambda_1^2)\bigcup_{\Lambda_i^n\times \Lambda_1^2}(\Lambda_i^n\times \Delta^2)\hookrightarrow \Delta^n\times \Delta^2$$
belongs to $\mathcal{M}$. Now we have the retract

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_i%5En%7D%20%26%26%20%7B(%5CDelta%5En%5Ctimes%20%5CLambda_1%5E2)%5Ccoprod_%7B%5CLambda_i%5En%5Ctimes%20%5CLambda_1%5E2%7D(%5CLambda_i%5En%5Ctimes%20%5CDelta%5E2)%7D%20%26%26%20%7B%5CLambda_i%5En%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%7D%20%26%26%20%7B%5CDelta%5En%5Ctimes%20%5CDelta%5E2%7D%20%26%26%20%7B%5CDelta%5En%7D%0A%09%5Carrow%5B%22%7Bs'%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7Br'%7D%22%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-5%2C%20to%3D3-5%5D%0A%09%5Carrow%5B%22s%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22r%22'%2C%20from%3D3-3%2C%20to%3D3-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_i^n} &amp;&amp; {(\Delta^n\times \Lambda_1^2)\coprod_{\Lambda_i^n\times \Lambda_1^2}(\Lambda_i^n\times \Delta^2)} &amp;&amp; {\Lambda_i^n} \\
	\\
	{\Delta^n} &amp;&amp; {\Delta^n\times \Delta^2} &amp;&amp; {\Delta^n}
	\arrow[&quot;{s'}&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;{r'}&quot;, from=1-3, to=1-5]
	\arrow[hook, from=1-3, to=3-3]
	\arrow[hook, from=1-5, to=3-5]
	\arrow[&quot;s&quot;', from=3-1, to=3-3]
	\arrow[&quot;r&quot;', from=3-3, to=3-5]
\end{tikzcd}
" /></p>

where $s$ is the $n$-simplex corresponding to the map of posets $[n]\to [n]\times [2]$ where sends $j$ to $(j,0)$ is $j < i$, $(j,1)$ is $j = i$, and $(j,2)$ if $j > i$. The map $r$ is given by the map of posets $[n]\times [2]\to [n]$ given by  
$$r(j,k) = \left\{\begin{array}{cc} j & j < i,k=0 \\ j & j > i,k=2 \\ i & \text{else} \end{array}\right.$$

Composing $f$ with $s$ we have component maps $f:\Lambda_i^n\to \Delta^n$, so $s'$ is the restriction of $s$ which corresponds to a map $\Lambda_i^n\to (\Lambda_i^n\times \Delta^2)$. On the other hand, $r'$ is given by restriction on $r$ on each component. Since $\mathcal{M}$ is saturated it follows it follows that all inner horns, and hence all inner anodyne morphisms are in $\mathcal{M}$.

It remains to show that every morphism in $\mathcal{M}$ is inner anodyne which is equivalent to showing that each inclusion $$(\Delta^m\times \Lambda_1^2)\coprod_{\partial\Delta^m\times \Lambda_1^2}(\partial\Delta^m\times \Delta^2)\hookrightarrow \Delta^m\times \Delta^2$$ is inner anodyne. For $0 \leq i \leq j \leq m$, let $\tau_{ij}$ denote the $(m+2)$-simplex of $\Delta^m\times \Delta^2$ represented by the map of partially ordered sets $g_{ij}:[m+2]\to [m]\times [2]$ given by 
$$g_{ij}(k) = \left\{\begin{array}{cc} (k,0) & 0\leq k \leq i \\ (k-1,1) & i+1\leq k \leq j+1 \\ (k-1,2) & j+2\leq k \leq m+2 \end{array}\right.$$
For $0 \leq i \leq j < m$, let $\sigma_{ij}$ be the $(m+1)$-simplex of $\Delta^m\times \Delta^2$ given by the map of partially ordered sets $f_{ij}:[m+1]\to [m]\times [2]$ given by
$$f_{ij} = g_{ij}\circ \delta_{m+2}^{m+2}$$
We regard the $\sigma_{ij}$ and $\tau_{ij}$ as simplicial subsets of $\Delta^m\times \Delta^2$ generated by the simplex they represent.

Next, set $X(0) = (\Delta^m\times \Lambda_1^2)\coprod_{\partial\Delta^m\times \Lambda_1^2}(\partial\Delta^m\times \Delta^2)$. For $0 \leq j < m$, define
$$X(j+1) = X(j)\cup \sigma_{0j}\cup \cdots\cup \sigma_{jj}$$
which induces a chain of inclusions 
$$X(j)\hookrightarrow X(j)\cup \sigma_{0j}\hookrightarrow \cdots \hookrightarrow X(j)\cup \sigma_{0j}\cup \cdots\cup \sigma_{jj} = X(j+1)$$
We can fit each such inclusion into a pushout square

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_%7Bi%2B1%7D%5E%7Bm%2B1%7D%7D%20%26%26%20%7BX(j)%5Ccup%20%5Csigma_%7B0j%7D%5Ccup%20%5Ccdots%5Ccup%20%5Csigma_%7B(i-1)j%7D%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Csigma_%7Bij%7D%7D%20%26%26%20%7BX(j)%5Ccup%20%5Csigma_%7B0j%7D%5Ccup%20%5Ccdots%5Ccup%20%5Csigma_%7Bij%7D%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_{i+1}^{m+1}} &amp;&amp; {X(j)\cup \sigma_{0j}\cup \cdots\cup \sigma_{(i-1)j}} \\
	\\
	{\sigma_{ij}} &amp;&amp; {X(j)\cup \sigma_{0j}\cup \cdots\cup \sigma_{ij}}
	\arrow[from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[hook, from=1-3, to=3-3]
	\arrow[from=3-1, to=3-3]
\end{tikzcd}
" /></p>
so each inclusion, and hence $X(j)\hookrightarrow X(j+1)$, are inner anodyne. Let $Y(0) = X(m)$, so $X(0)\hookrightarrow Y(0)$ is inner anodyne. Now for $0 \leq j \leq m$ set $Y(j+1) = Y(j)\cup \tau_{0j}\cup \cdots \cup \tau_{jj}$, which again gives a chain of inclusions which fit into a pushout diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5CLambda_%7Bi%2B1%7D%5E%7Bm%2B1%7D%7D%20%26%26%20%7BY(j)%5Ccup%20%5Ctau_%7B0j%7D%5Ccup%20%5Ccdots%20%5Ccup%20%5Ctau_%7B(i-1)j%7D%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Ctau_%7Bij%7D%7D%20%26%26%20%7BY(j)%5Ccup%20%5Ctau_%7B0j%7D%5Ccup%20%5Ccdots%20%5Ccup%20%5Ctau_%7Bij%7D%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\Lambda_{i+1}^{m+1}} &amp;&amp; {Y(j)\cup \tau_{0j}\cup \cdots \cup \tau_{(i-1)j}} \\
	\\
	{\tau_{ij}} &amp;&amp; {Y(j)\cup \tau_{0j}\cup \cdots \cup \tau_{ij}}
	\arrow[from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[hook, from=1-3, to=3-3]
	\arrow[from=3-1, to=3-3]
\end{tikzcd}
" /></p>

so again the inclusion $Y(j)\hookrightarrow Y(j+1)$ is inner anodyne. It follows that $X(0)\hookrightarrow Y(m+1)$ is inner anodyne. However, $Y(m+1)$ is exactly $\Delta^m\times \Delta^2$ as we have added all the non-degenerate $(m+1)$ and $(m+2)$-simplices, represented by poset maps, that were missing from $X(0)$. Therefore our desired inclusion is inner anodyne, and this completes the proof.
`\end{proof}`

We can now finally prove [[Introduction to Quasi-Categories#^d95c8b]].

`\begin{proof}[Proof of Classification of Quasi-Categories.]`
Let $S$ be a simplicial set and let $p:\text{Fun}(\Delta^2,S)\to \text{Fun}(\Lambda_1^2,S)$ be the restriction map. Consider the lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cpartial%20%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7BFun%7D(%5CDelta%5E2%2CS)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%7D%20%26%26%20%7B%5Ctext%7BFun%7D(%5CLambda_1%5E2%2CS)%7D%0A%09%5Carrow%5B%22u%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22v%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\partial \Delta^n} &amp;&amp; {\text{Fun}(\Delta^2,S)} \\
	\\
	{\Delta^n} &amp;&amp; {\text{Fun}(\Lambda_1^2,S)}
	\arrow[&quot;u&quot;, from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[dashed, from=3-1, to=1-3]
	\arrow[&quot;v&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

Using the product-Fun adjunction this lifting problem is equivalent to a lifting problem

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B(%5Cpartial%20%5CDelta%5En%5Ctimes%5CDelta%5E2)%5Ccoprod_%7B%5Cpartial%5CDelta%5En%5Ctimes%20%5CLambda_1%5E2%7D(%5CDelta%5En%5Ctimes%20%5CLambda_1%5E2)%7D%20%26%26%20S%20%5C%5C%0A%09%5C%5C%0A%09%7B%5CDelta%5En%5Ctimes%20%5CDelta%5E2%7D%20%26%26%20%7B%5CDelta%5E0%7D%0A%09%5Carrow%5B%22%7B(u%5E%5Cflat%2Cv%5E%5Cflat)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B(i_1%2Ci_2)%7D%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{(\partial \Delta^n\times\Delta^2)\coprod_{\partial\Delta^n\times \Lambda_1^2}(\Delta^n\times \Lambda_1^2)} &amp;&amp; S \\
	\\
	{\Delta^n\times \Delta^2} &amp;&amp; {\Delta^0}
	\arrow[&quot;{(u^\flat,v^\flat)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{(i_1,i_2)}&quot;', hook, from=1-1, to=3-1]
	\arrow[from=1-3, to=3-3]
	\arrow[dashed, from=3-1, to=1-3]
	\arrow[from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where a lift $k:\Delta^n\to \text{Fun}(\Delta^2,S)$ in the original lifting problem, so $p\circ k = v$ and $k\circ \iota = u$, becomes a lift $k^\flat:\Delta^n\times \Delta^2\to S$ such that $k^\flat \circ i_1 = u^\flat$ and $k^\flat \circ i_2 = v^\flat$, where $i_1 = \iota_{\partial\Delta^n}\times 1_{\Delta^2}$ and $i_2 = 1_{\Delta^n}\times \iota_{\Lambda_1^2}$. Thus, we can equivalently show that $S$ is a quasi-category if and only if this diagram has a solution. 

This lifting problem always has a solution if and only if ${^{\perp_w}}\{S\to \Delta^0\}$ contains all inclusions
$$(\Delta^m\times \Lambda_1^2)\coprod_{\partial\Delta^m\times \Lambda_1^2}(\partial\Delta^m\times \Delta^2)\hookrightarrow \Delta^m\times \Delta^2$$
However, all maximal left-orthogonal classes are weakly saturated by [[Introduction to Quasi-Categories#^193325]], so this is equivalent to saying that ${^{\perp_w}}\{S\to \Delta^0\}$ contains all inner anodyne morphisms by [[Introduction to Quasi-Categories#^ef92d0]], which is equivalent to $S$ being a quasi-category by [[Introduction to Quasi-Categories#^4c6682]].
`\end{proof}`

## Path Categories and Universality

**TBD**
#### References

[^1]: Lurie, J. (n.d.). Kerodon. https://kerodon.net/. Accessed 16 May 2024
