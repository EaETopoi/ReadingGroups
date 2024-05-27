---
date: 2024-05-20T15:48:00
tags:
  - CommutativeAlgebra
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

These notes go through some of the basic results and properties of flat modules with the goal of setting up the necessary theory to talk about flatness in the context of algebraic geometry in [[Flatness and Descent]]. The main reference for these notes are sections 1.1-1.3 of Fu[^1].

## Flat Modules

Throughout when we say a ring $A$ we mean commutative and unital with ring homomorphisms preserving the unit. Recall that an $A$-module is **flat** if the associated functor $$M\otimes_A -:A\mathsf{Mod}\to A\mathsf{Mod}$$
is **exact** (that is it preserves finite limits and colimits, or equivalently it preserves short exact sequences). Note that $M\otimes_A-$ is always right exact since it is the left adjoint to $\mathsf{Hom}_A(M,-)$, and hence preserves all small colimits. First we prove that, given suitable assumptions, flatness is preserved under change of scalars.

>[!proposition] Flatness and Change of Scalars
>If $M$ is a flat $A$-module and $f:A\to B$ is a ring homomorphism, then $B\otimes_AM$ is a flat $B$-module. Further, if $N$ is a flat $B$-module, and $B$ is flat over $A$, then the restriction of scalars $f^{-1}N$ is flat over $A$.

^47ed09

`\begin{proof}`
Note that for a $B$-module $N$ we have $N\otimes_B B \cong N$ as $B$ modules. In particular, $B$ is flat as a $B$-module (as are all free $B$-modules), so $-\otimes_B B$ is exact, and hence $(-\otimes_BB)\otimes_AM$ is exact since a sequence of $B$ modules is short exact if and only if it is short exact as viewed as a sequence of $A$ modules (since the exactness relies just on the underlying abelian groups). 

Similarly, as to view $N$ as an $A$-module we tensor $B\otimes_BN$, and use the natural $A$-module action on $B$ induced by the ring homomorphism. Then $-\otimes_A(B\otimes_BN)$ is a composite of exact functors, and hence is exact.
`\end{proof}`
Recall that for $A$-modules $M$ and $N$, $\text{Tor}_\bullet^A(M,N)$ are the left-derived functors of $M\otimes_A-$ at $N$ (or equivalently the left-derived functors of $-\otimes_AN$ at $M$). With this in mind, we have the following list of equivalent conditions for a module being flat.

>[!proposition] Flatness TFAE
>Let $A$ be a ring and $M$ be an $A$-module. Then the following are equivalent:
>1. $M$ is a flat $A$-module
>2. For any $A$-module $N$, $\text{Tor}_i^A(M,N) = 0$ for all $i \geq 1$
>3. For any finitely generated $A$-module $N$, $\text{Tor}_i^A(M,N) = 0$ for all $i \geq 1$
>4. For any $A$-module $N$, $\text{Tor}_1^A(M,N) = 0$
>5. For any finitely generated $A$-module $N$, $\text{Tor}_1^A(M,N)=0$
>6. For any ideal $I$ of $A$, $\text{Tor}_1^A(M,A/I) = 0$
>7. For any finitely generated ideal $I$ of $A$, $\text{Tor}_1^A(M,A/I) = 0$
>8. For any ideal $I$ of $A$, the canonical homomorphism $I\otimes_A M\to M$ is injective
>9. For any finitely generated ideal $I$ of $A$, the canonical homomorphism $I\otimes_AM\to M$ is injective.

^79d8e7

