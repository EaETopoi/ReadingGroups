---
date: 2024-06-09T10:30:00
tags:
  - AlgebraicGeometry
  - Sheaves
  - EtaleCohomology
  - ReadingGroup
type: Notes
summary:
---

## Introduction

These notes aim to introduce the theory of direct and inverse image functors on sheaves in the context of Milne[^1], with added generalizations from Mac Lane and Moerdijk[^2]. Additional material on (op)fibrations and base change functors inducing geometric morphisms is included after the main material.
## Morphisms of Sites

We begin with looking at morphisms of sites. We say that a functor $\phi:\mathcal{C}\to \mathcal{D}$ between small categories with Grothendieck topologies is a **morphism of sites** if it preserves finite limits and covers. Then such a functor induces a geometric morphism $f:\mathsf{Sh}(\mathcal{D},K)\to \mathsf{Sh}(\mathcal{C},J)$ given by pre-composition as its direct image functor and inverse image functor the functor tensor product $-\otimes_\mathcal{C}A_\phi$, for $A_\phi = \mathfrak{a}\circ y \circ \phi$[^2].

`\begin{proof}`
Since $\phi$ is a morphism of sites, $A_\phi$ is left-exact, and as $\phi$ preserves covers $A_\phi$ sends covers to colimit diagrams. From last lecture we have that $A_\phi$ induces a geometric morphism with inverse image functor $-\otimes_\mathcal{C}A_\phi$ and direct image functor $\mathsf{Sh}(\mathcal{D},K)(A_\phi(-),-)$. The main content of the theorem is that this direct image functor is naturally isomorphic to pre-composition by $\phi$, which follows from the simple computation
$$
\begin{align*}
\mathsf{Sh}(\mathcal{D},K)(\mathfrak{a}y\phi(C),\mathscr{F}) &\cong \mathsf{Ps}(\mathcal{D})(y^{\phi(C)},i(\mathscr{F})) \cong \mathscr{F}(\phi(C))
\end{align*}
$$
using the adjunction for sheafification and Yoneda's lemma.
`\end{proof}`

This is all well and good when $\mathcal{C}$ and $\mathcal{D}$ are finitely complete, but what about in general? When $\mathcal{C}$ and $\mathcal{D}$ are not finitely complete we can not be certain the functor used in the proof above, $A_\phi$, is flat.

In general we can still construct a geometric morphism if we have an adjoint pair $\pi\dashv \phi:\mathcal{D}\to \mathcal{C}$ between small categories with Grothendieck topologies such that $\phi$ preserves covers. Then we obtain an induced geometric morphism $f:\mathsf{Sh}(\mathcal{D},K)\to \mathsf{Sh}(\mathcal{C},J)$, where $f^* = \mathfrak{a}\circ \pi^*$ and $f_* = \phi^*$. This is simply the composition of the adjunctions $\pi^*\dashv \phi^*:\mathsf{Ps}(\mathcal{C})\to \mathsf{Ps}(\mathcal{D})$ and $\mathfrak{a}\dashv i:\mathsf{Ps}(\mathcal{D})\to \mathsf{Sh}(\mathcal{D},K)$, where we are using the fact that $\phi$ preserves covers to conclude that $\phi^*\circ i:\mathsf{Sh}(\mathcal{D},K)\to \mathsf{Sh}(\mathcal{C},J)$.

`\begin{proof}`
As before $A_\phi := \mathfrak{a}y\phi$ determines a geometric morphism, being flat and continuous.  The direct image functor is given by pre-composition by $\phi$, while for $P$ a pre-sheaf we have 
$$
\begin{align*}
(P\otimes_\mathcal{C}y\phi)(D) &\cong P\otimes_\mathcal{C}\mathcal{D}(D,\phi-) \cong P\otimes_\mathcal{C}\mathcal{C}(\pi D,-) \cong P(\pi(D))
\end{align*}
$$
and so $-\otimes_\mathcal{C}y\phi \cong \pi^*$. Then since $-\otimes_\mathcal{C}\mathfrak{a}y\phi \cong \mathfrak{a}(-\otimes_\mathcal{C}y\phi)$, the inverse image functor is given by $\mathfrak{a}\circ \pi^*$.
`\end{proof}`

