---
date: 2024-05-20T18:57:00
tags:
  - AlgebraicGeometry
  - EtaleCohomology
  - ReadingGroup
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

These notes are from a lecture by Jiantong Liu on Descent Theory in Algebraic Geometry at UIUC as part of a reading group on Etale Cohomology during the summer of 2024. Specifically, as we are at the beginning of the talks we will begin with looking at descent theory from the perspective of the Zariski site. The aim of this approach is that it can be extended to a descent theory when moving to the etale site.

An extremely important piece of Zariski descent is the theory of flat morphisms. For example, if we have a flat morphism of schemes $\pi:X\to Y$, the pullback on **quasi-coherent** sheaves $\pi^*:\mathsf{QCoh}(Y)\to \mathsf{QCoh}(X)$ will be exact (although this is not true in general if $\pi$ is not flat). Thus, geometrically, when describing flat morphisms the geometry is described by looking at pullbacks.

## Descent Theory

### Flatness

>[!def] fpqc
>A morphism of schemes $f:A\to B$ is said to be **fpqc** if it is **faithfully flat** and **quasi-compact**. Related, we say that $f$ is **fppf** if it is faithfully flat and locally of finite presentation.

These types of morphisms are the appropriate setting for dealing with Zariski descent. In other words, we would like to work with morphisms that are faithfully flat, and have some kind of finiteness condition.

>[!rmk] Notation
>Let $q:S'\to S$ be fpqc and let $S'' =S'\times_SS'$ with projections $p_i:S''\to S'$, $i = 1,2$, and let $p_{ij}:S'\times_SS'\times_SS'\to S''$ be the double projections for $1 \leq i,j \leq 3$.

### Descent Data

So what exactly is descent data? What do  we require of it?

>[!def] Descent Data
>Let $F$ be a quasi-coherent sheaf over $S'$. An isomorphism $\sigma:p_1^*F\to p_2^*F$ that satisfies the **cocycle condition** $$p_{13}^*(\sigma) = p_{23}^*(\sigma)\circ p_{12}^*(\sigma)$$
>is called a **descent datum**.

Note that in general $p_{ij}^*(\sigma)$ should be thought of as a morphism of type $p_{ij}^*(\sigma):\pi_i^*F\to \pi_j^*F$, where $\pi_i:S'\times_SS'\times_SS'\to S'$, but note this relies on performing certain identification under canonical isomorphisms with respect to pullbacks of sheaves.

Okay, this is how we talk about "descent datum", but why do we care? The main motivation comes from solving the **Descent Problem**. Consider a morphism $g:S'\to S$ with quasi-coherent sheaves $F$ and $G$ on $S$ together with morphisms $\varphi:F\to G$ and $\varphi':g^*F\to g^*G$ in $S'$. Then we would like to know when $\varphi' = g^*\varphi$? Well we have some necessary conditions:
- Since $g\circ p_1 = g\circ p_2:S'' \to S$, we must have that $$p_1^*\varphi' = p_2^*\varphi'$$
To solve this problem it is sufficient to have that $\varphi'$ "**descends**", which is the first part of the following theorem.

>[!theorem] Descent
>1. Let $F,G$ be quasi-coherent $\mathcal{O}_S$-modules and let $F',F'',G',G''$ be inverse images in $S',{S'}'$. Then the sequence $$\mathsf{Hom}(F,G)\xrightarrow{g^*}\mathsf{Hom}(F',G')\xrightarrow{p_1^*,p_2^*}\mathsf{Hom}(F'',G'')$$
>is exact.
>2. Suppose $F'$ is quasi-coherent over $S'$ with descent datum $\sigma$. Then there exists $F$ quasi-coherent over $S$ with $\tau:g^*F\xrightarrow{\cong}F'$ such that we have a commutative square
>$$\begin{CD} p_1^*g^*F @>p_1^*\tau>> p_1^*F' \\ @V\cong VV @V\cong V\sigma V \\ p_2^*g^*F @>>p_2^*\tau> p_2^*F' \end{CD}$$

`\begin{proof}[Proof Idea.]`
Since are maps are quasi-compact we are reduced to proving the affine case, so $S = \mathsf{Spec}(A)$ and $S' = \mathsf{Spec}(A')$, with $A'$ faithfully flat over $A$. This reduces to proof to a homological algebra problem.
`\end{proof}`

Descent data can be made to form a category where an object is a pair $(F,\sigma)$ of a quasi-coherent sheaf with a descent datum and a map of descent data $(F,\sigma)\to (G,\tau)$ is a commutative square
$$\begin{CD} p_1^*F @>>> p_1^*G \\ @VVV @VVV \\ p_2^*F @>>> p_2^*G \end{CD}$$

