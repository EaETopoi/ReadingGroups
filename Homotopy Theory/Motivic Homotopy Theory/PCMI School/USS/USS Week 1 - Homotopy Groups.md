---
date: 2024-07-08T12:57:00
tags:
  - Homotopy
  - StableHomotopy
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

In these notes we begin a series of lectures by Anna Marie Bohmann at the PCMI 2024 Undergraduate Summer School. We begin with an introduction to algebraic topology and homotopy theory before introducing the notions of stability.

In algebraic topology we wish to study topological spaces through the assignment of (algebraic) invariants, which are necessarily functorial. Further, we want these invariants, at least at first, to be homotopy invariants, so they send homotopic spaces to isomorphic invariants. 

One of the simplest examples of algebraic invariants is the zeroth fundamental "group", i.e. the set of path components, $\pi_0:\mathsf{Top}\to \mathsf{Set}$. This is indeed a homotopy invariant since continuous deformations cannot collapse or create path components, since homotopies act through paths.

Extending up the proverbial tower we have the fundamental group $\pi_1:\mathsf{Top}_*\to \mathsf{Grp}$ and higher homotopy groups, $\pi_n:\mathsf{Top}_*\to \mathsf{Ab}, n\geq 2$.

>[!def] Fundamental Group
>If $x:*\to X$ is a pointed topological space, its first fundamental group is the set $[I,X]_{(rel\;\partial I)}$ of homotopy equivalence classes of paths $I\to X$, relative to $\partial I$, (equivalently $[S^1,X]$, equivalence classes of pointed maps up to pointed homotopy). We endow a group structure on $[I,X]_{(rel\;\partial I)}$ by sending a pair of maps $f:S^1\to X$ and $g:S^1\to X$, representing equivalence classes in the set, to the composite
>$$S^1\xrightarrow{i}S^1\lor S^1\xrightarrow{f\lor g} X$$
>where $i$ contracts a copy of $S^0$ in $S^1$ to obtain $S^1\lor S^1$ (i.e. contracting an "equator").

We can generalize this definition to obtain the definition of higher homotopy groups.

