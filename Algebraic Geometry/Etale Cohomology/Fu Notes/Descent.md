---
date: 2024-05-25T11:39:00
tags:
  - AlgebraicGeometry
  - Descent
  - FiberedCategories
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

In this note we introduce the notions of descent in algebraic geometry, as laid out in Fu[^1]. We will begin with the notion of Zariski descent as a familiar backdrop.

## Descent of Quasi-coherent Sheaves

Let $f:X\to Y$ be a morphism of schemes which is **quasi-compact** (i.e. the pre-image of a quasi-compact open set is quasi-compact). In terms of affine open subsets this is equivalent to the following.


>[!proposition] Quasi-Compact in terms of Affines
>A map of schemes $f:X\to Y$ is quasi-compact if and only if there exists an affine open cover $\{U_i\}_{i \in I}$ of $Y$ such that each $f^{-1}(U_i)$ is a union of finitely many affine open subsets in $X$.

`\begin{proof}`
Recall that all affine schemes are quasi-compact. Indeed, we can refine a cover of $\mathsf{Spec}(A)$ into a cover by basic open sets $\mathsf{Spec}(A_{f_i})$, where the covering condition is the statement that the $f_i$ generate the unit ideal. But since $A$ is unital, only finitely many such $f_i$ are needed to form the unit, and hence generate the unit ideal, so we obtain a finite subcover.

This observation, and the fact that a finite union of quasi-compact sets is quasi-compact, implies the only if case, since we can always write an open as a union of affine opens in a scheme.

On the other hand, for the reverse direction suppose we have such an affine open cover of $Y$, $\{U_i\}_{i \in I}$. Let $V$ is an open quasi-compact subset of $Y$. Then there exists a finite set $U_{i_1},...,U_{i_n}$ which cover $V$. We can refine this, if necessary, to an affine open cover $V_{k_1},...,V_{k_m}$ of $V$ such that each affine open $V_{k_r}$ is a basic affine open in some $U_{i_j}$. Now, by assumption $f^{-1}U_{i_j} = \bigcup_{\ell=1}^{n'}W_{i_j,\ell}$ for some affine opens $W_{i_j,\ell}$. Note that $f\vert_{W_{i_j,\ell}}:W_{i_j,\ell}\to U_{i_j}$ is a map of affine schemes, so $f^{-1}V_{k_r}\cap W_{i_j,\ell} = f\vert_{W_{i_j,\ell}}^{-1}(V_{k_r})$ is a basic affine open subset of $W_{i_j,\ell}$. It follows that $f^{-1}V_{k_r} = \bigcup_{\ell=1}^{n'}(W_{i_j,\ell}\cap f^{-1}V_{k_r})$ is covered by finitely many affine opens. In particular this means that $f^{-1}V$ is covered by finitely many affine opens, and hence is quasi-compact.
`\end{proof}`
The next theorem summarizes the notion of descent data, and why it is interesting:

