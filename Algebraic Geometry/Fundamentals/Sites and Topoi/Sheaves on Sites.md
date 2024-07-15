---
date: 2024-05-23T12:12:00
tags:
  - AlgebraicGeometry
  - CategoryTheory
  - Sheaves
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

One of the most important structures in algebraic geometry, and modern geometry more generally, is the concept of a sheaf on a space. The primary reason for the prevalence of sheaves in geometry is the fact that they provide a framework for formalizing when locally defined objects on a space can be glued uniquely into a globally defined object. For example, in differential geometry we have a number of important sheaves including sheaves of $C^k$-functions for $k \in \mathbb{N}\cup \{\infty\}$, sheaves of analytic functions, and even sheaves of holomorphic functions on complex manifolds. 


Since the introduction of categorical language into algebraic geometry, category theory has provided an elegant way of describing sheaves on a topological space. On the other hand, the equivalence of categories between the category of affine schemes and the category of commutative rings with identity suggests a more general approach to sheaf theory which includes sheaves on categories that aren't derived from the open sets on a topological space. 


In these notes we provide an introduction to this theory, which has roots in the notion of a Grothendieck site on a category[^1]. We will begin with introducing the notion of covering families and grothendieck topologies on a category before formalizing a number of equivalent notions of sheaves on a site. We will also prove a number of important properties of sheaves on a site, including the fact that the category of sheaves is (co)complete. 

## Sites

Although sheaves are initially introduced in the setting of point set topological spaces, their categorical formalizations have been drastically generalized by Grothendieck and his school. A first hint to this approach is that for any (small) category $\mathcal{C}$ we can considered the (set-valued) presheaf category $\mathsf{Ps}(\mathcal{C}) := [\mathcal{C}^{op},\mathsf{Set}]$. Recall that if $X$ is a topological space, we consider the presheaf category $\mathsf{Ps}(\mathsf{Top}(X)) = [\mathsf{Top}(X)^{op},\mathsf{Set}]$, in which case the sheaf condition is phrased in terms of open coverings on $X$. Explicitly, we state that a presheaf $F:\mathsf{Top}(X)^{op}\to \mathsf{Set}$ is a sheaf if for any open set $U \subseteq X$ with cover $U = \bigcup_{i \in I}U_i$, a collection of sections $s_i \in F(U_i)$ such that $F(U_i\cap U_j\subseteq U_i)(s_i) = F(U_i\cap U_j\subseteq U_j)(s_j)$ has a unique gluing $s \in F(U)$ such that $F(U_i\subseteq U)(s) = s_i$ for all $i \in I$. In the categorical language this is exactly the statement that we have the equalizer diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BF(U)%7D%20%26%26%20%7B%5Cprod_%7Bi%20%5Cin%20I%7DF(U_i)%7D%20%26%26%20%7B%5Cprod_%7Bi%2Cj%5Cin%20I%7DF(U_i%5Ccap%20U_j)%7D%0A%09%5Carrow%5B%22%7B%5Clangle%20F(U_i%5Csubseteq%20U)%3Ai%20%5Cin%20I%5Crangle%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20F(U_i%5Ccap%20U_j%5Csubseteq%20U_i)%5Ccirc%20%5Cpi_i%3Ai%2Cj%20%5Cin%20I%5Crangle%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20F(U_i%5Ccap%20U_j%5Csubseteq%20U_j)%5Ccirc%20%5Cpi_j%3Ai%2Cj%20%5Cin%20I%5Crangle%7D%22'%2C%20shift%20right%3D2%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{F(U)} &amp;&amp; {\prod_{i \in I}F(U_i)} &amp;&amp; {\prod_{i,j\in I}F(U_i\cap U_j)}
	\arrow[&quot;{\langle F(U_i\subseteq U):i \in I\rangle}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\langle F(U_i\cap U_j\subseteq U_i)\circ \pi_i:i,j \in I\rangle}&quot;, shift left=2, from=1-3, to=1-5]
	\arrow[&quot;{\langle F(U_i\cap U_j\subseteq U_j)\circ \pi_j:i,j \in I\rangle}&quot;', shift right=2, from=1-3, to=1-5]
\end{tikzcd}
" /></p>
In order to generalize this we introduce a suitable notion of topology not just on a set, but on a category. This can be done in terms a covering families and sieves.[^1].

>[!def] Sieves
>A **sieve** on an object $C \in \mathcal{C}_0$ is a presheaf $S:\mathcal{C}^{op}\to \mathsf{Set}$ such that $S(D) \subseteq y_C(D)$ for all $D \in \mathcal{C}_0$, and for all $f:D\to E$ in $\mathcal{C}$, $S(f)$ is $y_C(f)$ restricted to $S(E)$.

Note that a sieve $S$ on an object $C$ is equivalent to a subset of all maps into $C$ which is closed under pre-composition.

Next, for $C \in \mathcal{C}_0$, let $\mathsf{Sieve}(C)$ denote the poset of sieves on $C$ ordered by restriction. That is, if $S$ and $R$ are sieves on $C$, then $S \subseteq R$ if and only if $S(D) \subseteq R(D)$ for all $D \in \mathcal{C}_0$. Then for every $h:D\to C$ in $\mathcal{C}$ we have a natural map of posets $h^*:\mathsf{Sieve}(C)\to \mathsf{Sieve}(D)$ given on $S \in \mathsf{Sieve}(C)$ by 
$$h^*(S)(E) = \{g:E\to D\,|\,h\circ g \in S(E)\}$$
These operations define a functor $y_{sv}:\mathcal{C}^{op}\to \mathsf{Poset}$ from $\mathcal{C}$ to the category of posets with monotone maps between them.

Sieves will now take the place of coverings by open sets in our definition of a sheaf. In this way we can define a topology on a category.

>[!def] Grothendieck Topology
>A **Grothendieck topology** on a category $\mathcal{C}$ consists of a functor $J:\mathcal{C}\to \mathsf{Poset}$ such that for each $C \in \mathcal{C}_0$, $J(C) \subseteq \mathsf{Sieve}(C)$ is a sub-poset of the sieve poset with induced maps such that the following hold:
>1. (Maximality) $y_C \in J(C)$ for all $C \in \mathcal{C}_0$
>2. (Transitivity) if $S \in J(C)$ and $R \subseteq y_C$ such that for any $h:D\to C$ in $S$, $h^*(R) \in J(D)$, then $R \in J(C)$
>
>Classically the condition that for $h:D\to C$, $h^*$ restricts to a map $J(C)\to J(D)$, is usually referred to as a third axiom called the stability axiom. A **site** is then a category $\mathcal{C}$ together with a Grothendieck Topology (for size considerations we often take $\mathcal{C}$ to be small).

^f8480d

Intuitively we think of sieves in a Grothendieck topology as covering the objects they lie over. In particular, for a topological space $X$ we have a natural site on $\mathsf{Top}(X)$ given by covers of open sets. A sieve on an open set $U$ in $\mathsf{Top}(X)$ is then exactly a families of open sets contained in $U$ which is closed downward, and a covering sieve is such a family with union equal to $U$. As in the case of point-set topology it is often more convenient to work with simpler structure which generate topologies than the topology in full. This brings us to the notion of a basis of a Grothendieck topology.

>[!def] Basis for a Grothendieck Topology
>A basis for a Grothendieck topology on a category $\mathcal{C}$ is a set function $K$ such that $K(C) \subseteq \mathcal{P}(\mathcal{C}(-,C))$, where we view $\mathcal{C}(-,C)$ as the set of arrows into $C$. The function $K$ must satisfy the following conditions:
>1. $\{f:D\to C\} \in K(C)$ for any isomorphism $f:D\to C$ in $\mathcal{C}$
>2. (Stability) If $A \in K(C)$, then for any $g:D\to C$ there exists a $B \in K(D)$ such that for every $h:E\to D$ in $B$ , there exists $f:D'\to C$ in $A$ and $h':E\to D'$ such that 
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%20%20%20%20%09E%20%26%20D%20%26%20C%20%5C%5C%0A%20%20%20%20%20%20%20%20%09%26%20%7BD'%7D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5B%22h%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists%20h'%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%20%20%20%20%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]        	E &amp; D &amp; C \\        	&amp; {D'}        	\arrow[&quot;h&quot;, from=1-1, to=1-2]        	\arrow[&quot;g&quot;, from=1-2, to=1-3]        	\arrow[&quot;{\exists h'}&quot;', dashed, from=1-1, to=2-2]        	\arrow[&quot;f&quot;', from=2-2, to=1-3]        \end{tikzcd}" /></p>
>commutes.
>3. If $A \in K(C)$ and for each $f \in A$, $B_f \in K(\text{dom}(f))$, then the composite $A\circ \{B_f\}_{f \in A} \in K(C)$ where $$A\circ \{B_f\}_{f \in A} := \{f\circ g:D\to C:f \in A,g \in B_f\}$$

