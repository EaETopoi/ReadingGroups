---
date: 2024-06-11T00:02:00
tags:
  - DifferentialGeometry
  - Manifolds
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

In these notes we aim to provide an introduction to the basics of manifold theory, with a view towards a calculus on manifolds approach. Throughout we will be following the work of Warner[^1].

## Differentiable Manifolds: Definitions and Examples

There are a number of ways to formulate the theory of differentiable manifolds, but all formulations rely on one key philosophy - manifolds are geometric spaces locally modelled on Euclidean space. 

>[!def] Locally Euclidean
>A topological space $M$ is **locally Euclidean of dimension $d$** if it is a Hausdorff topological space and every point $p \in M$ has a neighborhood $U$ which is homeomorphic to an open subset of Euclidean space, $\mathbb{R}^d$. Such a homeomorphism $\varphi$ rom a connected open set $U \subseteq M$ onto an open subset of $\mathbb{R}^d$ is said to be a **coordinate map**, with **coordinate functions** $x_i = r_i\circ \varphi$. We say that the pair $(U,\varphi)$ is a **coordinate system** or **coordinate chart** on $M$.

The invariance of the dimension $d$ in the definition of a Locally Euclidean topological space is subtle, and comes down to a long-exact sequence argument on homology. This can be seen to follow from two observations: the homology of the sphere $S^m$ is $\mathbb{Z}$ concentrated in degrees $0$ and $m$ (this can be computed easily using simplicial homology); by excision if $U \subseteq \mathbb{R}^m$ is an open subset containing a point $x$, then we can apply excision to the pair $U,\mathbb{R}^m-\{x\}$ to conclude that $H_n(U,U-\{x\})\cong H_n(\mathbb{R}^m,\mathbb{R}^m-\{x\})$ for each $n \geq 0$, and $H_n(\mathbb{R}^m,\mathbb{R}^m-\{x\})\cong \widetilde{H}_{n-1}(\mathbb{R}^m-\{x\})\cong \widetilde{H}_{n-1}(S^{m-1})$ using the long-exact sequence for a pair and a standard deformation retract of $\mathbb{R}^m-\{x\}$ onto $S^{m-1}$. Thus, although subtle the notion of dimension is a sensible one.

In these notes we aren't interested in general topological manifolds, but rather differentiable manifolds, i.e. topological manifolds that are sufficiently smooth and that we can study differential equations on.

>[!def] Differentiable Structure
>A **differentiable structure of class $C^k$** for $1\leq k \leq \infty$, $\mathscr{F}$, on a locally Euclidean space $M$ is a collection of coordinate systems $\{(U_\alpha,\varphi_\alpha)\mid \alpha \in A\}$ such that
>1. $M = \bigcup_{\alpha \in A}U_\alpha = M$
>2. $\varphi_\alpha\circ \varphi_\beta^{-1}:\varphi_\beta(U_\alpha\cap U_\beta)\to \varphi_\alpha(U_\alpha\cap U_\beta)$ is $C^k$ for all $\alpha,\beta \in A$
>3. $\mathscr{F}$ is maximal with respect to **(2)**

Any collection of coordinate systems satisfying **(1)** and **(2)** automatically extends to a unique differentiable structure. In addition to $C^k$ differentiable structures, there are also $C^\omega$ (i.e. analytic) and complex analytic (i.e. holomorphic) structures, though we will not encounter them here.

>[!def] Differentiable Manifold
>A **$d$-dimensional differentiable manifold of class $C^k$** is a pair $(M,\mathscr{F})$ of a $d$-dimensional, second countable, locally Euclidean space $M$ together with a differentiable structure $\mathscr{F}$ of class $C^k$.

^1e0887

Moving forward we will take $k = \infty$, unless stated otherwise.

>[!def] $C^\infty$ Function
>Let $U\subseteq M$ be an open subset of a differentiable manifold. A function $f:U\to \mathbb{R}$ is a $C^\infty$ function on $U$ if $f\circ \varphi^{-1}$ is $C^\infty$ for all coordinate maps $\varphi$ on $M$. A continuous map $\Phi:M\to N$ is said to be **differentiable of class $C^\infty$** if $g\circ \psi$ is a $C^\infty$ function for all $C^\infty$ functions $g$ defined on open sets in $N$.


A differentiable manifold, in this sense, naturally comes equipped with the structure of a locally ringed space, with sheaf of $\mathscr{C}^{\infty}$-functions $\mathcal{O}_M$, where 
$$\mathcal{O}_M(U) = \{f:U\to \mathbb{R}\mid \forall (V,\varphi) \in \mathscr{F},f\circ \varphi^{-1}\vert_{\varphi(U\cap V)} \in C^\infty\}$$
and by definition we have that for any coordinate chart $(V,\varphi)$, there is an isomorphism of locally ringed spaces $(V,\mathcal{O}_M\vert_V)\cong (\varphi(V),\mathcal{O}_{\mathbb{R}^d}\vert_{\varphi(V)})$ with map on the level of topological spaces given by $\varphi$, and map $\mathcal{O}_{\mathbb{R}^d}\vert_{\varphi(V)}\to \varphi_*\mathcal{O}_M$ given by sending a function $f:W\to \mathbb{R}$ to $f\circ \varphi^{-1}:\varphi^{-1}(W)\to \mathbb{R}$. 

The stalk of $\mathcal{O}_M$ at a point $p \in M$ is given by the ring of germs
$$\mathcal{O}_{M,p} = \{[(U,f)]\mid (U,f)\sim (V,g)\iff\exists W \subseteq U\cap V,f\vert_W=g\vert_W\}$$
which is a local ring with maximal ideal given by the ideal of vanishing germs.

>[!example]
>1. $\mathbb{R}^d$ has a standard differentiable structure given by taking the maximal collection containing the identity
>2. If $V$ is a finite dimensional vector space with basis $\{e_i\}$ and dual basis $\{r_i\}$, then the $r_i$ induce a linear isomorphism $V\to \mathbb{R}^d$ as coordinate functions, which can then be used to give $V$ a topological and differentiable structure. This definition is independent of the choice of basis since change of basis operators are constant non-singular matrices.
>3. $\mathbb{C}^n$ is a $2n$-dimensional real manifold.
>4. The $d$-sphere $S^d$ has a natural differentiable structure given by taking the one which contains the stereographic projections from the north and south poles.

### Second Countability