>[!theorem] Descent Data for fpqc Maps
>Let $g:S'\to S$ be a quasi-compact faithfully flat morphism of schemes (i.e. **fpqc**), and let $S'' = S'\times_SS'$ be the pullback of $g$ along itself. For $1 \leq i \leq2$, let $p_i:S'' \to S'$ denote the projections of the pullback, and for $1 \leq i < j \leq 3$, let 
>$$p_{ij}:S'\times_SS'\times_SS'\to S'\times_SS' = S''$$
>be the map induced by projecting onto the $i$th and $j$th factors.
>1. Let $\mathcal{F},\mathcal{G}$ be quasi-coherent $\mathcal{O}_S$-modules, and let $\mathcal{F}'$ and $\mathcal{G}'$ (resp. $\mathcal{F}''$ and $\mathcal{G}''$) be their pullbacks on $S'$ (resp. $S''$), respectively. Then the sequence $$\mathsf{Hom}_{\mathcal{O}_S}(\mathcal{F},\mathcal{G})\xrightarrow{g^*}\mathsf{Hom}_{\mathcal{O}_{S'}}(\mathcal{F}',\mathcal{G}')\xrightarrow[p_2^*]{p_1^*}\mathsf{Hom}_{\mathcal{O}_{S''}}(\mathcal{F}'',\mathcal{G}'')$$
>is an equalizer diagram.
>2. For any $1\leq i \leq 3$, let $$\pi_i:S'\times_SS'\times_SS'\to S'$$
>denote the projection onto the $i$th factor. Let $\mathcal{F}'$ be a quasi-coherent sheaf on $S'$ such that there exists an isomorphism $\sigma:p_1^*\mathcal{F}'\to p_2^*\mathcal{F}'$ satisfying the **1-cocycle condition**: $$p_{13}^*(\sigma) = p_{23}^*(\sigma)\circ p_{12}^*(\sigma)$$
>where we identify $p^*_{ij}(\sigma)$ with a morphism $\pi_i^*\mathcal{F}'\to \pi_j^*\mathcal{F}'$ through the natural isomorphism $p_{ij}^*\circ p_1^* \cong \pi_i^*$ and $p^*_{ij}\circ p_2^* \cong \pi_j^*$. Then there exists a quasi-coherent $\mathcal{O}_S$-module $\mathcal{F}$ and an isomorphism $\tau:g^*\mathcal{F}\cong \mathcal{F}'$ such that the diagram
>$$\begin{CD}p_1^*g^*\mathcal{F} @>p_1^*\tau>> p_1^*\mathcal{F}' \\ @V\cong VV @V\cong V \sigma V \\ p_2^*g^*\mathcal{F} @>> p_2^*\tau> p_2^*\mathcal{F}' \end{CD}$$
>commutes, and $\mathcal{F}$ is unique up to unique isomorphism with these properties.

We say that an isomorphism $\sigma:p_1^*\mathcal{F}'\to p_2^*\mathcal{F}'$ satisfying the **1-cocycle condition** $p_{13}^*\sigma = p_{23}^*\sigma \circ p_{12}^*\sigma$ is called a **descent datum** for $\mathcal{F}$.

`\begin{proof}[Proof of Affine Case]`
We begin by proving the theorem in the case that $S = \mathsf{Spec}(A)$ and $S' = \mathsf{Spec}(A')$, where necessarily $A'$ is a faithfully flat $A$-algebra. Then all quasi-coherent sheaves on affine schemes are those associated with modules **REFERENCE**, it suffices to reduce to this case.