In the case when $\mathcal{C}$ has pullbacks the stability axiom can be phrased slightly differently. In particular, if $A \in K(C)$, then for any $g:D\to C$ we want the base-change of $A$ by $g$, $\{\pi_f:E\times_CD\to D|f:E\to C \in A\}$, to be in $K(D)$. This begins to illuminate the naming convention of the stability axiom, since it says that covers are stable under base change.

From a basis $K$ we generate a topology $J$ by saying $S \in J(C)$ if and only if there exists $R \in K(C)$ such that $R \subseteq S$. Intuitively this says that a sieve covers $C$ if and only if it covers a basis element that covers $C$. This indeed generates a topology on $\mathcal{C}$.

`\begin{proof}[Proof of Basis.]`
Let $K$ be a basis for a topology on $\mathcal{C}$, and we show that the described condition defines a topology $J$ on $\mathcal{C}$. First, since $K$ contains all singletons with isomorphisms, in particular $\{1_C:C\to C\} \in K(C)$, so the maximal sieve $y_C \in J(C)$ as it contains the identity on $C$.

Next, to show that $J:\mathcal{C}\to \mathsf{Poset}$ is a functor, we need to show that for $h:D\to C$ in $\mathcal{C}$ and for $S \in J(C)$, $h^*(S) \in J(D)$. Since $S \in J(C)$ there exists $A \in K(C)$ such that $A \subseteq S$. By the stability axiom for Grothendieck bases we have a $B \in K(D)$ such that for any $g:E\to D$ in $B$, we have $f:D'\to C$ in $A$ ad $h':E\to D'$ such that $h\circ g = f\circ h'$. In terms of $S$ this says that for any $g:E\to D$ in $B$, $h\circ g= f\circ h' \in S$ since $A \subseteq S$ and $S$ is a sieve, so $g \in h^*(S)$. In other words, $B \subseteq h^*(S)$, so $h^*(S) \in J(D)$.

Finally, to show transitivity suppose $S \in J(C)$ is a covering sieve and $R \subseteq y_C$ such that for any $h:D\to C$ in $S$, $h^*(R) \in J(D)$. In terms of $K$ this says that there exists $A \in K(C)$ such that $A \subseteq S$, and for all $h:D\to C$ in $S$, there exists $B_h \in J(D)$ such that $B_h \subseteq h^*(R)$. Then by axiom (3) for $K$ we have that 
$$A\circ \{B_h\}_{h \in A} = \{h\circ g:E\to C\,\vert\,h \in A,g \in B_h\} \in K(C)$$
Since $A \subseteq S$, we have that for all $h \in A$ and all $g \in B_h$, $g \in h^*(R)$ so $h\circ g \in R$ by definition. In other words, $A\circ \{B_h\}_{h \in A} \subseteq R$, so $R \in J(C)$, as desired.
`\end{proof}`
A few examples of Grothendieck topologies and sites can now be given, including the famed Zariski site as a structure on a purely algebraic category[^1].

