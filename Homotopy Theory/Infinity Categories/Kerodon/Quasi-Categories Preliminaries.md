---
date: 2024-05-18T20:02:00
tags:
  - InfinityCategories
  - Homotopy
  - TextbookNotes
  - Simplicial
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

In these notes we analyze and interpret the notes of Lurie collected on [Kerodon](https://kerodon.net/)[^1]. Explicitly, these notes focus on the model of infinity categories given by **quasi-categories**, which are described in the language of simplicial objects. Due to this context, we begin with preliminary comments on simplicial things for use in our development of quasi-categories.

To begin motivating this study recall that algebraic topology principally works with analyzing topological spaces using algebraic invariants. Two **fundamental** such invariants are given by path components, $\pi_0(X)$, of a space, and the fundamental groups, $\{\pi_1(X,x)\}_{x \in X}$, which are the first parts of a tower of complicated algebraic objects known as higher fundamental groups, $\pi_n(X,x)$ for $n \geq 2$. Given a topological space $X$ we can assemble the first two pieces of this data into a special type of category, namely a **groupoid** called the **fundamental groupoid** of $X$, $\pi_{\leq 1}(X)$, which has as objects points of $X$ and as arrows path-homotopy classes of paths between points. The path components, $\pi_0(X)$, is given by the skeleton of the groupoid $\pi_{\leq 1}(X)$, namely the set of isomorphism classes of objects of the category, whereas $\pi_1(X,x)$ is the automorphism group of $x \in \pi_{\leq 1}(X)$. 

A primary motivation for considering higher, and hence $\infty$-categories, is the desire for a single object which contains the information of all the higher homotopy groups $\{\pi_n(X,x)\}_{n \geq 2,x \in X}$ along with our fundamental groupoid, $\pi_{\leq 1}(X)$. This naturally leads to the theory of simplicial sets. Indeed, as one can recall from introductory algebraic topology every topological space $X$ has a natural simplicial set $\text{Sing}_\bullet(X)$, consisting of continuous maps $\sigma:\Delta^n\to X$ from $n$-simplices into $X$ for each $n \geq 0$. As we will see later, we can recover the homotopy groups of a space from its simplicial set of singular simplices. 

A primary motivator for our coming definition of quasi-categories comes from an observation of Kan, which is that we can apply the above hinted to procedure to any simplicial set $S_\bullet$ satisfying the condition that for any $n \geq 0$ and any $0 \leq i \leq n$, a simplicial horn $\sigma_0:\Lambda_i^n\to S_\bullet$ admits an extension $\sigma:\Delta^n\to S_\bullet$. Such simplicial sets are called **Kan complexes**, and as we will see soon every simplicial set of singular chains is such a complex, and up to homotopy these are all such Kan complexes. 

From the above observations $\text{Sing}_\bullet(X)$ might be the *right* context for collecting our higher homotopy groups into a single invariant. However, at first glance this doesn't seem at all like the invariant we started with, $\pi_{\leq 1}(X)$, which was a category. The connection we wish for will come from the nerve construction for categories, which will define a simplicial set from a category which completely determines the category. As we will soon show, simplicial sets which result as the nerve of a category (possibly up to isomorphism) satisfy a certain version of the Kan extension property which describes Kan complexes. Indeed, instead of asking for all horns to admit extensions, we only ask for inner horns to (i.e. $0 < i < n$), but we add the requirement that such extensions be unique. As we will see, the addition of outer horn extensions implies that our category is in fact a groupoid.

These observations are the primary motivator for our definition of quasi-categories. Namely, we require the same condition as that satisfied by nerves of categories, minus the uniqueness constraint. This tells us that although $\text{Sing}_\bullet(X)$ is rarely a nerve of a category, it is always a quasi-category (in fact what we will call an $\infty$-groupoid). However, this doesn't fully justify the use of the term "quasi-categories", though we will justify this in the coming sections by showing that we can extend definitions in elementary category theory. 

## Simplicial sets 

We will begin with some standard notation. For $n \geq 0$, we write $[n]$ for the linearly ordered set $\{0 < 1 < \cdots < n-1 < n\}$. Then we can define the simplex category as follows.

>[!def] Simplex Category
>We define a category $\mathbb{\Delta}$ to consist of the linearly ordered sets $[n]$ for $n\geq 0$ as objects, and morphisms $\alpha:[m]\to [n]$ being non-decreasing set functions. We will write $\mathbb{\Delta}_{inj}$ for the wide-subcategory whose morphisms are **strictly increasing** (and hence injective) functions.

Note that $\mathbb{\Delta}$ is equivalent to the full sub-category of $\mathsf{Cat}$ consisting the categories $\iota([n])$ generated by the directed graph $0\to 1\to \cdots \to n$. Additionally, note that $\mathbb{\Delta}$ is the skeleton of the category of all non-empty finite linearly ordered sets with non-decreasing set functions as morphisms. Further, the definition of our morphisms ensures that every such non-empty finite linearly ordered set $I$ is uniquely isomorphic in the category to $\left[|I|\right]$. 

The simplex category on its own isn't our primary interest, but rather the functor categories it creates.

>[!def] (Co)Simplicial Objects
>Let $\mathcal{C}$ be a category. The category of **(co)simplicial objects** of $\mathcal{C}$ is the functor category $\text{Fun}(\mathbb{\Delta}^{op},\mathcal{C})$ (resp. $\text{Fun}(\mathbb{\Delta},\mathcal{C})$). The category of **semi(co)simplicial objects** of $\mathcal{C}$ is the functor category $\text{Fun}(\mathbb{\Delta}^{op}_{inj},\mathcal{C})$ (resp. $\text{Fun}(\mathbb{\Delta}^{op}_{inj},\mathcal{C})$).

We will often denote simplicial objects by $C_\bullet$ and cosimplicial objects by $C^\bullet$. Recall that if a category $\mathcal{C}$ has all $\mathcal{J}$ shaped )(co)limits, then for a small category $\mathcal{I}$ the functor category $\text{Fun}(\mathcal{I},\mathcal{C})$ also has all $\mathcal{J}$ shaped (co)limits computed pointwise.

Moving forward we will write $\Delta^-$ for the Yoneda embedding into simplicial sets, $\mathbb{\Delta}\to \text{Fun}(\mathbb{\Delta}^{op},\mathsf{Set})$. We will also write $\Delta^{-1}$ for the initial object of the functor category that sends every object of the simplex category to the empty set. Note that additionally $\Delta^0$ is the final object of the category of simplicial sets. 

Recall that Yoneda's lemma allows us naturally identify the set of $n$ simplices of a simplicial set $S_\bullet$, $S_n$, to the set of natural transformations $\mathsf{Set}^{\mathbb{\Delta}^{op}}(\Delta^n,S_\bullet)$, where we send such a natural transformation $\alpha:\Delta^n\to S_\bullet$ to the image of identity, $\alpha_n(1_{[n]})$. 

Next, we have a simple description of subobjects of simplicial sets from theory of subobjects of sets. In particular, we say that $T_\bullet$ is a **simplicial subset** of a simplicial set $S_\bullet$ if $T_n \subseteq S_n$ for all $n \geq 0$, and the inclusions form a natural transformations $T_\bullet\to S_\bullet$. 

Our next goal is to turn our categorical definition of simplicial sets into a combinatorial description. To do this we begin by making observations about the simplicial category $\mathbb{\Delta}$. For each $0 \leq i \leq n$, we have a unique isomorphism $[n-1]\cong [n]\backslash\{i\}$, which gives the unique embedding (**co-face maps**) $\delta^i_{n}:[n-1]\to [n]$ that skips $i$, while we also have the unique surjections (**co-degeneracy maps**) $\sigma^{i}_{n}:[n+1]\to [n]$ which double up at $i$. For each $0 \leq i < j \leq n$, the co-face maps form the following pullback

$$
\begin{CD}
[n-2] @>\delta^i_{n}>> [n-1] \\
@V\delta^{j-1}_{n}VV   @VV\delta^j_{n}V \\
[n-1] @>>\delta^i_{n}> [n]
\end{CD}
$$

^c588f2