>[!def] Higher Homotopy Groups
>Let $n \geq 2$ and let $x:*\to  X$ be a pointed topological space. Then the $n$-th homotopy group, $\pi_n(X,x)$, of $X$ at $x$ is the set $[I^n,X]_{(rel\;\partial I^n)}$ of maps relative to $\partial I^n$ up to homotopy equivalence, relative to $\partial I^n$, or equivalently the set $[S^n,X]$ of pointed homotopy classes of pointed maps $S^n\to X$.
>
>We can endow a group structure on $\pi_n(X,x)$ in a number of equivalent ways. In the sphere perspective, we can take the generalization of the previous example
>$$S^n\xrightarrow{i}S^n\lor S^n\xrightarrow{f\lor g}X$$
>for $[f],[g] \in \pi_n(X,x)$, where $i$ contracts the equator copy of $S^{n-1}$ in $S^n$. In the perspective of maps $f,g:I^n\to X$, we can define the composite by
>$$f\cdot g(t_1,\dots,t_n) = \left\{\begin{array}{cc} g(2t_1,t_2,\dots,t_n) & t_1 \leq1 / 2 \\ f(2t_1-1,t_2,\dots,t_n) & 1 / 2 \leq t_1 \leq 1\end{array}\right.$$

Recall that the notion of relative homotopies:

>[!def] Relative Homotopies
>Let $A \subseteq X$ be a topological space together with a subspace $A$. Let $f,g:X\to Y$ be continuous maps such that $f\vert_A = g\vert_A$. Then a homotopy $H:X\times I\to Y$ relative to $A$ is a continuous map such that $H\vert_{X\times\{0\}} = f$, $H\vert_{X\times\{1\}}=g$, and $H\vert_{A\times I} = f\vert_A\pi_A=g\vert_A\pi_A$.


To see that this group structure will be abelian for $n \geq 2$ we can use the Eckmann-Hilton argument, since for $n \geq 2$ we have multiple definitions of different group operations on $\pi_n(X,x)$, given by speeding up different variables in $(t_1,...,t_n)$, which induce monoid homomorphisms relative to one another.

>[!thm] Eckmann-Hilton Argument
>Let $M$ be a set with two binary operations $*,\star:M\times M\to M$ and units $e_*,e_\star$ with respect to each binary operation such that $(M,*,e_*)$ and $(M,\star,e_\star)$ are monoids, which satisfy the four-interchange law $$(m*n)\star(m'*n') = (m\star m')*(n\star n'),\;\;\forall m,n,m',n' \in M$$ Then $M$ is a commutative monoid.

`\begin{proof}`
First, I claim that $e_*$ and $e_\star$ agree. Observe that
$$e_\star = e_\star \star e_\star = (e_\star*e_*)\star (e_**e_\star) = (e_\star \star e_*)*(e_*\star e_\star) = e_* * e_* = e_*$$
Now we show that $*$ and $\star$ are the same, which will help us show that $M$ is commutative. Let $a,b \in M$. First, we have the sequence of equalities:
$$a*b = (e_\star \star a)*(b\star e_\star) = (e_\star*b)\star (a*e_\star) = (e_* * b)\star (a * e_*) = b\star a$$
On the other hand, we have that
$$a*b = (a\star e_\star)*(e_\star \star b) = (a*e_\star)\star (e_\star *b) = (a*e_*)\star (e_* * b) = a\star b$$
Together these equational identities imply that $* = \star$ are equivalent binary operations, and $(M,*,e_*)$ is a commutative monoid.
`\end{proof}`

Let us give a second argument to show that $\pi_n(X)$ is abelian for $n \geq 2$ using the first component composition. Let $f,g:I^n\to X$ such that $f(\partial I^n) = g(\partial I^n) = x$. We have a homotopy $H:I^n\times I\to X$ from $f\cdot g$ to a thickening by constant maps, and then we can give a homotopy of $I^n$, preserving the boundary, which moves the resulting rectangles around each-other using appropriate convex homotopies in $I$. Note that this kind of argument cannot be carried out when $n = 1$, since we do not have enough degrees of freedom to pass maps obtained after thickening constant maps around each other.
### Functoriality

We wish to now show that the $\pi_n$, $n\geq 1$, induce homotopical functors. By post-composition, it is immediate to see that $\pi_n$ is a functor, so the main difficulty lies in the homotopical claim. First let us consider an observation for non-based homotopies for $\pi_1$.

>[!scenario]
>Suppose $f,g:X\to Y$ are homotopic maps, with witnessing homotopy $H:X\times I\to Y$ such that $H(x,0) = f(x)$ and $H(x,1) = g(x)$. Then if $x \in X$, let $a = H\circ \iota_x$ be the path given by $H(x,t)$ for $t \in I$. Now, I claim that $\overline{a}\cdot f_*[\omega]\cdot a = g_*[\omega]$ for any loop $\omega \in \pi_1(X,x)$.
>
>Let $J$ denote the homotopy $g_*[\omega]\simeq f_*[\omega]$ obtained from $H$. Note that $J(0,t) = H(\omega(0),t) = H(x,t)$ while $J(1,t) = H(x,t)$. We can obtain our desired homotopy by concatenating with homotopies $J_1:\overline{a}\simeq c_{g(x)}$ and $J_2:a\simeq c_{g(x)}$, where these homotopies are based on one side. Explicitly,
>$$J_1(s,t) = \left\{\begin{array}{cc} \overline{a}(s) & 0 \leq s \leq 1-t \\ \overline{a}(t) & 1-t \leq s \leq 1 \end{array}\right.$$
>and 
>$$J_1(s,t) = \left\{\begin{array}{cc} a(s) & 0 \leq s \leq t \\ a(t) & t \leq s \leq 1 \end{array}\right.$$
>We can also equivalently show that $\overline{g_*[\omega]}\cdot \overline{a}\cdot f_*[\omega]\cdot a\simeq c_{g(x)}$ using a wrapping of successively larger squares as one goes up in time.

However, when dealing with based homotopies, $\pi_n$ **will** be a homotopical functor, namely one of the form $\pi_n:\mathsf{Top}_*\to \mathsf{Ab}$, $n\geq 2$, or $\pi_1:\mathsf{Top}_*\to \mathsf{Grp}$.
## Applications

One of many applications of the fundamental group is Brouwer's fixed point theorem:

>[!thm] Brouwer's Fixed Point Theorem
>Any continuous map $f:D^2\to D^2$ has a fixed point.

`\begin{proof}`
Towards a contradiction suppose $f$ has no fixed points. Then we have a map $r:D^2\to S^1$ given by sending a point $p \in D^2$, to  the point on $S^1$ obtained by extending the line from $p$ to $f(p)$ to the boundary. This is given by
$$r(p) = p+\left(-p\cdot \frac{f(p)-p}{||f(p)-p||}+\sqrt{\left(p\cdot\frac{f(p)-p}{||f(p)-p||}\right)^2+1-||p||}\right)\frac{f(p)-p}{||f(p)-p||}$$
which is continuous, being the composite of continuous maps. Then if $i:S^1\to D^2$ denotes the inclusion, we have a factorization of the identity
$$\pi_1(S^1)\xrightarrow{i_*}\pi_1(D^2)\xrightarrow{r_*}\pi_1(S^1)$$
However, $\pi_1(S^1)\cong \mathbb{Z}$, from a covering space argument, while $D^2$ is contractible, so such a factorization of the identity is impossible.
`\end{proof}`

## Properties of Higher Homotopy Groups

We start by showing that the two definitions of $\pi_n(X,x)$ agree, and that the group operations are well-defined. Let us consider the $[I^n,X]_{\partial I^n}$ definition first. Let $f,g,f' :I^n\to X$, relative to $\partial I^n$, be such that $f\simeq_{\partial I^n}f'$. Let $H:I^n\times I\to X$ be the homotopy, which fits into a diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cpartial%20I%5En%5Ctimes%20I%7D%20%26%26%20%7B*%7D%20%5C%5C%0A%09%5C%5C%0A%09%7BI%5En%5Ctimes%20I%7D%20%26%26%20X%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bhook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22x%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22H%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\partial I^n\times I} &amp;&amp; {*} \\
	\\
	{I^n\times I} &amp;&amp; X
	\arrow[from=1-1, to=1-3]
	\arrow[hook, from=1-1, to=3-1]
	\arrow[&quot;x&quot;, from=1-3, to=3-3]
	\arrow[&quot;H&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

Then we define $K:I^n\times I\to X$ from $f\cdot g\simeq_{\partial I^n}f'\cdot g$, by $H\cdot g$, where 
$$H\cdot g(t_1,\dots,t_n,s) = \left\{\begin{array}{cc}
H(2t_1,t_2,\dots,t_n,s) & 0\leq t_1 \leq \frac{1}{2}  \\
g(2t_1-1,t_2,\dots,t_n) & \frac{1}{2}
 \leq t_1 \leq 1\end{array}\right.
$$
where $K\vert_{\partial I^n\times I} = x$. The other side is similar. Further, unity and associativity follow similar proofs to that for $\pi_1$. Explicitly, if $f,g,h:I^n\to X$, we want to have a homotopy $\omega:I\times I\to I$ that sends $\omega_0(s) = 4s, 0\leq s\leq 1/4$, $\omega_0(s) = 4s-1,1/4\leq s\leq 1/2$, and $\omega_0(s) = 2s-1,1/2 \leq s \leq 1$, to $\omega_1(s) = 2s,0\leq s\leq 1/2$, $\omega_1(s) = 4s-2,1/2 \leq s \leq 3/4$, and $\omega_1(s) = 4s-3,3/4\leq s \leq 1$. However, this can easily be done by a convex homotopy, since $I$ is convex. Composing this homotopies with their inclusion in the first component of $I^n$, we have that $f\cdot (g\cdot h)\simeq_{\partial I^n}(f\cdot g)\cdot h$.


Now, let us show that this is equivalent to our $S^n$ definition.

>[!claim]
>We have a homeomorphism $S^n\cong I^n/\partial I^n$.

`\begin{proof}`
Note that $D^n\cong I^n$ with homeomorphism inducing a homeomorphism $S^{n-1} = \partial D^n\cong \partial I^n$. Thus, we show $S^n\cong D^n/\partial D^n$. First, we have a map $p:D^n\to S^n$ given by $p\vert_{\partial D^n} = S$, where $S$ is the north pole of $S^n$, and $p\vert_{(D^n)^\circ}$ is the homeomorphism from $(D^n)^{\circ}\to \mathbb{R}^n$ given by $x\mapsto \frac{x}{1-||x||}$, followed by the stereographic projection $\mathbb{R}^n\xrightarrow{\cong } S^n\backslash \{S\}$. Note that $p$ is continuous since for any sequence in $D^n$ with limit point in the boundary of $D^n$, the resulting sequence after applying the homeomorphism approaches $\infty$, and hence after composing with the stereographic projection, approaches the south-pole.

Thus, $p:D^n\to S^n$ sends $\partial D^n$ to $\{S\}$, and restricts to a homeomorphism from the interior of the ball to $S^n\backslash\{S\}$. Thus, we obtain an induced injective map $D^n/\partial D^n\to S^n$. Further, since $p$ is an open mapping, it follows that this is a homeomorphism.
`\end{proof}`

As with $\pi_1$, $\pi_n$ is functorial in the sense that $\pi_n:\mathsf{Top}_*\to \mathsf{Ab}$, and these functors are homotopical.

### $\pi_0$ Reformalization

Right now our definition of homotopy groups seems somewhat antisymmetric with that of $\pi_0$. However, a path component in a space, $X$, is equivalent to the set of points $*\to X$, which can be connected by a path $I\times *\cong I\to X$, or in other words homotopy classes of points. To further the analogy, if $X$ is a based space, this is the same as based homotopy classes of based maps $S^0\to X$, where $S^0 = *\amalg *$. This formalization shows that $\pi_0(X)$, for $X$ a based space, comes naturally equipped with a basepoint, namely the path-component containing the basepoint of $X$. Thus, we have a functor
$$\pi_0:\mathsf{Top}_*\to \mathsf{Set}_*$$

Okay, we are closer to our story with higher homotopy groups, but there is still a disparity with the fact that $\pi_n,n\geq 1$ has a group structure, while $\pi_0$ does not. Well if we did have a natural group structure, it should be given by $S^0\to S^0\lor S^0\to X$ in some way, but the only maps from $S^0$ into $S^0\lor S^0$ are the inclusions, so there is no way to get the interaction between two such "paths", representing points.
### Computations

For any contractible space, $X$, we have that $\pi_n(X) \cong *$ for any $n \geq 0$, where $*$ is the terminal object in the suitable category. We also have a nice description of higher homotopy groups of $S^1$, as well as some homotopy groups of higher spheres.

>[!proposition] Homotopy groups of order less than the dimension are trivial
>If $n,i \geq 0$ are integers such that $i < n$, then $\pi_i(S^n)\cong 0$.

`\begin{proof}`
We can use smooth/cellular approximation/the idea of dimension to see that any element of $[S^i,S^n]$, i.e. any map $S^i\to S^n$, can be homotoped to miss a point, and hence land in $S^n\backslash\{pt\}$. But $S^n\backslash\{pt\}\cong \mathbb{R}^n$ by stereographic projection, and this is contractible.
`\end{proof}`

>[!claim]
>$\pi_n(S^1) \cong (0)$ for all $n\geq 2$.

`\begin{proof}`
Let $p:\mathbb{R}\to S^1$ be the covering space map. Let $f:S^n\to S^1$ be a based map. But $\pi_1(S^n) \cong 0$, so by the homotopy lifting property we have a lift $\widetilde{f}:S^n\to \mathbb{R}$, which we can then contract, which descends to a contraction of $f$.
`\end{proof}`
Therefore, we have that $S^1$ is a $K(\mathbb{Z},1)$ space.

In higher homotopy groups we have no analogue of Van-Kampen, making their computation much more difficult. However, the higher homotopy group functors are still product preserving, by the same proof as for $\pi_1$. Thus, for $X,Y$ based spaces,
$$\pi_n(X\times Y)\cong \pi_n(X)\times \pi_n(Y)$$
As mentioned previously, these functors are also homotopical, with respect to homotopy equivalence.

>[!proposition] Homotopy Invariance
>Let $f,g:X\to Y$ be homotopic maps, with homotopy $H:X\times I\to Y$. Then we have a commuting diagram
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cpi_n(X%2Cx)%7D%20%26%26%20%7B%5Cpi_n(Y%2Cg(x))%7D%20%5C%5C%0A%09%5C%5C%0A%09%26%20%7B%5Cpi_n(Y%2Cf(x))%7D%0A%09%5Carrow%5B%22%7Bg_*%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bf_*%7D%22'%2C%20from%3D1-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%7B%5Cbeta_%7B%5Coverline%7BH%7D%7D%7D%22'%2C%20from%3D3-2%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\pi_n(X,x)} &amp;&amp; {\pi_n(Y,g(x))} \\	\\	&amp; {\pi_n(Y,f(x))}	\arrow[&quot;{g_*}&quot;, from=1-1, to=1-3]	\arrow[&quot;{f_*}&quot;', from=1-1, to=3-2]	\arrow[&quot;{\beta_{\overline{H}}}&quot;', from=3-2, to=1-3]\end{tikzcd}" /></p>

`\begin{proof}`
Here if $H$ is a based homotopy then we directly have $f(x) = g(x)$ and $f_* = g_*$. 

Otherwise, for $x\in X$, we have $a:I\to Y$ given by $a(t) = H(x,t)$, which gives a path from $f(x)$ to $g(x)$. Now, given $\omega:I^n\to X$ such that $\omega(\partial I^n) = x$, $J := H(\omega(-),-):I^n\times I\to Y$ is a homotopy from $f\circ \omega$ to $g\circ \omega$, where $J\vert_{\partial I^n\times I} = a$. We then define $\widetilde{J}:I^n\times I\to Y$ by
$$\widetilde{J}(t_1,\dots,t_n,s) := \left\{\begin{array}{cc}
a(1-3\min\{t_1,\dots,t_n\}) & 0\leq 1-3\min\{t_1,\dots,t_n\}\leq s,  \\
a(s) & 0\leq s\leq 1-3\min\{t_1,\dots,t_n\}  \\
J(3t_1-1,\dots,3t_n-1,s) & \frac{1}{3} \leq \min\{t_1,\dots,t_n\},\max\{t_1,\dots,t_n\} \leq \frac{2}{3}  \\
a(3\max\{t_1,\dots,t_n\}-2) & 0\leq 3\max\{t_1,\dots,t_n\}-2\leq s,  \\
a(s) & 0 \leq s\leq 3\max\{t_1,\dots,t_n\}-2  \\
\end{array}\right.$$
To see that this is well-defined note that $J(t_1,...,t_n,s) = H(x,s) = a(s)$ when some $t_i$ is zero or $1$, which when some $t_i$ is zero we have $\alpha(s)$, and when some $t_i$ is $1$, we again get $a(s)$. It remains to see that when some $t_i$ **TBD**
`\end{proof}`

### Constructions on Based Spaces

Let us explore the category $\mathsf{Top}_*$ of based spaces (possibly restricting to nice based spaces, such as CGWH spaces). In based spaces what do our limits and colimits look like? Well for limits it is quite simple, where the categorical product is simply given by the cartesian product, $X\times Y$. On the other hand, the coproduct is given by the so-called wedge sum
$$X\lor Y = (X\amalg Y)/\{x_0\sim y_0\}$$
obtained by gluing basepoints.

Now, although $X\times Y$ is our categorical product, it is not the best product, and in particular not the best monoidal product on $\mathsf{Top}_*$ for homotopy theory due to the "excess of basepoint candidates". Instead, we want to identify all basepoint candidates $(x_0,y)\sim (x,y_0)$, which forms what we call the **smash product**

$$X\land Y := \text{coeq}\left(X\lor Y\rightrightarrows X\times Y\right)$$
where one map is the unique one induced by the product and coproduct structures, which behaves as the inclusion on underlying sets, and the other map factors through the basepoint of the category, $*$.

>[!example]
>Recall that $S^1\times S^1$ is the torus. On the other hand, $S^1\land S^1 \cong S^2$, is the sphere.

>[!claim]
>For all $n \geq 0$, $S^1\land S^n \cong S^{n+1}$.

`\begin{proof}`
Recall that
$$S^1\land S^n := \text{coeq}\left(S^1\lor S^n\rightrightarrows S^1\times S^n\right)$$
Now $S^1 \cong I/\partial I$, from our previous work, so as colimits commute, and products with $S^1$ in $\mathsf{Top}$ commute with colimits since it is a locally compact Hausdorff space, we have
$$
\begin{align}
S^1\land S^n &\cong (I / \partial I)\land S^n  \\
&\cong ((I / \partial I)\times S^n) / ((I / \partial I)\lor S^n)  \\
&\cong ((I\times S^n) / (\partial I \times S^n)) / ((I\lor S^n) / (\partial I \lor S^n))  \\
&\cong (I\times S^n) / (\{0\}\times S^n\cup \{1\}\times S^n\cup I\times \{x_0\})
\end{align}
$$
Note that we have a natural map $I\times S^n\to S^{n+1}$ given by $(t,x)\mapsto (2t-1,cx)$ where $c = \sqrt{1-(2t-1)^2}$, which sends the copies of $S^n$ at $t=0,1$ to either the south pole, $S$, or the north pole, $N$, respectively. Then it remains to see that quotienting $S^{n+1}$ out by a line segment connecting the north and south poles gives $S^{n+1}$ again, up to homeomorphism. However, this can be viewed as contracting one piece of a CW structure on $S^{n+1}$ which produces another CW structure on $S^{n+1}$.


**Below is TBD Proof**
Now, also recall $S^n\cong D^n/\partial D^n$, so $S^1\land S^n \cong (S^1\land D^n)/(S^1\land S^{n-1})$ when $n \geq 1$. Thus, the claim follows if $S^1\land D^n \cong D^{n+1}$ and, by induction, $S^1\land S^0 \cong S^1$. However, $S^0\land X \cong X$ for any space $X$ since $S^0\times X = X\amalg X$, with one copy having the basepoint, and $S^0\land X$ is obtained by taking the other copy and gluing it to the basepoint in the other copy.

Therefore, it suffices to show that $S^1\land D^n \cong D^{n+1}$. Note that if $n = 1$, $D^1$ is the unit interval, and $S^1\times D^1$ is the cylinder. Quotienting by $S^1\lor D^1$ glues one whole to obtain the desired disk, $D^2$. Similarly, $S^1\times D^2$ is the filled torus, and quotienting by $S^1\lor D^2$  contracts the central circle and a disk on the torus to obtain a sphere. Let us consider this generally.

Note that $S^1 \cong I/\partial I$, so $S^1\land D^n\cong (I\land D^n)/(\partial I\land D^n)$, where $\partial I\land D^n \cong D^n$ as $\partial I = S^0$. On the other hand, $I\times D^n\mapsto D^{n+1}$ given by

`\end{proof}`
The functor $S^1\land -$ is so important that we give it a special name.

>[!def] (Reduced) Suspension
>The **(reduced suspension)** of a topological space $X$ is $\Sigma X := S^1\land X$.

Note that since $\land$ is a colimit, we have that $\Sigma$ preserves colimits. In particular, this implies that $\Sigma(S^n\lor S^n) \cong S^{n+1}\lor S^{n+1}$. Geometrically in the case of $n=1$ we can think of a figure eight turning into a wedge of tori under the product, which then after amalgamating the wedge of circles gives a wedge of spheres.

Now, observe that since $\mathsf{Top}_*$ is complete and cocomplete and $\Sigma$ commutes with colimits, we should expect that it has a right adjoint. This right adjoint will be given by the loop space $\Omega:\mathsf{Top}_*\to \mathsf{Top}_*$ given by sending a space $X$ to the set $\mathsf{Top}_*(S^1,X)$ with the compact open topology. Since $S^1$ is a locally compact Hausdorff space, we have an adjunction $S^1\times-\dashv \mathsf{Top}(S^1,-)$, where upon restricting to $\mathsf{Top}_*(S^1,-)$ we obtain from a basepoint preserving map $f:X\to \mathsf{Top}_*(S^1,Y)$ we obtain a map $\widetilde{f}:X\times S^1\to Y$ given by $\widetilde{f}(x,\theta) = f(x)(\theta)$, where since $f$ is basepoint preserving $\widetilde{f}\vert_{\{x_0\}\times S^1}=y_0$ and since $f(x)$ is basepoint preserving for all $x$, $\widetilde{f}_{X\times \{\theta_0\}} = y_0$. Thus, this is the same as specifying $\widetilde{f}':X\land S^1\to Y$. Therefore, the bijection restricts to a bijection
$$\mathsf{Top}_*(X\land S^1,Y)\cong \mathsf{Top}_*(X,\mathsf{Top}_*(S^1,Y))$$
or in other words $\Sigma \dashv \Omega$. Further, this adjunction preserves based homotopy classes of maps. Indeed, if $f,g:X\land S^1\to Y$ are homotopic via $H:(X\land S^1)\times I\to Y$ such that $H\vert_{(X\land S^1)\times \{0\}} = f$, $H\vert_{(X\land S^1)\times \{1\}} = g$, and $H\vert_{\{x_0\}\times I} = y_0$, precomposition with $X\times S^1\to X\land S^1$ gives a map $J:(X\times S^1)\times I\to Y$, and using our previous adjunction gives a map $\widetilde{J}:X\times I\to \mathsf{Top}(S^1,Y)$, which at $X\times \{0\}$ co-restricts to $f^\#$ and at $X\times \{1\}$ co-restricts to $g^\#$. Note that for any $(x,t) \in X\times I$,
$$\widetilde{J}(x,t)(\theta_0) = J(x,\theta_0,t) = H(x_0,t) = y_0$$
so $\widetilde{J}$ co-restricts to a continuous map $\widetilde{J}:X\times I\to \mathsf{Top}_*(S^1,Y)$. Finally, for any $t \in I$, and any $\theta \in S^1$,

$$\widetilde{J}(x_0,t)(\theta) = J(x_0,\theta,t) = H(x_0,t) = y_0$$
so $\widetilde{J}$ is a base-point preserving homotopy from $f^\#$ to $g^\#$. Following this argument in reverse then shows that our adjunction restricts to an isomorphism
$$[\Sigma X,Y]\cong [X,\Omega Y]$$

>[!scenario]
>We can define a group operation on $[\Sigma X,Y]$ inherited from that on $\pi_1$ by sending $f,g:\Sigma X\to Y$ to the composite $$S^1\land X\xrightarrow{e\land \text{id}_X} (S^1\lor S^1)\land X\cong \Sigma X\lor \Sigma X\xrightarrow{f\lor g} Y$$
>Explicitly, we can realize the composite of $f$ and $g$ as a map $f\cdot g:S^1\land X\to Y$ which sends $(e^{it},x)\mapsto f(e^{i2t},x)$ if $0\leq t \leq \pi$ and $(e^{it},x)\mapsto g(e^{2it},x)$ if $\pi \leq t \leq 2\pi$. Using the same types of proofs for $\pi_1$, adjusting the rate at which the $t$ parameter varies, we see that this defines a group operation where $\overline{f}:(e^{it},x)\mapsto f(e^{-it},x)$ is the inverse of $f$ and $c_{y_0}:(e^{it},x)\mapsto y_0$ is the identity.

Note that the above remarks give an alternate proof that $[S^n,X]$ is a group. Indeed, if $n = 1$ then we have a group from the base case with $\pi_1$. Otherwise, for $n \geq 2$ our group structure is induced by the equivalence
$$[S^n,X]\cong [S^1,\Omega^{n-1}X]\cong [S^0,\Omega^nX] \cong \pi_0(\Omega^nX)$$
Further, this also gives an alternative proof that the higher homotopy groups are abelian after we prove the following result:

>[!proposition] Abelian Loop Space Fundamental Group
>If $X$ is a pointed topological space, then its loop space $\Omega X$ has abelian fundamental group.

`\begin{proof}`
Let $f,g:S^1\to \Omega X = \mathsf{Top}_*(S^1,X)$. We want to use the existing group structure on $\Omega X$ to show that $[f][g] = [g][f]$. First, note that we have a based homotopy $H:I\times I\xrightarrow{f\times g} \Omega X\times \Omega X \xrightarrow{m} \Omega X$ where we denote the multiplication in $\Omega X$ by $m$. Observe that
$$H(t,0) = m(f(t),c_{x_0}) = f(t),\;H(0,s) = m(c_{x_0},g(s)) = g(s)$$
We then obtain a homotopy from $f\cdot g$ to $g\cdot f$ by rotating the domain of $H$ and expanding the diamond to a square by adding triangles where the paths are taken independent of the height before scaling the resulting square to be unit side lengths. Explicitly, if $H$ is the homotopy given, let $R:D\to I\times I$ rotate and scale the diamond $D \subseteq I\times I$. Then we can define a homotopy
`\end{proof}`

Another important construction on based spaces is the cone on a space:

>[!def] (reduced) Cone of a Based space
>The **(reduced) cone** over a based space $X$ is the smash product $CX :=X\land I$

With this perspective, we can think of the suspension as the a gluing of cones of $X$. A similar type of relation, now for the loop space, can be obtained by defining first the path space.

>[!def] Path Space
>Let $X$ be a based space. Then the path space on $X$ is given by
>$$PX = \{q:I\to X\,\vert\,q(0) = *\} = \mathsf{Top}_*(I,X)$$

Note that from a similar argument to that for suspension and loop space, we obtain an adjunction $C\dashv P$ which is homotopical in the sense that
$$[CX,Y] \cong [X,PY]$$
Further, the resulting evaluation for the adjunction, $PX\land I\to X$ sends a point $f:I\to X$ in the path space to $f(1)$ when considering the inclusion $PX\cong PX\land \partial I\to PX\land I\to X$.

In addition, the path space $PX$ is contractible, where the homotopy $H:PX\times I\to PX$ is given by $H(q,t) = q\vert_{[0,t]}$, which is a homotopy from the identity to the constant path map. As a right homotopy this is exactly $PX\to \mathsf{Top}(I,PX)$ given by sending a path $f$ to the map $t\mapsto q\vert_{[0,t]}$ This implies $\pi_n(PX)\cong 0$ for all $n \geq 0$.

>[!remark] Fibers of Path Space
>The **fiber** of $p_1:PX\to X$, i.e. $p_1^{-1}(*)$, is just all paths that are loops, which is exactly $\Omega X$. Thus, we obtain a sequence
>$$\Omega X\to PX\xrightarrow{p_1}X$$
>which is a fiber sequence, and is in fact also a **fibration**.

>[!def] Fibrations
>A **fibration** is a map $p:E\to B$, where $E$ is called the **total space of the fibration** and $B$ is called the **base space of the fibration**, that satisfies the right lifting property with respect to cylinder inclusions (i.e. $p$ satisfies the homotopy lifting property).
>
>In other words, for any commuting square
>
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09Y%20%26%26%20E%20%5C%5C%0A%09%5C%5C%0A%09%7BY%5Ctimes%20I%7D%20%26%26%20B%0A%09%5Carrow%5B%22%7Bf_0%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bi_0%7D%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cexists%20%5Cwidetilde%7BH%7D%7D%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22H%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	Y &amp;&amp; E \\	\\	{Y\times I} &amp;&amp; B	\arrow[&quot;{f_0}&quot;, from=1-1, to=1-3]	\arrow[&quot;{i_0}&quot;', hook, from=1-1, to=3-1]	\arrow[&quot;p&quot;, from=1-3, to=3-3]	\arrow[&quot;{\exists \widetilde{H}}&quot;, dashed, from=3-1, to=1-3]	\arrow[&quot;H&quot;', from=3-1, to=3-3]\end{tikzcd}" /></p>

For example, all covering space maps $p:E\to B$ are fibrations, and in fact satisfy a stronger condition since they satisfy the strong right lifting property with respect to cylinder inclusions.

>[!claim]
>The map $p_1:PX\to X$ is a fibration.

`\begin{proof}`
Consider a diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09Y%20%26%26%20PX%20%5C%5C%0A%09%5C%5C%0A%09%7BY%5Ctimes%20I%7D%20%26%26%20X%0A%09%5Carrow%5B%22%7Bf_0%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bi_0%7D%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p_1%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22H%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	Y &amp;&amp; PX \\
	\\
	{Y\times I} &amp;&amp; X
	\arrow[&quot;{f_0}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{i_0}&quot;', hook, from=1-1, to=3-1]
	\arrow[&quot;p_1&quot;, from=1-3, to=3-3]
	\arrow[&quot;H&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

We want to construct a lift of $H$. For each $y \in Y$ we have a path $f_0(y):I\to X$ such that $f_0(y)(1) = H(y,0)$. Then, in general, we can construct $\widetilde{H}:Y\times I\to PX$ by sending $(y,t)$ to $f_0(y)\cdot \widetilde{H}(y,-)\vert_{[0,t]}$.

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09Y%20%26%26%20PX%20%5C%5C%0A%09%5C%5C%0A%09%7BY%5Ctimes%20I%7D%20%26%26%20X%0A%09%5Carrow%5B%22%7Bf_0%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bi_0%7D%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%5Carrow%5B%22%7B%5Cwidetilde%7BH%7D%7D%22%2C%20dashed%2C%20from%20%3D3-1%2C%20to%20%3D1-3%5D%0A%09%5Carrow%5B%22p_1%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22H%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	Y &amp;&amp; PX \\
	\\
	{Y\times I} &amp;&amp; X
	\arrow[&quot;{f_0}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{i_0}&quot;', hook, from=1-1, to=3-1]
\arrow[&quot;{\widetilde{H}}&quot;, dashed, from =3-1, to =1-3]
	\arrow[&quot;p_1&quot;, from=1-3, to=3-3]
	\arrow[&quot;H&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>
`\end{proof}`

>[!def] Based Fibration
>A map of based space $p:E\to B$ is said to be a **based fibration** if **TBD**

>[!thm]
>Suppose we have a (based) fibration $p:E\to B$, and let $F = p^{-1}(*)$ is the fiber above the basepoint, so we have a sequence
>$$F\to E\xrightarrow{p}B$$
>Then we get a map $\Omega B\to F$, which assembles into what's called a fibration sequence.

`\begin{proof}`
Given a loop $q \in \Omega B$, we can obtain a lift along the fibration

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5C%7B*%5C%7D%7D%20%26%26%20E%20%5C%5C%0A%09%5C%5C%0A%09%7B%5C%7B*%5C%7D%5Ctimes%20I%7D%20%26%26%20B%0A%09%5Carrow%5B%22%7Be_0%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bi_0%7D%22'%2C%20hook%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22p%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cexists%20%5Cwidetilde%7Bq%7D%7D%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22q%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\{*\}} &amp;&amp; E \\
	\\
	{\{*\}\times I} &amp;&amp; B
	\arrow[&quot;{e_0}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{i_0}&quot;', hook, from=1-1, to=3-1]
	\arrow[&quot;p&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\exists \widetilde{q}}&quot;, dashed, from=3-1, to=1-3]
	\arrow[&quot;q&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

where $p(\widetilde{q}(1)) = q(1) = e_0$ must again be the basepoint in $e$, and so this defines a map $\Omega B\to F$.  Now, I claim that this is independent of the lift $\widetilde{q}$, up to homotopy. Indeed, if $p$ is a (based) fibration, then any homotopy for $q$ lifts to a homotopy in $E$ which preserves endpoints.
`\end{proof}`

This implies that we obtain an extended fiber sequence

$$\cdots \to \Omega^2B\to \Omega F\to \Omega E\to \Omega B\to F\to E\to B$$


#### References