`\begin{proof}`
Note by definition of torsion $(1) \iff (2) \iff (4)$ Further, $(2),(4)\implies (3),(5),(6),(7),(8),(9)$. Thus, it suffices to show that $(9) \implies (2)$. We first show $(9)\implies (8)$. Let $I \subseteq A$ be an ideal and consider the canonical homomorphism $I\otimes_AM\to M$. Towards a contradiction suppose that this map is not injective. Then we have some $\sum_{k=0}^ni_k\otimes m_k,\sum_{\ell=0}^mj_\ell\otimes m_\ell'$ which are distinct in $I\otimes_AM$, but $\sum_{k=0}^ni_km_k = \sum_{\ell=0}^mj_\ell m_\ell'$. We can take the sub-ideal $\langle i_0,...,i_n,j_0,...,j_m\rangle =: J$. Now, we have a natural map $J\otimes_AM\to I\otimes_AM$, and $J\otimes_AM\to M$ factors through $I\otimes_AM\to M$ via this map. But by assumption $J\otimes_AM\to M$ is injective, while $J\otimes_AM\to I\otimes_AM\to M$ is not, a contradiction. Similar arguments show $(6)\iff (7), (4)\iff(5)$ and $(2) \iff (3)$. Thus, it suffices to show that $\text{Tor}_1^A(M,N) = 0$ for any finitely generated $A$-module $N$. 

Let $K\hookrightarrow N$ be the inclusion of a finitely generated $A$-submodule. By a similar argument to that above (which holds since $M\otimes_A-$ preserves small colimits), we can assume without loss of generality that $A$ is also a finitely generated $A$-module. Write $0 \to L\to A^{\oplus n}\to N\to 0$ for a SES describing $N$ in terms of generators and relations. Then there is some submodule $L' \subseteq A^{\oplus n}$ containing $L$ which surjects onto $K$, and so we have $0\to L\to L' \to K\to 0$.  For the remainder of the argument we follow Lemma 10.39.5[^2].