- For any category $\mathcal{C}$, there is a trivial topology where the only covering sieves are maximal sieves.
- On the other extreme, for any category $\mathcal{C}$ we have the atomic topology where all non-empty sieves are covering sieves. For this topology to exist we must require that two morphisms $f:D\to C$ and $g:E\to C$ can be completed into a commuting square (not necessarily uniquely).
- If $P$ is a partially ordered set viewed as a category, the **dense topology** is given by specifying the covering sieves of $p \in P$ to be those subsets $D \subseteq y_p$ such that for any $r \leq p$, there exists $q \leq r$ with $q \in D$. In general, $\mathcal{C}$ has a dense topology where $S \subseteq y_C$ is a covering sieve if and only if for any $f:D\to C$ there exists $g:E\to D$ such that $f\circ g \in S$.
- The **Zariski site** on $\mathsf{CRing}^{op}$ can be defined in terms of a basis. A cover of a cring $A$ is a finite family of the form $$\{A\to A_{f_i}|1\leq i \leq n\}$$ in $\mathsf{CRing}$ up to possible isomorphism such that $A = \langle f_1,...,f_n\rangle$.

`\begin{proof}[Proof of Zariski Site]`
Let $K$ be the proposed basis. The up to isomorphism condition in the definition ensures that all singleton isomorphisms are are in $K$, so condition (1) is satisfied.

Since $\mathsf{CRing}^{op}$ has pullbacks given by pushouts in $\mathsf{CRing}$, we can use the pullback version of the stability condition. To this effect let $\{A\to A_{f_i}|1 \leq i \leq n\}$ be in $K(A)$ and let $g:A\to B$ be a map of crings. For each $i$ we can perform the pushout
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%20%20%20%20%09A%20%26%20%7BA_%7Bf_i%7D%7D%20%5C%5C%0A%20%20%20%20%20%20%20%20%09B%20%26%20%7BB%5Cotimes_AA_%7Bf_i%7D%7D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5B%22g%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%20%20%20%20%20%20%20%20%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D180%7D%2C%20draw%3Dnone%2C%20from%3D2-2%2C%20to%3D1-1%5D%0A%20%20%20%20%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
        	A &amp; {A_{f_i}} \\
        	B &amp; {B\otimes_AA_{f_i}}
        	\arrow[&quot;g&quot;', from=1-1, to=2-1]
        	\arrow[from=1-1, to=1-2]
        	\arrow[from=1-2, to=2-2]
        	\arrow[from=2-1, to=2-2]
        	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=180}, draw=none, from=2-2, to=1-1]
        \end{tikzcd}
" /></p>
However, since $A_{f_i} \cong  A[x]/\langle f_ix-1\rangle$, we can use properties of the tensor to conclude that 
$$B\otimes_AA_{f_i} \cong B\otimes_AA[x]/\langle f_ix-1\rangle \cong (B\otimes_AA[x])/(B\otimes\langle f_ix-1\rangle) \cong B[x]/\langle g(f_i)x-1\rangle$$
This implies that the base changed set is isomorphic to
$$\{B\to B_{g(f_i)}:1\leq i \leq n\}$$
where $\langle g(f_1),...,g(f_n)\rangle = g(\langle f_1,...,f_n\rangle)B = g(A)B = B$, since we are working with unital rings. This shows that the base change of a cover is again a cover.

Finally, to show transitivity consider again a basic cover $\{A\to A_{f_i}:1 \leq i \leq n\}$ along with for each $1 \leq i \leq n$, a basic cover $\{A_{f_i}\to (A_{f_i})_{g_{i,j}}:1 \leq j \leq n_i\}$, where $\langle g_{i,1},...,g_{i,n_i}\rangle$ in $A_{f_i}$. Note that if $g_{i,j} = \frac{a_{i,j}}{f_i^k}$ for some integer $k \geq 0$ and some $a_{i,j} \in A$, then $(A_{f_i})_{g_{i,j}} \cong A_{f_i,a_{i,j}} \cong A_{f_ia_{i,j}}$ using properties of the localization using its universal property. This gives us isomorphic basic covers
$$\{A_{f_i}\to A_{f_ia_{i,j}}:1\leq j \leq n_i\}$$
Then the composite set is exactly the collection of localizations
$$\{A\to A_{f_ia_{i,j}}:1\leq i \leq n,1\leq j \leq n_i\}$$
To see that this is a basic open cover, note that if $1 \leq i \leq n$, then by assumption we have $b_{i,j} \in A$ such that for a sufficiently large integer $K$,
$$f_i^K = \sum_{j=1}^{n_i}b_{i,j}a_{i,j}$$
Since we are dealing with a finite set of localizations we can choose a large enough $K$ that works for all $i$. Now since $\langle f_1,...,f_n\rangle = A$, we also have that $\langle f_1^{K+1},...,f_n^{K+1}\rangle = A$. This fact follows by raising the expression of $1\in A$ in terms of the $f_i$ to a suitably high power (e.g.\ $n(K+1)$). Then we have some $c_1,...,c_n \in A$ such that
$$1 = \sum_{i=1}^nc_if_i^{K+1} = \sum_{i=1}^nc_if_i \sum_{j=1}^{n_i}b_{i,j}a_{i,j} = \sum_{i=1}^n\sum_{j=1}^{n_i}(c_ib_{i,j})(f_ia_{i,j})$$
as desired.
`\end{proof}`
The Zariski site is our primary motivating example of a site, but as we will see soon we also have another extremely important site that in a rigourous sense gives a finer topology for studying schemes.

### Sheaves on a Site

Now that we have a sensible notion of topology on a category we can start discussing sheaves. There are many equivalent formulations of sheaves, and we will provide a few to illuminate the concept. 