Now that we have these structures setup we can begin Zariski descent with the following lemma.

>[!lemma]
>Let $g:S'\to S$ be fpqc and $F/S$ quasi-coherent. Then $g^*F$ is locally of finite type if and only if $F$ is locally of finite preserntation (or free of finite rank).


`\begin{proof}[Proof Idea]`
Once again quasi-compactness allows us to reduce to the affine case. Then the proof reduces to the question when dealing with finitely generated modules. In particular, we write $M \cong \lim\limits_{\to \lambda}M_\lambda$ over finitely generated $A$-modules, so then faithful flatness $M\otimes_AA' \cong \lim\limits_{\to\lambda}M_\lambda\otimes_AA'$ becomes a limit of finitely generated flat modules, and then one shows for some $\lambda$ we have an isomorphism $M_\lambda\otimes_AA'\cong M\otimes_AA'$, which implies $M_\lambda \cong M$ by faithful flatness.
`\end{proof}`

A key point in descent theory is when considering properties which are **fpqc-local**. 

>[!def]
>Let $f:X\to S$ be a morphism of schemes
>- We say $f$ is **universally injective** if for all $S'\to S$ map of schemes, the base change $f':X\times_SS'\to S'$ is injective as a map of topological spaces
>- We say$f$ is **Radiciel** if $f$ is injective and $\kappa(x)/\kappa(f(x))$ is **purely inseperable** for all $x \in X$.

We have the following equivalence of conditions

>[!theorem]
>Let $f:X\to S$ be a map of schemes. Then the following are equivalent
>- $f$ is universally injective
>- $f$ is radiciel
>- For all algebraically closed fields $k$, $X(\mathsf{Spec}(k)) \to S(\mathsf{Spec}(k))$ is injective
>- $\Delta:X\to X\times_SX$ is surjective as a map of topological spaces

(Recall that injectivity on the level of sets is equivalent to surjectivity of the diagonal map)

As an important corollary we obtain the following.

>[!corollary]
>If $f:X\to S$ is a map of schemes that is radiciel, then $X\to S$ is separated.


### What can we descend?

>[!theorem]
>Consider the pullback square $$\begin{CD} X\times_SS' @>g'>> X \\ @Vf'VV @VVfV \\ S' @>>g> S\end{CD}$$
>with $g$ surjective, then
>1. $f$ is surjective if and only if $f'$ is
>2. $f$ is universally injecive if and only if $f'$ is
>3. if $g$ is quasi-compact, then $f$ is quasi-compact if and only if $f'$ is 