Now, recall that we have a canonical map $L'\otimes_AM \to A^{\oplus n}\otimes_AM\cong M^{\oplus n}$, and similarly $L\otimes_AM\to M^{\oplus n}$. Observe that $K\otimes_AM \cong (L'\otimes_AM)/(L\otimes_AM)$, so we wish to show $(L'\otimes_AM)/(L\otimes_AM)\to M^{\oplus n}/(L\otimes_AM)$ is injective. Hence, it suffices to show that $L'\otimes_AM\to M^{\oplus n}$ and $L\otimes_AM\to M^{\oplus n}$ are injective. Hence, we need only show that $L\otimes_AM\to M^{\oplus n}$ is injective when $L \subseteq A^{\oplus n}$ is a submodule. We can show this by proceeding by induction on $n$. The base case, $n = 1$, is exactly our assumption. Now, suppose $n > 1$ and that the claim for $n-1$ holds. Let $L' = L\cap R\oplus 0^{\oplus (n-1)}\subseteq L$, so $L'' = L/L'$ is naturally a submodule of $R^{\oplus (n-1)}$. We now obtain the commuting diagram
$$\begin{CD} @. L'\otimes_AM @>>> L\otimes_AM @>>> L''\otimes_AM @>>> 0 \\@. @VVV @VVV @VVV @. \\ 0 @>>> M @>>> M^{\oplus n} @>>> M^{\oplus (n-1)} @>>> 0 \end{CD}$$
where the rows  are exact, and by the inductive hypothesis and the base case the left and right arrows are injective, so the middle arrow is injective, as desired.
`\end{proof}`
If $M$ is a flat $A$-module and $N$ is an $A$-module with submodules $N'$ and $N''$, then $M\otimes_AN'$ and $M\otimes_AN''$ can be naturally regarded as submodules of $M\otimes_AN$. Since $M$ is flat $M\otimes_A-$ commutes with finite limits and (small) colimits, so we have the natural isomorphisms
$$
\begin{align*}
M\otimes_A(N'\cap N'')&\cong (M\otimes_A N')\cap (M\otimes_AN'') \\
M\otimes_A(N'+N'')&\cong (M\otimes_A N')+(M\otimes_AN'')
\end{align*}
$$
where on the right we can perform these operations in $M\otimes_AN$.

As will be important for many algebro-geometric applications, localization plays well with flatness of modules.

>[!proposition] Flatness and Localization
>Let $f:A\to B$ be a homomorphism of rings, and let $S$ and $T$ be multiplicative subsets of $A$ and $B$, respectively, such that $f(S) \subseteq T$ (i.e. we obtain an induced map $S^{-1}f:S^{-1}A\to S^{-1}B\to T^{-1}B$). Then for any flat module $M$ over $A$, $S^{-1}M$ is a flat $S^{-1}A$-module and $S^{-1}A$ is flat over $A$. Further, if $N$ is a $B$ module that is flat over $A$, then $T^{-1}N$ is flat over $A$ and $S^{-1}A$. 
>
>Finally, if for every maximal ideal $\mathfrak{n}$ of $B$ we have $N_\mathfrak{n}$ is flat over $A$, then $N$ is flat over $A$.

`\begin{proof}`
We first note that for any $A$ module $M$, $S^{-1}A\otimes_A M$, as an $A$-module and as an $S^{-1}A$-module, is isomorphic to $S^{-1}M$ as it satisfies the desired universal property. Thus, for the first claim it suffices to show that $S^{-1}A$ is a flat $A$-module by [[Fu Flat Modules#^47ed09|Proposition 1]]. For this let $I \subseteq A$ be an ideal. Then we have that $S^{-1}A\otimes_AI \cong S^{-1}I$ and $S^{-1}A\otimes_A\cong S^{-1}A$ as $A$-modules (in fact also as $S^{-1}A$-modules), so the inclusion $0\to I \to A$ becomes the inclusion $0\to S^{-1}I\to S^{-1}A$ which is injective since it is simply an inclusion.

Now, suppose $N$ is a $B$-module which is flat over $A$. By a universal property argument we have that for any $A$-module
$$T^{-1}N\otimes_AM\cong T^{-1}(N\otimes_AM)$$
so $T^{-1}N\otimes_A-$ is naturally isomorphic to the composite $T^{-1}(N\otimes_A-)$. Since localization is exact and $N$ is flat over $A$, this functor is exact. Further, by our first argument $S^{-1}T^{-1}N$ is flat over $S^{-1}A$, but as they satisfy the same universal property $S^{-1}T^{-1}N\cong T^{-1}N$.

The final claim is a direct application of [[Atiyah Localization#^191764]].
`\end{proof}`

Next we show how flatness interacts with integrality.

>[!proposition] Flat v. Zero Divisors
>Let $A$ be a ring and $M$ a flat $A$-module. If $a \in A$ is not a zero divisor then the multiplication map $m_a:M\to M$ is injective. Thus, if $A$ is an integral domain then $M$ has no torsion.
>
>If $A$ is an integral domain such that $A_\mathfrak{m}$ is a [[Atiyah Discrete Valuations|discrete valuation ring]] for each maximal ideal $\mathfrak{m}$ of $A$. Then an $A$-module $M$ is flat if and only if it has no torsion.

`\begin{proof}`
For the first part, if $a \in A$ is not a zero divisor then the multiplication map $m_a:A\to A$ is injective. Thus, tensoring with $M$ we obtain the injective map $m_a:M\to M$ using the fact that $M$ is flat and $M\otimes_AA \cong M$.

Now, suppose $A$ is an integral domain in which $A_\mathfrak{m}$ is a discrete valuation ring for each maximal ideal $\mathfrak{m}$ of $A$. The only if portion follows from our first argument, so suppose $M$ is an $A$-module with no torsion. Since localization is exact, [[Atiyah Localization#^191764]] implies that it suffices to show $M_\mathfrak{m}$ is a flat $A_\mathfrak{m}$ module for each maximal ideal $\mathfrak{m}$ of $A$, so without loss of generality we can assume that $A$ itself is a discrete valuation ring since localizing a module with no-torsion gives again a module with no torsion.

Let $I \subseteq A$ be an ideal. Since $A$ is a discrete valuation ring $I$ is principal, so $I = rA$ for some $r \in A$. The map $A\to I$ given by multiplication by $r$ is then both surjective and injective, since $A$ is an integral domain, and so is an isomorphism of $A$-modules. Thus, we obtain an isomorphism $M\to I\otimes_AM$ given by $x \mapsto r\otimes x$. Composing with the canonical map $I\otimes_AM\to M$ we obtain the multiplication map $M\to M$, $x\mapsto rx$, which is injective since $M$ has no torsion. It follows that $I\otimes_AM\to M$ must be injective, and so the result follows by [[Fu Flat Modules#^79d8e7|Proposition 2 (8)]].
`\end{proof}`


## Faithfully Flat Modules

Note that if $F:\mathcal{C}\to \mathcal{D}$ is an additive functor between additive categories, $F$ being faithful gives that $F(X) = 0$ for $X \in \mathcal{C}$ if and only if $X = 0$. 

When working with abelian categories we obtain a number of important equivalent classifications of exact and faithful functors.

>[!proposition] Exact and Faithful
>Let $F:\mathcal{A}\to \mathcal{B}$ be an additive functor between abelian categories. Then the following are equivalent:
>1. $F$ is exact and faithful
>2. A sequence $M'\to M\to M''$ in $\mathcal{A}$ is exact if and only if $F(M')\to F(M)\to F(M'')$ is exact
>3. $F$ is exact and the condition $F(X) = 0$ implies $X = 0$
>Suppose further there exists a family of non-zero objects $\{Z_i\}_{i \in I}$ of $\mathcal{A}$ such that for any non-zero object $X$ in $\mathcal{A}$, there exists some $Z_i$ and some object $Y$ of $\mathcal{A}$ admitting a monomorphism $Y\to X$ and an epimorphism $Y\to Z_i$. Then (1),(2),(3) are equivalent to the following
>4. $F$ is exact and $F(Z_i)\neq 0$ for all $Z_i$.

`\begin{proof}`
Suppose (1). The only if part of (2) follows by exactness. Now, suppose $M'\to M\to M''$ is a sequence in $\mathcal{A}$ such that $F(M')\to F(M)\to F(M'')$ is exact. Since $F$ is faithful we must have that the composite $M'\to M\to M''$ is zero$. Further, since $F$ is exact, and hence preserves finite limits and colimits, we have
$$F(\ker v/\text{im} u) \cong F(\ker v)/F(\text{im} u)\cong \ker F(v)/\text{im}F(u)\cong 0$$
so $\ker v/\text{im}u \cong 0$ since $F$ is faithful, and so $\ker v \cong \text{im}u$.
For $(2)\implies (3)$ suppose $F(X) = 0$. Then $F(0)\to F(X)\to F(0)$ is exact since $F(0) = 0$, so by assumption $0 \to X \to 0$ must also be exact, which is only possible if $X = 0$.

For $(3)\implies (1)$ let $u:X\to Y$ such that $F(u) = 0$. Then $\text{im}F(u)\cong 0 $, but since $F$ is exact this implies $F(\text{im}u)\cong 0$, and by assumption $\text{im}u \cong 0$. But this is exactly the statement that $u = 0$.

Next, $(3)\implies (4)$ always holds, so it suffices that with the additional assumptions we show $(4) \implies (3)$. For any non-zero object $X$ of $\mathcal{A}$, choose an object $Y$ satisfying the hypotheses. Then $F(Y)\to F(Z_i)$ is an epimorphism and $F(Y)\to F(X)$ is a monomorphism. As $F(Z_i)\neq 0$ we have $F(Y) \neq 0$, so $F(Y)\to F(X)$ being a monomorphism implies $F(X) \neq 0$.
`\end{proof}`

As an immediate corollary we obtain the following

>[!corollary] 
>Let $A$ be a ring and $M$ an $A$-module. Then the following are equivalent:
>1. $M\otimes_A-$ is exact and faithful
>2. A sequence of $A$ modules $N'\to N\to N''$ is exact if and only if $M\otimes_AN'\to M\otimes_AN\to M\otimes_AN''$ is exact
>3. $M$ is flat and the condition $M\otimes_AN = 0$ implies $N = 0$
>4. $M$ is flat and $M\otimes_AA/\mathfrak{m} \neq 0$ for any maximal ideal $\mathfrak{m}$ of $A$.

^c9b8a2

We say that $M$ is **faithfully flat** if it satisfies any of the above equivalent conditions. We immediately obtain a large class of faithfully flat modules.

>[!corollary]
>Let $(A,\mathfrak{m})\to (B,\mathfrak{n})$ be a local homomorphism of local rings and let $M$ be a finitely generated $B$-module. Then $M$ is faithfully flat over $A$ if and only if it is flat over $A$ and non-zero.

^2cced2

Indeed, by [[Atiyah Localization#^942eff]], the condition $M\otimes_A A/\mathfrak{m}\neq 0$ is equivalent to the condition that $M_\mathfrak{m} \neq 0$  for all maximal ideals, and hence $M \neq 0$.

One of the essential reasons for studying faithfully flatness in algebraic geometry is due to the many important geometric features that it implies upon taking $\mathsf{Spec}$. 

>[!proposition]
>Let $f:A\to B$ be a map of rings. If there exists a $B$-module $M$ which is faithfully flat over $A$, then the map $\mathsf{Spec}(f):\mathsf{Spec}(B)\to \mathsf{Spec}(A)$ is surjective.

^cdc973

`\begin{proof}`
Recall that $\kappa(\mathfrak{p}) := A_\mathfrak{p}/\mathfrak{p}A_\mathfrak{p}$. Now, it suffices to show that for any point $\mathfrak{p} \in \mathsf{Spec}(A)$, the fiber $\mathsf{Spec}(B\otimes_A \kappa(\mathfrak{p}))$ of the map $\mathsf{Spec}(B)\to \mathsf{Spec}(A)$ over $\mathfrak{p}$ is not empty, or equivalently $B\otimes_A \kappa(\mathfrak{p})$ is non-zero. Since $M$ is faithfully flat over $A$, $M\otimes_A\kappa(\mathfrak{p})$ is faithfully flat over $\kappa(\mathfrak{p})$. This implies that $M\otimes_A\kappa(\mathfrak{p})\neq 0$, but $M\otimes_A\kappa(\mathfrak{p})$ is a $(B\otimes_A\kappa(\mathfrak{p}))$-module, and so $B\otimes_A\kappa(\mathfrak{p}) \neq 0$.
`\end{proof}`
>[!corollary]
>Let $\phi:A\to B$ be a map of rings and let $M$ be a finitely generated $B$-module that is flat over $A$. Suppose $\text{Supp}(M) = \mathsf{Spec}(B)$ (i.e. $M_\mathfrak{p}\neq 0$ for all prime ideals $\mathfrak{p}$ in $B$). Then for any $\mathfrak{p} \in \mathsf{Spec}(A)$ and any prime ideal $\mathfrak{q} \in \mathsf{Spec}(B)$ which is minimal among those prime ideals of $B$ containing $\mathfrak{p}B$, we have $\phi^{-1}(\mathfrak{q}) = \mathfrak{p}$. In particular, for any minimal prime ideal $\mathfrak{q}$ of $B$, $\phi^{-1}(\mathfrak{q})$ is a minimal prime ideal of $A$.

`\begin{proof}`
Since $M$ is supported everywhere in particular it is not zero. Then by [[Fu Flat Modules#^2cced2]] we have that $M$ is faithfully flat over $A$, and so $M_\mathfrak{q}$ is faithfully flat over $A_{\phi^{-1}(\mathfrak{q})}$. Then, by [[Fu Flat Modules#^cdc973]] the map $\mathsf{Spec}(B_\mathfrak{q})\to \mathsf{Spec}(A_{\phi^{-1}(\mathfrak{q})})$ is surjective. Note as $\mathfrak{p} \subseteq \phi^{-1}(\mathfrak{q})$, $\mathfrak{p}A_{\phi^{-1}(\mathfrak{q})}\in \mathsf{Spec}(A_{\phi^{-1}(\mathfrak{q})})$. By minimality of $\mathfrak{q}$, the pre-image of $\mathfrak{p}A_{\phi^{-1}(\mathfrak{q})}$ in $\mathsf{Spec}(B_\mathfrak{q})$ must be $\mathfrak{q}B_\mathfrak{q}$. Thus, $\phi^{-1}(\mathfrak{q}) = \mathfrak{p}$. 
`\end{proof}`

Next we give a number of equivalent conditions for a ring being faithfully flat over another.

>[!proposition]
>Let $\phi:A\to B$ be a map of rings. Then the following are equivalent:
>1. $B$ is faithfully flat over $A$
>2. $B$ is flat over $A$ and $\mathsf{Spec}(B)\to \mathsf{Spec}(A)$ is onto
>3. $B$ is flat over $A$ and for each maximal ideal $\mathfrak{m}$ of $A$, there exists a maximal ideal $\mathfrak{n}$ of $B$ such that $\phi^{-1}(\mathfrak{n}) = \mathfrak{m}$ 
>4. $B$ is flat over $A$, and for any $A$-module the canonical homomorphism $M\to M\otimes_AB$ mapping $x\mapsto x\otimes 1$ is injective
>5. For every ideal $I$ of $A$, the canonical homomorphism $I\otimes_AB\to B$ given by $x\otimes b\mapsto bx$ is injective and $\phi^{-1}(IB) = I$
>6. $\phi$ is injective and $\text{coker}\,\phi$ is flat over $A$.

^050665

`\begin{proof}`
$(1)\implies (2)$ by [[Fu Flat Modules#^cdc973]]. For $(2)\implies (3)$ if $\mathfrak{m}$ is a maximal ideal the spec map being onto implies we have a prime ideal $\mathfrak{p}$ of $B$ such that $\phi^{-1}(\mathfrak{p}) = \mathfrak{m}$. Now, if $\mathfrak{n}$ is a maximal ideal containing $\mathfrak{p}$, which exists by Zorn's lemma, $\phi^{-1}(\mathfrak{n})$ is a prime ideal containing $\mathfrak{m}$, so $\phi^{-1}(\mathfrak{n}) = \mathfrak{m}$.

Next, to see that $(3)\implies (1)$ observe that for any maximal ideal $\mathfrak{m}$ of $A$, with maximal ideal $\mathfrak{n}$ of $B$ such that $\phi^{-1}(\mathfrak{n}) = \mathfrak{m}$, we have $B\otimes_AA/\mathfrak{m}\cong B/\mathfrak{m}B$, and $B/\mathfrak{m}B$ has quotient $B/\mathfrak{n}$ which is non-zer. It follows that $B\otimes_AA/\mathfrak{m}\neq 0$, so we can apply [[Fu Flat Modules#^c9b8a2]].

Next, we show $(1)\implies (4)$. Since $B$ is faithfully flat it suffices to show $M\otimes_AB\to M\otimes_AB\otimes_AB$ given by $x\otimes b\mapsto x\otimes 1\otimes b$ is injective, which indeed it is since it has a retraction $M\otimes_AB\otimes_AB\to M\otimes_AB$ given by $x\otimes b_1\otimes b_2\mapsto x\otimes b_1b_2$. For $(4)\implies (5)$ the canonical homomorphism given is injective since $B$ is flat. Further, taking $M = A/I$ we have that the canonical homomorphism $A/I\to A/I\otimes_AB$ is injective, which is equivalent to $A/I\to B/IB$ being injective. But this is exactly the statement that $\phi^{-1}(IB) = I$.

Next we show $(5)\implies (3)$. By [[Fu Flat Modules#^79d8e7]] we have that $B$ is a flat $A$-module. Next, if $\mathfrak{m}$ is a maximal ideal of $A$, we have $\phi^{-1}(\mathfrak{m}B) = \mathfrak{m}$. In particular, this implies that $\mathfrak{m}B$ is a proper ideal of $B$. Let $\mathfrak{n}$ be a maximal ideal of $B$ containing $\mathfrak{m}B$, so that $\phi^{-1}(\mathfrak{n}) = \mathfrak{m}$. 

So far we have that $(1)$ through $(5)$ are equivalent. Next, we show $(4)\implies (6)$. Take $M = A$ in $(4)$, so we have that the canonical map $A\to A\otimes_AB\cong B$, which is $\phi$, is injective. Thus, we have a short exact sequence $$0 \to A \to B \to \text{coker}\,\phi \to 0$$
If $M$ is an $A$-module we can use the long exact sequence for homology to get the long exact sequence of torsion and use the fact that $A$ is flat over itself, to obtain the exact sequence
$$0 \to \text{Tor}_1^A(M,B) \to \text{Tor}_1^A(M,\text{coker}\,\phi)\to M\to M\otimes_A B$$
Since $B$ is flat over $A$ we have that $\text{Tor}_1^A(M,B)\cong 0$. Additionally, as $M\to M\otimes_AB$ is injective we must have that $\text{Tor}_1^A(M,\text{coker}\,\phi) = 0$, which since $M$ was arbitrary says that $\text{coker}\,\phi$ is flat over $A$.

Finally, we show that $(6) \implies (4)$. By assumption we have an exact sequence $$0\to A\to B \to \text{coker}\,\phi\to 0$$
For an $A$-module $M$ we can again use the long exact sequence of torsion modules to obtain 
$$0\to \text{Tor}_1^A(M,B)\to \text{Tor}_1^A(M,\text{coker}\,\phi)\to M\to M\otimes_AB$$
But $\text{coker}\,\phi$ is flat over $A$, so $\text{Tor}_1^A(M,\text{coker}\,\phi) \cong 0$, and so $M\to M\otimes_AB$ is injective and $\text{Tor}_1^A(M,B) \cong 0$, which is to say $B$ is also flat over $A$. This completes the proof of the equivalences.
`\end{proof}`

When $A$ is noetherian we can talk about the completion of $A$ with respect to an ideal being flat over $A$.

>[!proposition]
>Let $A$ be a noetherian ring, $I$ an ideal of $A$, and $\hat{A}$ the $I$-adic completion of $A$[^3]. Then $\hat{A}$ is flat over $A$. It is faithfully flat over $A$ if and only if $I$ is contained in the Jacobson radical of $A$ (i.e. $\bigcap_{\mathfrak{m} \in \mathsf{Specm}(A)}\mathfrak{m}$).

See [[Atiyah Ring Completions]] for a proof.

>[!proposition] Free Module Equivalences
>Let $A$ be a ring, $I$ an ideal of $A$, and $M$ an $A$-module. Suppose that either $I$ is nilpotent or $A$ is noetherian and $I$ is contained in the Jacobson radical of $A$ with $M$ finitely generated. Then the following are equivalent:
>1. $M$ is free over $A$
>2. $M\otimes_AA/I$ is free over $A/I$ and $\text{Tor}_1^A(M,A/I) = 0$ 
>3. $M\otimes_AA/I$ is free over $A/I$ and the canonical homomorphism $$M/IM\otimes_{A/I}\left(\bigoplus_{n=0}^{\infty}I^n/I^{n+1}\right)\to \bigoplus_{n=0}^{\infty}I^nM/I^{n+1}M$$
>is an isomorphism.

^b5b22b

`\begin{proof}`
The implications $(1)\implies (2)$ and $(1)\implies (3)$ always hold. We show the other statements for (b) first. To show $(2)\implies (1)$ let $\{x_\lambda\}_{\lambda \in \Lambda}$ be a family of elements in $M$ such that their images in $M\otimes_AA/I\cong M/IM$ form a basis. By [[Atiyah Localization#^635d86]]  the $\{x_\lambda\}$ generates $M$. Next, let $L$ be a free $A$-module of rank $|\Lambda|$, and let $L\to M$ be an epimorphism mapping a basis of $L$ to $\{x_\lambda\}$ with kernel $K$. Then we have a SES $$0 \to K\to L \to M \to 0$$
Since by assumption $\text{Tor}_1^A(M,A/I)=0$, we can use the long exact sequence of torsion modules to determine that the sequence
$$0\to K\otimes_A A/I \to L\otimes_A A/I \to M\otimes_A A/I \to 0$$
is exact. But, $L\otimes_A A/I\to M\otimes_A A/I$ is a map of free $A/I$ modules which sends a basis to a basis by definition of the homomorphism $L\to M$, so $K/IK\cong K\otimes_A A/I = 0$. By [[Atiyah Localization#^635d86]] again we must have that $K = 0$, and so $L \cong M$, so $M$ is free.

To prove $(3)\implies (1)$ consider the commutative diagram
$$\begin{CD} L/IL \otimes_{A/I}\left(\bigoplus_{n=0}^{\infty}I^n/I^{n+1}\right) @>>> \bigoplus_{n=0}^{\infty}I^nL/I^{n+1}L \\ @VVV @VVV \\ M/IM \otimes_{A/I}\left(\bigoplus_{n=0}^{\infty}I^n/I^{n+1}\right) @>>\cong> \bigoplus_{n=0}^{\infty}I^nM/I^{n+1}M  \end{CD}$$
Note that by definition of the homomorphism $L\to M$ we have $L/IL\cong M/IM$ since $M/IM$ is free. The top horizontal arrow is an isomorphism since $L$ is and our assumptions. It follows that the vertical map on the right is an isomorphism. This implies that $K \subseteq \bigcap_{n=0}^{\infty}I^nL$. Since $L$ is free and $\bigcap_{n=0}^{\infty}I^n = 0$ under either condition (a) or condition (b), we have $K = 0$. Hence $L \cong M$ and $M$ is free.
`\end{proof}`
Note that in the proof of the direction $(2)\implies (1)$  [[Atiyah Localization#^635d86]] is an immediate consequence of [[Atiyah Localization#^942eff]] which has an equivalent formulation and simpler proof when the ideal $I$ is nilpotent (indeed, if $IM = M$ then as $I^n = 0$ for suitably large $n$, $M = IM =I^2M=\cdots = I^nM = 0$). We have a simple corollary in the case the ideal $I$ is maximal

>[!corollary]
>Let $\mathfrak{m}$ be a maximal ideal of a ring $A$ and let $M$ be an $A$-module. Suppose that either $\mathfrak{m}$ is nilpotent or $A$ is notherian and local and $M$ is finitely generated. Then the following are equivalent:
>1. $M$ is free
>2. $M$ is projective
>3. $M$ is flat
>4. $\text{Tor}_1^A(M,A/\mathfrak{m}) = 0$
>5. The canonical homomorphism $$M/\mathfrak{m}M\otimes_{A/\mathfrak{m}}\left(\bigoplus_{n=0}^{\infty}\mathfrak{m}^n/\mathfrak{m}^{n+1}\right)\to \bigoplus_{n=0}^{\infty}\mathfrak{m}^nM/\mathfrak{m}^{n+1}M$$
>is an isomorphism
>
>If $(A,\mathfrak{m})$ is a local noetherian integral domain with residue field $k$ and fraction field $K$, ad $M$ is finitely generated, then the above conditions are equivalent to
>6. $\text{dim}_K(M\otimes_AK) = \dim_k(M\otimes_Ak)$

`\begin{proof}`
The chain $(1)\implies (2)\implies (3)\implies (4)$, and by [[Fu Flat Modules#^b5b22b]] we have the implications $(4)\implies (5)\implies (1)$. Further, $(1)\implies (6)$ is immediate from tensors preserving colimits.

Now, suppose $(6)$ holds. Choose $x_1,...,x_n \in M$ such that their images in $M/\mathfrak{m}M\cong M\otimes_Ak$ form a basis. By  [[Atiyah Localization#^635d86]] the $x_1,...,x_n$ generate $M$. Let $L$ be a free $A$-module of rank $n$, let $L\to M$ be an epimorphism mapping a basis of $L$ to the $x_i$, and let $R$ be the kernel of $L\to M$. Then we have an exact sequence
$$0\to R\otimes_A K\to L\otimes_AK \to M\otimes_A K\to 0$$
Since $M\otimes_AK$ has the same dimension as $L\otimes_AK$, we have $R\otimes_AK = 0$. But $R$ being in the free $A$-module $L$ has no torsion. It follows that $R = 0$, so $L \cong M$ and $M$ is free.
`\end{proof}`


## Local Criteria for Flatness






#### References
[^1]: Fu, L. (2015). Etale Cohomology Theory: Revised Edition (Vol. 14). WORLD SCIENTIFIC. https://doi.org/10.1142/9569
[^2]: Section 10.39 (00H9): Flat modules and flat ring maps—The Stacks project. (n.d.). https://stacks.math.columbia.edu/tag/00H9. Accessed 20 May 2024
[^3]: For more on ring completions see [[Atiyah Ring Completions]].