Recall that by definition of a sieve $S$ on $C$, we have a natural inclusion $\iota_S:S\hookrightarrow y_C$ given on components by inclusion of subsets. In the setting of topological spaces we consider the unique gluing of sections defined over open coverings. If a sieve $S$ is supposed to be a covering of $C$, then for a presheaf $P$ on $\mathcal{C}$, we want to say that $P$ is a sheaf if for any assignment $f\mapsto x_f$ from $f \in S$ to $x_f \in P(\text{dom}(f))$ such that $P(g)(x_f) = x_{f\circ g}$, there exists a unique $x \in P(C)$ for which $P(f)(x) = x_f$ for $f \in S$. Categorically this can be phrased as an extension problem
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09S%20%26%20P%20%5C%5C%0A%09%7By_C%7D%0A%09%5Carrow%5B%22%7B%5Ciota_S%7D%22'%2C%20tail%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7B%5Cexists!%5Cwidehat%7B%5Calpha%7D%7D%22'%2C%20dashed%2C%20from%3D2-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Calpha%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	S &amp; P \\
	{y_C}
	\arrow[&quot;{\iota_S}&quot;', tail, from=1-1, to=2-1]
	\arrow[&quot;{\exists!\widehat{\alpha}}&quot;', dashed, from=2-1, to=1-2]
	\arrow[&quot;\alpha&quot;, from=1-1, to=1-2]
\end{tikzcd}
" /></p>
In other words we can describe sheaves as those presheaves $P$ which lift maps from covers uniquely into maps from maximal covers. As in the classical setting, this condition is equivalent to $P(C)$ being an equalizer of a diagram over the maps in a covering sieve:<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BP(C)%7D%20%26%26%20%7B%5Cprod_%7Bf%20%5Cin%20S%7DP(%5Ctext%7Bdom%7D%20f)%7D%20%26%26%20%7B%5Cprod_%7Bf%5Ccirc%20g%20%5Cin%20S%7DP(%5Ctext%7Bdom%7D%20g)%7D%0A%09%5Carrow%5B%22%7B%5Clangle%20P(f)%3Af%20%5Cin%20S%5Crangle%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20%5Cpi_%7B%5Ctext%7Bdom%7D%20g%7D%5C%2C%5Cvert%5C%2Cf%5Ccirc%20g%5Cin%20S%5Crangle%7D%22'%2C%20shift%20right%3D2%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20P(g)%5Ccirc%20%5Cpi_%7B%5Ctext%7Bdom%7Df%7D%5C%2C%5Cvert%5C%2Cf%5Ccirc%20g%20%5Cin%20S%5Crangle%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{P(C)} &amp;&amp; {\prod_{f \in S}P(\text{dom} f)} &amp;&amp; {\prod_{f\circ g \in S}P(\text{dom} g)}
	\arrow[&quot;{\langle P(f):f \in S\rangle}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\langle \pi_{\text{dom} g}\,\vert\,f\circ g\in S\rangle}&quot;', shift right=2, from=1-3, to=1-5]
	\arrow[&quot;{\langle P(g)\circ \pi_{\text{dom}f}\,\vert\,f\circ g \in S\rangle}&quot;, shift left=2, from=1-3, to=1-5]
\end{tikzcd}
" /></p>

If a topology is generated by a basis $K$ we can also describe the sheaf condition in another form using this equalizer classification. This re-characterization can be seen to have a very geometric flavour when considering a category $\mathcal{C}$ with pullbacks. If $K$ is a basis on such a category, then the sheaf condition becomes the statement that for any basic cover $\{f_i:C_i\to C\,\vert\,i \in I\}$, $P(C)$ is an equalizer of the following diagram:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BP(C)%7D%20%26%26%20%7B%5Cprod_%7Bi%20%5Cin%20I%7DP(C_i)%7D%20%26%26%20%7B%5Cprod_%7Bi%2Cj%20%5Cin%20I%7DP(C_i%5Ctimes_CC_j)%7D%0A%09%5Carrow%5B%22%7B%5Clangle%20P(f_i)%3Ai%20%5Cin%20I%5Crangle%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20P(%5Cpi_%7Bi%2Cj%7D%5E2)%5Ccirc%20%5Cpi_j%5C%2C%5Cvert%5C%2Ci%2Cj%20%5Cin%20I%5Crangle%7D%22'%2C%20shift%20right%3D2%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5B%22%7B%5Clangle%20P(%5Cpi_%7Bi%2Cj%7D%5E1)%5Ccirc%20%5Cpi_i%5C%2C%5Cvert%5C%2Ci%2Cj%20%5Cin%20I%5Crangle%7D%22%2C%20shift%20left%3D2%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{P(C)} &amp;&amp; {\prod_{i \in I}P(C_i)} &amp;&amp; {\prod_{i,j \in I}P(C_i\times_CC_j)}
	\arrow[&quot;{\langle P(f_i):i \in I\rangle}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\langle P(\pi_{i,j}^2)\circ \pi_j\,\vert\,i,j \in I\rangle}&quot;', shift right=2, from=1-3, to=1-5]
	\arrow[&quot;{\langle P(\pi_{i,j}^1)\circ \pi_i\,\vert\,i,j \in I\rangle}&quot;, shift left=2, from=1-3, to=1-5]
\end{tikzcd}
" /></p>
For any site $(\mathcal{C},J)$, we obtain a natural subcategory $\mathsf{Sh}(\mathcal{C},J)$ of the category of presheaves on $\mathcal{C}$, $\mathsf{Ps}(\mathcal{C})$, given by sheaves on the site. As we will see soon this category satisfies a number of important properties, including being complete and cocomplete. Note that $\mathsf{Ps}(\mathcal{C})$ is (co)complete since $\mathsf{Set}$ is, where all the (co)limits in $\mathsf{Ps}(\mathcal{C})$ can be computed term-wise in $\mathsf{Set}$. To show $\mathsf{Sh}(\mathcal{C})$ is (co)complete we will show that it is what is known as a reflective subcategory under the inclusion $\iota:\mathsf{Sh}(\mathcal{C})\hookrightarrow \mathsf{Ps}(\mathcal{C})$. $\mathsf{Sh}(\mathcal{C})$ being a reflective subcategory means that $\iota$ has a left-adjoint, $\mathfrak{a}$, which we call the associated sheaf functor. 


To construct $\mathfrak{a}$ we proceed in stages. First, a presheaf is said to be separated if it satisfies the uniqueness axiom of a sheaf, but not necessarily the gluing axiom. That is when a lift along a sieve inclusion exists, it is necessarily unique. We begin by defining a functor that produces a separated presheaf from a general presheaf and then we show that the functor applied to a separated presheaf produces a sheaf.


Define $(-)^+:\mathsf{Ps}(\mathcal{C})\to \mathsf{Ps}(\mathcal{C})$ by 
$$P^+(C) := \lim_{\to R \in J(C)}\mathsf{Nat}(R,P)$$
where the diagram the limit is taken over has a map $\mathsf{Nat}(R,P)\to \mathsf{Nat}(S,P)$ for all $S \subseteq R$ given by pre-composition along the inclusion. This defines a presheaf since for a map $f:D\to C$ we have a natural transformation $\alpha_{f,R}:f^*R\to R$ given by sending $g \in f^*R$ to $f\circ g\in R$. Pulling back along this natural transformation gives maps of hom-sets which induce a map on the level of $P^+$ by the universal property of the colimit:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BP%5E%2B(C)%7D%20%26%20%7BP%5E%2B(D)%7D%20%5C%5C%0A%09%7B%5Ccat%7BNat%7D(R%2CP)%7D%20%26%20%7B%5Ccat%7BNat%7D(f%5E*R%2CP)%7D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%7B(%5Calpha_%7Bf%2CR%7D)%5E*%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D1-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{P^+(C)} &amp; {P^+(D)} \\
	{\cat{Nat}(R,P)} &amp; {\cat{Nat}(f^*R,P)}
	\arrow[dashed, from=1-1, to=1-2]
	\arrow[from=2-1, to=1-1]
	\arrow[&quot;{(\alpha_{f,R})^*}&quot;', from=2-1, to=2-2]
	\arrow[from=2-2, to=1-2]
\end{tikzcd}
" /></p>
Note that since we are considering set valued presheaves we can give an explicit realization of $P^+(C)$ as the set
$$P^+(C) \cong \coprod_{R \in J(C)}\mathsf{Nat}(R,P)/\sim$$
where $\alpha:R\to P$ and $\beta:T\to P$ are equivalent if there is a common refinement $S \subseteq R\cap T$ such that $\beta\vert_S = \alpha\vert_S$.

Associated to the functor $(-)^+$ we have a comparison natural transformation $\eta_P:P\to P^+$ for any presheaf $P$ where $(\eta_P)_C:P(C)\to P^+(C)$ factors through the yoneda isomorphism<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7BP(C)%7D%20%26%26%20%7BP%5E%2B(C)%7D%20%5C%5C%0A%09%26%20%7B%5Ccat%7BNat%7D(y_C%2CP)%7D%0A%09%5Carrow%5B%22%7B(%5Ceta_P)_C%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%5Ccong%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bhook%2C%20from%3D2-2%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{P(C)} &amp;&amp; {P^+(C)} \\
	&amp; {\cat{Nat}(y_C,P)}
	\arrow[&quot;{(\eta_P)_C}&quot;, from=1-1, to=1-3]
	\arrow[&quot;\cong&quot;', from=1-1, to=2-2]
	\arrow[hook, from=2-2, to=1-3]
\end{tikzcd}
" /></p>
where the inclusion is the natural map from the colimit.

As in[^1] we now show that this construction with its associated natural transformation allows us to characterize sheaves and separated presheaves.

>[!lemma] Separability Condition
>A presheaf $P$ is separated if and only if $\eta_P:P\to P^+$ is monic and is a sheaf if and only if it is an isomorphism.

^682ab3

`\begin{proof}`
To begin, let $P$ be a presheaf. We start with the claim on being separated, which can be proven in both directions simultaneously.

Note that as with limits, a map of presheaves is monic if and only if each component set function is monic in $\mathsf{Set}$ since $\mathsf{Set}$ is (co)complete. Then we must show that for each $C \in \mathcal{C}_0$, $(\eta_P)_C:P(C)\to P^+(C)$ is injective. Since this map can be written as yoneda followed by the inclusion $\mathsf{Nat}(y_C,P)\to P^+(C)$, this is equivalent to this later map being injective. However, this map being injective is precisely the statement that $P$ is a separated presheaf since it says that each map $y_C\to P$ can be the lift of at most one map $S\to P$ for each covering sieve $S$. Note that here we are using the classification of $P^+(C)$ in terms of its equivalence relation, which is given by equality upon restriction.

The second claim can be proven in an equally easy fashion from observing that the map $\mathsf{Nat}(y_C,P)\to P^+(C)$ being a isomorphism is exactly the lifting condition for being a sheaf.
`\end{proof}`
This result allows us to easily show that the $(-)^+$ construction produces separated presheaves.

>[!lemma] Separated Associated Presheaf
>For any presheaf $P$, $P^+$ is separated.

^2cd19a

`\begin{proof}`
To show $P^+$ is separated it is sufficient to show that $\eta_{P^+}:P^+\to (P^+)^+$ is monic, or equivalently that for every $C \in \mathcal{C}_0$, $(\eta_{P^+})_C:P^+(C)\to P^{++}(C)$ is injective. Recall from the definition of $(-)^+$ that 
$$P^{++}(C) = \lim\limits_{\to R\in J(C)}\mathsf{Nat}(R,P^+)$$
and $(\eta_{P^+})_C$ is determined by the inclusion of $\mathsf{Nat}(y_C,P^+)$ in $P^{++}(C)$.

Let $S,R \in J(C)$ such that $\alpha:S\to P$ and $\beta:R\to P$ are maps of presheaves that get sent to the same equivalence class in $P^{++}(C)$. Let $\widehat{\alpha}:y_C\to P^+(C)$ and $\widehat{\beta}:y_C\to P^+(C)$ be the representing maps under yoneda. Then by definition there exists a sieve $T \in J(C)$ for which $\widehat{\alpha}\vert_T:T\to P^+(C)$ and $\widehat{\beta}\vert_T:T\to P^+(C)$ are equal. Note that this says that for any $f:D\to C$ in the covering sieve $T$, $P^+(f)(\alpha)=\widehat{\alpha}_D(f) = \widehat{\beta}_D(f) = P^+(f)(\beta)$. This says exactly that for all $f:D\to C$ in $T$, there exists a common refinement $T_f$ of $f^*(S)$ and $f^*(R)$ such that the pullbacks of $\alpha$ and $\beta$ agree on $T_f$. From the transitivity axiom these $T_f$ glue together to give a covering sieve $U$ of $C$ which refines both $S$ and $R$, and by construction of $U$, $\alpha$ and $\beta$ agree on $U$ so by definition of the equivalence relation defining $P^+(C)$, are equal in $P^+(C)$.
`\end{proof}`

Next we can use our construction of $P^+$ to show that it is minimal with respect to certain maps of presheaves[^1].

>[!lemma] Universal Property of Associated Presheaf
>If $F$ is a sheaf and $P$ is a presheaf, then any map $\phi:P\to F$ of presheaves factors uniquely through $\eta$.

^c375a1

`\begin{proof}`
Suppose $\phi:P\to F$ is a map of presheaves with $F$ a sheaf. Then for any covering sieve $R \in J(C)$ we have a map $\phi_*:\mathsf{Nat}(R,P) \to \mathsf{Nat}(R,F)$ given by post-composition by $\phi_*$. Since $F$ is a sheaf we have a natural isomorphism $\mathsf{Nat}(R,F) \cong \mathsf{Nat}(y_C,F)$ given by the lifting criterion. Composing with the yoneda isomorphism then gives a map $\phi'_R:\mathsf{Nat}(R,P)\to F(C)$. 

This map is evidently natural with respect to sieve inclusions, $S\subseteq R$, and so induces a unique map $\Phi_C:P^+(C)\to F(C)$ given by the colimit universal property. The naturality of $\Phi$ follows from the naturality of $\phi$ and the uniqueness of the $\Phi_C$ with respect to the colimit universal property. Further, $\phi$ factors through $\Phi$ since in the commutative diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%7BP(C)%7D%20%26%20%7BP%5E%2B(C)%7D%20%26%20%7BF(C)%7D%20%5C%5C%0A%20%20%20%20%09%26%20%7B%5Ccat%7BNat%7D(y_C%2CP)%7D%20%26%20%7B%5Ccat%7BNat%7D(y_C%2CF)%7D%0A%20%20%20%20%09%5Carrow%5Bdashed%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cphi_*%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Ccong%22'%2C%20from%3D2-3%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%5Ccong%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	{P(C)} &amp; {P^+(C)} &amp; {F(C)} \\
    	&amp; {\cat{Nat}(y_C,P)} &amp; {\cat{Nat}(y_C,F)}
    	\arrow[dashed, from=1-2, to=1-3]
    	\arrow[from=2-2, to=1-2]
    	\arrow[&quot;{\phi_*}&quot;', from=2-2, to=2-3]
    	\arrow[&quot;\cong&quot;', from=2-3, to=1-3]
    	\arrow[&quot;\cong&quot;', from=1-1, to=2-2]
    	\arrow[dashed, from=1-1, to=1-2]
    \end{tikzcd}
" /></p>
the bottom yoneda isomorphisms and pushforward by $\phi$ compose to give $\phi$ by naturality.

Uniqueness of this factorization follows from the uniqueness of the map out of the colimit which is determined by the $\phi_*$ maps.
`\end{proof}`

Finally, we show that $(-)^+$ for separated presheaves produces full sheaves.

>[!lemma] Sheaf From Separated Presheaf
>If $P$ is a separated presheaf, then $P^+$ is a sheaf.

`\begin{proof}`
From [[Sheaves on Sites#^682ab3]] we already have that $P^+$ is separated. Using [[Sheaves on Sites#^2cd19a]] it remains only to show that for each $C \in \mathcal{C}_0$, the map $\mathsf{Nat}(y_C,P^+)$ into $P^{++}(C)$ is surjective.

To this effect we can consider a covering sieve $S\in J(C)$ along with a natural transformation $\alpha:S\to P^+$. We need only show that there exists a refinement of $S$ for which the restriction of $\alpha$ to the refinement is in our image. Note that for each $D \in \mathcal{C}_0$ and each $f:D\to C$ in $S$, $\alpha_D(f) \in P^+(D)$ is an equivalence class of natural transformations. For each $f$ in $S$ where $\text{dom}(f) = D$ choose a representative from $\alpha_D(f)$, $\widetilde{\alpha}_{f}:S_f\to P$. Note that by definition of the equivalence relation we have for each $f:D\to C$ in $S$ and each $g:E\to D$, a refinement $S_{f,g}$ of $g^*(S_f)$ and $S_{f\circ g}$ on which the representatives agree.

By the transitivity part of the Grothendieck topology we have a covering sieve $T = \{f\circ h:f \in S,h \in S_f\}$. We then define $\widetilde{\alpha}:T\to P$ by $\widetilde{\alpha}_E(f\circ h) := \widetilde{\alpha}_{f,E}(h)$. To see this is well-defined suppose $f\circ h = k\circ g$ for $f,k \in S$ and $h \in S_f, g \in S_k$. Consider the to maps $y_E\to P$ represented by $\widetilde{\alpha}_E(f\circ h)$ and $\widetilde{\alpha}_E(k\circ g)$, respectively. Then let $S_{(f,h),(k,g)}$ be a common refinement of $S_{f,h}$ and $S_{k,g}$. It follows that $\widetilde{\alpha}_f$ and $\widetilde{\alpha}_k$ are equivalent when restricted to this cover, so in particular both of our maps $y_E\to P$ are lifts of these equivalent restrictions, so as $P$ is separated they must be the same. In other words, $\widetilde{\alpha}_E$ is well-defined, and since it is defined in terms of natural transformations it too is natural.

Finally, we consider the map $y_C\to P^+$ represented by $\widetilde{\alpha}$. For each $f:D\to C$ in $S$ we have that $\alpha_D(f)$ is represented by $\widetilde{\alpha}_f:S_f\to P$, while $P^+(f)(\widetilde{\alpha}) = \widetilde{\alpha}\circ \alpha_{f,T}:f^*T\to P$. Now, by construction $S_f$ is a refinement of $f^*T$, and on $S_f$, $\widetilde{\alpha}_f$ and $\widetilde{\alpha}\circ \alpha_{f,T}$ agree by construction. It follows that these objects are equal in $P^+$ since they agree upon refinement of the cover, and so $\widetilde{\alpha}$ is a lift of $\alpha$.
`\end{proof}`

This collection of lemmas shows that not only do we have a functor $\mathfrak{a} := ((-)^+)^+:\mathsf{Ps}(\mathcal{C})\to \mathsf{Sh}(\mathcal{C})$, $\mathfrak{a}$ is left adjoint to $\iota$ using the universal property characterization of adjunctions. 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D(X)%7D%20%26%20%7B%5Cmathsf%7BPs%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-2%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ciota%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Sh}(X)} &amp; {\mathsf{Ps}(X)}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathfrak{a}}&quot;', bend right = 30, from=1-2, to=1-1]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\iota}&quot;', bend right = 30, from=1-1, to=1-2]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]
\end{tikzcd}
" /></p>
Indeed, applying [[Sheaves on Sites#^c375a1]] twice gives for any presheaf map $\alpha:P\to F$ into a sheaf $F$, a unique factorization
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09P%20%26%20%7BP%5E%2B%7D%20%26%20%7BP%5E%7B%2B%2B%7D%3D%5Cmathfrak%7Ba%7D(P)%7D%20%5C%5C%0A%09%26%26%20F%0A%09%5Carrow%5B%22%5Calpha%22'%2C%20from%3D1-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7B%5Ceta_P%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B!%7D%22%2C%20dashed%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5B%22%7B%5Ceta_%7BP%5E%2B%7D%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B!%7D%22%2C%20dashed%2C%20from%3D1-3%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	P &amp; {P^+} &amp; {P^{++}=\mathfrak{a}(P)} \\
	&amp;&amp; F
	\arrow[&quot;\alpha&quot;', from=1-1, to=2-3]
	\arrow[&quot;{\eta_P}&quot;, from=1-1, to=1-2]
	\arrow[&quot;{!}&quot;, dashed, from=1-2, to=2-3]
	\arrow[&quot;{\eta_{P^+}}&quot;, from=1-2, to=1-3]
	\arrow[&quot;{!}&quot;, dashed, from=1-3, to=2-3]
\end{tikzcd}
" /></p>
It follows that $\mathsf{Sh}(\mathcal{C})$ is co-complete since $\mathsf{Ps}(\mathcal{C})$ is co-complete. Indeed, $\mathfrak{a}$ being a left-adjoint implies that it preserves colimits[^2]. On the other hand, since $\iota$ is a full and faithful inclusion of categories, the co-unit of the adjunction, $\epsilon:\mathfrak{a}\circ \iota\to 1_{\mathsf{Sh}(\mathcal{C})}$, is an isomorphism. This implies that a colimit of a diagram can be obtained by including into presheaves, computing the colimit, and then applying the associated sheaf functor.

Additionally, this shows that $\mathsf{Sh}(\mathcal{C})$ is a reflective subcategory of $\mathsf{Ps}(\mathcal{C})$. Although the proof is beyond the scope of these notes, it is an important fact that $\mathsf{Sh}(\mathcal{C})$ being a reflective subcategory of $\mathsf{Ps}(\mathcal{C})$ implies that it is equivalent to the category of Eilenberg-Moore algebras $\mathsf{Ps}(\mathcal{C})^T$ for the monad $T=\iota\circ a$ on $\mathsf{Ps}(\mathcal{C})$. This algebra category is complete since the functor $\mathsf{Ps}(\mathcal{C})^T\to \mathsf{Ps}(\mathcal{C})$ reflects limits, and these limits are computed as in $\mathsf{Ps}(\mathcal{C})$[^2]. This shows that $\mathsf{Sh}(\mathcal{C})$ is a complete category. ^bd4bd7


We also have an adjunction for the global sections functor $\Gamma:\mathsf{Ps}(\mathcal{C})\to \mathsf{Set}$, just as in the case of sheaves on topological spaces, given by the constant presheaf $\Delta:\mathsf{Set}\to \mathsf{Ps}(\mathcal{C})$. In particular, $\Gamma$ is right-adjoint to $\Delta$. It follows that $\Gamma\circ \iota$ is right-adjoint to $\mathfrak{a}\circ \Delta$ by composition of adjunctions[^2]. The functor $\mathfrak{a}\circ \Delta$ is often called the constant sheaf functor.


The sheaf category on a site is also what is known as a cartesian closed category. Explicitly this means that the product functor has a left adjoint, often called an exponential. Explicitly, a sheaf category inherits the exponential structure from presheaves. In particular, if $P \in \mathsf{Ps}(\mathcal{C})$ and $F \in \mathsf{Sh}(\mathcal{C})$, then we have a sheaf $F^P$ given by 
$$F^P(C) := \mathsf{Nat}(y_C\times P,F)$$
This fact will be important for showing the existence of certain adjunctions in the section to follow.


Finally, an important property related to the theory of enriched categories is that the yoneda embedding for presheaves can also be extended to sheaves using the associated sheaf functor by considering
$$a\circ y:\mathcal{C}\to \mathsf{Sh}(\mathcal{C},J)$$
This functor is isomorphic to the yoneda embedding if the topology $J$ is sub-canonical (i.e.\ all representable presheaves are sheaves). This extension of yoneda satisfies a number of analogous properties to yoneda due to the fact that $\mathfrak{a}$ is a left adjoint to the inclusion of sheaves into presheaves[^1].


Another important property of the category of sheaves on a site is that it has a sub-object classifier. To demonstrate this property we require some preliminary concepts. First, a sieve $S$ on $C$ is said to be **closed** (for $J$) if and only if for all arrows $f:D\to C$ in $\mathcal{C}$, $f^*S \in J(D)$ implies $f \in S$. This property is stable under pullback, so if a sieve $S$ is closed so is $h^*S$ for any $h:B\to C$. We then define a presheaf $\Omega$ on $\mathcal{C}$ by
$$\Omega(C) = \{S \subseteq y_C|S\;\text{closed}\}$$
for which restriction is given by pullback. Any sieve $S$ can be replaced by a closed sieve $\overline{S}$ consisting of all arrows that $S$ covers (so $S \subseteq \overline{S}$). $\Omega$ is in fact a sheaf, and is the sub-object classifier for the category with $\text{true}:1\to \Omega$ given by sending the singleton for $C$ to the maximal sieve $y_C$.

## Grothendieck Topoi

Among others, the properties demonstrated for the category of sheaves over a site in the previous section illustrate that such a category is an object known as a topos. In particular, a category equivalent to a category of sheaves over a site is referred to as a **Grothendieck topos**. For the sake of space we will not delve into the generalizations of our current work to the setting of arbitrary topoi, but we refer the interested reader to sources such as[^1][^3][^4][^5].

An important step in understanding Grothendieck topoi comes from understanding what maps are appropriate for defining a category of Grothendieck topoi. In other words, what maps would preserve the structure of a Grothendieck topoi? To motivate our definition we can go back to where our story began, which was with sheaves on topological spaces. In this setting a map of topological spaces, $f:X\to Y$, induces an adjunction between sheaf categories
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Ccat%7BSh%7D(X)%7D%20%26%20%7B%5Ccat%7BSh%7D(Y)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf%5E*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-2%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\cat{Sh}(X)} &amp; {\cat{Sh}(Y)}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f^*}&quot;', bend right = 30, from=1-2, to=1-1]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{f_*}&quot;', bend right = 30, from=1-1, to=1-2]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]
\end{tikzcd}
" /></p>
where $f_*:\mathsf{Sh}(X)\to \mathsf{Sh}(Y)$ is the familiar functor from lecture which takes a sheaf $\mathcal{F}$ on $X$ to the sheaf $f_*\mathcal{F}$ on $Y$ given at an open $U \subseteq Y$ by $f_*\mathcal{F}(U) = \mathcal{F}(f^{-1}(U)$. On the other hand, the functor $f^*$ is given by taking the associated sheaf functor of the following definition for a sheaf $\mathcal{G}$ on $Y$:
$$f^*_{pre}\mathcal{G}(V) := \lim\limits_{\to,f(V)\subseteq U}\mathcal{G}(U),\;\forall V \in \mathsf{Top}(X)$$
In general this adjoint pair between sheaf categories preserves the desired data and so is appropriate for use as a map of sheaf categories. We generalize this notion to the case of sites to define what we call **geometric morphisms**[^1].

>[!def] Geometric Morphisms
>A **geometric morphism** $f:\mathcal{B}\to \mathcal{E}$ between Grothendieck topoi is an adjoint pair $f^*:\mathcal{E}\to \mathcal{B}:f_*$ such that $f^*$ is left exact (i.e. $f^*$ preserves finite limits).

With geometric morphisms and composition of adjoint pairs, Grothendieck topoi form a category, $\mathsf{GrTopoi}$. In fact, $\mathsf{GrTopoi}$ has a natural 2-categorical structure given by taking a 2-cell between geometric morphisms $f,g:\mathcal{B}\to \mathcal{E}$ to be a natural transformation $\alpha^*:f^*\Rightarrow g^*$ (which is equivalent to a natural transformation $\alpha_*:g_*\Rightarrow f_*$ using the adjunction units and co-units). 


Grothendieck topoi and geometric morphisms provide an excellent framework for studying base-change. In particular, although we will not prove it here as it goes beyond the scope of these notes, slice categories for Grothendieck topoi are themselves Grothendieck topoi[^1], and the associated base-change functors described in [[Basic Fibered Categories]] assemble into geometric morphisms between these Grothendieck topoi. Further, the slice categories for a Grothendieck topoi can be described in a particular elegant form using what is known as the Grothendieck construction.

Suppose $(\mathcal{C},J)$ is a site, and $\mathcal{F} \in \mathsf{Sh}(\mathcal{C},J)$ is a sheaf on the site. Then the slice category is equivalent to
$$\mathsf{Sh}(\mathcal{C},J)/\mathcal{F}\simeq \mathsf{Sh}\left(\int_\mathcal{C}\mathcal{F},J_\mathcal{F}\right)$$
where $\int_\mathcal{C}\mathcal{F}$ is the Grothendieck construction for $\mathcal{F}:\mathcal{C}^{op}\to \mathsf{Set}$, which is defined by the following data:
- (Objs) Pairs $(C,X)$ for $C \in \mathcal{C}_0$ and $X \in \mathcal{F}(C)$
- (Maps) A map $(C,X)\to (D,Y)$ is a map $f:C\to D$ such that the triangle
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%20%20%20%20%09%26%20%7B*%7D%20%5C%5C%0A%20%20%20%20%09%7B%5Cmathcal%7BF%7D(C)%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(D)%7D%0A%20%20%20%20%09%5Carrow%5B%22X%22'%2C%20from%3D1-2%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22Y%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cmathcal%7BF%7D(f)%7D%22%2C%20from%3D2-3%2C%20to%3D2-1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
    	&amp; {*} \\
    	{\mathcal{F}(C)} &amp;&amp; {\mathcal{F}(D)}
    	\arrow[&quot;X&quot;', from=1-2, to=2-1]
    	\arrow[&quot;Y&quot;, from=1-2, to=2-3]
    	\arrow[&quot;{\mathcal{F}(f)}&quot;, from=2-3, to=2-1]
    \end{tikzcd}
" /></p>
commutes.

There is a natural projection functor $\pi_0:\int_\mathcal{C}\mathcal{F}\to \mathcal{C}$ given by forgetting the element in the pair. The Grothendieck topology $J_\mathcal{F}$ is then induced by this projection functor.


#### References

[^1]: Sheaves in Geometry and Logic: A First Introduction to Topos Theory | SpringerLink. (n.d.). https://link.springer.com/book/10.1007/978-1-4612-0927-0. Accessed 23 May 2024
[^2]: Mac Lane, S. (1978). Categories for the Working Mathematician (Vol. 5). New York, NY: Springer. https://doi.org/10.1007/978-1-4757-4721-8
[^3]: Sketches of an Elephant in nLab. (n.d.). https://ncatlab.org/nlab/show/Sketches+of+an+Elephant. Accessed 23 May 2024
[^4]: Johnstone, P. T. (2014). Topos theory. Dover Publications. https://books.google.ca/books?id=zO8WAgAAQBAJ
[^5]: Categorical Logic and Type Theory. (n.d.). https://www.cs.ru.nl/B.Jacobs/CLT/bookinfo.html. Accessed 23 May 2024