^8c694e
where it is easy to see that this diagram commutes. To see that it is a pullback, consider non-decreasing maps $f:[m]\to [n-1]$ and $g:[m]\to [n-1]$ such that $\delta_n^i\circ g = \delta_n^j\circ f$. Note that this implies $g^{-1}([i-1]) = f^{-1}([i-1]) =: I$ and $f\vert_I = g\vert_I$. Further, $g^{-1}(\{i,..,j-2\}) = f^{-1}(\{i+1,...,j-1\}) =: J$, and $g\vert_J +1 = f\vert_J$. Finally, $g^{-1}(\{j,...,n-1\}) = f^{-1}(\{j,...,n-1\}) =: K$, and $g\vert_K = f\vert_K$. In particular, we have that $g^{-1}(\{j-1\}) = \emptyset = f^{-1}(\{i\})$. Then we define $h:[m]\to [n-2]$ by $h(k) = g(k)$ if $k \in I \amalg J$, and $h(k) = g(k)-1$ if $k \in K$. This is a well-defined function as $[m] = I\amalg J \amalg K$ and $j > 0$, and it is non-decreasing since $g$ and $f$ are, and $\forall a \in I\amalg J$, $h(a) \in [j-2]$ while $\forall b \in K$, $h(b) \in [n-2]\backslash[j-2]$. Further, by construction $\delta^{j-1}_n\circ h = g$ and $\delta^i_n\circ h = f$. Finally, $h$ is unique since the co-face maps are monic. Thus, Eq. [[#^c588f2|(1)]] is a pullback in $\mathbb{\Delta}$ (in fact in the full finite linearly ordered sets category).

When talking about semi-simplicial objects these are the only conditions we have to apply. We will write $d_i^n$ for the image of the co-face maps under a simplicial set (which we call **face maps**) and we will write $s_i^n$ for the image of the co-degeneracy maps under a simplicial set (which we call **degeneracy maps**).

>[!proposition] Free Semisimplex Category
>Let $\mathcal{C}$ be a category and let $\{C_n\}_{n\geq 0}$ be a sequence of objects in $\mathcal{C}$ together with a system of morphisms $\{d_i^n:C_n\to C_{n-1}\}_{{0\leq i \leq n,n>0}}$. Then these objects and morphisms generate a semisimplicial object $C_\bullet$ if and only if they satisfy the dual to the co-face identities.

^c8b78a

`\begin{proof}`
It suffices to show that $\mathbb{\Delta}_{inj}$ is isomorphic to the free category $\overline{\mathbb{\Delta}_{inj}}$ generated by objects $[n]$ and co-face type morphisms quotiented by the co-face relations. Note that by the universal property of free and quotient categories, we have a unique map $F_{inj}:\widetilde{\Delta_{inj}}\to \Delta_{inj}$, where the left-hand category is the quotient of the free-category. This functor is bijective on objects and faithful on morphisms, using the fact that co-face maps are monics, so it only remains to show that it is also surjective on morphisms.

For this fix $0 \leq m \leq n$, and let $b = n-m-1$. Let $\beta:[m]\to [n]$ be an injective non-decreasing map. If $n = m$ then $\beta$ must be the identity. Otherwise, let $\{i_0 < \cdots < i_b\}$ be the complement of the image of $\beta$. Note $m+1 = n-b$, and we have that $\beta = \delta_n^{i_0}\circ \cdots \circ \delta_{n-b+1}^{i_{b-1}-(b-1)}\circ \delta_{n-b}^{i_b-b}$, as desired.
`\end{proof}`
Dually, we can consider the subcategory $\mathbb{\Delta}_{surj}$ of $\mathbb{\Delta}$ consisting only of surjections. In this case for each $0 \leq i \leq j \leq n$ we have a pushout of linearly ordered sets

$$
\begin{CD}
[n+2] @>\sigma_{n+1}^i> >[n+1] \\
@V\sigma_{n+1}^{j+1}VV @VV\sigma_{n}^jV \\
[n+1] @> >\sigma_{n}^i> [n]
\end{CD}
$$
Indeed, consider non-decreasing maps $f,g:[n+1]\to [m]$ such that $f\circ \sigma_{n+1}^i = g\circ \sigma_{n+1}^{j+1}$. This implies that for $0 \leq k \leq i$, $f(k) = g(k)$,  $i \leq k \leq j$, $f(k) = g(k+1)$ (in particular $g(i+1) = f(i) =g(i)$), and for $j+1 \leq k \leq n+1$, $f(k)=g(k)$ (in particular $f(j+1) = g(j+1) = f(j)$). Then, we define $h:[n]\to [m]$ by $h(k) = f(k)$ for $0 \leq k \leq j$, and $h(k) = f(k+1)$ for $j\leq k \leq n$, which is well-defined since $f(j) = f(j+1)$. By construction $h\circ \sigma_n^j = f$, and additionally $h\circ \sigma_n^i = g$ from our observations on the relationships between $f$ and $g$. Then, since the $\sigma_n^i$ are surjective, $h$ is also unique, completing the proof that this is a pushout diagram.

We now move to showing a dual version of [[Quasi-Categories Preliminaries#^c8b78a|Proposition 3]].

>[!proposition] Free Surj-simplex Category
>Let $\mathcal{C}$ be a category and let $\{C_n\}_{n\geq 0}$ be a sequence of objects in $\mathcal{C}$ together with a system of morphisms $\{s_i^n:C_n\to C_{n-1}\}_{{0\leq i \leq n,n>0}}$. Then these objects and morphisms generate a surj-simplicial object $C_\bullet$ if and only if they satisfy the dual to the co-degeneracy identities.

^9e2339

`\begin{proof}`
As before we obtain a quotient of a free category, $\widetilde{\mathbb{\Delta}_{surj}}$, from which we have a natural functor $F_{surj}:\widetilde{\mathbb{\Delta}_{surj}}\to \mathbb{\Delta}_{surj}$ which is bijective on objects and faithful, using the fact that all maps in $\mathbb{\Delta}_{surj}$ are epimorphisms. It remains to show that it is full.

One again fix $0 \leq m \leq n$ and $b = n-m-1$. Let $\beta:[n]\to [m]$ be a non-decreasing surjection. If $ n = m$ then $\beta$ has to be the identity, and we're done vacuously. Otherwise, let $\{i_0 < i_1 < \cdots < i_b\}$ be the collection of integers, $j$, such that $\beta(j) = \beta(j+1)$. Then since $\beta$ is non-decreasing we must have that $\beta = \sigma_m^{i_0}\circ \cdots \circ \sigma_{m+b}^{i_b}$, as desired.
`\end{proof}`

Now that we have a better understanding of how face and degeneracy maps work individually, we need to understand how they interact. Namely, they interact via the following commuting diagrams, for $0 \leq i,j \leq n$:
- $i < j$:
$$
\begin{CD}
[n] @>\delta^i_{n+1}> >[n+1] \\
@V\sigma_{n-1}^{j-1}VV @VV\sigma_{n}^jV \\
[n-1] @> >\delta^i_{n} > [n]
\end{CD}
$$
- $i > j+1$:
$$
\begin{CD}
[n] @>\delta^i_{n+1}> >[n+1] \\
@V\sigma_{n-1}^{j}VV @VV\sigma_{n}^jV \\
[n-1] @> >\delta^{i-1}_{n} > [n]
\end{CD}
$$
- $i = j$ or $i = j+1$:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Bn%5D%7D%20%26%20%7B%5Bn%2B1%5D%7D%20%5C%5C%0A%09%7B%5Bn%2B1%5D%7D%20%26%20%7B%5Bn%5D%7D%0A%09%5Carrow%5B%22%7B%5Cdelta_%7Bn%2B1%7D%5Ei%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B%5Cdelta_%7Bn%2B1%7D%5E%7Bi%2B1%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Csigma_n%5Ei%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Csigma_n%5Ei%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{[n]} &amp; {[n+1]} \\
	{[n+1]} &amp; {[n]}
	\arrow[&quot;{\delta_{n+1}^i}&quot;, from=1-1, to=1-2]
	\arrow[&quot;{\delta_{n+1}^{i+1}}&quot;', from=1-1, to=2-1]
	\arrow[Rightarrow, no head, from=1-1, to=2-2]
	\arrow[&quot;{\sigma_n^i}&quot;, from=1-2, to=2-2]
	\arrow[&quot;{\sigma_n^i}&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>
We can now put together these and our previous relations to fully describe simplicial objects in terms of their face and degeneracy maps.

>[!proposition] Combinatorial Description
>If $\{C_n\}_{n\geq 0}$ is a sequence of objects in a category $\mathcal{C}$ together with morphisms $\{d_i^n:C_n\to C_{n-1}\}_{0\leq i \leq n,n > 0}$ and $\{s_i^n:C_n\to C_{n+1}\}_{0\leq i \leq n}$, then this data extends to a unique simplicial object if and only if all of the duals of relations for the co-face and co-degeneracy maps hold.

^5a13d8

`\begin{proof}`
It suffices to show that $\mathbb{\Delta}$ is isomorphic to the category $\widetilde{\mathbb{\Delta}}$ freely generated by a collection of objects $\{[n]\}_{n\geq 0}$ together with formal co-face and co-degeneracy maps, modulo the relations given previously. As with our previous arguments, we have a unique functor $F:\widetilde{\mathbb{\Delta}}\to \mathbb{\Delta}$ which is bijective on objects and sends co-face to co-face and co-degeneracy to co-degeneracy maps. 

First, I claim that every map in $\mathbb{\Delta}$ can be uniquely factored as a surjection followed by an injection. Indeed, if $\beta:[m]\to [n]$ is a non-decreasing map, then we have the unique isomorphism $\varphi$ from the image of $\beta$, as a finite linearly ordered set, and some $[k]$, $k \leq n$. Then $\beta$ is precisely the composite $[m]\xrightarrow{\beta_{surj}}[k]\xrightarrow{\beta_{inj}}[n]$, where $\beta_{surj} = \varphi\circ \beta$ and $\beta_{inj} = \varphi^{-1}$, modulo inclusions into $[n]$. Such a factorization is necessarily unique. Indeed, $\beta_{inj}$ is always fully determined by the image of $\beta$. Thus, the only possibility for non-uniqueness is in $\beta_{surj}$, but since $\beta_{inj}$ is monic this guarantees the uniqueness of $\beta_{surj}$. In this form we can use [[Quasi-Categories Preliminaries#^c8b78a|Proposition 3]] to write $\beta_{inj}$ in standard form as a unique composite of $\delta^i$ and we can use [[Quasi-Categories Preliminaries#^9e2339|Proposition 4]] to write $\beta_{surj}$ in standard form as a unique composite of $\sigma^j$.

It remains only to see that all maps in $\widetilde{\mathbb{\Delta}}$ can be written uniquely in this way. Existence follows from repeated application of the identities relating the co-face and co-degeneracy maps. Further, our added relations do not change how co-face maps interact among themselves, and vice-versa for co-degeneracy maps, so once in standard form the injective and surjective pieces are unique by [[Quasi-Categories Preliminaries#^c8b78a|Proposition 3]] and [[Quasi-Categories Preliminaries#^9e2339|Proposition 4]], respectively. This completes the proof.
`\end{proof}`

With these ideas we say that an $n$-simplex $\sigma \in S_n$ is **degenerate** if it lies in the image of some degeneracy operator. In general, every $0$ simplex of a simplicial set is non-degenerate.

We have a special kind of degeneracy we would like to keep track of. If $S_\bullet$ is a simplicial set, $x \in S_0$ is a vertex, then we denote its image under $s_0^0:S_0\to S_1$ is denoted $\text{id}_x$. Thinking of $d^1_1:S_1\to S_0$ as the source map and $d_0^1:S_1\to S_0$ as the target map, it is easy to see that $x$ is both the source and target of $\text{id}_x$, as we would hope. 

>[!remark]
>Since $\mathsf{Set}$ is (co)complete this implies that $\mathsf{Set}^{\mathbb{\Delta}^{op}}$ is (co)complete with all (co)limits computed pointwise. In particular, this implies that monics and epics are pointwise monics and epics (i.e. injections and surjections). 

^cb8463

We have another characterization of epimorphisms of simplicial sets. Namely, a map of simplicial sets $\alpha:S_\bullet\to T_\bullet$ is epic if and only if every non-degenerate simplex of $T_\bullet$ falls in the image of $\alpha$. The only if direction is immediate from [[Quasi-Categories Preliminaries#^cb8463|Remark 6]], and in the if case we can realize that every degenerate simplex of $T_\bullet$ is of the form $\beta(x)$ for some composite of degeneracies $\beta$ and some non-degenerate simplex $x$, in which case naturality gives us the desired surjection. 

We know what degenerate 1-simplices look like (identities), but what about degenerate 2-simplices?

>[!example] Degenerate 2-Simplices
>Let $S_\bullet$ be a simplicial object of $\mathcal{C}$ and $\sigma$ a $2$-simplex in $S_\bullet$.  We say $\sigma$ is **left-degenerate** if it is of the form $s_0^1(e)$ for some edge $e:x\to y$, and **right-degenerate** if it is of the form $s_1^1(e)$ for some edge $e:x\to y$. Using our identities we can describe these $2$-simplices diagrammatically as
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20x%20%26%26%26%20y%20%5C%5C%0A%09x%20%26%26%20y%20%26%20x%20%26%26%20y%0A%09%5Carrow%5B%22e%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22e%22'%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22e%22%2C%20from%3D2-4%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22e%22'%2C%20from%3D2-4%2C%20to%3D2-6%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]&amp; x &amp;&amp;&amp; y \\x &amp;&amp; y &amp; x &amp;&amp; y\arrow[&quot;e&quot;, from=1-2, to=2-3]\arrow[Rightarrow, no head, from=1-5, to=2-6]\arrow[Rightarrow, no head, from=2-1, to=1-2]\arrow[&quot;e&quot;', from=2-1, to=2-3]\arrow[&quot;e&quot;, from=2-4, to=1-5]\arrow[&quot;e&quot;', from=2-4, to=2-6]\end{tikzcd}" /></p>
>
>respectively.

### Dimension

We've talked a lot about degeneracy of individual simplices up to this point. We can also talk about how this might effect a simplicial object itself. We say that $S_\bullet$ has **dimension $\leq k$** if for $n> k$, every $n$-simplex of $S_\bullet$ is degenerate. If $S_\bullet$ has dimension $\leq k$ but not dimension $\leq k-1$, then we say that $S_\bullet$ has **dimension $k$**. If such a finite $k$ exists we say that $S_\bullet$ is **finite-dimensional**.

It follows easily that epimorphisms are non-increasing in dimension while monomorphisms are non-decreasing in dimension. Further, coproducts and products behave well with dimension. It is easy to see that the dimension of a coproduct is simply the supremum of the dimensions of the pieces. On the other hand, dimensions sum under products.  We begin by characterizing non-degenerate cells in $\Delta^n\times\Delta^m$. Note that a $k$ simplex in $\Delta^n\times \Delta^m$ is a pair of non-decreasing maps $f:[k]\to [n]$ and $g:[k]\to [m]$. These pair of maps are equivalent to a map $\langle f,g\rangle:[k]\to [n]\times [m]$, where $[n]\times[m]$ is the product in $\text{Poset}$ with product ordering. Indeed, we have natural projections $[n]\times [m]\to [n]$ and $[n]\times [m]\to [m]$ since $(a,b)\leq (c,d)$ if and only if $a\leq c$ and $b \leq d$.

>[!proposition] Product of Standard Simplices
>The non-degenerate simplices of $\Delta^n\times \Delta^m$ correspond to those $\sigma:\Delta^{n+m}\to \Delta^n\times \Delta^m$ such that the corresponding map of partially ordered sets $[n+m]\to [n]\times [m]$ is strictly monotone.

^6fc0d8

`\begin{proof}`
First let us show that if $k > n+m$, then any $k$-simplex is degenerate. Let $f:[k]\to [n]\times [m]$ be a $k$-simplex. Then we obtain $k$-simplices $f_1:[k]\to [n]$ and $f_2:[k]\to [m]$. Now we must have that there are at least $k-n$ $0\leq i < k$'s such that $f_1(i) = f_1(i+1)$ as well as $k-m$ such $i$s with $f_2(i)=f_2(i+1)$. Since $2k-n-m > k$, by assumption, the Pigeon Hole principle guarantees the existence of a $0 \leq i < k$ such that $f_1(i) = f_1(i+1)$ and $f_2(i) = f_2(i+1)$. Then $f(i) = f(i+1)$, and so we have some $f':[k-1]\to [n]\times [m]$ such that $f = f' \circ \eta_i^{k-1}$. Thus, $f$ is a degenerate simplex.

The above argument also shows that $f$ is a non-degenerate simplex if and only if it is a monomorphism of partially ordered sets (or equivalently is injective). Then $f:[n+m]\to [n]\times [m]$ is non-degenerate if and only if for each $0 \leq i < n+m$, $f(i) < f(i+1)$. This is equivalent to the statement that for each $0 \leq i < n+m$, if $f(i) = (a,b)$, then $f(i+1)$ is either $(a+1,b)$ or $(a,b+1)$.

Now, suppose $g:[p]\to [n]\times [m]$ is a non-degenerate simplex, so in particular $p \leq n+m$. Then $g$ corresponds to some sequence $(a_0,b_0),(a_1,b_1),...,(a_p,b_p)$. Since $(a_0,b_0) < (a_1,b_1) < \cdots < (a_p,b_p)$, we have a sequence $(0,0) < (k_1,\ell_1) < \cdots < (k_{n+m-1},\ell_{n+m-1}) < (n,m)$ which contains $(a_0,b_0) < \cdots < (a_p,b_p)$ as a subsequence and increases by $1$ in one component at each step. In other words, we find that $g$ is a $p$-face of a $(n+m)$-simplex.
`\end{proof}`

>[!proposition] Dimension Sum
>Let $S_\bullet$ and $T_\bullet$ be simplicial sets with dimensions $k$ and $\ell$, respectively. Then $S_\bullet\times T_\bullet$ has dimension $k+\ell$.

`\begin{proof}`
We will prove the claim via a pair of inequalities. First, let $\sigma = (\sigma_S,\sigma_T)$ denote a non-degenerate $n$-simplex in the product. By [[Quasi-Categories Preliminaries#^5a13d8|Proposition 5]] we can uniquely factor $\sigma_S:\Delta^n\xrightarrow{\alpha_S} \Delta^{n_S}\xrightarrow{\tau_S}S_\bullet$ and $\sigma_T:\Delta^n\xrightarrow{\alpha_T}\Delta^{n_T}\xrightarrow{\tau_T}T_\bullet$ where $n_S,n_T \leq n$ and $\tau_S,\tau_T$ are non-degenerate simplices. In particular, this implies that $n_S \leq k$ and $n_T\leq \ell$. We then obtain a factorization of $\sigma$
$$
\Delta^n\xrightarrow{(\alpha_{S},\alpha_{T})}\Delta^{n_{S}}\times \Delta^{n_{T}}\xrightarrow{\tau_{S}\times \tau_{T}}S_{\bullet}\times T_{\bullet}
$$
The non-degeneracy of $\sigma$ implies that $(\alpha_S,\alpha_T)$ is a monomorphism. The associated map of partially ordered sets, $[n]\to [n_S]\times [n_T]$, is hence a monomorphism, where $[n_S]\times [n_T]$ has the product order. The image must be a linearly ordered subset of $[n_S]\times [n_T]$. But the largest subset is of size $n_S+n_T \leq k+\ell$ which can be seen by visualizing a $n_S\times n_T$ grid and considering paths that start in the bottom left corner and can only move up and to the right with each move. Finally, if we take $n = k+\ell$ with $\tau_S$ and $\tau_T$ non-degenerate $k$ and $\ell$ simplices, respectively, than the previous observation implies that the composite is exactly a $k+\ell = n$ simplex.
`\end{proof}`

>[!example]
>A simplicial set of dimension $\leq 0$ is fully determined by $S_0$, and hence determined by a set. In particular, a simplicial set $S_\bullet$ has dimension $\leq 0$ if and only if it is isomorphic to a constant functor, and we say the simplicial set $S_\bullet$ is **discrete** in this case.
>
>Going one higher, a simplicial set of dimension $\leq 1$ can be thought of as a directed graph. This will be formalized as an equivalence of categories.

Extending these examples, we will show that a simplicial object of dimension $\leq k$ is determined by its $n$-simplices for $n \leq k$. First we prove a unique factorization result.

>[!proposition] Unique Factorization of Simplices
>If $\sigma:\Delta^n\to S_\bullet$ is a morphism of simplicial sets, represented by an $n$-simplex, then $\sigma$ can be factored uniquely as a composite $$\Delta^n\xrightarrow{\alpha}\Delta^m\xrightarrow{\tau}S_{\bullet}$$
>where $\alpha$ is represented by a surjective map of linearly ordered sets, $[n]\twoheadrightarrow [m]$, and $\tau$ is a non-degenerate $m$-simplex of $S_\bullet$.

^88170c

`\begin{proof}`
Let $m$ be the smallest non-negative integer for which $\sigma$ can be factored as such a composite of $\alpha:\Delta^n\to \Delta^m$ and $\tau:\Delta^m\to S_{\bullet}$. If $\alpha$ is not a surjection we can replace $[m]$ by an object of cardinality the image of $\alpha$, say $[k]$, contradicting minimality. Similarly, $\tau$ is non-degenerate as otherwise we would have a simplex $\tau':\Delta^{m-1}\to S_\bullet$ such that $\tau = \tau'\circ s_i^{m-1}$ for some $0 \leq i \leq m-1$, once again contradicting minimality.

Finally, to show uniqueness suppose we had another such factorization $\alpha':\Delta^n\to \Delta^{m'}$ and $\tau':\Delta^{m'}\to S_\bullet$. Towards a contradiction suppose that we have $0 \leq i < j \leq n$ such that $\alpha'(i) = \alpha'(j)$ but $\alpha(i) \neq \alpha(j)$. Let $\beta:\Delta^m\to \Delta^n$ be a section of $\alpha$ such that $i$ and $j$ land in the image of $\beta$. Then 
$$\tau = \tau\circ \alpha\circ \beta = \sigma\circ \beta = \tau'\circ \alpha' \circ \beta$$
Then by assumption $\alpha'\circ \beta$ is not injective on vertices, and hence we have factored $\tau$ as a composite of a non-trivial surjection and another simplex, contradicting it being non-degenerate.

With this argument in mind, we can factor $\alpha$ as $\Delta^n\xrightarrow{\alpha'}\Delta^{m'}\xrightarrow{\alpha''}\Delta^m$ for some $\alpha''$, which must necessarily be surjective. Fix a section $\beta'$ of $\alpha'$. Then
$$\tau' = \tau'\circ \alpha'\circ \beta' = \sigma\circ \beta' = \tau\circ \alpha\circ \beta' = \tau \circ \alpha''\circ \alpha'\circ \beta' = \tau\circ \alpha''$$
Since $\tau'$ is non-degenerate, $\alpha''$ must be also injective, and hence the identity map. Thus $\alpha = \alpha'$ and $\tau = \tau'$, as desired. 
`\end{proof}`

As with any functor into $\mathsf{Set}$ (and more generally into $\mathsf{Cat}$) we have  the Grothendieck construction. Let $\mathsf{Cat}_2$ denote the $2$-category of categories, functors, and natural transformations. Let $*$ denote the terminal category. Let $\mathsf{Cat}_{*,\ell}$ denote the **lax-slice** of $\mathsf{Cat}_2$ under $*$, which is given explicitly as follows:
- Objects are functors $*\to \mathcal{C}$ (i.e. pairs $(\mathcal{C},C)$ of a category and an object of that category)
- Morphisms are triangles which lax-ly commute. That is, a morphism from $c:*\to \mathcal{C}$ to $d:*\to \mathcal{D}$ is a pair $(F,\Gamma)$ of a functor $F:\mathcal{C}\to \mathcal{D}$ and a natural transformation $\Gamma:F\circ c\Rightarrow d$, which pictorially is given as 
<p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%20%7B*%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BC%7D%7D%20%26%26%20%7B%5Cmathcal%7BD%7D%7D%0A%09%5Carrow%5B%22c%22'%2C%20from%3D1-2%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22d%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%5CGamma%22%2C%20shorten%20%3C%3D8pt%2C%20shorten%20%3E%3D8pt%2C%20Rightarrow%2C%20from%3D2-1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]&amp; {*} \\{\mathcal{C}} &amp;&amp; {\mathcal{D}}\arrow[&quot;c&quot;', from=1-2, to=2-1]\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;d&quot;, from=1-2, to=2-3]\arrow[&quot;F&quot;', from=2-1, to=2-3]\arrow[&quot;\Gamma&quot;, shorten &lt;=8pt, shorten &gt;=8pt, Rightarrow, from=2-1, to=0]\end{tikzcd}" /></p>

>[!def] Grothendieck Construction
>The **Grothendieck construction** for a pseudofunctor $F:\mathbb{C}\to \mathsf{Cat}_2$ is then the strict 2-pullback $p:\int_\mathbb{C}F\to \mathbb{C}$ of $\mathsf{Cat}_{*,\ell}\to \mathsf{Cat}_2$ along $F$ 
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cint_%5Cmathbb%7BC%7DF%7D%20%26%20%7B%5Cmathsf%7BCat%7D_%7B*%2C%5Cell%7D%7D%20%5C%5C%0A%09%7B%5Cmathbb%7BC%7D%7D%20%26%20%7B%5Cmathsf%7BCat%7D_2%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22p%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%7D%2C%20draw%3Dnone%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22F%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{\int_\mathbb{C}F} &amp; {\mathsf{Cat}_{*,\ell}} \\{\mathbb{C}} &amp; {\mathsf{Cat}_2}\arrow[from=1-1, to=1-2]\arrow[&quot;p&quot;', from=1-1, to=2-1]\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125}, draw=none, from=1-1, to=2-2]\arrow[from=1-2, to=2-2]\arrow[&quot;F&quot;', from=2-1, to=2-2]\end{tikzcd}" /></p>
>
>Explicitly, $\int_\mathbb{C}F$ can be realized as a category with objects being pairs of functors $c:*\to \mathbb{C}$ with natural transformations $a:*\Rightarrow F\circ c$, which can be thought of as object of $\mathbb{C}$ together with an object of $F(c)$. A morphism in the category between pairs $(c,a)$ and $(c',a')$ is given by a pair of a natural transformation $f:c\Rightarrow c'$ (i.e. a map in $\mathbb{C}$) together with a natural transformation $\Phi:F(f)\circ a\Rightarrow a'$.

A discussion of the Grothendieck construction and strict 2-(co)limits can be found in [[Strict 2-(co)limits]]. Now, since simplicial sets can be realized as strict 2-functors into $\mathsf{Cat}_2$ by realizing sets as discrete categories and 1-categories as 2-categories with only identity 2-cells, we can also obtain the category $\mathbb{\Delta}_{S_\bullet}$ associated with any simplicial set $S_\bullet$. As above, objects of $\mathbb{\Delta}_{S_\bullet}$ are pairs $([n],\sigma)$ of an object in the simplex category and an $n$-simplex, and a morphism $([n],\sigma)$ to $([n'],\sigma')$ is a non-decreasing map $f:[n]\to [n']$ such that $S_f(\sigma') = \sigma$ (not the opposite order of the application here due to the fact that simplicial sets are contravariant functors).

We refer to $\mathbb{\Delta}_{S_\bullet}$ as the **category of simplices** of $S_\bullet$, and for $k \geq 0$ an integer, we write $\mathbb{\Delta}_{S_\bullet,\leq k}$ for the full-subcategory spanned by $n$-simplices, with $n \leq k$. We now classify finite dimensional simplicial sets in terms of colimits.

>[!proposition] Finite Simplicial Sets as Colimits
>Let $k\geq 0$ be an integer and $S_\bullet$ a simplicial set. Then the following are equivalent:
>1. $S_\bullet$ has dimension $\leq k$
>2. $S_\bullet$ is isomorphic to a colimit $\lim\limits_{\to J\in\mathcal{J}}S(J)_\bullet$ of simplicial sets of dimension $\leq k$
>3. $S_\bullet$ is isomorphic to a colimit $\lim\limits_{\to J\in\mathcal{J}}\Delta^{J}$ of standard simplices of dimension $\leq k$.
>4. The tautological map $$\lim\limits_{\xrightarrow[{([n],\sigma)\in \mathbb{\Delta}_{S_\bullet\leq k}}]{}}\Delta^n\to S_\bullet$$
>is an isomorphism of simplicial sets.

^21b90a


`\begin{proof}`
Note that $(4) \implies (3) \implies (2)$ is trivial. Note that any colimit of simplicial sets, can be realized as a coproduct of simplicial sets followed by an epimorphism. Thus, $(2)\implies (1)$. Finally, to show $(1)\implies (4)$ let $S_\bullet$ be a simplicial set of dimension $\leq k$. To show the natural map in (4) is an isomorphism we must show that it gives a bijection at each $n$. First, since all non-degenerate simplices lie in the image of the map, by definition, we have that the map must be an epimorphism, and hence surjective at each $n$. 

To show injectivity let $\gamma$ denote the natural map and let $\tau,\tau'$ be $\ell$-simplices on the left such that $\gamma(\tau) = \gamma(\tau')$. Extending our construction of colimits in set we have at some $([n],\sigma) \in \mathbb{\Delta}_{S_\bullet,\leq k}$ a representative $\ell$-simplex $\overline{\tau}$  of $\Delta^n$ for $\tau$, and similarly $([m],\sigma')$ and $\overline{\tau'}$ for $\Delta^m$. We can factor $\overline{\tau}$ uniquely as a composite $[\ell]\twoheadrightarrow [n']\hookrightarrow [n]$. Replacing $\sigma$ by its composite with the inclusion if necessary, we can assume that the representative $\overline{\tau}$ is a surjective. Using our [[Quasi-Categories Preliminaries#^88170c|unique factorization]] result we can then factor $\sigma$ unique as a composite $\Delta^n\xrightarrow{\nu}\Delta^p\xrightarrow{\rho}S_\bullet$, where $\nu$ is surjective and $\rho$ is non-degenerate. Replacing $\sigma$ by $\rho$ and $\overline{\tau}$ by $\nu\circ \overline{\tau}$, we can without loss of generality assume $\sigma$ is non-degenerate, while $\overline{\tau}$ is still surjective. We can go through similar steps for $\tau'$ to obtain an $\ell$-simplex $\overline{\tau'}$ which is representative by a surjective map and for some object $([n'],\sigma') \in \mathbb{\Delta}_{S_\bullet,\leq k}$, where $\sigma'$ is non-degenerate. Then, the equality reads 
$$\sigma \circ \overline{\tau} = f(\tau) = f(\tau') = \sigma'\circ \overline{\tau'}$$
But from our [[Quasi-Categories Preliminaries#^88170c|unique factorization]] we must have that $\sigma = \sigma'$ and $\overline{\tau} = \overline{\tau'}$, so that $\tau = \tau'$ in the colimit.
`\end{proof}`

We can phrase [[Quasi-Categories Preliminaries#^21b90a|Proposition 12]] in terms of the language of [[Kan Extensions]]. Explicitly, we have a natural inclusion functor $\iota_k:\mathbb{\Delta}_{\leq k}\to \mathbb{\Delta}$. Since $\mathbb{\Delta}_{\leq k}$ is small and $\mathsf{Set}$ is (co)complete, [[Kan Extensions#^8ae769]] tells us that $\iota_k^*:\mathsf{Set}^{\mathbb{\Delta}^{op}}\to \mathsf{Set}^{\mathbb{\Delta}^{op}_{\leq k}}$ has left and right adjoints:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSet%7D%5E%7B%5Cmathbf%7B%5CDelta%7D%5E%7Bop%7D%7D%7D%20%26%26%20%7B%5Cmathsf%7BSet%7D%5E%7B%5Cmathbf%7B%5CDelta%7D_%7B%5Cleq%20k%7D%5E%7Bop%7D%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ciota_k%5E*%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ctext%7BLan%7D_%7B%5Ciota_k%7D%7D%22'%2C%20bend%20right%20%3D%2070%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ctext%7BRan%7D_%7B%5Ciota_k%7D%7D%22%2C%20bend%20left%20%3D%2070%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-89%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D2%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-91%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Set}^{\mathbf{\Delta}^{op}}} &amp;&amp; {\mathsf{Set}^{\mathbf{\Delta}_{\leq k}^{op}}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\iota_k^*}&quot;, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\text{Lan}_{\iota_k}}&quot;', bend right = 70, from=1-3, to=1-1]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{\text{Ran}_{\iota_k}}&quot;, bend left = 70, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-89}, draw=none, from=0, to=2]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-91}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>
where the comonad $\text{Lan}_{\iota_k}\circ \iota_k^* = \text{sk}_k$ is the $k$th skeleton. Then the statement that a simplicial set $S_\bullet$ is dimension $\leq k$ is exactly the statement that $\text{Lan}_{\iota_k}(\iota_k^*S_\bullet)\cong S_\bullet$. 

More generally, the proof of [[Quasi-Categories Preliminaries#^21b90a|Proposition 12]] shows that every simplicial set can be recovered as the colimit over representables indexed by its category of simplices. This is a general result for presheafs on locally small categories, which in terms of coends is the [[Ends and coEnds#^d2333d]]. 



### Skeletal Filtration 

For $S_\bullet$ a simplicial set and $k \geq 0$, we write $\text{sk}_k(S)$, called the **$k$-skeleton of $S_\bullet$**, for the largest simplicial subset of $S$ of dimension $\leq k$. We can realize $S_\bullet$ as a directed colimit of simplicial sets of finite dimension
$$
\emptyset=\text{sk}_{-1}(S) \hookrightarrow \text{sk}_{0}(S)\hookrightarrow \text{sk}_{1}(S)\hookrightarrow \text{sk}_{2}(S) \hookrightarrow \cdots
$$
which can be called the **skeletal filtration of $S_\bullet$**.

As we saw in the last section, $\text{sk}_k = \text{Lan}_{\iota_k}\circ \iota_k^*$. However, we can give a bit more explicit description of this functor, namely in terms of [[Kan Extensions#^42a123]]:
$$\text{sk}_k(S_\bullet)_n =  \text{colim}\left((\iota_k\downarrow [n])\xrightarrow{\pi_0^n}\mathbb{\Delta}^{op}_{\leq k}\xrightarrow{\iota_k}\mathbb{\Delta}^{op}\xrightarrow{S_\bullet}\mathsf{Set}\right)$$
so for every $[n]\to [\ell]$, $\ell \leq k$, we have a copy of $S_\ell$. We can also [[Kan Extensions#^79496e]] to write the skeleton as 
$$\text{sk}_k(S_\bullet)_n = \int^{\ell:\mathbb{\Delta}^{op}_{\leq k}}\mathbb{\Delta}^{op}([\ell],[n])\times S_\ell = \int^{\ell:\mathbb{\Delta}^{op}_{\leq k}}\mathbb{\Delta}([n],[\ell])\times S_\ell$$
Note that the "equivariance" of the coend ensures that when $n \leq k$, $\text{sk}_k(S_\bullet)_n \cong S_n$, which is the copy of $S_n$ indexed by the identity. For $n > k$, $\text{sk}_k(S_\bullet)_n$ can be realized as containing factorizations $\Delta^n\to \Delta^\ell\to S_\bullet$ of $n$-simplices into $\ell$ simplices for $\ell \leq k$.  In fact, this says that one realization of $\text{sk}_k(S_\bullet)_n$ is as the subset of $S_n$ consisting of $n$-simplices which factor through $m$ simplices for some $m \leq k$. It follows that $S_\bullet$ is the colimit, as described above in the skeletal filtration schematic. In particular from our [[Quasi-Categories Preliminaries#^88170c|unique factorization of simplices]] it follows that the $k$ skeleton of $S_\bullet$ is a simplex of dimension $\leq k$. 


Every simplicial set $T_\bullet$ of dimension $\leq k$ that maps into $S_\bullet$ uniquely factors through $\text{sk}_k(S_\bullet)$, and hence it is the largest simplicial subset of $S_\bullet$ of dimension $\leq k$. Additionally, from our Kan extension description of the $k$th skeleton we immediately obtain the following Corollary.

>[!corollary] Skeletons Preserve Colimits
>The $k$th skeleton functor, $\text{sk}_k:\mathsf{Set}^{\mathbb{\Delta^{op}}}\to \mathsf{Set}^{\mathbb{\Delta^{op}}}$, preserves small colimits, being a composite $\text{Lan}_{\iota_k}\circ \iota_k^*$ of left adjoint functors.

#### Simplicial Boundaries

The use of skeleta also allows us to construct boundaries of standard simplices. Namely, the boundary $\partial\Delta^n$ of the standard $n$-simplex $\Delta^n$ is precisely the $(n-1)$-skeleton of $\Delta^n$. Using our simplicial subset description of the $(n-1)$-skeleton we can realize the boundary $\partial\Delta^n$ as being the simplicial subset with $m$ simplices
$$\partial\Delta^n([m]) = \{\alpha\in \mathbb{\Delta}([m],[n])\,\vert\,\alpha\;\text{ is not surjective}\}$$
For example, the simplicial set $\partial\Delta^0$ is empty. 

Now, for $S_\bullet$ a simplicial set, let $S_n^{nd}$ denote the set of non-degenerate $n$-simplices. From our previous remarks any such $n$-simplex factors through a map $\Delta^n\xrightarrow{\sigma}\text{sk}_n(S_\bullet)$ into the $n$-skeleton of $S_\bullet$. Using our remarks on skeleta again, when restricted to the boundary of the simplex this map factors through the $(n-1)$-skeleton, $\partial\Delta^n\xrightarrow{\sigma\vert_{\partial\Delta^n}}\text{sk}_{n-1}(S_\bullet)$.  Putting these remarks together we obtain the following proposition.

>[!proposition] Simplicial Gluing
>Let $S_\bullet$ be a simplicial set and let $k \geq 0$. Then we have a pushout
>$$\begin{CD} \coprod_{\sigma\in S_k^{nd}}\partial\Delta^k @>>> \text{sk}_{k-1}(S_\bullet) \\ @VVV @VVV \\ \coprod_{\sigma \in S_k^{nd}}\Delta^k @>>> \text{sk}_k(S_\bullet)\end{CD}$$
>in $\mathsf{Set}^{\mathbb{\Delta}^{op}}$.

^4a1ee9

`\begin{proof}`
The lemma follows concretely from our [[Quasi-Categories Preliminaries#^88170c|unique factorization of simplices]]. We can also proceed formally using our coend calculus **LOOK AT RIEHL CATEGORICAL HOMOTOPY THEORY OR RIEHL VERITY THEORY AND PRACTICE OF REEDY CATEGORIES**
`\end{proof}`

As with all colimits, we can realize the $k$-skeleton in terms of an equalizer of a map of disjoint unions. Explicitly, we have that $\text{sk}_k(S_\bullet)$ is the coequalizer of the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ccoprod%5Climits_%7B(f%3A%5B%5Cell%5D%5Cto%20%5Bn%5D)%5Cin%5Cmathbf%7B%5CDelta%7D_%7B%5Cleq%20k%7D%7D%5Cmathbf%7B%5CDelta%7D(-%2C%5B%5Cell%5D)%5Ctimes%20S_n%7D%20%26%26%20%7B%5Ccoprod%5Climits_%7B%5B%5Cell%5D%20%5Cin%20%5Cmathbf%7B%5CDelta%7D_%7B%5Cleq%20k%7D%7D%5Cmathbf%7B%5CDelta%7D(-%2C%5B%5Cell%5D)%5Ctimes%20S_%5Cell%7D%20%26%26%20%7B%5Ctext%7Bsk%7D_k(S_%5Cbullet)%7D%0A%09%5Carrow%5B%22%7B%5Clangle%20%5Ciota_n%5Ccirc%20%5Cmathbf%7B%5CDelta%7D(-%2Cf)%5Ctimes%201_%7BS_n%7D%7Cf%3A%5B%5Cell%5D%5Cto%20%5Bn%5D%5Crangle%7D%22%2C%20shift%20left%3D5%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20%5Ciota_%5Cell%5Ccirc%201_%7B%5Cmathbf%7B%5CDelta%7D(-%2C%5B%5Cell%5D)%7D%5Ctimes%20S_f%7Cf%3A%5B%5Cell%5D%5Cto%20%5Bn%5D%5Crangle%7D%22'%2C%20shift%20right%3D5%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\coprod\limits_{(f:[\ell]\to [n])\in\mathbf{\Delta}_{\leq k}}\mathbf{\Delta}(-,[\ell])\times S_n} &amp;&amp; {\coprod\limits_{[\ell] \in \mathbf{\Delta}_{\leq k}}\mathbf{\Delta}(-,[\ell])\times S_\ell} &amp;&amp; {\text{sk}_k(S_\bullet)}
	\arrow[&quot;{\langle \iota_n\circ \mathbf{\Delta}(-,f)\times 1_{S_n}|f:[\ell]\to [n]\rangle}&quot;, shift left=5, from=1-1, to=1-3]
	\arrow[&quot;{\langle \iota_\ell\circ 1_{\mathbf{\Delta}(-,[\ell])}\times S_f|f:[\ell]\to [n]\rangle}&quot;', shift right=5, from=1-1, to=1-3]
	\arrow[from=1-3, to=1-5]
\end{tikzcd}
" /></p>
In the case of $\partial\Delta^n$ we have an even simpler description.

>[!proposition] Characterization
>For $n \geq 1$, and $S_\bullet$ a simplicial set, the map 
>$$\mathsf{Set}^{\Delta^{op}}(\partial\Delta^n,S_\bullet)\to (S_{n-1})^{n+1}$$
>which sends $f$ to $f\circ \delta_n^i$ for $0 \leq i \leq n$ is injective with image those tuples $(\sigma_0,...,\sigma_n)$ of $(n-1)$-simplices of $S_\bullet$ satisfying the identity
>$$\sigma_j\cdot \delta_n^i = \sigma_i\cdot \delta_{n-1}^{j-1}$$
>for $0 \leq i < j\leq n$.

`\begin{proof}`
It suffices to show that $\partial\Delta^n$ is the coequalizer of the following diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ccoprod%5Climits_%7B0%20%5Cleq%20i%20%3C%20j%5Cleq%20n%7D%5CDelta%5E%7Bn-2%7D%7D%20%26%26%20%7B%5Ccoprod%5Climits_%7B0%5Cleq%20i%20%5Cleq%20n%7D%5CDelta%5E%7Bn-1%7D%7D%20%26%26%20%7B%5Cpartial%5CDelta%5En%7D%0A%09%5Carrow%5B%22%7B%5Clangle%20%5Ciota_i%5Ccirc%20%5Cdelta_%7Bn-1%7D%5E%7Bj-1%7D%7C0%5Cleq%20i%20%3C%20j%5Cleq%20n%5Crangle%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20%5Ciota_j%5Ccirc%20%5Cdelta_%7Bn-1%7D%5Ei%7C0%20%5Cleq%20i%20%3C%20j%20%5Cleq%20n%5Crangle%7D%22'%2C%20shift%20right%3D4%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Clangle%5Cdelta_n%5Ei%7C0%5Cleq%20i%5Cleq%20n%5Crangle%7D%22%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\coprod\limits_{0 \leq i &lt; j\leq n}\Delta^{n-2}} &amp;&amp; {\coprod\limits_{0\leq i \leq n}\Delta^{n-1}} &amp;&amp; {\partial\Delta^n}
	\arrow[&quot;{\langle \iota_i\circ \delta_{n-1}^{j-1}|0\leq i &lt; j\leq n\rangle}&quot;, shift left=2, from=1-1, to=1-3]
	\arrow[&quot;{\langle \iota_j\circ \delta_{n-1}^i|0 \leq i &lt; j \leq n\rangle}&quot;', shift right=4, from=1-1, to=1-3]
	\arrow[&quot;{\langle\delta_n^i|0\leq i\leq n\rangle}&quot;, from=1-3, to=1-5]
\end{tikzcd}
" /></p>

Note that it is indeed a cofork for the diagram, using the simplicial identity for $0 \leq i < j \leq n$:
$$\delta_n^i\circ \delta_{n-1}^{j-1} = \delta_n^j\circ \delta_{n-1}^i$$
To see that it is the coequalizer let $S_\bullet$ be a simplex with maps $\sigma_0,...,\sigma_n:\Delta^{n-1}\to S_\bullet$ making the diagram commute, which means that $\sigma_j\circ \delta_{n-1}^i = \sigma_i\circ \delta_{n-1}^{j-1}$ for every $0 \leq i < j \leq n$. Now, for each $0 \leq \ell \leq n-1$, we can define a map $\Delta^\ell\times \Delta([\ell],[n])\to S_\bullet$ by defining the map at $g:[\ell]\to [n]$ to be given by first putting $g$ in standard form $g:[\ell]\xrightarrow{s_k^{i_{\ell-k-1}}\cdots s_{\ell-1}^{i_0}} [k]\xrightarrow{\delta_n^{j_{n-k-1}}\cdots \delta_{k+1}^{j_0}} [n]$ where $i_0 > i_1 > \cdots > i_{\ell-k-1}$ and $j_0 < j_1 < \cdots < j_{n-k-1}$, and then taking the composite $\sigma_{j_{n-k-1}}\circ \overline{g}$ where $\overline{g}$ is the composite of all terms except the last. Note that $\ell-k-1 \geq 0$, so this is well-defined.

We need only show compatibility with individual face and degeneracy maps since all other maps, like $g$, can be expressed as a (unique) composite of them. Note that by definition composing with a degeneracy map will not change the end result. For the face maps, consider $\delta_\ell^i:[\ell-1]\to [\ell]$, $0 \leq i \leq \ell$.. Then at $g:[\ell]\to [n]$ going the top way gives 
$\sigma_{j_{n-k-1}}\circ \overline{g}\circ \delta_\ell^i$ while going the bottom way give the associated action on  $g\circ \delta^i_\ell:[\ell-1]\to [n]$. If $i = i_r,i_r+1$ for some $r$ then the $\delta_\ell^i$ will cancel with a degeneracy and the value of the action will still be $\sigma_{j_{n-k-1}}\circ \overline{g}\circ \delta_\ell^i$. Otherwise, we can use the simplicial identities to pass $\delta_\ell^i$ through we can write $\overline{g}\circ \delta_\ell^i$ as 
$$[\ell]\xrightarrow{s_{k}^{i_{\ell-k-1}'}\cdots s_{\ell-1}^{i_0'}} [k]\xrightarrow{\delta_{n-1}^{i'}\delta_{n-2}^{j_{n-k-2}'}\cdots \delta_{k+1}^{j_0'}} [n-1]$$
where $i'= i -\#$of $i_r < i-1$.  If $i' \leq j'_{n-k-2}$ we can re-order the face maps into standard form, and composing with $\delta_n^{j_{n-k-1}}$ will preserve the standard form, and we're done. Otherwise, $i' > j_{n-k-2}'$ and the decomposition is in standard form. If $j_{n-k-1} > i'$, it remains in standard form and nothing needs to be done. Otherwise, if $j_{n-k-1} \leq i'$ we can use the identity $\delta_n^{j_{n-k-1}}\circ \delta_{n-1}^{i'} = \delta_n^{i'+1}\circ \delta_{n-1}^{j_{n-k-1}}$. But, both directions then agree since $\sigma_{j_{n-k-1}}\circ \delta_{n-1}^{i'}\circ \overline{g}' = \sigma_{i'} \circ \delta_{n-1}^{j_{n-k-1}}\circ \overline{g}'$. Therefore, from the colimit definition of $\partial\Delta^n$ we obtain a unique map $\varphi:\partial\Delta^n\to S_\bullet$ such that for any $0 \leq \ell \leq n-1$ and any $g:[\ell]\to [n]$, $\varphi\circ g = \sigma_{j_{n-k-1}}\circ \overline{g}$. In particular, this means that $\varphi\circ \delta_n^i = \sigma_i$ for each $0 \leq i \leq n$. Further, these commutivity conditions are equivalent from our proof, so it follows that $\partial\Delta^n$ is indeed the co-equalizer of the diagram.
`\end{proof}`
Another proof can be given by arguing first that the cofork map into $\partial\Delta^n$ is surjective (and hence epi in simplicial sets) since all $m$-simplices $[m]\to [n]$ in $\partial\Delta^n$ are not surjective and hence miss some $0 \leq i \leq n$. This implies that they factor through the an $m$-simplex of the $i$th summand of $\coprod_{0\leq k \leq n}\Delta^{n-1}$. After showing surjectivity and that $\partial\Delta^n$ is a cofork, one can show that the unique map from the co-equalizer is an isomorphism of simplicial sets by showing that it is injective. For this we can again consider an $m$-simplex of $\partial\Delta^n$, namely $\alpha:[m]\to [n]$, which if in the image of two elements must miss two $0 \leq i < j \leq n$, and land as $\alpha = \delta_n^i\circ \beta_i = \delta_n^j\circ \beta_j$. Note that if $i = j$ then monotonicity of face maps imply that $\beta_i = \beta_j$, so dealing with the $i < j$ case is sufficient. But since $\delta_n^i\circ \beta_i = \delta^j_n\circ \beta_j$, and Equation [[Quasi-Categories Preliminaries#^c588f2]] is a pullback square, we obtain a unique $\beta:[m]\to [n-2]$ such that $\beta_i =\delta_{n-1}^{j-1}\circ \beta$ and $\beta_j = \delta^i_{n-1}\circ \beta$.


### Discrete Simplicial sets

As hinted to previously, simplicial sets of dimension $\leq 0$, have a simple description as **discrete simplicial sets**.

>[!proposition] Discrete Simplicial Sets
>The evaluation functor $\text{ev}_0:\mathsf{Set}^{\mathbb{\Delta}^{op}}\to \mathsf{Set}$ restricts to an equivalence of categories
>$$\{S_\bullet\;\vert\;\text{dim}(S_\bullet)\leq 0\}\simeq \mathsf{Set}$$
>with inverse given by the diagonal.

^b02003

`\begin{proof}`
Let $\Delta^*:\mathsf{Set}\to \mathsf{Set}^{\mathbb{\Delta}^{op}}$ be the diagonal or constant simplicial set functor. Then $\text{ev}_0\circ \Delta^* = 1_{\mathsf{Set}}$, so we need only show that when restricted to the full subcategory of simplicial sets of dimension $\leq 0$, $\Delta^*\circ \text{ev}_0\cong 1_{\mathsf{Set}^{\mathbb{\Delta}^{op}}_{\leq 0}}$. To prove this claim let $S_\bullet$ be a simplicial set of dimension $\leq 0$. This means that every $\sigma:\Delta^m\to S_\bullet$ factors as $\sigma:\Delta^m\to \Delta^0\xrightarrow{x_\sigma}S_\bullet$. Further, by our [[Quasi-Categories Preliminaries#^88170c|uniqueness of factorizations]], this assignment defines a bijection $S_m\cong S_0$. Additionally, if $f:[n]\to [m]$, then $\sigma\cdot f = (x_\sigma\cdot !)\cdot f = x_\sigma\cdot !$, so this assignment defines an isomorphism $S_\bullet \cong \Delta^*(\text{ev}_0(S_\bullet))$. Finally, this isomorphism is evidently natural in $S_\bullet$ since if we have a map of simplicial sets of dimension $\leq 0$, $g:S_\bullet\to T_\bullet$, then by definition $g(\sigma) = g(x_\sigma\cdot !) = g(x_\sigma)\cdot ! = x_{g(\sigma)}\cdot !$, using the fact that $!$ is epi. This completes the proof.
`\end{proof}`

The equivalence in [[Quasi-Categories Preliminaries#^b02003|Proposition 16]] is induced by an adjunction, $\Delta^*\dashv \text{ev}_0$.
Indeed, a map $\Delta^*(A)\to S_\bullet$ induces a map $A\to S_0$ by evaluation, and a map $A\to S_0$ induces a map $\Delta^*(A)\to S_\bullet$ by post-composition. Further, this is a special case of the adjunction $\text{Lan}_{\iota_k}\dashv \iota_k^*$ in the case of $k = 0$. That that in the case of $k = 0$, as above, this adjunction is equivalent to the statement that $\lim\limits_{\leftarrow[n]\in\mathbb{\Delta}^{op}}S_n$ exists and the canonical map to $S_0$ is an isomorphism, which follows formally from the fact that $[0]$ is terminal in $\mathbb{\Delta}$, and hence initial in $\mathbb{\Delta}^{op}$. 

Note that since limits and colimits of simplicial sets are computed levelwise, the fully faithful embedding $\Delta^*:\mathsf{Set}\hookrightarrow \mathsf{Set}^{\mathbb{\Delta}^{op}}$ preserves (small) limits and colimits, and so discrete simplicial sets are closed under the formation of (small) limits and colimits.


### Directed Graphs as Simplicial Sets

In the previous section we dealt with simplicial sets of dimension $\leq 0$. The theory of simplicial sets of dimension $\leq 1$, although more complicated, also admits an interesting description, now in terms of graphs. Recall that a directed (multi) graph (with loops) $G$ is a functor from $1\rightrightarrows 2$ to $\mathsf{Set}$. For any simplicial set $S_\bullet$ we have a natural directed graph, $G(S_\bullet)$ given by $G(S_\bullet)(2) = S_0$, $G(S_\bullet)(1) = S_1$, $G(S_\bullet)(s) = \cdot \delta_1^1$ and $G(S_\bullet)(t) = \cdot \delta_1^0$. This assignment is functorial as maps of graphs are simply natural transformations, and maps of simplicial sets are also natural transformations.

Moving forward we denote this functor by $\text{Gr}:\mathsf{Set}^{\mathbb{\Delta}^{op}}\to \mathsf{Graph}$, which is simply a functor of the form $\iota^*$ for the inclusion of $1 \rightrightarrows 2$ as $[1]\rightrightarrows [0]$. From our theory of [[Kan Extensions]] it follows that $\text{Gr}$ has left and right adjoints given by left and right pointwise Kan extensions. We show that when restricted to simplicial sets of dimension $\leq 1$ this functor gives an equivalence of categories.

>[!proposition] Gr is Fully-Faithful
>The functor $\text{Gr}$ is fully-faithful with respect to maps out of simplicial sets of dimension $\leq 1$.

`\begin{proof}`
Let $S_\bullet$ and $T_\bullet$ be simplicial sets, with $S_\bullet$ of dimension $\leq 1$. Then consider the assignment $\mathsf{Set}^{\mathbb{\Delta}^{op}}(S_\bullet,T_\bullet)\to \mathsf{Graph}(\text{Gr}(S_\bullet),\text{Gr}(T_\bullet))$. Since $S_\bullet$ is of dimension  we have the coequalizer diagram<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ccoprod%5Climits_%7B(f%3A%5B%5Cell%5D%5Cto%20%5Bm%5D)%5Cin%5Cmathbf%7B%5CDelta%7D_%7B%5Cleq%201%7D%7D%5Cmathbf%7B%5CDelta%7D(-%2C%5B%5Cell%5D)%5Ctimes%20S_m%7D%20%26%26%20%7B%5Ccoprod%5Climits_%7B0%20%5Cleq%20%5Cell%20%5Cleq%201%7D%5Cmathbf%7B%5CDelta%7D(-%2C%5B%5Cell%5D)%5Ctimes%20S_%5Cell%7D%20%26%26%20%7BS_%5Cbullet%7D%0A%09%5Carrow%5Bshift%20left%3D2%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bshift%20right%3D2%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\coprod\limits_{(f:[\ell]\to [m])\in\mathbf{\Delta}_{\leq 1}}\mathbf{\Delta}(-,[\ell])\times S_m} &amp;&amp; {\coprod\limits_{0 \leq \ell \leq 1}\mathbf{\Delta}(-,[\ell])\times S_\ell} &amp;&amp; {S_\bullet}
	\arrow[shift left=2, from=1-1, to=1-3]
	\arrow[shift right=2, from=1-1, to=1-3]
	\arrow[from=1-3, to=1-5]
\end{tikzcd}
" /></p>
Since $\text{Gr}$ preserves limits and co-limits and maps out of this equalizer diagram land in $\text{sk}_1(T_\bullet)$, we do indeed obtain a bijection.
`\end{proof}`


>[!proposition] Simplicial Sets of Dimension $\leq 1$ as Graphs
>Restricting $\text{Gr}$ to a map on simplicial sets of dimension $\leq 1$ induced an equivalence of categories 
>$$\mathsf{Set}^{\mathbb{\Delta}^{op}}_{\leq 1}\simeq \mathsf{Graph}$$

`\begin{proof}`
Note that the inclusion $\iota:(1\rightrightarrows 2)\to \mathbb{\Delta}$ is that of a full-subcategory. Thus, by [[Kan Extensions#^90826e]] we have that the natural transformation $\alpha:1_{\mathsf{Graph}}\Rightarrow\iota^*\text{Lan}_\iota$ can be given by the identity, or at least a natural isomorphism, which implies that $\iota^*$ is essentially surjective. Further, $\iota^*$ is also fully faithful upon restriction to dimension $\leq 1$ simplicial sets, and so it is an equivalence of categories.
`\end{proof}`

### Map from non-degenerate simplices

In this small subsection we prove that to give a map of simplices $S_\bullet\to T_\bullet$, it suffices to give a map $S_\bullet^{nd}\to T_\bullet$ which respects face maps, where $S_\bullet^{nd}$ is the subset of $S_\bullet$ consisting only of non-degenerate simplices. We prove this claim below.

>[!lem] Simplicial map from map on non-degenerate simplices
>Let $\varphi:S_\bullet^{nd}\to T_\bullet$ be a map of simplices such that for any non-degenerate $n$-simplex $\sigma$, and any face map $\delta_i^n$, if $\sigma\cdot \delta_i^n = \sigma'\cdot \alpha$, where $\sigma'\cdot \alpha$ is the unique factorization of $\sigma\cdot \delta_i^n$ as a non-degenerate simplex and an epimorphism, then $\varphi(\sigma)\cdot \delta_i^n = \varphi(\sigma')\cdot \alpha$. Then $\varphi$ extends uniquely to a map of simplicial sets $H:S_\bullet\to T_\bullet$.

^f585d6

`\begin{proof}`
First, let $f,g:S_\bullet\to T_\bullet$ such that $f(\sigma) = g(\sigma)$ for any non-degenerate simplex $\sigma$. Then if $\tau$ is an $n$-simplex in $S_\bullet$, by [[Quasi-Categories Preliminaries#^88170c]] we have a unique epimorphism $\alpha:[n]\to [m]$ and a non-degenerate $m$-simplex $\sigma$ such that $\tau = \sigma\cdot \alpha$. Then by assumption $f(\tau) = f(\sigma)\cdot \alpha = g(\sigma)\cdot \alpha = g(\tau)$.

Next, let $\varphi:S_\bullet^{nd}\to T_\bullet$ be a map as described in the problem statement. Let $\tau$ be an $n$-simplex in $S_\bullet$ with unique factorization $\tau = \sigma\cdot \alpha$. Define $H:S_\bullet\to T_\bullet$ by $H(\sigma\cdot \alpha) = h(\sigma)\cdot \alpha$. Since the factorization is unique this definition is well-posed, so we need only show that it gives a map of simplicial sets. Note that if $\eta_i^{n}$ is a degeneracy, then $\tau \cdot \eta_i^{n} = \sigma\cdot (\alpha\circ \eta_i^{n})$ is the unique factorization, so $H(\tau\cdot \eta_i^{n}) = H(\tau)\cdot \eta_i^{n}$ by definition.

Next, consider a face map $\delta_i^n$. Then $\alpha\circ \delta_i^n$ is either itself surjective (because $\delta_i^n$ cancels with some term), in which case the claim holds, or it is equal to $\delta_j^m\circ \beta$ where $\beta:[n]\to [m-1]$ is surjective. Then $H(\tau\cdot \delta_i^n) = H(\sigma\cdot \delta_j^m)\cdot\beta$ from our previous work. Thus, it suffices to show $H(\sigma\cdot \delta_j^m) = \varphi(\sigma)\cdot\delta_j^m$. Factor $\sigma\cdot\delta_j^m$ as $\sigma'\cdot \alpha'$ for some non-degenerate $k$-simplex $\sigma'$ and some surjective $\alpha':[m-1]\to [k]$, necessarily unique. Then by assumption we have that $\varphi(\sigma)\cdot \delta_j^m = \varphi(\sigma')\cdot \alpha'$. It follows that 
$$H(\sigma \cdot\delta_j^m) = H(\sigma'\cdot\alpha) = \varphi(\sigma')\cdot \alpha = \varphi(\sigma)\cdot \delta_j^m$$
as desired.
`\end{proof}`

#### References

[^1]: Lurie, J. (n.d.). Kerodon. https://kerodon.net/. Accessed 16 May 2024