Now consider our case of interest, where $(\mathcal{C}/X)_E$ and $(\mathcal{D}/Y)_{E'}$ are sites with underlying categories sub-slice categories of schemes and Grothendieck topology given by $E$ or $E'$-coverings, respectively. A map of schemes $\pi:X\to Y$ induces a map of slice categories $\pi^*:\mathsf{Sch}/Y\to \mathsf{Sch}/X$ given by pullback. If for $Z \in \mathcal{D}/Y$ we have $\pi^*Z \in \mathcal{C}/X$, and $\pi^*$ sends $E'$-morphisms to $E$-morphisms, then $\pi^*$ is a morphism of sites. In our main cases of interest, $(\mathcal{C}/X)_E$ and $(\mathcal{D}/Y)_{E'}$ have finite limits. Thus, pre-composition by $\phi:= \pi^*$ induces a geometric morphism $\mathsf{Sh}((\mathcal{C}/X)_E)\to \mathsf{Sh}((\mathcal{D}/Y)_{E'})$, with left-adjoint given by the functor tensor $-\otimes_{\mathcal{D}/Y}\mathfrak{a}y\phi$.


Explicitly if $\mathscr{G}$ is a sheaf on $(\mathcal{D}/Y)_{E'}$ we have that at an object $h:U\to X$ in $\mathcal{C}/X$,
$$
\begin{align*}
\mathscr{G}\otimes_{\mathcal{D}/Y}\mathfrak{a}y\phi(U) &= \left(\int^{V:\mathcal{D}/Y}\mathscr{G}(V)\cdot \mathfrak{a}(y^{\phi(V)})\right)(U) \\
&\cong \mathfrak{a}\left(\int^{V:\mathcal{D}/Y}\mathscr{G}(V)\cdot y^{\phi(V)}\right)(U)
\end{align*}
$$
where we use the fact that sheafification commutes with colimits as it is a left-adjoint. Now observe that
$$\left(\int^{V:\mathcal{D}/Y}\mathscr{G}(V)\cdot y^{\phi(V)}\right)(U) = \text{colim}\left(\coprod_{V\to V':\mathcal{D}/Y,f:U\to \phi(V)}\mathscr{G}(V')\rightrightarrows \coprod_{V:\mathcal{D}/Y,f:U\to \phi(V)}\mathcal{G}(V)\right)$$
where one map is given by mapping a triple $(k:V\to V',f:U\to \phi(V),s \in \mathscr{G}(V'))$  to $(V,f:U\to \phi(V),\mathscr{G}(k)(s))$ and the other maps it to $(V',\phi(k)\circ f:U\to \phi(V'),s \in \mathscr{G}(V'))$. Pictorially we can represent the data of the left coproduct as follows:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%26%20%26%20%7B%5Cphi(V')%7D%20%26%20%7BV'%7D%20%5C%5C%0A%09U%20%26%20%7B%5Cphi(V)%7D%20%26%20V%20%5C%5C%0A%09%26%20X%20%26%20Y%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-3%2C%20to%3D3-2%5D%0A%09%5Carrow%5Bfrom%3D1-4%2C%20to%3D3-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%26quot%3Bh%26quot%3B'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-4%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%26quot%3B%5Cpi%26quot%3B'%2C%20from%3D3-2%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	&amp; &amp; {\phi(V')} &amp; {V'} \\
	U &amp; {\phi(V)} &amp; V \\
	&amp; X &amp; Y
	\arrow[from=1-3, to=1-4]
	\arrow[dashed, from=1-3, to=3-2]
	\arrow[from=1-4, to=3-3]
	\arrow[from=2-1, to=1-3]
	\arrow[from=2-1, to=2-2]
	\arrow[&amp;quot;h&amp;quot;', from=2-1, to=3-2]
	\arrow[from=2-2, to=1-3]
	\arrow[from=2-2, to=2-3]
	\arrow[from=2-2, to=3-2]
	\arrow[from=2-3, to=1-4]
	\arrow[from=2-3, to=3-3]
	\arrow[&amp;quot;\pi&amp;quot;', from=3-2, to=3-3]
\end{tikzcd}
" /></p>
By the universal property of the pullback this data is equivalent to taking a colimit over the category $W_U$, where objects of $W_U$ are commuting squares
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09U%20%26%20V%20%5C%5C%0A%09X%20%26%20Y%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Cpi%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	U &amp; V \\
	X &amp; Y
	\arrow[from=1-1, to=1-2]
	\arrow[&quot;h&quot;', from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[&quot;\pi&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

where $V\to Y$ is in $\mathcal{D}/Y$, and a morphism is given by a map $V\to V'$ making the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%26%20%26%20%7BV'%7D%20%5C%5C%0A%09U%20%26%20V%20%5C%5C%0A%09X%20%26%20Y%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D3-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%5Cpi%22'%2C%20from%3D3-1%2C%20to%3D3-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	&amp; &amp; {V'} \\
	U &amp; V \\
	X &amp; Y
	\arrow[from=1-3, to=3-2]
	\arrow[from=2-1, to=1-3]
	\arrow[from=2-1, to=2-2]
	\arrow[&quot;h&quot;', from=2-1, to=3-1]
	\arrow[from=2-2, to=1-3]
	\arrow[from=2-2, to=3-2]
	\arrow[&quot;\pi&quot;', from=3-1, to=3-2]
\end{tikzcd}
" /></p>
commute. Thus we have that

$$\mathscr{G} \otimes_{\mathcal{D}/Y}y\phi(U)  = \int^{V:\mathcal{D}/Y}\mathscr{G}(V)\cdot y^{\phi(V)}(U) \cong \text{colim}_{(U\to V) \in W_U}\mathscr{G}(V)$$


In other words, we can interpret a section for this pre-sheaf as a pair of a map $U\to V$ in $W_U$ together with a section $s \in \mathscr{G}(V)$, where another map $U\to V'$ and section $s' \in \mathscr{G}(V')$ is equivalent to this if there exists maps $k:V''\to V$ and $g:V''\to V'$ in $W_U$ such that $\mathscr{G}(k)(s) = \mathscr{G}(k)(s')$ in $\mathscr{G}(V'')$.

Finally, we can use the zeroth Cech-cohomology to express the sheafification, and so for $U\to X$ in $\mathcal{C}/X$, we have that
$$
\begin{align*}
\pi^*\mathscr{G}(U) &= \lim_{\to,S \in J(U)}\check{H}^0(S,\mathscr{G}\otimes_{\mathcal{D}/Y}y\phi) \\
&= \lim_{\to,S \in J(U)}\left\{[(D\to V_f,s_f)]_{(f:D\to U \in S)} \in \prod_{f \in S}(\mathscr{G}\otimes_{\mathcal{D}/Y}y\phi)(D)\;\Bigg\vert\; s_f\vert_{V_f\times_YV_g} = s_g\vert_{V_f\times_YV_g} \right\}
\end{align*}$$
where the colimit is taken over the poset category of covers ordered by refinement. 

An important aspect of this construction is that it is functorial, up to natural isomorphism.

>[!proposition] Morphisms of Sites Induced by Pullbacks Compose
>If $\pi:X\to Y$ and $\rho:Y\to Z$ are maps of schemes which induce morphisms of sites $(\mathcal{C}/X)_E,(\mathcal{D}/Y)_{E'},(\mathcal{E}/Z)_{E''}$ via-pullback, then the composite geometric morphism induced by the morphisms of sites is that given by $\rho\circ \pi:X\to Z$.

^eca82e

`\begin{proof}`
Since pullbacks can be done iteratively, we have that $\pi^*\circ \rho^* \cong (\rho\circ \pi)^*$. As the direct image functor on sheaves is given by pre-composition by these functors, and adjoint are unique up to unique natural isomorphism, we have that the composite of the inverse image functors is naturally isomorphic to the inverse image functor induced by $\rho\circ \pi$.
`\end{proof}`

## Stalks and Direct and Inverse Image Sheaves

As in classical sheaf theory on spaces, an important tool for us will be the reduction of certain statements to equivalent formulations in terms of stalks. Recall that a point of a Grothendieck topos is a geometric morphism $p:\mathsf{Set}\to \mathsf{Sh}(\mathcal{C},J)$, which is equivalent to a functor $p^*\circ \mathfrak{a}y:\mathcal{C}\to \mathsf{Set}$ which is filtering and continuous. For example, if we have a site of the form $(\mathcal{C}/X)_E$, as we have been considering thus far, such a functor $p:\mathcal{C}/X\to \mathsf{Set}$ being filtering means that
1. For any $U\to X$ and $V\to X$ in $\mathcal{C}/X$, together with $a \in p(U)$ and $b \in p(V)$, there exists a $W\to X$ in $\mathcal{C}/X$ with maps $k:W\to U$ and $h:W\to V$, as well as $c \in p(W)$, such that $p(k)(c) = a$ and $p(h)(c) = b$.
2. For any pair of maps $f,g:U\to V$ in $\mathcal{C}/X$, and any $a \in p(U)$ such that $p(f)(a) = p(g)(a)$, there exists $k:W\to U$ in $\mathcal{C}/X$ and $b \in p(W)$ such that $p(k)(b)=a$ and $f\circ k = g\circ k$. 
On the other hand, $p$ being continuous means that for any cover $\{U_i\to U\}$ by $E$-maps in $\mathcal{C}/X$,
$$p(U) \cong \lim_{\to,U_i\to U}p(U_i)$$

Let us briefly recall the motivation for this definition of a point of a topos. First, if $\{*\}$ is a one-point space, or $\mathbb{1}$ is the free-living arrow (i.e. the category with two objects and one non-identity morphism between them) with the trivial topology, then $\mathsf{Sh}(\{*\})\cong \mathsf{Sh}(\mathbb{1}) \cong \mathsf{Set}$. Additionally, in the topological setting, if $X$ is a space which is suitably separated (for example Sober or Hausdorff), then any geometric morphism $p:\mathsf{Sh}(\{*\})\to \mathsf{Sh}(X)$ is determined by a map of topological spaces $x:\{*\}\to X$, which is the same as a point of $X$.

Next we move on to studying stalks of sheaves at points.

>[!def] Stalks of Sheaves
>If $\mathscr{F}$ is a sheaf on a site $(\mathcal{C},J)$ and $p:\mathsf{Set}\to \mathsf{Sh}(\mathcal{C},J)$ is a point, then the stalk of $\mathscr{F}$ at $p$ is defined to be
>$$\mathscr{F}_p := p^*\mathscr{F}$$


Equivalently, if we are given the point as a continuous filtering functor $p:\mathcal{C}\to \mathsf{Set}$, then the stalk of a sheaf $\mathscr{F}$ can be computed via the colimit
$$\mathscr{F}_p \cong \text{colim}\left(\left(\int_{\mathcal{C}}p\right)^{op}\xrightarrow{\pi_0^{op}}\mathcal{C}^{op}\xrightarrow{\mathscr{F}}\mathsf{Set}\right)$$
over the opposite of the category of elements of $p$.

To see that these notions of stalk are equivalent suppose we start with a point $p:\mathsf{Set}\to \mathsf{Sh}(\mathcal{C},J)$ and form the associated continuous filtering functor $p^*\circ \mathfrak{a}y:\mathcal{C}\to \mathsf{Set}$. Then from Sheaves in Geometry and Logic[^2] we have that $p^*\cong -\otimes_{\mathcal{C}}(p^*\circ \mathfrak{a}y)$, and so
$$p^*\mathscr{F} \cong \mathscr{F}\otimes_\mathcal{C}(p^*\circ \mathfrak{a}y) = \text{colim}\left(\coprod_{C\to C':\mathcal{C},s \in p^*(\mathfrak{a}y^C)}\mathscr{F}(C')\rightrightarrows \coprod_{C:\mathcal{C},s\in p^*(\mathfrak{a}y^C)}\mathscr{F}(C)\right)$$
where one arrow is given by sending the triple $(f:C\to C',s \in p^*(\mathfrak{a}y^C),t \in \mathscr{F}(C'))$ to $(C,s,\mathscr{F}(f)(t))$ while the other arrow sends the triple to $(C',p^*(\mathfrak{a}y^f)(s),t)$. However, this colimit on the right is exactly the data of the colimit
$$\mathscr{F}_p := \text{colim}\left(\left(\int_{\mathcal{C}}p^*\circ \mathfrak{a}y\right)^{op}\xrightarrow{\pi_0^{op}}\mathcal{C}^{op}\xrightarrow{\mathscr{F}}\mathsf{Set}\right)$$


>[!example]
>If $x$ is a point of the scheme $X$, as a topological space, and $u_x:\overline{x}\to X$ is a corresponding geometric point, where $\overline{x}$ is given by the spectra of a separably closed field containing $k(x)$, then $u_x$ induces a geometric morphism $\mathsf{Sh}(\overline{x}_{et})\to \mathsf{Sh}(X_{et})$, where $\mathsf{Sh}(\overline{x}_{et})\cong \mathsf{Set}$, and the inverse image functor is a stalk functor.

By [[Inverse and Direct Image Sheaves#^eca82e]] we have the following simple description of stalks of inverse images of sheaves.[^1]

>[!proposition]
>Let $\pi:X\to Y$ be a morphism of schemes which induces a morphism of sites $\phi:=\pi^*:(\mathcal{D}/Y)_{E'}\to (\mathcal{C}/X)_E$:
>1. For any sheaf $\mathscr{F}$ on $(\mathcal{D}/Y)_{E'}$, and any point $u_x:x\to X$, we have an isomorphism $$(\phi^*\mathscr{F})_x\cong \mathscr{F}_{\pi(x)}$$
>2. If $\pi$ is quasi-compact and we are working with the etale site then for any point $y \in Y$, with $\overline{y} = \mathsf{Spec}(k(y)_{sep})$, if $f:\mathsf{Spec}\mathcal{O}_{Y,\overline{y}}^{sh}\to Y$ is the canonical morphism, then for any sheaf $\mathscr{F}$ on $X$, $$(\pi_*\mathscr{F})_\overline{y} \cong \Gamma(X\times_Y\mathsf{Spec}\mathcal{O}_{Y,\overline{y}}^{sh},{f'}^*\mathscr{F})$$
>where $f'$ is the map obtained from $f$ by pullback along $Y$.


As a consequence we obtain a nice description of stalks for sheaves obtained by pushing forward along closed/open immersions.

>[!corollary] Stalks for Open/Closed Immersions
>1. Let $i:Z\hookrightarrow X$ be a closed immersion, and let $\mathscr{F}$ be a sheaf on $Z_{et}$. For $x \in X$, and $\overline{x} = \mathsf{Spec}(k(x)_{sep})$, we have $$(i_*\mathscr{F})_\overline{x} = \left\{\begin{array}{cc} 0 & x\notin i(Z) \\ \mathscr{F}_{\overline{x_0}} & \exists x_0 \in Z,i(x_0) = x \end{array}\right.$$
>2. Let $j:U\hookrightarrow X$ be an open immersion, and let $\mathscr{F}$ be a sheaf on $U_{et}$. For $x_0 \in U$, $(j_*\mathscr{F})_\overline{j(x_0)} = \mathscr{F}_{\overline{x_0}}$.
>3. If $\pi:X\to Y$ is a finite morphism and $\mathscr{F}$ is a sheaf on $X_{et}$, then for any $y \in Y$, $(\pi_*\mathscr{F})_\overline{y} = \prod_{x \in \pi^{-1}(\{y\})}\mathscr{F}_\overline{x}^{d(x)}$, where $d(x)$ is the separable degree of $k(x)$ over $k(y)$.



## Splitting Sheaves Along Closed and Open Subschemes

Moving forward let $X$ be a scheme, $i:Z\hookrightarrow X$ a closed subscheme and $j:U\hookrightarrow X$ an open subscheme, with $i(Z) = X\backslash j(U)$. Let $\mathscr{F}$ be a sheaf on $X_{et}$. Then we have a the unit of the adjunction $\eta:\mathscr{F}\to j_*j^*\mathscr{F}$, which upon whiskering with $i^*$ gives a morphism $i^*\eta:i^*\mathscr{F}\to i^*j_*j^*\mathscr{F}$. We aim to show that the triple $(i^*\mathscr{F},j^*\mathscr{F},i^*\eta)$ determines $\mathscr{F}$ in the sense that we obtain an equivalence of categories.

Let $\mathsf{T}(X_{et},U_{et},Z_{et})$ be the category of triples $(F_1,F_2,\phi)$, where $F_1$ is a sheaf on $Z_{et}$, $F_2$ is a sheaf on $U_{et}$, and $\phi$ is a map of sheaves $F_1\to i^*j_*F_2$. A morphism between triples $(F_1,F_2,\phi)$ and $(G_1,G_2,\psi)$ is a pair of morphisms $\omega_1:F_1\to G_1$ and $\omega_2:F_2\to G_2$ making the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7BF_1%7D%20%26%20%7Bi%5E*j_*F_2%7D%20%5C%5C%0A%09%7BG_1%7D%20%26%20%7Bi%5E*j_*G_2%7D%0A%09%5Carrow%5B%22%5Cphi%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B%5Comega_1%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7Bi%5E*j_*%5Comega_2%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Cpsi%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{F_1} &amp; {i^*j_*F_2} \\
	{G_1} &amp; {i^*j_*G_2}
	\arrow[&quot;\phi&quot;, from=1-1, to=1-2]
	\arrow[&quot;{\omega_1}&quot;', from=1-1, to=2-1]
	\arrow[&quot;{i^*j_*\omega_2}&quot;, from=1-2, to=2-2]
	\arrow[&quot;\psi&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

>[!thm]
>The natural map $(i^*,j^*):\mathsf{Sh}(X_{et})\to \mathsf{T}(X_{et},U_{et},Z_{et})$ is an equivalence of categories.

`\begin{proof}`
To finish defining the functor we send a map $\psi:\mathscr{F}\to \mathscr{G}$ to the pair $(i^*\psi,j^*\psi)$. We now define an inverse functor $s:\mathsf{T}(X_{et},U_{et})\to \mathsf{Sh}(X_{et})$ by sending a triple $(F_1,F_2,\phi)$ to the pullback
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7BS(F_1%2CF_2%2C%5Cphi)%7D%20%26%20%7Bj_*F_2%7D%20%5C%5C%0A%09%7Bi_*F_1%7D%20%26%20%7Bi_*i%5E*j_*F_2%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22unit%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7Bi_*%5Cphi%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{S(F_1,F_2,\phi)} &amp; {j_*F_2} \\
	{i_*F_1} &amp; {i_*i^*j_*F_2}
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[&quot;unit&quot;, from=1-2, to=2-2]
	\arrow[&quot;{i_*\phi}&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

The universal property of the pullback sends a pair $(\omega_1,\omega_2):(F_1,F_2,\phi)\to (G_1,G_2,\psi)$ to a unique morphism $s(\omega_1,\omega_2):s(F_1,F_2,\phi)\to s(G_1,G_2,\psi)$. As it is constructed from this universal property, we have that $s$ is functorial. 

Now, by naturality f the unit for the $i^*\dashv i_*$ adjunction we have a morphism $\mathscr{F}\to s(i^*,j^*)\mathscr{F}$ given applying the universal property of the pullback to the commuting square
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7B%5Cmathcal%7BF%7D%7D%20%26%20%7Bj_*j%5E*%5Cmathcal%7BF%7D%7D%20%5C%5C%0A%09%7Bi_*i%5E*%5Cmathcal%7BF%7D%7D%20%26%20%7Bi_*i%5E*j_*j%5E*%5Cmathcal%7BF%7D%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{\mathcal{F}} &amp; {j_*j^*\mathcal{F}} \\
	{i_*i^*\mathcal{F}} &amp; {i_*i^*j_*j^*\mathcal{F}}
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[from=2-1, to=2-2]
\end{tikzcd}
" /></p>

To show that this is an isomorphism it suffices to show that it is a pullback square. Since stalk functors are left exact and the family of stalk functors is conservative for the etale site, we can show this property on the level of stalks. At a point $x \in U$ we obtain the pullback square
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7B%5Cmathcal%7BF%7D_%7B%5Coverline%7Bx%7D%7D%7D%20%26%20%7B%5Cmathcal%7BF%7D_%7B%5Coverline%7Bx%7D%7D%7D%20%5C%5C%0A%090%20%26%200%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{\mathcal{F}_{\overline{x}}} &amp; {\mathcal{F}_{\overline{x}}} \\
	0 &amp; 0
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[from=2-1, to=2-2]
\end{tikzcd}
" /></p>

On the other hand, if $x \in Z$ then the square is
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7B%5Cmathcal%7BF%7D_%7B%5Coverline%7Bx%7D%7D%7D%20%26%20%7B(j_*j%5E*%5Cmathcal%7BF%7D)_%7B%5Coverline%7Bx%7D%7D%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BF%7D_%7B%5Coverline%7Bx%7D%7D%7D%20%26%20%7B(j_*j%5E*%5Cmathcal%7BF%7D)_%7B%5Coverline%7Bx%7D%7D%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{\mathcal{F}_{\overline{x}}} &amp; {(j_*j^*\mathcal{F})_{\overline{x}}} \\
	{\mathcal{F}_{\overline{x}}} &amp; {(j_*j^*\mathcal{F})_{\overline{x}}}
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[from=2-1, to=2-2]
\end{tikzcd}
" /></p>

which is again a pullback square. A similar check on the level of morphisms completes the proofs.
`\end{proof}`

>[!corollary]
>If $i:Z\hookrightarrow X$ is a closed immersion, then $i_*:\mathsf{Sh}(Z_{et})\to \mathsf{Sh}(X_{et})$ induces an equivalence of categories between sheaves on $Z_{et}$ and sheaves on $X_{et}$ with support in $i(Z)$.

Under this equivalence an exact sequence in $\mathsf{T}(X_{et},U_{et},Z_{et})$ corresponds to a pair of exact sequences in $\mathsf{Sh}(Z_{et})$ and $\mathsf{Sh}(U_{et})$. For instance, we have an exact sequence
$$0\to (0,j^*\mathscr{F},0)\to (i^*\mathscr{F},j^*\mathscr{F},\phi_\mathscr{F})\to (i^*\mathscr{F},0,0)\to 0$$
### Six-Functors

Identifying $\mathsf{Sh}(X_{et})$ with $\mathsf{T}(X_{et},U_{et},Z_{et})$ for some open subscheme $j:U\hookrightarrow X$ and closed subscheme $i:Z\hookrightarrow X$, $i(Z) = X\backslash j(U)$, we can re-interpret our direct and inverse image functors, and introduce two additional functors. Namely, we have that $i^*$ sends $(F_1,F_2,\phi)\mapsto F_1$, $j^*$ sends $(F_1,F_2,\phi)\mapsto F_2$, $i_*$ sends $F_1\mapsto (F_1,0,0)$, and $j_*$ sends $F_2\mapsto (i^*j_*F_2,F_2,1)$. In addition to these functors we define $j_!$ which maps $F_2 \mapsto (0,F_2,0)$ (the skyscraper functor) and $i^!$ which maps $(F_1,F_2,\phi)\to \ker\phi$, which we think of as a subsheaf of sections of the original sheaf with support in $Z$.


>[!proposition]
>1. $i^*\dashv i_*\dashv i^!$ and $j_!\dashv j^*\dashv j_*$
>2. $j_!$ is left-exact
>3. The composites $i^*j_!,i^!j_!,i^!j_*,j^*i_*$ are zero
>4. $i_*$ and $j_*$ are fully-faithful and a sheaf $\mathscr{F}$ on $X_{et}$ has support in $Z$ if and only if $\mathscr{F}\cong i_*i^*\mathscr{F}$
>5. $j_*,j^*,i^!,$ and $i_*$ map injectives to injectives.

`\begin{proof}`
For claim **(1)** we need only show $i_*\dashv i^!$ and $j_!\dashv j^*$. For $(F_1,F_2,\phi)$, we have a natural map $(\ker\phi,0,0)\to (F_1,F_2,\phi)$ given by the kernel. Further, if $G_1$ is any sheaf on $Z_{et}$ with map $(\omega,0):(G_1,0,0)\to (F_1,F_2,\phi)$, then we have the commuting diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7BG_1%7D%20%26%200%20%5C%5C%0A%09%7BF_1%7D%20%26%20%7Bi%5E*j_*F_2%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Comega%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Cphi%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{G_1} &amp; 0 \\
	{F_1} &amp; {i^*j_*F_2}
	\arrow[from=1-1, to=1-2]
	\arrow[&quot;\omega&quot;', from=1-1, to=2-1]
	\arrow[from=1-2, to=2-2]
	\arrow[&quot;\phi&quot;', from=2-1, to=2-2]
\end{tikzcd}
" /></p>

so by the universal property o the kernel we have a unique map $\omega^\flat:G_1\to \ker\phi$ which factors $\omega$ through the kernel, and so $i_*\dashv i^!$.

On the other hand, we have a natural map $(0,F_2,0)\to (F_1,F_2,\phi)$ given by the identity, and for any sheaf $G_2$ on $U_{et}$ with map $(0,G_2,0)\to (F_1,F_2,\phi)$, the same map can be used to factor it as $(0,G_2,0)\to (0,F_2,0)\to (F_1,F_2,\phi)$, and so $j_!\dashv j^*$. 

Property **(2)** comes from the structure of exact sequences in $\mathsf{T}(X_{et},U_{et},Z_{et})$, and property **(3)** is obvious. For **(4)** the only non-immediate piece is the fully-faithfulness of $j_*$, but if $(\omega_1,\omega_2):(i^*j_*F_2,F_2,1)\to (i^*j_*G_2,G_2,1)$ is a map between functors in the image of $j_*$, then we have that 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7Bi%5E*j_*F_2%7D%20%26%20%7Bi%5E*j_*F_2%7D%20%5C%5C%0A%09%7Bi%5E*j_*G_2%7D%20%26%20%7Bi%5E*j_*G_2%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%7B%5Comega_1%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7Bi%5E*j_*%5Comega_2%7D%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{i^*j_*F_2} &amp; {i^*j_*F_2} \\
	{i^*j_*G_2} &amp; {i^*j_*G_2}
	\arrow[from=1-1, to=1-2]
	\arrow[&quot;{\omega_1}&quot;', from=1-1, to=2-1]
	\arrow[&quot;{i^*j_*\omega_2}&quot;, from=1-2, to=2-2]
	\arrow[from=2-1, to=2-2]
\end{tikzcd}
" /></p>

which implies $\omega_1 = i^*j_*\omega_2$, and so $j_*$ is fully faithful. Finally, property **(5)** is a general fact about functors between abelian categories with exact left adjoints.
`\end{proof}`

## Cartesian Lifts and Fibered Categories

A large class of important examples for geometric morphisms, and hence inverse and direct image functors, come from base change between slice categories on topoi. In this section we will prove that if a category has pullbacks, then it has a notion of base-change between slice categories. Additionally, we will prove that base change always has a left-adjoint, and that in the case of categories such as topoi which locally have exponential objects, the base change also has a right-adjoint. 

We will begin by constructing base-change functors out of the theory of fibered categories[^5]. To begin we must define the notion of a cartesian lift.

>[!def] (Strong) Cartesian Lifts
>Let $p:\mathcal{E}\to \mathcal{B}$ be a functor. A **(strong) cartesian lift** of an arrow $f:B\to B'$ in $\mathcal{B}$ is an arrow $f^*_X:f^*X\to X$ in $\mathcal{E}$ above $f$ such that for any $g:Y\to X$ in $\mathcal{E}$ and any filling $h:p(Y)\to B$ of the triangle in $\mathcal{B}$, we have a unique filling of the triangle in $\mathcal{E}$:
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%20%20%20%20%09Y%20%5C%5C%20%20%20%20%09%7Bf%5E*X%7D%20%26%20X%20%5C%5C%20%20%20%20%09%7Bp(Y)%7D%20%5C%5C%20%20%20%20%09B%20%26%20%7BB'%7D%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D4-1%2C%20to%3D4-2%5D%20%20%20%20%09%5Carrow%5B%22p(g)%22%2C%20from%3D3-1%2C%20to%3D4-2%5D%20%20%20%20%09%5Carrow%5B%22h%22'%2C%20from%3D3-1%2C%20to%3D4-1%5D%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D1-1%2C%20to%3D2-2%5D%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists!%5Cwidetilde%7Bh%7D%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-1%5D%20%20%20%20%09%5Carrow%5Bdotted%2C%20from%3D2-1%2C%20to%3D3-1%5D%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}    	Y \\    	{f^*X} &amp; X \\    	{p(Y)} \\    	B &amp; {B'}    \arrow[&quot;f&quot;', from=4-1, to=4-2]    	\arrow[&quot;p(g)&quot;, from=3-1, to=4-2]    \arrow[&quot;h&quot;', from=3-1, to=4-1]    	\arrow[&quot;g&quot;, from=1-1, to=2-2]    \arrow[&quot;{f^*_X}&quot;', from=2-1, to=2-2]    	\arrow[&quot;{\exists!\widetilde{h}}&quot;', dashed, from=1-1, to=2-1]    	\arrow[dotted, from=2-1, to=3-1]    \end{tikzcd}" /></p>

Moving forward we drop the adjective **strong** and just refer to them as **cartesian lifts**. Cartesian lifts now let us characterize fibrations of categories.

>[!def] Fibered Categories
>A **fibration** of categories is a functor $p:\mathcal{E}\to \mathcal{B}$ such that for every $f:B\to B'$ in $\mathcal{B}$, and every $X \in p^{-1}(B')$, there exists a cartesian lift of $f$ with codomain $X$, $f^*_X:f^*X\to X$.
>
>An **opfibration** of categories is a functor $p:\mathcal{E}\to \mathcal{B}$ such that for every $f:B\to B'$ in $\mathcal{B}$, and every $X \in p^{-1}(B)$, there exists an **opcartesian lift** of $f$ with domain $X$, $f_{!,X}:X\to f_!X$.

One of the many reasons for studying fibrations, also known as fibered categories, is that they provide a sensible way of producing functors between fibers above objects in the base category $\mathcal{B}$. Here, the fiber $p^{-1}(B)$ above an object $B \in \mathcal{B}_0$ is the subcategory of $\mathcal{E}$ consisting of objects $X \in \mathcal{E}_0$ such that $p(X) = B$ and arrows $f:X\to Y$ between such objects such that $p(f) = 1_B$.


Provided we have a choice of cartesian lift above each arrow $f:B\to B'$ in $\mathcal{B}$ and each $X \in p^{-1}(B')_0$, these cartesian lifts provide base-change functors between the fibers. Classically a choice of cartesian lifts for a fibration is called a **cleavage**.

>[!proposition] Base Change
>Let $p:\mathcal{E}\to \mathcal{B}$ be a fibration with a cleavage. Then each $f:A\to B$ in $\mathcal{B}$ induces a functor $f^*:p^{-1}(B)\to p^{-1}(A)$.

^9803ab

`\begin{proof}`
Fix $f:A\to B$ in $\mathcal{B}$. For each $X \in p^{-1}(B)_0$ we have a specified cartesian lift $f^*_X:f^*X\to X$, where $f^*X$ lies above $A$. We define $f^*:p^{-1}(B)\to p^{-1}(A)$ on objects by $f^*(X) := \text{dom}(f^*_X)$. Next, let $g:Y\to X$ be a map in $p^{-1}(B)$. By the defining property of a cartesian lift we obtain a unique filling above the identity:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%20%20%20%20%09%7Bf%5E*Y%7D%20%26%20Y%20%26%26%20A%20%26%20B%20%5C%5C%0A%20%20%20%20%09%26%20%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_Y%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22g%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists%20!f%5E*g%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5Bshorten%20%3D19pt%2C%20shorten%20%3D19pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D0%2C%20to%3D1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
    	{f^*Y} &amp; Y &amp;&amp; A &amp; B \\
    	&amp; {f^*X} &amp; X &amp;&amp; A &amp; B
    	\arrow[&quot;{f^*_Y}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;g&quot;, from=1-2, to=2-3]
    	\arrow[&quot;{f^*_X}&quot;', from=2-2, to=2-3]
    	\arrow[&quot;{\exists !f^*g}&quot;', dashed, from=1-1, to=2-2]
    	\arrow[&quot;f&quot;, from=1-4, to=1-5]
    	\arrow[Rightarrow, no head, from=1-5, to=2-6]
    	\arrow[&quot;f&quot;', from=2-5, to=2-6]
    	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=2-5]
    	\arrow[shorten =19pt, shorten =19pt, dotted, tail reversed, from=0, to=1]
    \end{tikzcd}
" /></p>
We define $f^*(g)$ to be this unique filling. By uniqueness, $f^*1_X = 1_{f^*X}$ since it fills the diagram:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%20%20%20%20%09%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%20%5C%5C%0A%20%20%20%20%09%26%20%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20Rightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5Bshorten%20%3D13pt%2C%20shorten%20%3D13pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D0%2C%20to%3D1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
    	{f^*X} &amp; X &amp;&amp; A &amp; B \\
    	&amp; {f^*X} &amp; X &amp;&amp; A &amp; B
    	\arrow[&quot;{f^*_X}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, Rightarrow, no head, from=1-2, to=2-3]
    	\arrow[&quot;{f^*_X}&quot;', from=2-2, to=2-3]
    	\arrow[&quot;f&quot;, from=1-4, to=1-5]
    	\arrow[Rightarrow, no head, from=1-5, to=2-6]
    	\arrow[&quot;f&quot;', from=2-5, to=2-6]
    	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, Rightarrow, no head, from=1-4, to=2-5]
    	\arrow[Rightarrow, no head, from=1-1, to=2-2]
    	\arrow[shorten =13pt, shorten =13pt, dotted, tail reversed, from=0, to=1]
    \end{tikzcd}
" /></p>
Finally, if $h:Z\to Y$ is another map in the fiber $p^{-1}(B)$, then we have the composite diagram:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7Bf%5E*Z%7D%20%26%20Z%20%26%26%20A%20%26%20B%20%5C%5C%0A%09%26%20%7Bf%5E*Y%7D%20%26%20Y%20%26%26%20A%20%26%20B%20%5C%5C%0A%09%26%26%20%7Bf%5E*X%7D%20%26%20X%20%26%26%20A%20%26%20B%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_Y%7D%22%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D2-3%2C%20to%3D3-4%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_X%7D%22'%2C%20from%3D3-3%2C%20to%3D3-4%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists%20!f%5E*g%7D%22'%2C%20dashed%2C%20from%3D2-2%2C%20to%3D3-3%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D2-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-6%2C%20to%3D3-7%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D3-6%2C%20to%3D3-7%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-5%2C%20to%3D3-6%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf%5E*_Z%7D%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%20%20%20%20%09%5Carrow%5B%22h%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists!f%5E*h%7D%22'%2C%20dashed%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5B%22f%22%2C%20from%3D1-4%2C%20to%3D1-5%5D%0A%20%20%20%20%09%5Carrow%5Bshorten%20%26lt%3B%3D14pt%2C%20shorten%20%26gt%3B%3D14pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D2-3%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-5%2C%20to%3D2-6%5D%0A%20%20%20%20%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D1-4%2C%20to%3D2-5%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cexists%20!f%5E*(g%5Ccirc%20h)%7D%22'%2C%20bend%20right%20%3D%2060%2C%20dashed%2C%20from%3D1-1%2C%20to%3D3-3%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{f^*Z} &amp; Z &amp;&amp; A &amp; B \\
	&amp; {f^*Y} &amp; Y &amp;&amp; A &amp; B \\
	&amp;&amp; {f^*X} &amp; X &amp;&amp; A &amp; B
    	\arrow[&quot;{f^*_Y}&quot;, from=2-2, to=2-3]
    	\arrow[&quot;g&quot;, from=2-3, to=3-4]
    	\arrow[&quot;{f^*_X}&quot;', from=3-3, to=3-4]
    	\arrow[&quot;{\exists !f^*g}&quot;', dashed, from=2-2, to=3-3]
    	\arrow[&quot;f&quot;, from=2-5, to=2-6]
    	\arrow[Rightarrow, no head, from=2-6, to=3-7]
    	\arrow[&quot;f&quot;', from=3-6, to=3-7]
    	\arrow[Rightarrow, no head, from=2-5, to=3-6]
    	\arrow[&quot;{f^*_Z}&quot;, from=1-1, to=1-2]
    	\arrow[&quot;h&quot;, from=1-2, to=2-3]
    	\arrow[&quot;{\exists!f^*h}&quot;', dashed, from=1-1, to=2-2]
    	\arrow[&quot;f&quot;, from=1-4, to=1-5]
    	\arrow[shorten &amp;lt;=14pt, shorten &amp;gt;=14pt, dotted, tail reversed, from=2-3, to=2-5]
    	\arrow[Rightarrow, no head, from=1-5, to=2-6]
    	\arrow[Rightarrow, no head, from=1-4, to=2-5]
    	\arrow[&quot;{\exists !f^*(g\circ h)}&quot;', bend right = 60, dashed, from=1-1, to=3-3]
    \end{tikzcd}
" /></p>
where by uniqueness of the filling $f^*(g\circ h) = f^*g\circ f^*h$. Thus $f^*:p^{-1}(B)\to p^{-1}(A)$ is a functor.
`\end{proof}`

The primary example of interest for us is called the standard fibration. For a category $\mathcal{C}$, we always have a category $\mathcal{C}^2$ which has arrows, $f:A\to B$, as objects, and commutative squares between arrows
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09A%20%26%20B%20%5C%5C%0A%09X%20%26%20Y%0A%09%5Carrow%5B%22f%22%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22g%22'%2C%20from%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22k%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	A &amp; B \\
	X &amp; Y
	\arrow[&quot;f&quot;, from=1-1, to=1-2]
	\arrow[&quot;h&quot;', from=1-1, to=2-1]
	\arrow[&quot;g&quot;', from=2-1, to=2-2]
	\arrow[&quot;k&quot;, from=1-2, to=2-2]
\end{tikzcd}
" /></p>
as maps. Additionally, we have a natural projection functor $\pi_1:\mathcal{C}^2\to \mathcal{C}$ given by sending arrows to their codomains and squares to the maps between codomains on the right edge of the square. 

When $\mathcal{C}$ has pullbacks the functor $\pi_1$ is a fibration of categories, where the cartesian lifts are pullback squares. Indeed, going through our definition of a cartesian arrow we obtain that a filling corresponds to the closing of a wedge, where the closing map is the unique one induced by the pullback
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%26%20X%20%26%26%20M%20%5C%5C%0A%09Y%20%26%20A%20%26%20N%20%5C%5C%0A%09B%20%26%20M%20%26%26%20Y%20%26%26%20B%0A%09%5Carrow%5B%22g%22'%7Bpos%3D0.2%7D%2C%20dashed%2C%20from%3D2-2%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22k%22'%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22h%22%2C%20from%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22f%22'%2C%20from%3D1-2%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22k%22'%2C%20from%3D3-4%2C%20to%3D3-6%5D%0A%09%5Carrow%5B%22s%22%2C%20from%3D2-3%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22%5Cell%22%2C%20from%3D3-2%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22r%22'%2C%20from%3D2-3%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%5Cell%22%2C%20from%3D1-4%2C%20to%3D3-6%5D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22t%22'%2C%20from%3D1-4%2C%20to%3D3-4%5D%0A%09%5Carrow%5B%22t%22'%7Bpos%3D0.2%7D%2C%20from%3D3-2%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7B%5Cexists!%5Cwidetilde%7Bt%7D%7D%22'%2C%20dashed%2C%20from%3D2-3%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Clrcorner%22%7Banchor%3Dcenter%2C%20pos%3D0.125%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1-2%2C%20to%3D3-1%5D%0A%09%5Carrow%5Bshorten%20%3D12pt%2C%20dotted%2C%20tail%20reversed%2C%20from%3D2-3%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	&amp; X &amp;&amp; M \\
	Y &amp; A &amp; N \\
	B &amp; M &amp;&amp; Y &amp;&amp; B
	\arrow[&quot;g&quot;'{pos=0.2}, dashed, from=2-2, to=3-1]
	\arrow[&quot;k&quot;', from=2-1, to=3-1]
	\arrow[&quot;h&quot;, from=1-2, to=2-2]
	\arrow[&quot;f&quot;', from=1-2, to=2-1]
	\arrow[&quot;k&quot;', from=3-4, to=3-6]
	\arrow[&quot;s&quot;, from=2-3, to=3-2]
	\arrow[&quot;\ell&quot;, from=3-2, to=3-1]
	\arrow[&quot;r&quot;', from=2-3, to=2-2]
	\arrow[&quot;\ell&quot;, from=1-4, to=3-6]
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;t&quot;', from=1-4, to=3-4]
	\arrow[&quot;t&quot;'{pos=0.2}, from=3-2, to=2-1]
	\arrow[&quot;{\exists!\widetilde{t}}&quot;', dashed, from=2-3, to=1-2]
	\arrow[&quot;\lrcorner&quot;{anchor=center, pos=0.125, rotate=-90}, draw=none, from=1-2, to=3-1]
	\arrow[shorten =12pt, dotted, tail reversed, from=2-3, to=0]
\end{tikzcd}
" /></p>
A cleavage is simply a choice of pullback for each diagram. Then for $C \in \mathcal{C}_0$, the fiber category $\pi_1^{-1}(C)$ is isomorphic to the slice category $\mathcal{C}/C$. It follows that given a cleavage for $\pi_1$, [[Basic Fibered Categories#^9803ab]] implies that we have well-defined base-change functors $f^*:\mathcal{C}/B\to \mathcal{C}/A$ for $f:A\to B$ in $\mathcal{C}$ induced by pullback.


Dually to all of the definitions and results so far we have a notion of opfibrations of categories where we consider opcartesian lifts which have the dual property. Given an opfibration $p:\mathcal{E}\to \mathcal{B}$ with opcleavage we denote the induced functor on fibers for a map $f:A\to B$ by $f_!:p^{-1}(A)\to p^{-1}(B)$. We will now show that a fibration is also an opfibration, and vice-versa, if and only if its pullback functors have left-adjoints[^4].

>[!proposition] Fibration v Opfibration
>A fibration $p:\mathcal{E}\to \mathcal{B}$ is an opfibration if and only if all pullback functors $f^*:p^{-1}(B)\to p^{-1}(A)$, for $f:A\to B$, have left adjoints.

`\begin{proof}`
Let $f:A\to B$ be a map in $\mathcal{B}$. Note that by the classification of cartesian lifts applied to identity fillings, we have a natural bijection between maps $Y\to X$ in $\mathcal{E}$ lying over $f$ and maps $Y\to f^*X$ in $p^{-1}(A)$. On the other hand, the dual property for opcartesian lifts gives a bijection between maps $Y\to X$ over $f$ and maps $f_!Y\to X$ in $p^{-1}(B)$. In other words, we have the natural bijection
$$p^{-1}(B)(f_!Y,X)\cong p^{-1}(B)(Y,f^*X)$$
so the existence of opcartesian lifts is equivalent to the existence of right adjoints, and vice-versa if we start with an opfibration.
`\end{proof}`

The standard fibration $\pi_1:\mathcal{C}^2\to \mathcal{C}$ has left-adjoints for all of its base-change functors, and so itself is also an opfibration. Indeed, given $f:A\to B$, the left adjoint to $f^*$, $f_!:\mathcal{C}/A\to \mathcal{C}/B$ is given by post-composition. Indeed, the universal property of the pullback tells us that the two-dashed maps in the diagram

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7BA%5Ctimes_BX%7D%20%26%26%20Y%20%5C%5C%0A%09A%20%26%20X%20%5C%5C%0A%09%26%20B%0A%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22g%22%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%09%5Carrow%5B%22h%22'%2C%20from%3D1-3%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-3%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{A\times_BX} &amp;&amp; Y \\
	A &amp; X \\
	&amp; B
	\arrow[&quot;f&quot;', from=2-1, to=3-2]
	\arrow[&quot;g&quot;, from=2-2, to=3-2]
	\arrow[&quot;h&quot;', from=1-3, to=2-1]
	\arrow[from=1-1, to=2-1]
	\arrow[from=1-1, to=2-2]
	\arrow[dashed, from=1-3, to=2-2]
	\arrow[dashed, from=1-3, to=1-1]
\end{tikzcd}
" /></p>
are equivalent, so having one immediately implies having the other. 


Thus, $f_!\dashv f^*$, so in this context $f^*$ always preserves limits since it has a left adjoint. In order to obtain a geometric morphism, however, we still need a right adjoint for $f^*$. This doesn't exist in general, but as we will now show, it will for Grothendieck topoi, since the standard fibration has right adjoints for its base-change functors if the base category is locally cartesian closed.

>[!def] Cartesian Closed
>A category $\mathcal{C}$ with finite products is said to be **cartesian closed** if for every object $C \in \mathcal{C}$, the product functor $-\times C:\mathcal{C}\to \mathcal{C}$ has a right adjoint, $(-)^C$.  
>
>$\mathcal{C}$ is said to be **locally cartesian closed** if for every $C \in \mathcal{C}_0$, $\mathcal{C}/C$ is cartesian closed.

With locally cartesian closedness we can now construct right adjoints for base-change functors.

>[!proposition] Right Adjoint to Base Change
>Let $\mathcal{C}$ be a locally cartesian closed category with pullbacks. Then the base-change functors for the standard fibration $\pi_1:\mathcal{C}^2\to \mathcal{C}$ have right adjoints.

`\begin{proof}`
Let $f:A\to B$, and let $f^*:\mathcal{C}/B\to \mathcal{C}/A$ be its base-change functor. For a right adjoint $f_*:\mathcal{C}/A\to \mathcal{C}/B$ we must have a natural correspondence between the dashed maps in the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%20%20%20%20%09%7Bf%5E*X%7D%20%26%26%20Y%20%5C%5C%0A%20%20%20%20%09A%20%26%20X%20%26%26%20%7Bf_*Y%7D%20%5C%5C%0A%20%20%20%20%09%26%20B%0A%20%20%20%20%09%5Carrow%5B%22f%22'%2C%20from%3D2-1%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5B%22g%22%2C%20from%3D2-2%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5B%22h%22'%2C%20from%3D1-3%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-2%5D%0A%20%20%20%20%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7Bf_*h%7D%22%2C%20from%3D2-4%2C%20to%3D3-2%5D%0A%20%20%20%20%09%5Carrow%5Bdashed%2C%20from%3D2-2%2C%20to%3D2-4%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
    	{f^*X} &amp;&amp; Y \\
    	A &amp; X &amp;&amp; {f_*Y} \\
    	&amp; B
    	\arrow[&quot;f&quot;', from=2-1, to=3-2]
    	\arrow[&quot;g&quot;, from=2-2, to=3-2]
    	\arrow[&quot;h&quot;', from=1-3, to=2-1]
    	\arrow[from=1-1, to=2-1]
    	\arrow[from=1-1, to=2-2]
    	\arrow[dashed, from=1-1, to=1-3]
    	\arrow[&quot;{f_*h}&quot;, from=2-4, to=3-2]
    	\arrow[dashed, from=2-2, to=2-4]
    \end{tikzcd}
" /></p>


Note that products in a slice category are exactly pullbacks. Then since $\mathcal{C}/B$ is cartesian closed, the equivalence between the arrows in the diagram is exactly given by the exponential adjunction, where $f_*h:f_*Y\to B$ is exactly the exponential functor, $(-)^A$, associated with $f:A\to B$ applied to $f\circ h:Y\to B$.
`\end{proof}`

Therefore for any locally cartesian closed category with pullbacks, $\mathcal{C}$, and in particular any topoi, we have for each $f:A\to B$ in $\mathcal{C}$ a triple adjunction

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%09%7B%5Cmathcal%7BC%7D%2FB%7D%20%26%26%20%7B%5Cmathcal%7BC%7D%2FA%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf%5E*%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_!%7D%22'%2C%20bend%20right%20%3D%2060%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D2%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%7D%22%2C%20bend%20left%20%3D%2060%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
	{\mathcal{C}/B} &amp;&amp; {\mathcal{C}/A}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f^*}&quot;, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{f_!}&quot;', bend right = 60, from=1-3, to=1-1]
	\arrow[&quot;&quot;{name=2, anchor=center, inner sep=0}, &quot;{f_*}&quot;, bend left = 60, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=2]
\end{tikzcd}
" /></p>
which in the case of topoi gives our desired geometric morphisms associated with base-change.

Note that in the case of a site $(\mathcal{C},J)$ and a sheaf $\mathcal{F} \in \mathsf{Sh}(\mathcal{C},J)$, the slice category is the Grothendieck topos

$$\mathsf{Sh}(\mathcal{C},J)/\mathcal{F}\simeq \mathsf{Sh}\left(\int_\mathcal{C}\mathcal{F},J_\mathcal{F}\right)$$
where $\int_\mathcal{C}\mathcal{F}$ is the Grothendieck construction for $\mathcal{F}:\mathcal{C}^{op}\to \mathsf{Set}$, which is defined by the following data:
- (Objs) Pairs $(C,X)$ for $C \in \mathcal{C}_0$ and $X \in \mathcal{F}(C)$
- (Maps) A map $(C,X)\to (D,Y)$ is a map $f:C\to D$ such that the triangle

<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%0A%20%20%20%20%09%26%20%7B*%7D%20%5C%5C%0A%20%20%20%20%09%7B%5Cmathcal%7BF%7D(C)%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(D)%7D%0A%20%20%20%20%09%5Carrow%5B%22X%22'%2C%20from%3D1-2%2C%20to%3D2-1%5D%0A%20%20%20%20%09%5Carrow%5B%22Y%22%2C%20from%3D1-2%2C%20to%3D2-3%5D%0A%20%20%20%20%09%5Carrow%5B%22%7B%5Cmathcal%7BF%7D(f)%7D%22%2C%20from%3D2-3%2C%20to%3D2-1%5D%0A%20%20%20%20%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}
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

[^1]: Milne, J. S. (1980). Etale Cohomology (PMS-33). Princeton University Press. https://www.jstor.org/stable/j.ctt1bpmbk1. Accessed 15 May 2024
[^2]: Sheaves in Geometry and Logic: A First Introduction to Topos Theory | SpringerLink. (n.d.). https://link.springer.com/book/10.1007/978-1-4612-0927-0. Accessed 23 May 2024
[^3]: sheafification in nLab. (n.d.). https://ncatlab.org/nlab/show/sheafification. Accessed 10 June 2024
[^4]: Shulman, M. A. (2009, January 9). Framed bicategories and monoidal fibrations. arXiv. https://doi.org/10.48550/arXiv.0706.1286
[^5]: Categorical Logic and Type Theory. (n.d.). https://www.cs.ru.nl/B.Jacobs/CLT/bookinfo.html. Accessed 23 May 2024