`\begin{proof}[Proof Idea]`
If we fix $s' \in S'$, then we have an isomorphism of fibers $${f'}^{-1}(s')\cong f^{-1}(g(s'))\otimes_{k(g(s'))}k(s')$$
then we proceed by looking at ${f'}^{-1}(s')\to f^{-1}(g(s'))$ and $k(s')/k(g(s'))$ faithfully flat.
`\end{proof}`

>[!theorem]
>Given the pullback square $$\begin{CD} X\times_SS' @>g'>> X \\ @Vf'VV @VVfV \\ S' @>>g> S\end{CD}$$
>if $g$ is fpqc, then $f$ is of finite type if and only if $f'$ is. Further, $f$ is quasi-finite if and only if $f'$ is.

Why is this a useful property? Well one interesting corollary is the following.

>[!corollary]
>If $g:Y'\to Y$ is fpqc, then on the level of topological spaces $g$ is a quotient morphism.


>[!theorem]
>Consider again the pullback square $$\begin{CD} X\times_SS' @>g'>> X \\ @Vf'VV @VVfV \\ S' @>>g> S\end{CD}$$
>where $g$ is fpqc. Then we can descend the following:
>1. If $f'$ is open/closed/quasi-compact/homeomorphism then $f$ is
>2. $f'$ is universally open/universally closed if and only if $f$ is
>3. $f'$ is separated/proper if and only if $f$ is

`\begin{proof}[Proof Idea]`
For (1), all of these topological type conditions follow from the fact that the topology downstairs is the quotient of the topology upstairs.

Observe that (2) is simply a statement about base changes, and hence holds more generally. Similarly for (3).
`\end{proof}`

>[!corollary]
>Let $f:S'\to S$ be fpqc and let $S'' = S'\times_SS'$ and $X,Y$ schemes over $S$. Then we obtain an exact sequence corresponding to maps over base changes
>$$\mathsf{Hom}_S(X,Y) \to \mathsf{Hom}_{S'}(X\times_SS',Y)\rightrightarrows \mathsf{Hom}_{S''}(X\times_SS'',Y)$$

`\begin{proof}[Proof Idea]`
The idea is to prove the claim when $Y$ is replaced by $S$.
`\end{proof}`
>[!corollary]
>$f:X\to Y$ over $S$ and $f':X'\to Y'$, $f$ is an isomorphism/closed/open/quasi-compact if and only if $f'$ is.


### Descent Structure on Schemes

>[!def]
>If $X'$ is over $S'$ as a scheme, and we have an $S''$-isomorphism $\sigma:p_1^*X'\cong p_2^*X'$ satisfying the cocycle condition
>$$p_{13}^*(\sigma) = p_{23}^*(\sigma)\circ p_{12}^*(\sigma)$$
>where again we need to be careful about canonical isomorphisms, where the pullback is defined by the square $$\begin{CD}p_i^*X @>>> X' \\ @VVV @VVV \\ S' @>>p_i> S\end{CD}$$

Then we obtain a similar theorem.

>[!theorem]
>We have the commutative square
>$$\begin{CD}p_1^*g^*X @>p_1^*\tau>> p_1^*X' \\ @V\cong VV @VVV \\ p_2^*g^*X @>>p_2^*\tau > p_2^*X' \end{CD}$$

This theorem again allows us to define a category of descent data.


### Passage to the Limit

We would like to now do the same story for a direct system satisfying some property. In this setting let $S_0$ be a base scheme and let $(A_\lambda,\varphi_{\lambda\mu})_I$ where the $A_\lambda$ are quasi-coherent algebras over $S_0$, and $\varphi_{\lambda\mu}:A_\lambda\to A_\mu$ for $\lambda \leq \mu \in I$. Then if $A = \lim\limits_{\to\lambda}A_\lambda$, we obtain $\varphi_\lambda:A_\lambda\to A$, and we can take spectrums to get schemes $S_\lambda = \mathsf{Spec}(A_\lambda)$, $S = \mathsf{Spec}(A)$ over $S_0$, we get induced maps $u_{\lambda\mu}:S_\mu\to S_\lambda$, for $\lambda \leq \mu$, associated with $\varphi_{\lambda\mu}$. Then if we have something true for the limit, we should have that it is true for something far enough in the sequence.

>[!theorem]
>Suppose $S_0$ is quasi-coherent and $f_0:X_0\to S_0$  is a map of finite presentation and $f:X\to S$ is a map upstairs, then if $f$ has property $P$, then $f_\lambda$ has property $P$ for large enough $\lambda$ where $P$ can be
>- Open immersion
>- Closed immersion
>-  Separated
>- Finite 
>- Affine
>- Surjective
>- Radiciel
>- Immersion
>- Quasi-finite
>- Proper

Why do we care about this situation? Well if $A$ is a ring, and $\{A_\lambda\}$ is a system of $A$-subalgebra finitely generated over $A$ such that $A = \lim\limits_{\to \lambda}A_\lambda$, then if you have a question about the spectrum of $A$ you can pass it to a question about the spectra of the elements of the limit. Another important scenario is that if we have $\{S_\lambda\}$ affine open neighborhoods of $x \in S_0$, with $S = \mathsf{Spec}(\mathcal{O}_{S_0,x})$, then $$\mathcal{O}_{S_0,x} \cong \lim\limits_{\to}\Gamma(S_\lambda,\mathcal{O}_{S_\lambda})$$
so we can pass questions about $S$ to question about this system of affine open neighborhoods.

## A Look Towards Etale

Recall that a morphism of schemes $f:X\to S$ is said to be etale if it is locally of finite presentation, flat, and unramified. Our slogan is that when talking in the etale setting we have some "local isomorphisms" that should be viewed as a generalization of open sets, which is made explicit in the construction of the Etale site and its Grothendieck topology.

Now, why do we care about this? Well, when doing algebraic geometry we like to work with things like the **open embedding** condition, $j:U\hookrightarrow X$, which are really determined by set theoretic data, namely its image, which is a rare property of maps of schemes.

>[!theorem]
>If $f$ is locally of finite presentation, $f$ is an open embedding if and only if for all $g:Y\to S$ such that $g(Y) \subseteq f(X)$, there exists a unique factorization $h:Y\to X$ such that $g = f\circ h$.

**Slogan**: When working with etale things, radiciel morphisms give us open embeddings.


## To Review for Next Time

The following are a list of items in order of importance which require further reading and investigation before the next meeting:
- [ ] Quasi-coherent sheaves
- [ ] Quasi-coherent schemes
- [ ] Quasi-finite
- [ ] Directed system of algebras
- [ ] Proper
- [ ] Separated



