---
date: 2024-05-23T09:39:00
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

These notes are for the final lecture in the 2024 mini-course on 2-Segal spaces hosted by Julie Bergner. We begin by returning to ![[2-Segal Spaces via Double Categories#^b6bbe5]] which involves partitions of subgraphs.

## 2-Segality and Hall Algebra of $X_\mathcal{G}$

The 2-Segal set $X_\mathcal{G}$ is strictly 2-Segal in the sense that it is not 1-Segal. This is due to the fact that, say, the the maps $(d_2,d_0):X_2\to X_1\times_{X_0}X_1$ sends both the partition with just vertices and that with edges to the same output.

Now, what is the Hall algebra for this 2-Segal set? First, note that $X_0 = *$, so the set is reduced and we do get an algebra. $\mathcal{H}_{\mathcal{G}}$ is then given by the vector space spanned by subgraphs of $\mathcal{G}$ (i.e. elements of $X_1$). The multiplication is given by $H*K = \sum_Jg_{HK}^JJ$, where $H,K,J \subseteq \mathcal{G}$ are subgraphs and $g_{HK}^J$ counts 2-simplices (i.e. subgraphs $J$ which contain $H$ and $K$ as disjoint subgraphs, and with vertices equal to the union of the vertices of $K$ and $H$), and the empty subgraph is the unit element.

>[!example]
>Consider $\mathcal{G} = (a\to b)$. The algebra is $5$-dimensional, with basis $[\emptyset], [a], [b], [a\;\;\;\;b],$ and $[a\to b]$. The only non-trivial multiplication is $$[a]*[b] = [a\;\;\;\;b]+ [a\to b]=[b]*[a]$$

>[!example]
>If $\mathcal{G}$ is the self-loop the subgraphs are $[\emptyset]$, $[a]$, and the self loop. In this case there is no nontrivial multiplication, since the two nonempty subgraphs are not disjoint.


>[!proposition] Properties of $\mathcal{H}(X_\mathcal{G})$
>1. If $H\cap K \neq \emptyset$, then $H*K = 0$ (no 2-simplex with $d_0 = K$ and $d_2 = H$)
>2. If $a \neq b$ are vertices of $\mathcal{G}$, then $a*b = \sum_{H}H$ where $V(H) = \{a,b\}$. 
>3. More generally, if $H \cap K = \emptyset$, then $H*K = \sum_JJ$ where $H\amalg K \subseteq J$ and $V(J) = V(H)\amalg V(K)$.
>4. $\mathcal{H}(X_\mathcal{G})$ is commutative since partitions come in pairs that are invisible $\mathcal{H}$.
>5. The coefficients $g_{HK}^J$ are always either $0$ or $1$.

>[!example]
>Consider the graph $\mathcal{G} = (a\to b\rightrightarrows c)$, with arrows $f:b\to c$ and $g:b\to c$, if $H = [a\to b]$ and $K  = [c]$, then
>$$H*K = [a\to b\;\;\;\;c]+[a\to b\xrightarrow{f}c]+[a\to b\xrightarrow{g}c]+[a\to b\rightrightarrows c]$$


## 2-Segal Sets Associated to Rooted Trees

This is joint work with Borghi, Day, Galvez-Cavrillo, Haekstra-Mandoral. Throughout let $T$ be a rooted tree, and we will keep the example
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09e%20%26%26%20f%20%5C%5C%0A%09%26%20d%20%26%26%20c%20%5C%5C%0A%09%26%26%20b%20%5C%5C%0A%09%26%26%20a%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D2-4%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D3-3%2C%20to%3D4-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	e &amp;&amp; f \\
	&amp; d &amp;&amp; c \\
	&amp;&amp; b \\
	&amp;&amp; a
	\arrow[from=1-1, to=2-2]
	\arrow[from=1-3, to=2-2]
	\arrow[from=2-2, to=3-3]
	\arrow[from=2-4, to=3-3]
	\arrow[from=3-3, to=4-3]
\end{tikzcd}
" /></p>
in mind. We say that a cut on a tree is **admissible** if the tree $T$ is divided into a lower subtree, either containing the root or empty, and an upper tree/forest.

We define a simplicial set $Y := Y_T$ associated with the tree $T$ as follows:
1. $Y_0 = *$
2. $Y_1 =$ the collection of all subforests of $T$ obtained from admissible cuts.
3. $Y_2 =$ the collection of elements of $Y_1$ together/equipped with an admissible cut (requires a notion of cuts for forests - a kind of tree-wise cut)
4. $Y_n =$ elements of $Y_1$ with $n-1$ admissible cuts.
For face and degeneracy maps we work top to bottom. Thus, if we have an element of $Y_2$, which is a tree with an admissible cut, $d_0$ sends the tree to sub-forest above the cut, $d_2$ sends it to the sub-forest below the cut, and $d_1$ just forgets the cut. On the other hand, degeneracy maps insert cuts. For example, again for element of $Y_2$, $s_0$ inserts a cut at the top, $s_2$ inserts a cut on the bottom, and $s_1$ duplicates the cut.


For a rooted tree $T$, $Y_T$ is again a $2$-Segal set. One piece tells you the tree and the other tells you what the missing cut is. However, it is not 1-Segal since you can't always compose.

Since any rooted tree can be thought of as a graph, how are $Y_T$ and $X_T$ related?

>[!proposition]
>Given a tree $T$, $Y_T$ forms a sub-2-Segal set of $X_T$, where we consider the underlying subgraph of $T$.

We can also look at the Hall algebras, but since this construction is not functorial we do not get an algebra map from $\mathscr{H}(Y_T)$ to $\mathscr{H}(X_T)$. Further, due to the "ordering" on the tree, $\mathscr{H}(Y_T)$ is not in general commutative, unlike $\mathscr{H}(X_T)$.


## Looking Towards Higher Segal Spaces

>[!proposition] Dyckerhoff-Kapronov
>A functor $X:\mathbb{\Delta}^{op}\to \mathsf{SSets}$ is $2$-Segal if and only if the $2$-Segal maps corresponding to the triangulation given by all diagonals radiating out of $0$, and the triangulation given by all diagonals radiating out of $n$, are weak equivalences for $n \geq 3$.

As a consequence we obtain the following definition.

>[!def]
>A simplicial space $X:\mathbb{\Delta}^{op}\to \mathsf{SSets}$ is 
>- **Lower $2$-Segal** if the maps for the $0$-ray triangulations are weak equivalences for all $n \geq 3$
>- **Upper $2$-Segal** if the maps for the $n$-ray triangulations are weak equivalences for all $n \geq 3$.

>[!corollary]
>$X$ is $2$-Segal if and only if it is both upper and lower $2$-Segal.

For $d \geq 3$, we can generalize these definitions to ones for upper and lower $d$-Segal spaces, using the theory of **cyclic polytopes**. Briefly consider the map $v:\mathbb{R}\to \mathbb{R}^d$ given by $v(t) = (t,t^2,...,t^d)$.

>[!def]
>The **cyclic $d$-dimensional polytope** on $[n]$ is the **convex hull** of $v([n])$, denoted by $C([n],d)$.

>[!example]
>- $C([3],0) = \{0\}$
>- $C([3],1) = (0\to 1 \to 2\to 3)$, $v:t \mapsto t$
>- $C([3],2)$ has $v:t\mapsto (t,t^2)$, giving a convex polytope
>- $C([3],3)\cong \Delta^3$

There is a combinatorial description of **upper** and **lower** subsets of $[n]$ that can be used to define upper and lower $d$-Segal maps, recovering the above notions when $d = 2$. This theory is related to that of **$n$-excisive functors** (Walde). It should also result from higher $S_\bullet$-construction (see Paguathe). Finally, we also want to see some algebraic structure (Gal-Gal).