`\begin{proof}[Proof of (1)]`
To prove claim (1) let $M$ and $N$ be $A$-modules and let $\mathcal{F} = \widetilde{M}$ and $\mathcal{G} = \widetilde{N}$ be their associated modules. Then the statement becomes the claim that the sequence
$$\mathsf{Hom}_A(M,N)\to \mathsf{Hom}_{A'}(M',N')\rightrightarrows \mathsf{Hom}_{A''}(M'',N'')$$
is an equalizer, where $A'' = A'\otimes_AA'$ as an $A$-algebra (in particular a ring). The first map sends a morphisms $f:M\to N$ of $A$-modules to the tensor morphism $f\otimes_A1_{A'}:M\otimes_AA'\to N\otimes_AA'$, while the two arrows on the right send a map $h:M\otimes_AA'\to N\otimes_AA'$ to $h\otimes_A1_{A'}:M\otimes_AA'\otimes_A A'\to N\otimes_AA'\otimes_A A'$ for the top arrow and to $$(1_M\otimes_A c)\circ (h\otimes_A1_{A'})\circ (1_M\otimes_A c):M\otimes_AA'\otimes_AA'\to N\otimes_AA'\otimes_AA'$$
where $c$ is the natural swap isomorphism for the tensor $\otimes_A$. Let $f:M\to N$ be a map of $A$-modules and let $f_1$ denote the result from the top arrow and $f_2$ the result from the bottom arrow. Then for any simple tensor $m\otimes a\otimes a'$, we have that 
$$f_2(m\otimes a\otimes a') = f(m)\otimes a \otimes a' = f_1(m\otimes a \otimes a')$$
so this sequence is indeed a fork. To show this is an equalizer it suffices to show that the first map is injective and that the image of the first map coincides with the kernel of the second. Note that by part (4) of [[Fu Flat Modules#^050665]], $A'$ being faithfully flat over $A$ implies that the natural map $N\to N\otimes_A A'$ is injective. Then, if for $f,k:M\to N$ we have that $f\otimes_A1_{A'} = k\otimes_A1_{A'}$, then by the commutative square
$$\begin{CD}M @>>> M\otimes_A A' \\ @VfVV @VVf\otimes_A 1_{A'}V \\ N @>>> N\otimes_A A' \end{CD}$$
we would have that $f = k$, so the first map is injective.

Let $h:M\otimes_A A'\to N\otimes_AA'$ be a map such that $h_1 = h_2$. Note that since $A'$ is faithfully flat over $A$, part (4) of [[Fu Flat Modules#^050665]] implies that we can think of $M$ and $N$ as submodules of $M\otimes_A A'$ and $N\otimes_A A'$. By hypothesis we have that $h(m\otimes a)\otimes a' = c(h(m\otimes a')\otimes a)$ for any $m \in M, a ,a' \in A'$. In particular, this implies that for any $m \in M$, $h(m\otimes 1)$ is equalized by $N\otimes_A A'\rightrightarrows N\otimes_A A'\otimes_A A'$. If the sequence
$$N\to N\otimes_A A'\rightrightarrows N\otimes_A A' \otimes_A A'$$
is an equalizer, then it follows that $h(m\otimes 1)$ is in the submodule $N$, and hence factors as a tensor of a map $M\to N$ with the identity. The exactness of this sequence is equivalent to the exactness of
$$0 \to N\xrightarrow{\phi} N\otimes_A A' \xrightarrow{\psi} N\otimes_A A' \otimes_A A'$$
such that $\phi(x) =x\otimes 1$ and $\psi(x\otimes a) = x\otimes a\otimes 1 - x\otimes 1\otimes a$. Since $A'$ is faithfully flat over $A$, it suffices to show that the sequence
$$0 \to N\otimes_A A'\xrightarrow{\phi \otimes_A 1_{A'}} N\otimes_A A'\otimes_A A' \xrightarrow{\psi \otimes_A 1_{A'}} N\otimes_A A'\otimes_A A' \otimes_A A'$$
is exact. We then can obtain a homotopy between the identity and zero chain maps given by $D_1:N\otimes_AA'\otimes_AA'\to N\otimes_AA'$ and $D_2:N\otimes_AA'\otimes_AA'\otimes_AA'\to N\otimes_AA'\otimes_AA'$ given by $D_1(n\otimes a\otimes a') = n\otimes aa'$ and $D_2(n\otimes a\otimes a'\otimes a'') = n\otimes a\otimes a'a''$. Since homotopic maps induce identical maps on homology, it follows that the homology at $N\otimes_AA'$ and $N\otimes_AA'\otimes_AA'$ are trivial, which is equivalent to the statement that the sequence is exact at these terms.
`\end{proof}`

`\begin{proof}[Proof of (2)]`
Note that the uniqueness claim follows from part (1), so it suffices to prove existence. Let $\mathcal{F}' = \widetilde{N'}$ for some $A'$-module $N'$. The isomorphism $\sigma:p_1^*\mathcal{F}'\to p_2^*\mathcal{F}'$ is induced by an isomorphism
$$\alpha:N'\otimes_A A'\to A'\otimes_AN'$$
of $A'\otimes_AA'$ modules. Let $N = \{x \in N' \mid \alpha(x\otimes 1) = 1\otimes x\}$, so $N$ is naturally an $A$-module, and it induces an exact sequence
$$N\to N'\rightrightarrows A'\otimes_AN'$$
Since $A'$ is faithfully flat over $A$, we can tensor to obtain another such exact sequence. Note that the morphism $$A'\to A'\otimes_A A'$$
sending $a'$ to $1\otimes a'$ makes $A'\otimes_AA'$ a faithfully flat $A'$-algebra using property (4) of  [[Fu Flat Modules#^050665]]  again. **Continue Middle of Page 24** 

#### References

[^1]: Fu, L. (2015). Etale Cohomology Theory: Revised Edition (Vol. 14). WORLD SCIENTIFIC. https://doi.org/10.1142/9569