So far we have not discussed why the second countability axiom is present in [[Basic Manifold Theory - Warner#^1e0887]]. Some of the many important consequences of this axiom are that manifolds are normal, metrizable, and paracompact.

>[!def] Separation Axioms
>A **normal** topological space is one where disjoint closed sets can be separated by disjoint open neighborhoods (such a space need not be Hausdorff, though it is if points are closed).


>[!def] Paracompact
>A topological space $X$ is **paracompact** if every open cover $\{U_i\}$ admits a refinement $\{V_j\}$ which is **locally finite** (i.e. every point has a neighborhood which only intersects finitely many $V_j$).

^350d32

Paracompactness is an essential tool for constructing partitions of unity, which are one of the most important elements of manifold theory.

>[!def] Partition of Unity
>A **partition of unity** on $M$ is a collection $\{\varphi_i\}_{i \in I}$ of $C^{\infty}$ functions on $M$ such that
>1. The collection of supports $\{\text{supp}\;\varphi_i\}_{i \in I}$ is locally finite
>2. $\sum_{i \in I}\varphi_i(p) = 1$ for all $p \in M$, and $\varphi_i(p) \geq 0$ for all $p \in M$ and $i \in I$.
>A partition of unity $\{\varphi_i\}_{i \in I}$ is **subordinate to a cover** $\{U_\alpha\}_{\alpha \in A}$ if for each $i \in I$ there exists $\alpha \in A$ such that $\text{supp}\;\varphi_i \subseteq U_\alpha$. 

We now prove that manifolds are paracompact.

>[!lem] Paracompactness
>Let $X$ be a topological space that is locally compact, Hausdorff, and second countable. Then $X$ is paracompact and every open cover has a countable locally finite refinement consisting of open sets with compact closures.

^4e686f

`\begin{proof}`
First, let $\{U_i\}_{i \in \mathbb{N}}$ be a countable base for the topology on $X$, which since $X$ is locally compact and hausdorff, can be assumed to be pre-compact (i.e. have compact closure).

Let $G_1 = U_1$. Inductively suppose we have a sequence of $G_i$ such that $\overline{G_i}$ is compact and $\overline{G_i}\subseteq G_{i+1}$, and $G_i = U_1 \cup \cdots \cup U_{j_i}$. Let $j_{i+1}$ be the smallest positive integer $> j_i$ such that $$\overline{G_i}\subseteq \bigcup_{k=1}^{j_{i+1}}U_k$$
and let $G_{i+1}$ be the union on the right. Then $G_{i+1}$ has compact closure, as its closure is contained in a compact set and the underlying space is Hausdorff. Inductively this gives a sequences of open sets $G_1,G_2,...$ with compact closure which cover $X$ and such that $\overline{G_i} \subseteq G_{i+1}$ for all $i$.

Now, let $\{U_\alpha\mid \alpha \in A\}$ be an arbitrary open cover. The set $\overline{G_i}-G_{i-1}$ is compact and contained in the open set $G_{i+1}-\overline{G_{i-2}}$. For each $i \geq 3$ we choose a finite subcover of $\{U_\alpha\cap (G_{i+1}-\overline{G_{i-2}})\}$ of $\overline{G_i}-G_{i-1}$ and a finite subcover of $\{U_\alpha\cap G_3\mid \alpha \in A\}$ of $\overline{G_2}$. Together this collection of open sets is countable (being a countable union of finite sets), consists of open sets with compact closures, and for any point $x \in X$ we have a basic open set $U_i$ containing $x$, and by construction of the $G_i$, $U_i intersects only finitely many opens in this cover, as $U_i\cap G_{i+3}-\overline{G_{i}} = \emptyset$, and similarly for any $j \geq i$.
`\end{proof}`

Now that we know the manifolds are paracompact we can begin constructing partitions of unity. Partitions of unity rely centrally on the notion of a bump function, which we now prove the existence of in Euclidean space.

>[!lem] Bump Function Existence
>There exists a non-negative $C^\infty$ function $\varphi$ on $\mathbb{R}^d$ which equals $1$ on the closed cube $\overline{C(1)}$ and zero on the complement of the open cube $C(2)$.

^5710f1

`\begin{proof}`
If $h$ is a non-negative $C^\infty$ function on the real line which is $1$ on $[-1,1]$ and zero outside $(-2,2)$, then $\varphi := \prod_{i=1}^rh\circ r_i$ will satisfy the claim. Thus to construct $h$ first observe that we have the non-negative $C^\infty$ function $f$ given by $f(t) = e^{-1/t}$ for $t > 0$ and $f(t) = 0$ for $t \leq 0$. Then, consider the function
$$g(t) = \frac{f(t)}{f(t)+f(1-t)}$$
Note that $g(t)$ is $C^\infty$ as $f$ is and the denominator is never zero. Further, $0 \leq g(t) \leq 1$, with $g(t) = 1$ for $t\geq 1$ and $g(t) = 0$ for $t \leq 0$. Now, set 
$$h(t) = g(t+2)g(2-t)$$
If $t \in [-1,1]$ then $t+2\geq 1$ and $2-t\geq 1$, so $h(t) = 1$. If $t \geq 2$ then $2-t \leq 0$, and so $h(t) = 0$, while for $t \leq -2$ $t+2 \leq 0$, and so $h(t) = 0$ again. Thus, $h$ is out desired function.
`\end{proof}`

We can now give an existence proof for partitions of unity.

>[!thm] Existence of Partitions of Unity
>Let $M$ be a differentiable manifold with open cover $\{U_\alpha\}_{\alpha \in A}$. Then there exists a countable partition of unity $\{\varphi_i\}_{i \geq 1}$ subordinate to the cover $\{U_\alpha\}$ with $\text{supp}\;\varphi_i$ compact for each $i$. If one does note require compact supports we have a partition of unity $\{\varphi_\alpha\}_{\alpha \in A}$ subordinate to the cover, with at most countably may $\varphi_\alpha$ not identically zero.

^96b8fc

`\begin{proof}`
Let $\{G_i\}_{i \geq 1}$ be a cover of $M$ constructed as in [[Basic Manifold Theory - Warner#^4e686f]], and set $G_0 = \emptyset$. For any point $p \in M$ choose the largest integer $i_p$ such that $p \in M-\overline{G_{i_p}}$, and choose $\alpha_p$ such that $p \in U_{\alpha_p}$. Let $(V,\tau)$ be a coordinate system centered around $p$ such that $V \subseteq U_{\alpha_p}\cap (G_{i_p+2}-\overline{G_{i_p}})$ and such that $\tau(V)$ contains the closed cube $\overline{C(2)}$, Let $\psi_p = \varphi\circ \tau$ on $V$ and $0$ elsewhere, where $\varphi$ is from [[Basic Manifold Theory - Warner#^5710f1]]. Then $\psi_p$ has compact support lying in $V$. Let $W_p$ be the open neighborhood of $p$ for which $\psi_p = 1$.

For each $i \geq 1$ choose a finite set of points $p$ in $M$ whose corresponding $W_p$ neighborhoods cover $\overline{G_i}-G_{i-1}$. Order the $\psi_p$ functions in a sequence $\psi_j,j\geq 1$, which is possible since again a countable union of finite sets is countable. Since the supports of the $\psi_j$ lie in $G_{i+2}-\overline{G_i}$ open sets, they form a locally finite family of subsets of $M$. Thus, we can define $\psi = \sum_{j\geq 1}\psi_j$, which is a well-defined $C^\infty$ function since in a sufficiently small open neighborhood around any point the sum is finite and $\psi(p) > 0$ for all $p \in M$. Define $\varphi_i = \psi_i/\psi$ for all $i \geq 1$. Then the $\varphi_i$ form our desired countable partition of unity with compact support and subordinate to the cover. If we let $\varphi_\alpha$ be the sum over $\psi_i$ with support in $U_\alpha$ then $\{\varphi_\alpha\}$ gives a partition of unity subordinate to the cover with at most countably many $\varphi_\alpha$ non-zero.
`\end{proof}`

As a simple corollary we obtain the we can always find bump functions on closed sets.

>[!corollary]
>Let $G$ be open in $M$ and let $A$ be closed in $M$ with $A \subseteq G$. Then there exists a $C^\infty$ function $\varphi:M\to \mathbb{R}$ such that 
>1. $0 \leq \varphi\leq 1$
>2. $\varphi\vert_A = 1$
>3. $\text{supp}\;\varphi \subseteq G$.

`\begin{proof}`
Take a partition of unity $\{\varphi,\psi\}$ which is subordinate to $\{G,M-A\}$ with $\text{supp}\;\varphi \subseteq G$ and $\text{supp}\;\psi \subseteq M-A$. Then $\varphi$ must satisfy properties **(1)** through **(3)**.
`\end{proof}`


### Differentials and the Tangent Bundle

A central part of the geometry of smooth manifolds come from their tangent  bundles. Tangent bundles collect local tangent vector information into a single mathematical object (in fact a manifold). Consider the classical case of $\mathbb{R}^d$. If $v = (v_1,...,v_d)^T$ is a vector, thought of as being attached to a point $p$, and $f$ is a function which is differentiable in a neighborhood of $p$, then $v$ can be thought of as giving an assignment that sends $f$ to the real number describing its directional derivative at $p$:
$$v(f) = \sum_{i=1}^dv_i\frac{\partial f}{\partial r_i}\Bigg\vert_p$$
This operation is linear in the function variable, and by the product rule satisfies what we call the Jacobi identity
$$v(f\cdot g) = f(p)v(g)+g(p)v(f)$$
We would like our abstract notion of tangent vectors on manifolds to mimic this kind of structure.

>[!def] Tangent Vectors
>A **tangent vector** $v$ at a point $p \in M$ is a linear derivation f the algebra $\mathcal{O}_{M,p}$ (i.e. $v:\mathcal{O}_{M,p} \to  \mathbb{R}$). so for all $f,g \in \mathcal{O}_{M,p}$ and $\lambda \in \mathbb{R}$,
>1. $v(f+\lambda g) = v(f) +\lambda v(g)$
>2. $v(f\cdot g) = f(p)v(g)+g(p)v(f)$
>
>We write $T_pM$ for the set of tangent vectors to $M$ at $p$.

Note that $T_pM$ is itself a real vector space. As we shall show, $\dim_\mathbb{R}T_pM = \dim M$. 

Although this definition is convenient in the smooth setting, it is not suitable in the $C^k$ case for $k < \infty$, although there are ways of defining such a structure in those settings which will give an isomorphic tangent space when $k = \infty$.

Germs of constant functions are zero, as one would expect for derivatives. We now show that $T_pM$ is naturally isomorphic to the dual of the Zariski cotangent space.

>[!lem] Zariski Cotangent Space Perspective
>$T_pM$ is naturally isomorphic to $(\mathfrak{m}_{M,p}/\mathfrak{m}_{M,p}^2)^\lor$.
>

`\begin{proof}`
We have a natural map $T_pM \to (\mathfrak{m}_{M.p}/\mathfrak{m}^2_{M,p})^\lor$ given by restriction and the first isomorphism theorem due to the Jacobi identity. On the other hand, if $w:\mathfrak{m}_{M,p}/\mathfrak{m}_{M.p}^2\to \mathbb{R}$ is a linear functional, then we can define $v:\mathcal{O}_{M,p}\to \mathbb{R}$ by $v(f) = w(\overline{f-f(p)})$, where $f(p)$ denotes the constant function with value $f(p)$. Linearity follows by linearity of $w$, and for any other $g$ we have
$$
\begin{align*}
v(f\cdot g) &= w(\overline{f\cdot g-f(p)g(p)}) \\
&= w(\overline{(f-f(p))(g-g(p))+f(p)(g-g(p))+g(p)(f-f(p))}) \\
&= f(p)w(\overline{g-g(p)})+g(p)w(\overline{f-f(p)}) \\
&= f(p)v(g)+g(p)v(f)
\end{align*}
$$
so $v$ is a derivation.
`\end{proof}`

We can now study the dimension of $T_pM$ by looking at the dimension of the Zariski cotangent space. For this we need the following lemma from calculus:

>[!lem] 
>If $g$ is of class $C^k$, $k\geq 2$, on a convex open subset $U$ about $p$ in $\mathbb{R}^d$, then for each $q \in U$
>$$g(q) = g(p)+\sum_{i=1}^d\frac{\partial g}{\partial r_i}\Bigg\vert_p(r_i(q)-r_i(p))+\sum_{i,j=1}^d(r_i(q)-r_i(p))(r_j(q)-r_j(p))\int_0^1(1-t)\frac{\partial^2g}{\partial r_i\partial r_j}\Bigg\vert_{(p+t(q-p))}dt$$

^757942

We can now prove the theorem on dimension

>[!thm] Dimension of Tangent Space
>$\dim_\mathbb{R}(\mathfrak{m}_{M,p}/\mathfrak{m}_{M,p}^2) = \dim M$.

`\begin{proof}`
Let $(U,\varphi)$ be a coordinate chart about $p$ with coordinate functions $x_1,...,x_d$. Let $f \in \mathfrak{m}_{M,p}$. Applying [[Basic Manifold Theory - Warner#^757942]] to $f\circ \varphi^{-1}$ and composing with $\varphi$ we can write $f$ as 
$$f = \sum_{i=1}^d\frac{\partial(f\circ \varphi^{-1})}{\partial r_i}\Bigg\vert_{\varphi(p)}(x_i-x_i(p))+\sum_{i,j=1}^d(x_i-x_i(p))(x_j-x_j(p))h$$
on some neighborhood of $p$, where $h \in C^\infty$. Thus reducing modulo $\mathfrak{m}_{M,p}^2$ we see that the residues of the $(x_i-x_i(p))$ span $\mathfrak{m}_{M,p}/\mathfrak{m}_{M,p}^2$. Composing with coordinate functions $\varphi^{-1}$ we find that they are also linearly independent since the derivative of $\sum_{i=1}^da_i(r_i-r_i(\varphi(p)))$ with respect to the $j$th coordinate would pull out $a_j$, but if the element is in $\mathfrak{m}_{M,p}^2$ then this must be zero.
`\end{proof}`

As an immediate corollary, since we are working with finite dimensional spaces, $\dim T_pM = \dim M$. Further, if $(U,\varphi)$ is a coordinate system about a point $p \in U$ with coordinate functions $x_1,...,x_d$, then we have a basis $(\partial/\partial x_i)\vert_p \in T_pM$ given by
$$\left(\frac{\partial}{\partial x_i}\Bigg\vert_p\right)(f) = \frac{\partial(f\circ \varphi^{-1})}{\partial r_i}\Bigg\vert_{\varphi(p)}$$
which is exactly the dual basis to the $(x_i-x_i(p))$ basis of the Zariski cotangent space. Indeed, for any other derivation $v \in T_pM$, we have that 
$$\begin{align}v = \sum_{i=1}^dv(x_i) \frac{\partial}{\partial x_i}\Bigg\vert_p\end{align}$$
If $(U,\varphi)$ and $(V,\psi)$ are different coordinate systems about the same point $p$, with coordinate functions $x_1,...,x_d$ and $y_1,...,y_d$, the above equation reads
$$\frac{\partial}{\partial y_j}\Bigg\vert_p = \sum_{i=1}^d\frac{\partial x_i}{\partial y_j}\Bigg\vert_p \frac{\partial}{\partial x_i}\Bigg\vert_p$$
which is exactly an instance of the chain rule. Thus, in one sense this form of the chain rule is simply a change of coordinates.

Throughout this work, if we had $k < \infty$ it turns out that the Zariski cotangent space $\mathfrak{m}_{M.p}/\mathfrak{m}_{M,p}^2$ is always infinite dimensional. 

Moving on from such considerations, and thinking about the tangent bundle as an intrinsic part of the structure of a smooth manifold, we can show that the tangent bundle $TM = \coprod_{p \in M}T_pM$ itself has a smooth manifold structure induced by the projection $\pi_M:TM\to M$ making the projection a differentiable map of smooth manifolds. To do this we first define the notion of the differential of a smooth map.

>[!def] The Differential
>Let $\psi:M\to N$ be $C^\infty$, and let $p \in M$. The differential $\psi$ at $p$ is the linear map $d\psi:T_pM\to T_{\psi(p)}N$ given by pre-composition on inputs, so $d\psi(v)(f) = v(f\circ \psi)$.
>
>We obtain a dual map $\delta\psi:T_{\psi(p)}N^\lor \to T_pM^\lor$ given by $\delta\psi(\omega)(v) = \omega(d\psi(v))$. We will often abuse notation and identify $df$ with $\delta f(\omega)$ for $f:M\to \mathbb{R}$ and $\omega$ the basis of the one dimensional space $T_{r_0}\mathbb{R}^\lor$ dual to $(d/dr)\vert_{r_0}$.

Now, given a chart $(U,\varphi)$ on $M$ we obtain a chart $(\pi_M^{-1}(U),\widetilde{\varphi})$ where $\widetilde{\varphi}:\pi^{-1}_M(U)\to \mathbb{R}^d\times \mathbb{R}^d$ is given by $(p,v)\mapsto (\varphi(p),d\varphi_p(v))$. For any two such maps we have the transition functions $\varphi\circ \psi^{-1} \times d(\varphi\circ \psi^{-1})$ which is a product of smooth maps, since $\varphi\circ \psi^{-1}$ being smooth implies its Jacobian is, and so determines a differentiable structure on $TM$. By construction this structure makes $\pi_M$ a differentiable map, and any differentiable map $\psi:M\to N$ between manifolds induces a differentiable map $d\psi:TM\to TN$ between tangent bundles, or $\delta\psi:T^\lor N \to T^\lor M$ between dual bundles.

If $\psi:M\to N$ and $f:N\to \mathbb{R}$ are $C^\infty$, and $p$ is a point of $M$, then $\delta\psi(df_{\psi(p)}) = d(f\circ \psi)_p:T_pM\to \mathbb{R}$, where again we identify the differentiable of a smooth function with the value of its dual differential at a basis element. 

We now exhibit some properties of the differentiable that might be familiar from introductory calculus courses.

>[!thm]
>Let $\psi:M\to N$ be a $C^\infty$ mapping and suppose $M$ is connected. Suppose that $d\psi_p \equiv 0$ for each $p \in M$. Then $\psi$ is a constant map.

`\begin{proof}`
Let $q \in \psi(M)$. Since manifolds are Hausdorff $\psi^{-1}(\{q\})$ is a closed set. I claim that it is also open. Let $p \in \psi^{-1}(\{q\})$ and choose coordinate systems $(U,x_1,...,x_d)$ and $(V,y_1,...,y_c)$ about $p$ and $q$ so that $\psi(U) \subseteq V$. Then by assumption we have that for any point on $U$
$$0 = d\psi\left(\frac{\partial}{\partial x_j}\right) = \sum_{i=1}^c\frac{\partial (y_i\circ \psi)}{\partial x_j} \frac{\partial}{\partial y_i}$$
which implies $\frac{\partial(y_i\circ \psi)}{\partial x_j} \equiv 0$ on $U$. Looking at coordinate components and using results from introductory calculus it follows that $y_i\circ \psi$ is constant on $U$ for all $i$, and so $\psi(U) = q$ is constant. Thus $\psi^{-1}(\{q\})$ is open, so as $M$ is connected we must have $\psi^{-1}(\{q\}) = M$.
`\end{proof}`

#### Higher Order Differentials

Using the point of view of $T_pM\cong (\mathfrak{m}_{M,p}/\mathfrak{m}_{M,p}^2)^\lor$ allows us to generalize to higher order tangent vectors and differentials. Note that we have a chain of ideals $\mathfrak{m}_{M,p}\supseteq \mathfrak{m}_{M,p}^2\supseteq \mathfrak{m}_{M,p}^3\supseteq \cdots$ in $\mathcal{O}_{M,p}$, and we can define the space of **$k$th other differentials at $p$** to be the quotient $\mathfrak{m}_{M,p}/\mathfrak{m}_{M,p}^{k+1}$, which we write as $T_{p}^{(k)}M$. In this setting the $k$th order differential of a smooth function $f$ defined on a neighborhood of $p$ is the image of the difference $f-f(p)$ in the quotient. We denote the $k$th order tangent vectors by $T_{p,(k)}M$. 

If $(U,\varphi)$ is a coordinate system about $p$ with coordinate functions $x_1,...,x_d$ such that $\varphi(U)$ is a convex open subset of $\mathbb{R}^d$, then by [[Basic Manifold Theory - Warner#^757942]] we have that a smooth function $f$ on $U$ can be given by
$$f = f(p)+\sum_{|\alpha| = 1}^ka_\alpha(x-x(p))^\alpha+\sum_{|\alpha|=k+1}h_\alpha(x-x(p))^\alpha$$
where the sum is indexed over multi-indices, the $h_\alpha$ are $C^\infty$ functions on $U$, and 
$$a_\alpha = \frac{1}{\alpha!}\frac{\partial^\alpha(f\circ \varphi^{-1})}{\partial r^\alpha}\Bigg\vert_{\varphi(p)}$$
Then $d^kf$ is given by the germ of the middle sum, and a similar proof to the $k=1$ case shows that the $(x-x(p))^\alpha$ for $1\leq |\alpha|\leq k$ forms a basis for the space of differentials. Thus the space is finite dimensional with dimension equal to $\sum_{i=1}^k{d+j-1 \choose j}$. For a general $k$th order tangent vector $v$ we have that
$$v = \sum_{|\alpha|=1}^kb_\alpha\frac{\partial^\alpha}{\partial x^\alpha}\Bigg\vert_p$$
where $$b_\alpha = \frac{1}{\alpha!}v((x-x(p))^\alpha)$$
The same definitions for tangent vectors and differentials give us linear maps between higher order tangent vectors and differentials when provided a differentiable map $\varphi:M\to N$.


## Submanifolds, Diffeomorphisms, and the Inverse Function Theorem

As with all fields of math in order to understand manifolds and the maps between them it is important to understand sub-objects in the category.

>[!def]
>Let $\psi:M\to N$ be smooth.
>1. $\psi$ is an **immersion** if $d\psi_p$ is non-singular (i.e. injective) for each $p \in M$
>2. The pair $(M,\psi)$ is a **submanifold** of $N$ if $\psi$ is an injective immersion
>3. $\psi$ is an **embedding** if $\psi$ is an injective immersion and a homeomorphism onto its image.
>4. $\psi$ is a **diffeomorphism** if $\psi$ is an isomorphism in the category of smooth manifolds.

We can immerse the real line into the plane in ways that are immersions, submanifolds, or embeddings. For example, to obtain an immersion we can loop the line so that the result has an intersection point, so this is not a submanifold. If we loop the line in such a way that it doesn't intersect, but instead approaches itself in the limit, we obtain a submanifold which is not an embedding. Finally a simple embedding can be given by just including the line as an axis.

An important tool for constructing local diffeomorphisms is the inverse function theorem. 

>[!def] Independent set of functions
>A set $y_1,...,y_j$ of $C^\infty$ functions on some neighborhood of a point $p$ in $M$ is called **independent at $p$** if the differentials $dy_1,...,dy_j$ form an independent set in $T_pM^\lor$.

>[!thm] Inverse Function Theorem
>Let $U \subseteq \mathbb{R}^d$ be open and let $f:U\to \mathbb{R}^d$ be $C^\infty$. If the Jacobian of $f$ is non-singular at $r_0 \in U$, then there exists an open set $V$ in $U$ containing $r_0$ such that $f\vert_V$ is a diffeomorphism onto its image.

^e4bd5b

We will prove the inverse function theorem through a succession of lemmas.

>[!lem]
>Let $U \subseteq \mathbb{R}^n$ be open. A function $f:U\to \mathbb{R}^m$ is $C^1$ if and only if all partial derivatives exist and are continuous on $U$.

^434392

`\begin{proof}`
By definition of the product topology and differentiation for a product map, $f$ is $C^1$ if and only if each $r_i\circ f = f_i$ for $1 \leq i \leq m$ is $C^1$, and in this case the Jacobian $Df$ has as rows the $Df_i$. Thus, we are reduced to prove the case when $m = 1$, and $f:U\to \mathbb{R}$. Now $Df:U\to \mathbb{R}^n$ is continuous if and only if each $D_if$ is continuous, by the universal property of the product. Thus, it suffices to show that if the partial derivatives of $f$ exist and are continuous, the resulting matrix of  partial derivatives serves as a derivative for $f$.

Let $h \in \mathbb{R}^n$ be suitably small with $||h|| > 0$. Then we have that at a point $p \in U$ 
$$
\begin{align*}
\frac{||f(p+h)-f(p)+\sum_{i=1}^nD_if(p)h_i||}{||h||} &= \frac{||\sum_{i=1}^n(f(p+h_i')-f(p+h_{i-1}')+D_if(p)h_i)||}{||h||} \\
&\leq \sum_{i=1}^n\frac{||f(p+h_i')-f(p+h_{i-1}')+D_if(p)h_i||}{||h||} \\
&= \sum_{i=1}^n\frac{||D_if(p')h_i+D_if(p)h_i||}{||h||} \\
&\leq \sum_{i=1}^n||D_if(p')-D_if(p)||
\end{align*}
$$
where in the second last equality we use the mean value theorem on the function $f(p_1+h_1,...,p_i+h_i,p_{i+1},...,p_n)$ to obtain $p' =(p_1+h_1,...,p_{i-1}+h_{i-1},p_i+c_i,p_{i+1},...,p_n)$, where $c_i \in (0,h_i)$ (or $(h_i,0)$). Finally, by continuity of the partial derivatives this last expression goes to zero as $h$ does, so the matrix of partial derivatives gives us a Jacobian.
`\end{proof}`

>[!proposition]
>Let $f:U\to \mathbb{R}^n$ be a $C^1$ function on $U$. Suppose that $Df$ is non-singular at some point $p \in U$. Then there exists $W\subseteq U$ open and $c > 0$ such that $$||f(y)-f(x)|| \geq c||y-x||$$
>for all $x,y \in W$.

^617db7

`\begin{proof}`
Let $A = [Df(p)]^{-1}$, and note that since non-singular matrices form an open subset of all $n\times n$ matrices, we have an open set $V \subseteq U$ such that $Df$ is non-singular at all points of $V$. Since all operators between finite dimensional vector spaces are continuous, $||A||_{op} < \infty$ and or any  $x,y \in \mathbb{R}^n$ we have the estimate $$||x-y|| \leq ||A||_{op}||A^{-1}x-A^{-1}y||$$
Let $c = \frac{1}{2||A||_{op}}$. Let $f_j = r_j\circ f$ be the coordinate functions for $f$, which are also $C^1$. Then we have an open ball $W \subseteq V$ such that $W$ contains $p$ and $||Df_j(x)-Df_j(y)||_{op}\leq \frac{c}{n}$. Together this gives the bound
$$||Df(x)-Df(y)||_{op}\leq c,\;\forall x,y \in W$$
Note that $W$ being an open ball is convex, so we can use the mean value theorem to conclude that for $x,y \in W$ there exists $\lambda_j \in (0,1)$, such that $z_j = (1-\lambda_j)x+\lambda_jy$, which is in $U$, satisfies
$$f_j(y)-f_j(x) = Df_j(z_j)(y-x)$$
Together with our last inequality we ind that
$$||f_j(y)-f_j(x)-Df_j(p)(y-x)|| = ||Df_j(z_j)(y-x)-Df_j(p)(y-x)|| \leq \frac{c}{n}||y-x||$$
which put together gives
$$||f(y)-f(x)-Df(p)(y-x)|| \leq c||y-x||\;\forall x,y \in W$$
Using the triangle inequality we can re-write this as 
$$||Df(p)(y-x)||-c||y-x|| \leq ||f(y)-f(x)||$$
Going back to our first estimate we have that
$$c||y-x||= 2c||y-x||-c||y-x||\leq ||f(y)-f(x)||$$
for all $x,y \in W$, as desired.
`\end{proof}`

>[!corollary]
>Let $f:U\to \mathbb{R}^n$ be $C^1$ smooth on $U$ and let $p \in U$ be a point where the jacobian of $f$ is non-singular. Then there exists an open set $W$ containing $p$ such that $f\vert_W:W\to f(W)$ is a homeomorphism.

`\begin{proof}`
If we take the open set $W$ constructed in [[Basic Manifold Theory - Warner#^617db7]] then $f\vert_W:W\to f(W)$ is a map such that for any $x,y \in W$ we have $c||y-x|| \leq ||f(y)-f(x)||$ for some positive constant $c$. In particular this implies that $f\vert_W$ is invertible and that the inverse is Lipschitz, and hence continuous. Thus $f\vert_W$ is a homeomorphism, as desired, and $Df$ is non-singular at all points of $W$.
`\end{proof}`

All that remains to show for the inverse function theorem is that upon possible shrinking of $W$, $f\vert_W$ has $C^1$ inverse.

`\begin{proof}[Proof of Inverse Function Theorem.]`
Let $W\subseteq U$ and be an open subset containing $p$ such that $f\vert_W$ is a homeomorphism and $Df$ is non-singular at all points of $W$. Note that the assignment $f(W) \to \mathbb{R}^{n^2}$ given by sending $f(x)\mapsto [Df(x)]^{-1}$ is continuous since $Df$ is continuous, the inversion operation on $\mathsf{Gl}(n,\mathbb{R})$ is continuous, and $(f\vert_W)^{-1}$ is continuous. Thus, it only remains to show that $Df(x)^{-1}$ serves as a differential for $g:=(f\vert_W)^{-1}$ at $f(x)$. For this observe that if $z,y \in f(W)$ with $y = f(x)$, $x \in W$, then
$$
\begin{align*}
||g(z)-g(y)-Df(x)^{-1}(z-y)|| &= ||Df(x)^{-1}(Df(x)g(z)-Df(x)g(y)-(z-y))|| \\
&\leq ||Df(x)^{-1}||_{op}||Df(x)g(z)-Df(x)g(y)-(z-y)||
\end{align*}
$$
Note that we can re-write our inequality from [[Basic Manifold Theory - Warner#^617db7]] as $||z-y|| \geq c||g(z)-g(y)|| = c||g(z)-x||$ for all $z,y \in f(W)$. It follows that our difference quotient is bounded as
$$\frac{||g(z)-g(y)-Df(x)^{-1}(z-y)||}{||z-y||} \leq \frac{||Df(x)^{-1}||_{op}}{c}\frac{||Df(x)g(z)-Df(x)x-(z-y)||}{||g(z)-x||}$$
The second half of our quotient is
$$\frac{||f(g(z))-f(x)-Df(x)(g(z)-x)||}{||g(z)-x||}$$
which goes to zero as $z$ approaches $y$ since $g$ is continuous and $f$ is differentiable. This completes the proof.
`\end{proof}`

Note that this results holds for $C^k$ maps for all $k \geq 1$. We can now upgrade this result to the setting of manifolds.

>[!corollary] Inverse Function Theorem For Manifolds
>Suppose $\psi:M\to N$ is $C^\infty$ and that $p \in M$ such that $d\psi_p$ is an isomorphism. Then there exists a neighborhood $U$ of $p$ such that $\psi\vert_U:U\to \psi(U)$ is a diffeomorphism onto an open subset of $N$.

^b914f8

`\begin{proof}`
By assumption we must have that $\dim M = \dim N$, say $d$. Let $(V,\varphi)$ be a coordinate system about $p$ and let $(W,\tau)$ be a coordinate system about $\psi(p)$ and containing $\psi(V)$. Let $\varphi(p) = q$ and $\tau(\psi(p)) = q'$. Then the differential of $\tau\circ \psi\circ \varphi^{-1}\vert_{\varphi(V)}$ is non-singular at $q$. Thus, by the classical inverse function theorem there exists an open subset $W \subseteq \varphi(V)$ containing $q$ such that the restriction $\alpha:W\to \alpha(W)$ is a diffeomorphism. Then $\tau^{-1}\circ \alpha\circ \varphi$ is our desired diffeomorphism given by restricting $\psi$ to the open neighborhood $\varphi^{-1}(W)$ of $p$.
`\end{proof}`

Another useful corollary comes in the form of determining when a collection of functions on a manifold determine a coordinate system on the manifold.

>[!corollary] Coordinates from Independent Functions
>Suppose $\dim M= d$ and $y_1,...,y_d:U\to \mathbb{R}$ is an independent set of functions at $p \in M$. Then the functions $y_1,...,y_d$ form a coordinate system on a neighborhood of $p$.

^8276e8

`\begin{proof}`
The independence of the $y_i$ implies that the unique map $\psi:U\to \mathbb{R}^d$ obtained from the universal property of the product is $C^\infty$ and has non-singular jacobian at $p$. This can be seen from the fact that $\delta\psi$ is an isomorphism on $(\mathbb{R}_{\psi(p)}^d)^\lor$ as it sends the standard basis $dr_i$ to the basis $dy_i$. The [[Basic Manifold Theory - Warner#^b914f8]] then applies to give $\psi$ as a diffeomorphism on some open neighborhood $V \subseteq U$ containing $p$, as desired.
`\end{proof}`

We can also extend independent functions to a coordinate system on a manifold using charts.

>[!corollary] Extending Independent Set to a Coordinate System
>Suppose $\dim M = d$ and that $y_1,...,y_l$ for $l < d$ is an independent set of functions at $p \in M$. Then we can extend the set to one which gives a coordinate system on a neighborhood of $p$.

^37ef72

`\begin{proof}`
Let $(U,x_1,...,x_d)$ be a coordinate system about $p$. Then $\{dy_1,...,dy_l,dx_1,...,dx_d\}$ spans $T_pM^\lor$, and so from standard techniques in linear algebra we can refine it to a basis $\{dy_1,...,dy_l,dx_{i_1},...,dx_{i_{d-l}}\}$ of $T_pM^\lor$, and the result now follows by [[Basic Manifold Theory - Warner#^8276e8]].
`\end{proof}`

>[!corollary] Pulling Back Coordinate Systems
>Let $\psi:M\to N$ be $C^{\infty}$ and suppose $d\psi:T_pM\to T_{\psi(p)}N$ is surjective. Let $x_1,...,x_l$ form a coordinate system on some neighborhood of $\psi(p)$ in $N$. Then $x_1\circ \psi,...,x_l\circ \psi$ can be extended to a coordinate system on some neighborhood of $p$.

^b13b17

`\begin{proof}`
Since $d\psi_p$ is surjective the dual map $\delta\psi_{\psi(p)}$ is injective. Thus the $x_i\circ \psi$ are independent at $p$ since $\delta\psi(dx_i) = d(x_i\circ \psi)$. The claim now follows from [[Basic Manifold Theory - Warner#^37ef72]].
`\end{proof}`

>[!corollary] Reducing a spanning set of functions to a coordinate system
>Suppose $y_1,...,y_k$ is a set of $C^\infty$ functions on a neighborhood of $p$ such that their differentials span $T_pM^\lor$. Then we can reduce the $y_i$ to a coordinate system on a neighborhood of $p$.

^97fa9e

`\begin{proof}`
We can simply choose a subset whose differentials form a basis of $T_pM^\lor$ and then apply [[Basic Manifold Theory - Warner#^8276e8]].
`\end{proof}`

>[!corollary] Pulling back coordinate systems along immersions
>Let $\psi:M\to N$ be $C^\infty$ and assume $d\psi:T_pM\to T_{\psi(p)}N$ is injective. Let $x_1,...,x_k$ form a coordinate system on a neighborhood of $\psi(p)$. Then a subset of $x_i\circ \psi$ forms a coordinate system on a neighborhood of $p$. In particular, $\psi$ is injective on a neighborhood of $p$.

^4474ea

`\begin{proof}`
Since $d\psi_m$ is injective its dual $\delta\psi_{\psi(p)}$ is surjective. This implies that the family $d(x_i\circ \psi) = \delta\psi(dx_i)$ spans $T_pM^\lor$, so we can just apply [[Basic Manifold Theory - Warner#^97fa9e]].
`\end{proof}`

We can now obtain the following result for factorization through submanifolds.

>[!thm] Factoring Through a Submanifold
>Suppose $\psi:N\to M$ is $C^\infty$, that $(P,\varphi)$ is a submanifold of $M$, and that $\psi$ factors through $(P,\varphi)$, that is $\psi(N)\subseteq \varphi(P)$. Since $\varphi$ is injective there is a unique map $\psi_0:N\to P$ such that $\varphi\circ \psi_0 = \psi$. Then
>1. $\psi_0$ is $C^\infty$ if it is continuous
>2. $\psi_0$ is continuous if $\varphi$ is an embedding.

`\begin{proof}`
Claim **(2)** is clear since $\varphi$ being an embedding implies that it is an open mapping, so $\psi_0^{-1}(U) = \psi^{-1}(\varphi(U))$, which is open.

Now suppose $\psi_0$ is continuous. We need to cover $P$ by coordinate systems which witness $\psi_0$ as $C^\infty$. Let $p \in P$ and let $(V,\gamma)$ be a coordinate system on a neighborhood of $\varphi(p)$ in $M$. Then by [[Basic Manifold Theory - Warner#^4474ea]] we have a projection $\pi$ of $\mathbb{R}^d$ onto a subspace obtained by setting certain coordinate functions to $0$, such that $\tau = \pi\circ \gamma\circ \varphi$ yields a coordinate system on a neighborhood $U$ of $p$. Then we have that 
$$\tau\circ \psi_0\vert_{\psi_0^{-1}(U)} = \pi\circ\gamma \circ  \varphi\circ \psi_0\vert_{\psi_0^{-1}(U)} = \pi\circ \gamma\circ \psi\vert_{\psi_0^{-1}(U)}$$
is $C^\infty$.
`\end{proof}`

We say that submanifolds of a manifold $M$ are equivalent if their are isomorphic in the slice category $\mathsf{Smooth}/M$. Equivalence defines an equivalence relation on submanifolds, with equivalence classes having a unique representative $(A,i)$ where $A \subseteq M$ and $i:A\to M$ is the inclusion, with manifold structure given by a diffeomorphism with any submanifold. Note that specifying a subset $A$ of $M$ is not enough to obtain a submanifold structure on $(A,i)$, and in fact $(A,i)$ can have none or many such sub-manifold structures. Note that a given sub-manifold structure on $A$ need not induce a topology which agrees with the subspace topology $A$ would inherit from $M$. However, if a topology is fixed, then there is at most one differentiable structure on $A$ such that $(A,i)$ is a submanifold of $M$.

Indeed, if $(U,\varphi)$ and $(V,\psi)$ are charts for two differentiable structures on $A$, making $A$ a submanifold of $M$ under inclusion, then for any chart $(W,\xi)$ on $M$ we have that
$$\xi\circ \psi^{-1} = \xi \circ \varphi^{-1}\circ \varphi\circ \psi^{-1}$$
is $C^\infty$, which implies $\varphi\circ \psi^{-1} = \varphi\circ \xi^{-1}\circ \xi\circ \psi^{-1}$ is $C^\infty$, and as this holds for any chart on $M$, and hence in a suitably small neighborhood of any point in $A$, we have that $\varphi$ and $\psi$ are compatible.

### Slices

If $(U,\varphi)$ is a coordinate system on $M$ with coordinate functions $x_1,...,x_d$, and $0\leq c\leq d$ is an integer, for $p \in \varphi(U)$ we define the slice
$$S=\{q \in U\mid x_i(q) = r_i(p),i=c+1,\dots,d\}$$
The subspace $S$ of $M$ together with the coordinate system $\{x_j\vert_S\mid j=1,...,c\}$ forms a submanifold of $M$.

>[!proposition] Immersion are Locally Slices
>Let $\psi:M\to N$ be an immersion and let $p \in M$. Then there exists a cubic-centered coordinate system $(V,\varphi)$ about $\psi(p)$ and a neighborhood $U$ of $p$ such that $\psi\vert_U$ is injective and $\psi(U)$ is a slice of $(V,\varphi)$.

^ec5cec

`\begin{proof}`
Let $(W,\tau)$ be a centered coordinate system about $\psi(p)$ with coordinate functions $y_1,...,y_d$. By [[Basic Manifold Theory - Warner#^4474ea]] we can renumber the coordinate functions so that $\widetilde{\tau} = \pi_c\circ \tau\circ \psi$ is a coordinate map on a neighborhood $V'$ of $p$ and $\pi_c:\mathbb{R}^d\to \mathbb{R}^c$ is a projection of the first $c$ coordinates, where $c$ is the dimension of $M$ and $d$ is the dimension of $N$. We define functions $x_i$ on $(\pi_c\circ \tau)^{-1}(\widetilde{\tau}(V'))$ by
$$x_i = \left\{\begin{array}{cc} y_i & i=1,\dots,c \\ y_i-y_i\circ \psi\circ \widetilde{\tau}^{-1}\circ \pi_c\circ \tau,i=c+1,\dots,d \end{array}\right.$$
These $x_i$ are independent at $\psi(p)$ since $dx_i = dy_i$ for $i = 1,...,c$, and $dx_i = dy_i + \sum_{j=1}^ca_{ij}dy_j$ for $i = c+1,...,d$ and some constants $a_{ij}$. Thus by [[Basic Manifold Theory - Warner#^8276e8]] the $x_i$ form a coordinate system on a neighborhood of $\psi(p)$. Restricting possibly to an open neighborhood $V$ of $\psi(p)$ we can assume that the $x_1,...,x_d$ form a cubic coordinate system on $V$ centered at $p$. Let $\varphi$ be the corresponding coordinate map and let $U = \psi^{-1}(V)\cap V'$. Then $U$ and $(V,\varphi)$ are the required neighborhood and coordinate system, indeed
$$\psi(U) = \{q \in V\mid x_i(q) = 0,i=c+1,\dots,d\}$$
as desired.
`\end{proof}`

When $(M,\psi)$ is an embedded submanifold the coordinate system in the proposition can be chosen so that $\psi(M)\cap V$ is a single slice of $V$.

We now move to describing how embeddings are related to pullbacks of smooth functions.

>[!proposition] Embedding in Terms of Pullbacks
>Let $\psi:M\to N$ be a submanifold. Then $\psi$ is an embedding with closed image if and only if for any $g \in C^\infty$, there exists $f \in C^\infty(N)$ such that $f\circ \psi = g$.

`\begin{proof}`
First, suppose $\psi$ is an embedding with closed image and let $p \in M$. Let $g:M\to \mathbb{R}$ be $C^\infty$. Let $U$ be a cubic-centered coordinate neighborhood of $\psi(p)$ for which $\psi(M)\cap U$ is a single slice. Then define $\widetilde{g}_p$ to be the composition of the projection of $U$ onto the slice followed by $g$. The collection of open sets $U_p$ for each $p \in M$ satisfying this property together with $N -\psi(M)$ forms an open cover of $N$. Then by [[Basic Manifold Theory - Warner#^96b8fc]] we have a partition of unity $\{\varphi_j\}_{j\geq 1}$ subordinate to this cover. Take the subsequence of $\varphi_j$ such that $\text{supp}\,\varphi_j\cap \psi(M) \neq \emptyset$. For each such $j$ we choose a point $p_j$ such that $\text{supp}\,\varphi_j$ is contained in $U_{p_j}$. Then $f = \sum_{j\geq 1}\varphi_j\widetilde{g}_{p_j}$ is a $C^\infty$ function on $N$, and $f\circ \psi = g$. 

On the other hand, if the extensions always exist let $(U,\varphi)$ be a coordinate chart on $M$ with coordinate functions $x_1,...,x_d$. Then there exist $y_1,...,y_d$ $C^\infty$ functions on $N$ such that $y_i\circ \psi = x_i$. Let $\tau$ be the map with coordinate functions $y_1,...,y_d$. Then we have that $\varphi^{-1}\circ \tau \circ \psi = 1_U$, and so $\psi$'s inverse is locally continuous, and hence continuous. Thus $\psi$ is a homeomorphism, and hence an embedding. Since $\psi$ is an embedding we can find a coordinate system such that $\psi(M)\cap V$ is a single slice of $V$, and hence closed. **TBC**
`\end{proof}`

### Implicit Function Theorems

An equivalent formulation of the inverse function theorem on $\mathbb{R}^n$ is known as the Implicit Function Theorem which we investigate in this section. This theorem will be incredibly useful for constructing new manifolds as solution sets to systems of differentiable equations.

>[!thm] Implicit Function Theorem
>Let $U \subseteq \mathbb{R}^{c-d}\times \mathbb{R}^d$ be open and let $f:U\to \mathbb{R}^d$ be $C^{k}$ ($k\geq 1$). Denoting points of $\mathbb{R}^{c-d}\times \mathbb{R}^d$ by pairs of vectors $(r,s)$, suppose that at a point $(r_0,s_0) \in U$ we have 
>$$f(r_0,s_0) = 0$$
>and the jacobian of $f\circ \iota_{r_0}$ is non-singular at $s_0$, where $\iota_{r_0}:\mathbb{R}^d\to \mathbb{R}^{c-d}\times \mathbb{R}^d$ is the inclusion given by inputting $r_0$ in the first $c-d$ coordinates. Then there exists an open neighborhood $V$ of $r_0$ in $\mathbb{R}^{c-d}$ and an open neighborhood $W$ of $s_0$ in $\mathbb{R}^d$ such that $V\times W \subseteq U$ and there exists a $C^k$ mapping $g:V\to W$ such that 
>$$\{(p,q)\in V\times W\mid q=g(p)\} = f^{-1}(\{0\})\cap V\times W$$

`\begin{proof}`
First define a function $G:U\to \mathbb{R}^{c-d}\times \mathbb{R}^d$ by $\langle \pi_{c-d},f\rangle$. Then $G$ is a $C^k$ map with non-singular differential at $(r_0,s_0)$. Thus by the [[Basic Manifold Theory - Warner#^e4bd5b]] we have an open subset $U' \subseteq U$ such that $G\vert_{U'}$ is a $C^k$ diffeomorphism onto its image. Let $H:G(U')\to U'$ be the inverse to $G\vert_{U'}$. Let $V = \{x \in \mathbb{R}^{c-d}\mid (x,0) \in G(U')\}$ which is open in $\mathbb{R}^{c-d}$ since $G(U')$ is open. Note that $H\vert_V(x,0) = (x,y_x)$ since $G(x,y_x) = (x,f(x,y_x))$. Further, it follows that composing with the projection $\pi_d$ we obtain a $C^k$ morphism $g:V\to g(V)$ where $g(x)$ is the unique $y_x \in \mathbb{R}^d\cap \pi_d(U')$ such that $f(x,y_x) = 0$.

In addition to these properties we have that $Dg(r_0) = -D(f\circ \iota_{r_0})(s_0)^{-1}D(f\circ \iota_{s_0})(r_0)$. 
`\end{proof}`

We can now upgrade this result to the setting of manifolds.

>[!thm] Implicit Function Theorem for Manifolds
>Suppose $\psi:M\to N$ is a $C^\infty$ and that $p \in N$ such that $P = \psi^{-1}(\{p\})$ is non-empty. If $d\psi_q:T_qM\to T_pN$ is surjective for all $q \in P$, then $P$ has a unique manifold structure such that $(P,i)$ is a submanifold of $M$, where $i$ is the inclusion map. Moreover, $i:P\to M$ is an embedding, and the dimension of $P$ is $\dim M - \dim N$.

^c66ad5

`\begin{proof}`
We will not prove it here (**TODO**), but if in the subspace topology $P$ has a differentiable manifold structure making it a submanifold of $M$ via the inclusion, then this structure is unique. Thus, it suffices to prove that if $p \in P$, then there exists a coordinate system on a neighborhood of $p$ in $M$ such that the intersection of this neighborhood with $P$ is a single slice of the correct dimension.

Let $x_1,...,x_d$ be a coordinate system centered at $p \in N$. Since $d\psi_p:T_qM\to T_pN$ is surjective, [[Basic Manifold Theory - Warner#^b13b17]] implies that the collection $y_i = x_i\circ \psi$ form part of a coordinate system about $q \in M$. Completing to a coordinate system $y_1,...,y_c$ on a neighborhood $U$ of $p$ we then have that $P\cap U$ is the slice of this coordinate system given by $y_1,...,y_d = 0$. 
`\end{proof}`

This theorem has a generalization, under suitable hypotheses, to higher dimensional submanifolds (the above result can be thought of as a special case for $0$-dimensional submanifolds, i.e. points).

>[!thm] Higher Implicit Function Theorem for Manifolds
>Let $\psi:M\to N$ be $C^\infty$ and that $(O,\varphi)$ is a submanifold of $N$. If for all $p \in \psi^{-1}(\varphi(O))$ we have that 
>$$T_{\psi(p)}N=d\psi(T_pM)+d\varphi(T_{\varphi^{-1}(\psi(p))}O)$$
>(i.e. the "submanifolds" $\psi(M)$ and $\varphi(O)$ are **transverse** in $N$) then if $P = \psi^{-1}(\varphi(O))$ is non-empty, $P$ can be given a manifold structure such that $(P,i)$ is a submanifold of $M$, where $i$ is the inclusion map, and $$\dim M - \dim P = \dim N - \dim O$$
>Moreover, if $(O,\varphi)$ is an embedded submanifold, then so is $(P,i)$, and in this case we have a unique manifold structure on $P$ such that $(P,i)$ is a submanifold of $M$.

`\begin{proof}`
We will prove the Theorem by reducing, at least locally, to the case of [[Basic Manifold Theory - Warner#^c66ad5]]. Let $p \in O$. By [[Basic Manifold Theory - Warner#^ec5cec]] we can pick a neighborhod $W$ of $p$ and a centered coordinate system $(V,\tau)$ with coordinate functions $x_1,...,x_d$ about $\varphi(p)$ such that $\varphi(W)$ is the slice 
$$x_{c+j} = 0,\,\,\,\,j=1,\dots,d-c$$
Let $\pi:\mathbb{R}^d\to \mathbb{R}^{d-c}$ be the projection onto the last $d-c$ coordinates. Then $\pi\circ \tau(\varphi(W)) = \{0\}$. Let $U = \psi^{-1}(V)$ and let $\psi_1=\pi\circ \tau\circ \psi\vert_U:U\to \mathbb{R}^{d-c}$.

It follows that $\psi_1^{-1}(\{0\}) = \psi^{-1}(\varphi(W))$. For each $q \in \psi_1^{-1}(\{0\})$, $d\psi_1\vert_{T_qM}$ is a surjection since $d(\pi\circ \tau)\vert_{T_{\psi(q)}N}$ is surjective, and so by the transversality assumption
$$d(\pi\circ \tau)(T_{\psi(q)}N) = d\psi_1(T_qM)+\{0\}$$
By [[Basic Manifold Theory - Warner#^c66ad5]] $\psi^{-1}(\varphi(W))$ has a unique manifold structure such that it paired with the inclusion is a submanifold of $M$. Further, in this manifold structure $\psi^{-1}(\varphi(W))$ has the subspace topology and has dimension $\dim M - (\dim N-\dim O)$. Cover $O$ by a countable collection $W_i,i\geq 1$, of such sets, which is possible since it has a countable base. Then
$$P = \bigcup_{i\geq 1}\psi^{-1}(\varphi(W_i))$$
If $i \neq j$, the submanifolds $\psi^{-1}(\varphi(W_i))$ and $\psi^{-1}(\varphi(W_j))$ intersect in open subsets of each other. Thus, the union of the various topologies on the $\psi^{-1}(\varphi(W_i))$ are compatible, and hence induce a topology on $P$ which is locally Euclidean of dimension $\dim M-\dim N+\dim O$, and further $P$ is second countable since it is a countable union over second countable spaces. 

The manifold structures of the $\psi^{-1}(\varphi(W_i))$ are compatible on overlaps because of the uniqueness of the manifold structure. Thus, together the collection of coordinate systems on $P$ containing coordinate systems on the $\psi^{-1}(\varphi(W_i))$ generates a differentiable structure on $P$ such that $(P,i)$ is a submanifold of $M$. 

If $(O,\varphi)$ is an embedding, the coordinate neighborhood $V$ can be chosen small enough that $\varphi(O)\cap V$ consists only of the single slice $\varphi(W)$, and so $U\cap P = \psi^{-1}(\varphi(W))$. In this case $P$ has the subspace topology, and so $(P,i)$ is an embedding.
`\end{proof}`

>[!example]
>Consider the function $f(p) = \sum_{i=1}^dr_i(p)^2$ on $\mathbb{R}^d$. Then $df_p = \sum_{i=1}^d2r_i(p)(dr_i)_p$, which is surjective except at the origin. Hence, by [[Basic Manifold Theory - Warner#^c66ad5]] for $r > 0$ we have that $f^{-1}(\{r^2\})$, which is the $(d-1)$-sphere of radius $r$, is a submanifold of $\mathbb{R}^d$.

>[!example]
>Define $\psi:\mathsf{Gl}(d,\mathbb{R})\to \mathsf{Sym}(d,\mathbb{R})$ by $\psi(A) = AA^t$, which is a smooth morphism. Then the orthogonal group, $O(d) = \psi^{-1}(\{I\})$, where $I$ is the $d\times d$ identity matrix, has a unique manifold structure such that it is a submanifold of $\mathsf{Gl}(d,\mathbb{R}))$, and that in this structure the inclusion is and embedding and $O(d)$ has dimension $\frac{1}{2}d(d-1)$. Indeed, this follows from [[Basic Manifold Theory - Warner#^c66ad5]] and the fact that $d\psi_I$ is surjective, which follows since $\delta\psi_I$ is injective.


## Vector Fields

In physics and applications of PDEs on manifolds an important tool and object of study is that of vector fields, or sections of vector bundles, which are often studies in algebraic settings such as with quasi-coherent sheaves in algebraic geometry. A common example of vector bundles given locally are those defined over curves.

>[!def] Smooth Curve
>We say that a map $\sigma:[a,b]\to M$ is a **smooth curve in $M$** if $\sigma$ extends to a $C^\infty$ mapping of $(a-\epsilon,b+\epsilon)$ into $M$ for some $\epsilon > 0$. The curve $\sigma$ is said to be **piecewise smooth** if there exists a partition $a=\alpha_0<\alpha_1<\cdots<\alpha_n=b$ such that $\sigma\vert_{[\alpha_i,\alpha_{i+1}]}$ is smooth for each $i = 0,...,n-1$. If $\sigma$ is a smooth curve then its tangent vector
>$$\dot{\sigma}(t) := d\sigma\left(\frac{d}{dr}\vert_t\right) \in T_{\sigma(t)}M$$
>is well-defined for each $t \in [a,b]$.

>[!def] Vector Field
>A **vector field** $X$ along a curve $\sigma:[a,b]\to M$ is a mapping $X:[a,b]\to TM$ which lifts $\sigma$, that is $\pi\circ X = \sigma$. A vector field $X$ is called a smooth vector field if it is a $C^\infty$ map of smooth manifolds (note we must extend $[a,b]$ to the infinitesimal open neighborhood around it so it *is* a manifold). 
>
>A **vector field $X$ on an open set $U$ in $M$** is a lifting of $U$ into $TM$, that is a map $X:U\to TM$ such that $\pi\circ X=$ the inclusion of $U$ into $M$.

The set of smooth vector fields ranging over open sets forms a sheaf of abelian groups on $M$, and further this sheaf of abelian groups is in fact a $\mathcal{O}_M$-module. Indeed, if $f:U\to \mathbb{R}$ is $C^\infty$ and $X:U\to TM$ is $C^\infty$, then $fX:U\to TM$ is the vector field given at a point $p \in U$ by $f(p)X(p)$.

On the other hand, we can define $X(f):U\to \mathbb{R}$ which is the $C^\infty$ mapping given by $X(f)_p := X_p(f)$. Let $\mathfrak{X}_M$ denote the sheaf of smooth vector fields on the manifold $M$. Then we have that $\mathfrak{X}_M$ is a $\mathcal{O}_M$-module and further that we have an action
$$\mathfrak{X}_M\otimes_{\underline{\mathbb{R}}}\mathcal{O}_M\to \mathcal{O}_M$$

>[!proposition] Smooth Vector Fields
>Let $X$ be a vector field on $M$. Then the following are equivalent:
>1. $X$ is $C^\infty$
>2. If $(U,x_1,...,x_d)$ is a coordinate system on $M$, and if $\{a_i\}$ is the collection of functions on $U$ defined such that $X\vert_U = \sum_{i=1}^da_i\frac{\partial}{\partial x_i}$, then the $a_i$ are smooth.
>3. Whenever $V$ is open in $M$ and $f \in C^\infty(V)$, then $X(f) \in C^\infty(V)$.

^6a5199

`\begin{proof}`
Suppose **(1)** and let $(U,x_1,...,x_d)$ be a coordinate system on $M$. Then let $(W,y_1,...,y_{2d})$ be the associated coordinate system on $TM$, with coordinate map $\psi$. Then
$$\psi \circ X(p) = (x_1(p),\dots,x_d(p),a_1(p),\dots,a_d(p))$$
Thus, since $X$ is $C^\infty$ so is $\psi \circ X$, and so taking projections we conclude that the $a_i(p)$ are smooth, proving **(2)**. Further, since these coordinate systems generate the differentiable structure on $TM$, it follows that **(2)** also implies **(1)**.

 Let $V$ be open and $f:V\to \mathbb{R}$ smooth. To show $X(f)$ is smooth let $(U,x_1,...,x_d)$ be a chart around a point $p \in V$ with coordinate map $\varphi$. We can write $X\vert_U = \sum_{i=1}^da_i\frac{\partial}{\partial x_i}$ as the restriction. Then $X(f)\vert_U = \sum_{i=1}^da_i\frac{\partial f}{\partial x_i}$, which is a sum and product of smooth functions, and hence smooth. As this holds for all coordinate charts around points in $V$, it follows that $X(f)$ is smooth. Further, taking $f$ to be the coordinate functions $x_i$ we see that **(3)** is equivalent to **(2)**.
 `\end{proof}`

One of the most powerful tools for study vector fields and vector bundles comes from the Lie Bracket.

>[!def] Lie Bracket
>If $X$ and $Y$ are smooth vector fields on $M$, we define a vector field $[X,Y]$ called the **Lie bracket** of $X$ and $Y$ by setting
>$$[X,Y]_p(f) = X_p(Y(f))-Y_p(X(f))$$

This Lie bracket structure turns $\mathfrak{X}_M$ into a Lie $\mathcal{O}_M$-algebra.

>[!proposition] Properties of Lie Bracket
>1. $[X,Y]$ is a smooth vector field on $M$
>2. If $f,g \in C^\infty(M)$, then $[fX,gY] = fg[X,Y]+(f\cdot X(g))Y-(g\cdot Y(f))X$
>3. $[X,Y]=-[Y,X]$
>4. For all smooth vector fields $X,Y,Z$ on $M$, $$[[X,Y],Z] + [[Y,Z],X] + [[Z,X],Y] = 0$$

`\begin{proof}`
For **(1)** observe that for a smooth function $f$, $[X,Y](f) = X(Y(f)) - Y(X(f))$ is a difference of smooth functions, and so by [[Basic Manifold Theory - Warner#^6a5199]] the Lie bracket $[X,Y]$ is a smooth manifold.

For **(2)** let $(U,x_1,...,x_d)$ be a coordinate chart such that $X\vert_U = \sum_{i=1}^da_i\partial_{x_i}$ and $Y\vert_U = \sum_{i=1}^db_i\partial_{x_i}$. Then we have that 
$$[X,Y]\vert_U = \sum_{i=1}^d\left( \sum_{j=1}^d(a_j\partial_{x_j}(b_i)-b_j\partial_{x_j}(a_i)) \right)\frac{\partial}{\partial x_i}$$
Note that in the case of the local basis $\partial_{x_i}$, which by abuse of notation we write as $x_i$, $[x_i,x_j] = 0$. Then at the $i$th coordinate we have that $[fX,gY]\vert_U$ is given by
$$\sum_{j=1}^d(fa_j\partial_{x_j}(gb_i)-gb_j\partial_{x_j}(fa_i)) = \sum_{i=1}^d\left(fg(a_j\partial_{x_j}(b_i)-b_j\partial_{x_j}(a_i))+fa_j\partial_{x_j}(g)b_i+gb_j\partial_{x_j}(f)a_i\right)$$
The left-most term is the coefficient for the $i$th coordinate of $fg[X,Y]$, the second is $(f\cdot X(g))Y$, and the third is $(g\cdot Y(f))X$. In the case of coordinate functions we have that $[f_ix_i,f_jx_j] = f_ix_i(f_j)x_j-f_jx_j(f_i)x_i$.

**(3)** is immediate, and so it remains to show **(4)**. Note that the Lie bracket is bilinear, so it suffices to prove the identity for $f_ix_i$ where the $x_i$ are part of a coordinate chart $(U,x_1,...,x_d)$ and the $f_i$ are smooth functions on $U$. Then using **(2)** we can observe that
$$\begin{align*}[[f_ix_i,f_jx_j],f_kx_k] &= [(f_ix_i(f_j)x_j-f_jx_j(f_i)x_i),f_kx_k]  \\
&= f_ix_i(f_j)x_j(f_k)x_k-f_kx_k(f_ix_i(f_j))x_j \\
&\quad -f_jx_j(f_i)x_i(f_k)x_k+f_kx_k(f_jx_j(f_i))x_i \\
&= f_ix_i(f_j)x_j(f_k)x_k-f_kx_k(f_i)x_i(f_j)x_j-f_if_kx_k(x_i(f_j))x_j \\
&\quad -f_jx_j(f_i)x_i(f_k)x_k+f_kx_k(f_j)x_j(f_i)x_i+f_jf_kx_k(x_j(f_i))x_i \\
\end{align*}
$$
On the other hand we have 
$$\begin{align*}[[f_jx_j,f_kx_k],f_ix_i] &= f_jx_j(f_k)x_k(f_i)x_i-f_ix_i(f_j)x_j(f_k)x_k-f_jf_ix_i(x_j(f_k))x_k \\
&\quad -f_kx_k(f_j)x_j(f_i)x_i+f_ix_i(f_k)x_k(f_j)x_j+f_kf_ix_i(x_k(f_j))x_j \\
\end{align*}$$
and $$\begin{align*}[[f_kx_k,f_ix_i],f_jx_j] &= f_kx_k(f_i)x_i(f_j)x_j-f_jx_j(f_k)x_k(f_i)x_i-f_kf_jx_j(x_k(f_i))x_i \\
&\quad -f_ix_i(f_k)x_k(f_j)x_j+f_jx_j(f_i)x_i(f_k)x_k+f_if_jx_j(x_i(f_k))x_k \\
\end{align*}$$
Adding these expressions together we see that all terms cancel, where we use the fact that since our functions are smooth the differentials $x_i$ commute.
`\end{proof}`

Just like how we can define vector fields over curves, we can consider when a vector field on an open set restricts to a vector field given by some curve.

>[!def] Integral Curve
>Let $X$ be a smooth vector field on $M$. A smooth curve $\sigma$ in $M$ is a **integral curve** of $X$ if $$\dot{\sigma}(t) = X_{\sigma(t)}$$
>for each $t$ in the domain of $\sigma$.

If $X$ is a $C^\infty$ vector field and $p \in M$ is a point in the domain of $X$, an important question is where there exists an integral curve for $X$ through $p$, and whether such a curve is unique (possibly as a germ)?

Recall that a curve $\gamma:(a,b)\to M$ is an integral curve of the vector field $X$ if and only if 
$$d\gamma\left(\frac{d}{dr}\Bigg\vert_t\right) = X_{\gamma(t)}$$
Suppose $0 \in (a,b)$ and $\gamma(0) = p$. Let $(U,\varphi)$ be a coordinate system about $p$ with coordinate functions $x_1,...,x_d$. Then $X\vert_U = \sum_{i=1}^df_i\frac{\partial}{\partial x_i}$ for some $f_i:U\to \mathbb{R}$ smooth. On the other hand, we have that
$$d\gamma\left(\frac{d}{dr}\Bigg\vert_t\right) = \sum_{i=1}^d\frac{d(x_i\circ \gamma)}{dr}\Bigg\vert_t\frac{\partial}{\partial x_i}\Bigg\vert_{(\gamma(t))}$$
Thus, $\gamma$ is an integral curve of $X$ on $\gamma^{-1}(U)$ if and only if
$$\frac{d\gamma_i}{dr}\Bigg\vert_t = f_i\circ \gamma(t) = f_i\circ \varphi^{-1}(\gamma_1(t),\dots,\gamma_d(t))$$
where $\gamma_i = x_i\circ \gamma$. This is a system of first order ordinary differential equations for which there exists fundamental existence and uniqueness theorems. Translating this into the language of manifolds we have the following result.


>[!thm] Existence and Uniqueness of Integral Curves
>Let $X$ be a $C^\infty$ vector field on a differentiable manifold $M$. For each $p \in M$ there exists $a(p),b(p) \in \mathbb{R}\cup \{\pm\infty\}$, and a smooth curve
>$$\gamma_p:(a(p),b(p))\to M$$
>such that 
>1. $0 \in (a(p),b(p))$ and $\gamma_p(0) = p$.
>2. $\gamma_p$ is an integral curve of $X$
>3. If $\mu:(c,d)\to M$ is a smooth curve satisfying conditions (1) and (2), then $(c,d) \subseteq (a(p),b(p))$ and $\mu = \gamma_p\vert_{(c,d)}$
>4. For each $p \in M$, there exists an open neighborhood $V$ of $p$ and an $\epsilon > 0$ such that the map $$(t,p)\mapsto X_t(p)$$
>is defined and is $C^\infty$ from $(-\epsilon,\epsilon)\times V$ into $M$
>5. $\mathscr{D}_t$ is open for each $t$
>6. $\bigcup_{t > 0}\mathscr{D}_t = M$
>7. $X_t:\mathscr{D}_t\to \mathscr{D}_{-t}$ is a diffeomorphism with inverse $X_{-t}$
>8. Let $s$ and $t$ be real numbers. Then the domain of $X_s\circ X_t$ is contained in but generally not equal to $\mathscr{D}_{s+t}$. However, the domain of $X_s\circ X_t$ is $\mathscr{D}_{s+t}$ in the case in which $s$ and $t$ both have the same sign. Moreover, on the domain of $X_s\circ X_t$, we have $$X_s\circ X_t = X_{s+t}$$

^58ba81

where 

>[!def]
>For each $t \in \mathbb{R}$, we define a transformation $X_t$ with domain
>$$\mathscr{D}_t = \{p \in M\mid t \in (a(p),b(p))\}$$
>by setting $X_t(p) = \gamma_p(t)$

`\begin{proof}[Proof of Thm.]`
Let $(a(p),b(p))$ be the union of all open intervals which contain the origin and which are domains of integral curves of $X$ satisfying the intiial condition that the origin maps to $p$. That $(a(p),b(p)) \neq \emptyset$ follows from an application of the fundamental existence theorem for first order ODEs. Now, if $\alpha$ and $\beta$ are integral curves of $X$ with domains the open intervals $A$ and $B$, with $A\cap B \neq \emptyset$, and if $\alpha$ and $\beta$ have the same initial conditions $\alpha(t_0) = \beta(t_0)$ at some point $t_0 \in A\cap B$, then the subset of $A\cap B$ on which $\alpha$ and $\beta$ agree is non-empty, open by the uniqueness theorem for first order ODEs, and closed by continuity; Hence, this subset is equal to $A\cap B$ by connectedness o $A\cap B$. It follows that we can glue these integral curves to obtain a unique curve $\gamma_p$ defined on $(a(p),b(p))$ and satisfying parts **(1)-(3)**.

The existence in **(4)** follows from the Euclidean case **TODO**. The map being smooth follows from a result on differentiability of solutions with respect to their initial values **TODO**.

For part **(8)** let $t \in (a(p),b(p))$. Then $s\mapsto \gamma_p(t+s)$ is an integral curve of $X$ with initial condition $0 \mapsto \gamma_p(t)$, and with maximal domain $(a(p)-t,b(p)-t)$. It follows from part **(3)** that $$(a(p)-t,b(p)-t) = (a(\gamma_p(t)),b(\gamma_p(t)))$$
and for $s$ in this interval
$$\gamma_{\gamma_p(t)}(s) = \gamma_p(t+s)$$
Now, let $p$ belong to the domain of $X_s\circ X_t$. Then $t \in (a(p),b(p))$ and $s \in (a(\gamma_p(t),b(\gamma_p(t))))$, so $s+t \in (a(p),b(p))$. Thus $p \in \mathscr{D}_{s+t}$, and and so $X_s\circ X_t = X_{s+t}$ follows from the above equation for $\gamma$.

For a counterexample for equality of the domain observe that the vector field $\frac{\partial}{\partial r_1}$ on $\mathbb{R}^2-\{0\}$ with $s = -1$ and $t = 1$ has $\mathscr{D}_0 = \mathbb{R}^2-\{0\}$, but $\mathscr{D}_1 = \mathbb{R}^2-(-1,0]$.

However, if $s$ and $t$ have the same sign and if $p \in \mathscr{D}_{s+t}$, then $s+t \in (a(p),b(p))$, and it follows that $t \in (a(p),b(p))$ and by our description of the interval above $s \in (a(\gamma_p(t)),b(\gamma_p(t)))$, and so $p$ is in the domain of $X_s\circ X_t$.

If $t = 0$ parts **(5)** and **(7)** are immediate. Otherwise, for $t > 0$ let $p \in \mathscr{D}_t$. From **(4)** and the compactness of $[0,t]$ there exists a neighborhood $W$ of $\gamma_p([0,t])$ and an $\epsilon > 0$ such that the map $(t,p)\mapsto X_t(p)$ is defined and $C^\infty$ on $(-\epsilon,\epsilon)\times W$. Choose $n \in \mathbb{Z}_{> 0}$ large enough so that $t/n \in (-\epsilon,\epsilon)$. Let $\alpha_1 = X_{t/n}\vert_W$, and let $W_1 = \alpha_1^{-1}(W)$. Then for $i = 2,...,n$ we inductively define $\alpha_i = X_{t/n}\vert_{W_{i-1}}$ and $W_i = \alpha_i^{-1}(W_{i-1})$, so $\alpha_i$ is a $C^\infty$ map on the open set $W_{i-1}\subseteq W$. IT follows that $W_n$ is an open subset of $W$ and that $W_n$ contains $p$, and that by **(8)** 
$$\alpha_1\circ \alpha_2\circ \cdots \circ \alpha_n\vert_{W_n} = X_t\vert_{W_n}$$
Consequently, $W_n \subseteq \mathscr{D}_t$, and so $\mathscr{D}_t$ is open.

Finally, $X_t$ is injective as a map from $\mathscr{D}_t$ onto $\mathscr{D}_{-t}$, with inverse $X_{-t}$. That $X_t$ is $C^\infty$ follows from the above equation which shows that $X_t$ is locally a composite of $C^\infty$ maps. Hence $X_t$ is a diffeomorphism from $\mathscr{D}_t$ to $\mathscr{D}_{-t}$, finishing the proof.
`\end{proof}`

Smooth vector fields $X$ for which $\mathscr{D}_t = M$ for all $t$ (i.e. integral curves exist at all times starting from any point) are of special interest.

>[!def] Complete Vector Fields
>A smooth vector field $X$ on $M$ is said to be **complete** if $\mathscr{D}_t = M$ for all $t \in \mathbb{R}$. In this case the $X_t$ form a group of diffeomorphisms on $M$, isomorphic to the group $\mathbb{R}$ under addition, called the **1-parameter group** of $X$.
>
>Otherwise, we refer to the collection of diffeomorphisms $X_t$ as the **local 1-parameter group** of $X$, although note this is not actually a group since the domains of the $X_t$ vary with $t$.

When $M$ is compact all smooth vector fields complete, so in one sense completeness of smooth vector fields is related to the compactness of a manifold.

>[!proposition] Complete Vector Fields on Compact Manifold
>Let $X$ be a  smooth vector field on the manifold $M$. If $M$ is compact then $X$ is complete.

`\begin{proof}`
Recall that $X$ being complete is equivalent to the integral curve $\gamma_p:(a(p),b(p))\to M$ for $X$ at $p \in M$ having $(a(p),b(p)) = (-\infty,\infty)$. Recall that from [[Basic Manifold Theory - Warner#^58ba81]] we have that the $\mathscr{D}_t$ are open, and $M = \bigcup_{t > 0}\mathscr{D}_t$. Since $M$ is compact there exist $t_1,...,t_n > 0$ such that $\mathscr{D}_{t_1}\cup\cdots \cup \mathscr{D}_{t_n} = M$, and we can order them such that $t_1 < t_2 < \cdots < t_n$. But then this implies that $\mathscr{D}_{t_1} = M$. 

Let $t \in [0,\infty]$ be the supremum of such $t_1$ and towards a contradiction suppose $t < \infty$ is a finite real number. For every $p \in M$ we have $t \in (a(p),b(p))$, so there exists $t < t_p < b(p)$, and so $p \in \mathscr{D}_{t_p}$. Thus, it follows that 
$$\mathscr{D}_t = \bigcup_{t' > t}\mathscr{D}_{t'}$$
But $\mathscr{D}_t = M$ is compact, so by the same argument as above we must have that $\mathscr{D}_t = \mathscr{D}_{t'}$ for some $t' > t$, contrary to assumption. Therefore we must have that $\mathscr{D}_t = M$ for all $t > 0$, and hence all $t \in \mathbb{R}$, so $X$ is complete.
`\end{proof}`

We now consider when we can extend a vector field along a smooth map of manifolds.

>[!def] Local Smooth Extensions of Vector Fields
>Let $\psi:M\to N$ be $C^{\infty}$. A smooth vector field $X$ along $\psi$, i.e. $X \in C^{\infty}(M,T(N))$ and $\pi\circ X = \psi$, is said to have **local smooth extensions in $N$** if for any $p \in M$ there exists a neighborhood $U$ of $p$ and a neighborhood $V$ of $\psi(p)$ such that $\psi(U) \subseteq V$ and there exists a smooth vector field $\widetilde{X}$ on $V$ such that 
>$$\widetilde{X}\circ \psi\vert_U = X\vert_U$$

>[!proposition] Local Extensions Exist along Immersions
>Let $X$ be a smooth vector field along an immersion $\psi:M\to N$. Then $X$ has a local smooth extension in $N$.

`\begin{proof}`
Let $p \in M$. Since $\psi$ is an immersion, [[Basic Manifold Theory - Warner#^ec5cec]] we have a coordinate chart $(V,\varphi)$ about $\psi(p)$ and a coordinate chart $(U,\tau)$ about $p$ such that $\psi(U) \subseteq V$, $\psi\vert_U$ is injective, and if we write $\varphi$ as $x_1,...,x_c$, then
$$\psi(U) = \{q\in V\,:\,x_{d+1}(q)=\cdots = x_c(q)=0\}$$where $N$ is $c$ dimensional and $M$ is $d$ dimensional, $0 \leq d \leq c$. Now, we can write $X\vert_U$ as
$$X\vert_U = \sum_{i=1}^cf_i\partial_{x_i}\vert_{\psi}$$
for some smooth functions $f_i$ on $U$. We define $\widetilde{X}\vert_V = \sum_{i=1}^c\widetilde{f}_i\partial_{x_i}$, where $\widetilde{f}_i:V\to \mathbb{R}$ is defined by $\widetilde{f}_i = f_i\circ \tau^{-1}\circ \pi_d \circ \varphi$ which is effectively extending $f_i$ by being "constant along the directions not in $\varphi(U)$". Then for any $q \in U$, $$\widetilde{X}\circ \psi(\tau(x)) = \sum_{i=1}^cf_i(\tau^{-1}(\pi_d(\varphi(\psi(q)))))\partial_{x_i}\vert_{\psi(q)} = \sum_{i=1}^cf_i(q)\partial_{x_i}\vert_{\psi(q)} = X(q)$$
as desired.
`\end{proof}`
In general such local extensions do not exist. For example, if $\alpha:\mathbb{R}\to \mathbb{R}$ is the curve given by $\alpha(t) = t^3$, so $\alpha = r^3$ where $r$ is the standard coordinate function on $\mathbb{R}$, then if $X$ is the smooth vector field
$$X(t) =\dot{\alpha}(t) = d\alpha\left(\frac{d}{dr}\Bigg\vert_t\right)$$
since $\alpha$ is a homeomorphism we have an induced vector field $\widetilde{X}$ on $\mathbb{R}$ such that $\widetilde{X}\circ \alpha = X$. However, $\widetilde{X}$ is *not smooth* since if $u = t^3$, then
$$\widetilde{X}_u = X(t) = \frac{d\alpha}{dr}\Bigg\vert_t\frac{d}{dr}\Bigg\vert_{\alpha(t)} = 3u^{2/3}\frac{d}{dr}\Bigg\vert_u$$
where $u^{2/3}$ is not differentiable at $0$.


Now we show that smooth vector fields are locally given by lines.

>[!proposition] Smooth Vector Field is Locally Linear
>Let $p \in M$ and let $X$ be a smooth vector field on $M$ such that $X(p) \neq 0$. Then there exists a coordinate system $(U,x_1,...,x_d)$ about $p$ such that
>$$X\vert_U = \frac{\partial}{\partial x_1}\vert_U$$

`\begin{proof}`
Choose a coordinate system $(V,\tau)$ centered about $p$ with coordinate functions $y_1,...,y_d$ such that $X_p = \frac{\partial}{\partial y_1}\vert_p$ (i.e. we extend $X_p \neq 0$ to a basis of the tangent space at $p$). By [[Basic Manifold Theory - Warner#^58ba81]] part **(4)** we have a neighborhood $V$ of $p$ and an $\epsilon > 0$ such that $X_{-}(-)$ is defined and smooth from $(-\epsilon,\epsilon)\times V\to M$. In particular, we have a neighborhood $W$ of the origin in $\mathbb{R}^{d-1}$ such that $\sigma(t,a_2,...,a_d) = X_t(\tau^{-1}(0,a_2,...,a_d))$ is well-defined and smooth from $(-\epsilon,\epsilon)\times W\to M$. 

Observe that 
$$d\sigma\left(\frac{\partial}{\partial r_1}\Bigg\vert_0\right) = X_p = \frac{\partial}{\partial y_1}\Bigg\vert_p$$
and for $i \geq 2$,
$$d\sigma\left( \frac{\partial}{\partial r_i}\Bigg\vert_0 \right)(f) = \frac{\partial (f\circ \sigma)}{\partial r_i}\Bigg\vert_0 = \lim\limits_{a_i\to 0}\frac{f(\tau^{-1}(0,\dots,0,a_i,0,\dots,0))-f(p)}{a_i} =\frac{\partial f}{\partial y_i}\Bigg\vert_p$$
It follows that $\sigma$ is non-singular at the origin, and so by [[Basic Manifold Theory - Warner#^b914f8]] we have that $\sigma^{-1}$ gives a coordinate map on some open neighborhood $U$ of $p$. If $x_1,...,x_d$ are its coordinate functions, then since
$$d\sigma\left(\frac{\partial}{\partial r_1}\Bigg\vert_{(t,a_2,\dots,a_n)}\right) = X_{\sigma(t,a_2,\dots,a_n)}$$
it follows that $X\vert_U = \frac{\partial}{\partial x_1}\big\vert_U$.
`\end{proof}`

>[!def] Smoothly Related Vector Fields
>Let $\varphi:M\to N$ be a smooth map of manifolds. If $X$ is a smooth vector field on $M$ and $Y$ is a smooth vector field on $N$, the we say $X$ and $Y$ are **$\varphi$-related** if $d\varphi \circ X = Y\circ \varphi$.


>[!proposition] Lie Braket of Related Vector Fields
>Let $\varphi:M\to N$ be smooth, and let $X,X'$ be smooth vector fields on $M$ and $Y,Y'$ be smooth vector fields on $N$. Then if $X\sim_\varphi Y$ and $X'\sim_\varphi Y'$, then $[X,X']\sim_\varphi [Y,Y']$.

`\begin{proof}`
Let $p \in M$ and $f \in C^{\infty}(N)$. Then observe that
$$
\begin{align*}
d\varphi([X,X']_p)(f) &= [X,X']_p(f\circ \varphi) \\
&= X_p(X'(f\circ \varphi))-X'_p(X(f\circ \varphi)) \\
&= X_p((d\varphi\circ X')(f))-X_p'((d\varphi\circ X)(f)) \\
&= X_p(Y'(f)\circ \varphi) - X_p'(Y(f)\circ \varphi) \\
&= (d\varphi\circ X_p)(Y'(f))-(d\varphi\circ X_p')(Y(f)) \\
&= Y_{\varphi(p)}(Y'(f))-Y'_{\varphi(p)}(Y(f)) \\
&= [Y,Y']_{\varphi(p)}(f)
\end{align*}
$$
which completes the proof.
`\end{proof}`

## Distributions and Frobenius

In this section we use the theory we have now developed to understand certain concepts which have important uses in areas such as fluid dynamics and electromagnetism.

>[!def] Distribution
>Let $m$ be an integer and $1 \leq m \leq n$. An **$m$-dimensional distribution** $\mathscr{D}$ on an $n$-dimensional manifold $M$ is a *choice* of an $m$-dimensional subspace $\mathscr{D}(p)$ of $M_p$ for each $p \in M$. We say $\mathscr{D}$ is **smooth** if for each $p \in M$, there exists a neighborhood $U$ of $p$ and smooth vector fields $X_1,...,X_m$ on $U$ which span $\mathscr{D}$ at each point of $U$.
>
>A vector field $X$ on $M$ is said to **belong to** the distribution $\mathscr{D}$ if $X_p \in \mathscr{D}(p)$ for each $p \in M$. A smooth distribution $\mathscr{D}$ is called **involutive** or **completely integrable** if $[X,Y] \in \mathscr{D}$ whenever $X$ and $Y$ are smooth vector fields lying in $\mathscr{D}$.

>[!def] Integral Manifold
>A submanifold $(N,\psi)$ of $M$ (i.e. a manifold together with an injective immersion $\psi:N\to M$) is an **integral manifold** of a distribution $\mathscr{D}$ on $M$ if for any $n \in N$
>$$d\psi(N_n) = \mathscr{D}(\psi(n))$$

In this section we classify the existence of integral manifolds for smooth distributions in terms of whether they are involutive. The reason that we have called being involutive also "completely integrable" is that it corresponds to the existence of submanifolds which have tangent spaces agreeing exactly with the distribution. However, more generally we can consider integrable distributions where the tangent spaces of the submanifold are only required to be contained in, but not necessarily equal to, the distribution at each point.

>[!proposition] Existence of integral manifolds implies involutive
>Let $\mathscr{D}$ be a smooth distribution on $M$ such that through each point of $M$ there exists an integral manifold of $\mathscr{D}$ containing that point. Then $\mathscr{D}$ is involutive.

`\begin{proof}`
Let $X$ and $Y$ be smooth vector fields lying in $\mathscr{D}$ and let $p \in M$. Let $(N,\psi)$ be an integral manifold of $\mathscr{D}$ through $p$, and let $q \in N$ such that $\psi(q) = p$. By assumption we have that for any $n \in N$, $d\psi_n:N_n\to \mathscr{D}(\psi(n))$ is an isomorphism, we can define $\widetilde{X} = d\psi^{-1}\circ X \circ \psi$ and $\widetilde{Y} = d\psi^{-1}\circ Y \circ \psi$, which will be smooth vector fields on $N$. To see that these vector fields are smooth take a chart $(U,x_1,...,x_d)$ on $M$ and a chart $(V,y_1,...,y_c)$ on $N$ such that $\psi(V) \subseteq U$. Further, we can choose the chart $U$ such that we have vector fields $X_1,...,X_c:U\to TM$ which span $\mathscr{D}$ at each point. 

It follows that $X\vert_U = \sum_{i=1}^cf_iX_i$ for some smooth functions $f_i$. Then we have that
$$d\psi^{-1}\circ X\circ \psi \vert_V(n) = \sum_{i=1}^cf_i(\psi(n))d\psi^{-1}(X_i)_{\psi(n)}$$


##### TODO
- [ ] Read existence and uniqueness theorem for ODEs
  
#### References

[^1]: Warner, F. W. (1983). Foundations of Differentiable Manifolds and Lie Groups (Vol. 94). New York, NY: Springer. https://doi.org/10.1007/978-1-4757-1799-0
