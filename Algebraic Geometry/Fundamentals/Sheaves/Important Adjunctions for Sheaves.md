---
date: 2024-05-23T11:41:00
tags:
  - AlgebraicGeometry
  - Sheaves
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

In these notes we collect and review the proofs of various adjunctions appearing in the category of sheaves on a space and on $\mathcal{O}_X$-modules on a ringed space, following the work in Vakil[^1]. Throughout these notes unless otherwise stated we will consider sheaves valued in a (co)complete abelian category $\mathcal{A}$, such as the category of modules over a ring. Additionally, we will fix a ringed space $(X,\mathcal{O}_X)$ throughout and write $\mathcal{O}_X{-}\mathsf{Mod}$ to denote the category of $\mathcal{O}_X$-modules on $X$.

## Pull and Push Adjunctions

^2a1b9e

### Sheaves on Spaces

In this subsection we go through the construction in the special case of the standard site on the category of open sets on a space.

Recall that if $f:X\to Y$ is a map of topological spaces, we obtain an adjunction for pre-sheaf categories
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D(X)%7D%20%26%20%7B%5Cmathsf%7BPs%7D(Y)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf%5E*_%7Bpre%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-2%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Ps}(X)} &amp; {\mathsf{Ps}(Y)}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f^*_{pre}}&quot;', bend right = 30, from=1-2, to=1-1]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{f_*}&quot;', bend right = 30, from=1-1, to=1-2]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]
\end{tikzcd}
" /></p>
Here we define $f_*:\mathsf{Ps}(X)\to \mathsf{Ps}(Y)$ on a presheaf $\mathcal{F}$ to be $f_*\mathcal{F}(U) = \mathcal{F}(f^{-1}(U))$ and on a map of presheaves $\alpha:\mathcal{F}\Rightarrow \mathcal{G}$ by $f_*\alpha_V = \alpha_{f^{-1}(V)}$. On the other hand $f^*_{pre}$ is defined on a presheaf $\mathcal{G}$ by
$$f_{pre}^*\mathcal{G}(U) = \lim\limits_{\to f(U) \subseteq V}\mathcal{G}(V)$$
with restriction along $W\subseteq U$ induced by the universal property of the colimit
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(U)%7D%20%26%26%20%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(W)%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(V)%7D%20%26%26%20%7B%5Cmathcal%7BG%7D(V%5Ccap%20W)%7D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BG%7D(V%5Ccap%20W%5Csubseteq%20V)%7D%22'%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{f_{pre}^*\mathcal{G}(U)} &amp;&amp; {f_{pre}^*\mathcal{G}(W)} \\
	{\mathcal{G}(V)} &amp;&amp; {\mathcal{G}(V\cap W)}
	\arrow[dashed, from=1-1, to=1-3]
	\arrow[from=2-1, to=1-1]
	\arrow[&quot;{\mathcal{G}(V\cap W\subseteq V)}&quot;', from=2-1, to=2-3]
	\arrow[from=2-3, to=1-3]
\end{tikzcd}
" /></p>
Similarly, a map of pre-sheaves $\alpha:\mathcal{G}\Rightarrow \mathcal{H}$ induces a map of presheaves $f_{pre}^*\alpha$ induced by the colimit
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(U)%7D%20%26%26%20%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BH%7D(U)%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(V)%7D%20%26%26%20%7B%5Cmathcal%7BH%7D(V)%7D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%7B%5Calpha_V%7D%22'%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{f_{pre}^*\mathcal{G}(U)} &amp;&amp; {f_{pre}^*\mathcal{H}(U)} \\
	{\mathcal{G}(V)} &amp;&amp; {\mathcal{H}(V)}
	\arrow[dashed, from=1-1, to=1-3]
	\arrow[from=2-1, to=1-1]
	\arrow[&quot;{\alpha_V}&quot;', from=2-1, to=2-3]
	\arrow[from=2-3, to=1-3]
\end{tikzcd}
" /></p>
To see that this induces an adjunction it suffices to show that we have co-universal pairs. Note that for a pre-sheaf $\mathcal{F}$ on $X$ we have a natural map $\epsilon_\mathcal{F}:f^*_{pre}f_*\mathcal{F}\Rightarrow \mathcal{F}$ induced by the universal property of the coproduct, since at an open $U$ we have 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Clim%5Climits_%7B%5Cto%20f(U)%20%5Csubseteq%20V%7Df_*%5Cmathcal%7BF%7D(V)%20%3D%20%5Clim%5Climits_%7B%5Cto%20f(U)%20%5Csubseteq%20V%7D%5Cmathcal%7BF%7D(f%5E%7B-1%7D(V))%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(U)%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BF%7D(f%5E%7B-1%7D(V))%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(U)%7D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7Bf%5E%7B-1%7D(V)%2CU%7D%7D%22'%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\lim\limits_{\to f(U) \subseteq V}f_*\mathcal{F}(V) = \lim\limits_{\to f(U) \subseteq V}\mathcal{F}(f^{-1}(V))} &amp;&amp; {\mathcal{F}(U)} \\
	{\mathcal{F}(f^{-1}(V))} &amp;&amp; {\mathcal{F}(U)}
	\arrow[dashed, from=1-1, to=1-3]
	\arrow[from=2-1, to=1-1]
	\arrow[&quot;{\text{res}_{f^{-1}(V),U}}&quot;', from=2-1, to=2-3]
	\arrow[Rightarrow, no head, from=2-3, to=1-3]
\end{tikzcd}
" /></p>
We wish to show that $\epsilon_\mathcal{F}$ gives a terminal object in the comma category $(f^*_{pre}\mid \mathcal{F})$. To this end let $\mathcal{G}$ be a presheaf on $Y$ and let $\alpha:f^*_{pre}\mathcal{G}\Rightarrow \mathcal{F}$ be a map of presheaves. Then for every open $U$ in $X$ and every open $V$ in $Y$ such that $f(U) \subseteq V$ we have a map
$$\mathcal{G}(V)\to f_{pre}^*\mathcal{G}(U)\xrightarrow{\alpha_U}\mathcal{F}(U)$$
In particular, this implies that for any $V$ open in $Y$ we have a map
$$\mathcal{G}(V)\to f_{pre}^*\mathcal{G}(f^{-1}(V))\xrightarrow{\alpha_{f^{-1}(V)}}\mathcal{F}(f^{-1}(V))$$
If $W \subseteq V$ is an inclusion of opens in $Y$ we obtain a commuting rectangle
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BG%7D(V)%7D%20%26%20%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(f%5E%7B-1%7D(V))%7D%20%26%20%7B%5Cmathcal%7BF%7D(f%5E%7B-1%7D(V))%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(W)%7D%20%26%20%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(f%5E%7B-1%7D(W))%7D%20%26%20%7B%5Cmathcal%7BF%7D(f%5E%7B-1%7D(W))%7D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5Bfrom%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7Bf%5E%7B-1%7D(V)%7D%7D%22%2C%20from%3D1-2%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-2%2C%20to%3D2-2%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Calpha_%7Bf%5E%7B-1%7D(W)%7D%7D%22'%2C%20from%3D2-2%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{G}(V)} &amp; {f_{pre}^*\mathcal{G}(f^{-1}(V))} &amp; {\mathcal{F}(f^{-1}(V))} \\
	{\mathcal{G}(W)} &amp; {f_{pre}^*\mathcal{G}(f^{-1}(W))} &amp; {\mathcal{F}(f^{-1}(W))}
	\arrow[from=1-1, to=1-2]
	\arrow[from=1-1, to=2-1]
	\arrow[&quot;{\alpha_{f^{-1}(V)}}&quot;, from=1-2, to=1-3]
	\arrow[from=1-2, to=2-2]
	\arrow[from=1-3, to=2-3]
	\arrow[from=2-1, to=2-2]
	\arrow[&quot;{\alpha_{f^{-1}(W)}}&quot;', from=2-2, to=2-3]
\end{tikzcd}
" /></p>
where the left square commutes by definition of the restrictions for $f_{pre}^*\mathcal{G}$ and the right square commutes by naturality of $\alpha$. This implies that we have an induced natural transformation $\alpha^\flat:\mathcal{G}\to f_*\mathcal{F}$. Further, applying $f_{pre}^*$ and composing with the co-unit we obtain the composite which at $U$ open in $X$ gives
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(U)%7D%20%26%26%20%7Bf_%7Bpre%7D%5E*f_*%5Cmathcal%7BF%7D(U)%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(U)%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(V)%7D%20%26%20%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(f%5E%7B-1%7D(V))%7D%20%26%20%7Bf_*%5Cmathcal%7BF%7D(V)%7D%0A%09%5Carrow%5Bdashed%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7Bf%5E%7B-1%7D(V)%2CU%7D%7D%22'%2C%20from%3D2-2%2C%20to%3D1-1%5D%0A%09%5Carrow%5Bfrom%3D2-2%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-3%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{f_{pre}^*\mathcal{G}(U)} &amp;&amp; {f_{pre}^*f_*\mathcal{F}(U)} &amp;&amp; {\mathcal{F}(U)} \\
	{\mathcal{G}(V)} &amp; {f_{pre}^*\mathcal{G}(f^{-1}(V))} &amp; {f_*\mathcal{F}(V)}
	\arrow[dashed, from=1-1, to=1-3]
	\arrow[from=1-3, to=1-5]
	\arrow[from=2-1, to=1-1]
	\arrow[from=2-1, to=2-2]
	\arrow[&quot;{\text{res}_{f^{-1}(V),U}}&quot;', from=2-2, to=1-1]
	\arrow[from=2-2, to=2-3]
	\arrow[from=2-3, to=1-3]
	\arrow[from=2-3, to=1-5]
\end{tikzcd}
" /></p>
where $V$ is an open in $Y$ such that $f(U) \subseteq V$. For uniqueness observe that if $\beta:\mathcal{G}\to f_*\mathcal{F}$ is another map of pre-sheaves making the diagram commute, 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bf_%7Bpre%7D%5E*%5Cmathcal%7BG%7D(f%5E%7B-1%7D(V))%7D%20%26%26%20%7Bf_%7Bpre%7D%5E*f_*%5Cmathcal%7BF%7D(f%5E%7B-1%7D(V))%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(f%5E%7B-1%7D(V))%7D%20%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(V)%7D%20%26%26%20%7Bf_*%5Cmathcal%7BF%7D(V)%7D%0A%09%5Carrow%5B%22%7Bf_%7Bpre%7D%5E*%5Calpha_%7Bf%5E%7B-1%7D(V)%7D%7D%22%2C%20dashed%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon_%7B%5Cmathcal%7BF%7D%2Cf%5E%7B-1%7D(V)%7D%7D%22%2C%20from%3D1-3%2C%20to%3D1-5%5D%0A%09%5Carrow%5Bfrom%3D2-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%7B%5Cbeta_V%7D%22'%2C%20from%3D2-1%2C%20to%3D2-3%5D%0A%09%5Carrow%5Bfrom%3D2-3%2C%20to%3D1-3%5D%0A%09%5Carrow%5BRightarrow%2C%20no%20head%2C%20from%3D2-3%2C%20to%3D1-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{f_{pre}^*\mathcal{G}(f^{-1}(V))} &amp;&amp; {f_{pre}^*f_*\mathcal{F}(f^{-1}(V))} &amp;&amp; {\mathcal{F}(f^{-1}(V))} \\
	{\mathcal{G}(V)} &amp;&amp; {f_*\mathcal{F}(V)}
	\arrow[&quot;{f_{pre}^*\alpha_{f^{-1}(V)}}&quot;, dashed, from=1-1, to=1-3]
	\arrow[&quot;{\epsilon_{\mathcal{F},f^{-1}(V)}}&quot;, from=1-3, to=1-5]
	\arrow[from=2-1, to=1-1]
	\arrow[&quot;{\beta_V}&quot;', from=2-1, to=2-3]
	\arrow[from=2-3, to=1-3]
	\arrow[Rightarrow, no head, from=2-3, to=1-5]
\end{tikzcd}
" /></p>
which uniquely determines $\beta$ in terms of $\alpha$, so in particular $\alpha = \beta$. Thus, we obtain the following statement:

>[!theorem] Presheaf Pushforward Adjunction
>Let $f:X\to Y$ be a continuous map of topological spaces. Then we have an adjoint pair between pre-sheaf categories
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BPs%7D(Y)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_%7Bpre%7D%5E*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white] {\mathsf{Ps}(X)} &amp;&amp; {\mathsf{Ps}(Y)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f_*}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{f_{pre}^*}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>

^d95e71

We could also show the adjunction using [[Ends and coEnds]] calculus:
$$
\begin{align*}
\mathsf{Ps}_X(f_{pre}^*\mathcal{G},\mathcal{F}) &\cong \int_{U :\mathsf{Top}(X)^{op}}\mathsf{Set}\left(\lim\limits_{\to f(U)\subseteq V}\mathcal{G}(V),\mathcal{F}(U)\right) \\
&=\int_{U :\mathsf{Top}(X)^{op}}\lim\limits_{\leftarrow f(U)\subseteq V}\mathsf{Set}(\mathcal{G}(V),\mathcal{F}(U)) \\
&\cong \int_{V:\mathsf{Top}(Y)^{op}}\mathsf{Set}(\mathcal{G}(V),\mathcal{F}(f^{-1}(V))) \\
&\cong \mathsf{Ps}_Y(\mathcal{G},f_*\mathcal{F})
\end{align*}
$$

Recall from [[Sheaves on Sites]] we have an important adjunction given by the associated sheaf functor
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D(X)%7D%20%26%20%7B%5Cmathsf%7BPs%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-2%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Ciota%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-2%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D0%2C%20to%3D1%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Sh}(X)} &amp; {\mathsf{Ps}(X)}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathfrak{a}}&quot;', bend right = 30, from=1-2, to=1-1]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\iota}&quot;', bend right = 30, from=1-1, to=1-2]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=0, to=1]
\end{tikzcd}
" /></p>
Note that $f_*$ preserves limits, and so restricts to a functor between sheaf categories, so composing on the left with the associated sheaf functor and replacing $\mathsf{Ps}(Y)$ with $\mathsf{Sh}(Y)$ on the right we obtain the following result.

>[!theorem] Sheaf Pushforward Adjunction
>Let $f:X\to Y$ be a continuous map of topological spaces. Then we have an adjoint pair between pre-sheaf categories
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D(Y)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%5Ccirc%20%5Ciota%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%5Ccirc%20f_%7Bpre%7D%5E*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Sh}(X)} &amp;&amp; {\mathsf{Sh}(Y)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f_*\circ \iota}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\mathfrak{a}\circ f_{pre}^*}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>

^48a080

In order to understand this result a bit better we can formulate the definition of $(-)^+:\mathsf{Ps}(X)\to \mathsf{Ps}(X)$ in a slightly simpler manner. In particular, on a presheaf $P$ we have that at an open $U$ of $X$, a section of $P^+(U)$ can be identified with an equivalence class where elements of the equivalence class are pairs $((U_i)_{i \in I}, (s_i)_{i \in I})$ of a cover $U = \bigcup_{i \in I}U_i$ of $U$ together with sections $s_i \in P(U_i)$ which agree on restrictions, and where equivalence of pairs is given in terms of refinement of the cover and restriction of the sections onto the refinement. In this way, a section of $\mathfrak{a}(P)(U)$ can be identified with an equivalence class of pairs, as before, where now the sections in the covers are themselves equivalence classes of covers and sections, which can be thought of as covering covers for an open.

Moving forward we write $f^*$ for $\mathfrak{a}\circ f_{pre}^*$. Note that the adjunction in [[Important Adjunctions for Sheaves#^48a080]] gives a number of important adjunctions as simple consequences. For example, using the isomorphism of categories $\mathsf{Sh}(pt) \cong \mathsf{Set}$, if $f:X\to *$ is the unique map to a point we obtain the adjunction
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BSet%7D%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%5CGamma%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22c%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Sh}(X)} &amp;&amp; {\mathsf{Set}}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;\Gamma&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;c&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>
where $\Gamma$ denotes the global sections functor and $c$ denotes the constant sheaf functor. Explicitly, the constant sheaf on a set $A$ , often denoted $\underline{A}_X$, is given at an open $U$ by $\underline{A}_X(U)$, which can be identified with functions $s:U\to A$ which is continuous when $A$ is given the discrete topology. This is called the **constant sheaf on $A$**. On the other hand, for a point $x \in X$ we can associate it with a map $x:*\to X$, which provides an adjunction
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSet%7D%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bx_*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B(-)_x%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Set}} &amp;&amp; {\mathsf{Sh}(X)}
	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{x_*}&quot;', bend right = 30, from=1-1, to=1-3]
	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{(-)_x}&quot;', bend right = 30, from=1-3, to=1-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]
\end{tikzcd}
" /></p>
where $(-)_x$ is the stalk map and $x_*A$ for a set $A$ is the **skyscraper sheaf at $A$**, which is given by $x_*A(U) = A$ if $x \in U$ and $x_*A(U) = *$ (in general this is the final object in the category that the sheaf lands in) if $x \notin U$.

>[!remark]
>Throughout we could, and will, often replace $\mathsf{Set}$ with the category of $R$-modules for a ring $R$, often $R=\mathbb{Z}$. We could also choose to land in the category of $R$-algebras.


A simple consequence of the above adjunctions we have that if $\mathcal{F}$ is a sheaf on $X$ and $p \in X$ is a point, then
$$\mathscr{Hom}(\underline{\{p\}},\mathcal{F})(U) = \mathsf{Ps}(\underline{\{p\}}\vert_U,\mathcal{F}\vert_U) \cong \mathsf{Ps}(\underline{\{p\}},\iota_{U,*}\mathcal{F}\vert_U) \cong \mathsf{Set}(\{p\},\Gamma(\iota_{U,*}\mathcal{F}\vert_U)) \cong \mathcal{F}(U)$$

#### Aside on Functoriality

Note that for any maps of spaces $f:X\to Y$ and $g:Y\to Z$, $g_*f_* = (g\circ f)_*$ by expanding definitions, so pushforward is functorial. Since adjoints are determined uniquely up to natural isomorphism, and the composite of adjoints is an adjoint, we have that 
$$f^*_{pre}g^*_{pre}\cong_{unique}(g\circ f)_{pre}^*\;\text{ and }\;f^*g^*\cong_{unique}(g\circ f)^*$$

#### Properties of Pullback

Although its definition is more complicated, the pullback of a (pre)sheaf along a map $f:X\to Y$ admits a simple description in terms of stalks. 

>[!proposition] Stalks of Pre-sheaf Pullback
>Let $\mathcal{G}$ be a pre-sheaf on $Y$. Then if $x \in X$ is a point in $X$, then we have an isomorphism
>$$(f^*_{pre}\mathcal{G})_x \cong \mathcal{G}_{f(x)}$$

`\begin{proof}`
The claim can be seen to follow simply by a careful inspection of colimits:
$$(f_{pre}^*\mathcal{G})_x = \lim\limits_{\to x \in U}f_{pre}^*\mathcal{G}(U) = \lim\limits_{\to x \in U}\lim\limits_{\to f(U) \subseteq V}\mathcal{G}(V) \cong \lim\limits_{\to f(x) \in V}\mathcal{G}(V) = \mathcal{G}_{f(x)}$$
`\end{proof}`
The sheaf case follows immediately from the fact that the associated sheaf functor induces isomorphisms on stalks.

>[!proposition] Stalks of Sheaf Pullback
>Let $\mathcal{G}$ be a sheaf on $Y$. Then if $x \in X$ is a point in $X$, then we have an isomorphism
>$$(f^*\mathcal{G})_x \cong \mathcal{G}_{f(x)}$$



### $\mathcal{O}_X$-Modules

Throughout this section let $(X,\mathcal{O}_X)$ be a ringed space. Recall we have a natural category of sheaves of $\mathcal{O}_X$-modules on $X$.

>[!def] $\mathcal{O}_X$-Modules
>A $\mathcal{O}_X$-module is a sheaf of abelian groups $\mathcal{F}$ on $X$ such that for any open subset $U$ of $X$, $\mathcal{F}(U)$ has the structure of a $\mathcal{O}_X(U)$ module, and the action of the module is compatible with restrictions in the sense that
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BO%7D_X(U)%5Ctimes%20%5Cmathcal%7BF%7D(U)%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(U)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathcal%7BO%7D_X(V)%5Ctimes%20%5Cmathcal%7BF%7D(V)%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(V)%7D%0A%09%5Carrow%5B%22%7Bm_U%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7BU%2CV%7D%5Ctimes%20%5Ctext%7Bres%7D_%7BU%2CV%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7BU%2CV%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bm_V%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathcal{O}_X(U)\times \mathcal{F}(U)} &amp;&amp; {\mathcal{F}(U)} \\	\\	{\mathcal{O}_X(V)\times \mathcal{F}(V)} &amp;&amp; {\mathcal{F}(V)}	\arrow[&quot;{m_U}&quot;, from=1-1, to=1-3]	\arrow[&quot;{\text{res}_{U,V}\times \text{res}_{U,V}}&quot;', from=1-1, to=3-1]	\arrow[&quot;{\text{res}_{U,V}}&quot;, from=1-3, to=3-3]	\arrow[&quot;{m_V}&quot;', from=3-1, to=3-3]\end{tikzcd}" /></p>

In order to obtain an adjunction in this case we need to specialize to maps of ringed spaces. Then if $(f,f^\#):(X,\mathcal{O}_X)\to (Y,\mathcal{O}_Y)$ is a map of ringed spaces (i.e. a continuous map $f:X\to Y$ together with a sheaf map $f^\#:\mathcal{O}_Y\Rightarrow f_*\mathcal{O}_X$), as in the proof of [[Important Adjunctions for Sheaves#^d95e71]] we obtain an adjunction
<p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BPs%7D(Y)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_%7Bpre%7D%5E*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white] {\mathsf{Ps}(X)} &amp;&amp; {\mathsf{Ps}(Y)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f_*}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{f_{pre}^*}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>
between presheaves landing in the category of abelian groups, and hence similarly we get an adjunction on sheaves
<p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D(Y)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7Bf_*%5Ccirc%20%5Ciota%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%5Ccirc%20f_%7Bpre%7D%5E*%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Sh}(X)} &amp;&amp; {\mathsf{Sh}(Y)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{f_*\circ \iota}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\mathfrak{a}\circ f_{pre}^*}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>
upon sheafification. For simplification, moving forward we will write $f^* := \mathfrak{a}\circ f^*_{pre}$. Further, both functors preserve the module structure, so for an $\mathcal{O}_X$-module $\mathcal{F}$ we have that $f_*\mathcal{F}$ is a $f_*\mathcal{O}_X$ module, and using $f^\#$ this gives $f_*\mathcal{F}$ the structure of a $\mathcal{O}_Y$ module. On the other hand, if $\mathcal{G}$ is an $\mathcal{O}_Y$-module, then $f^*\mathcal{G}$ is a $f^*\mathcal{O}_Y$-module, which using the adjoint of $f^\#$ gives the $\mathcal{O}_X$-module $f^*\mathcal{G}\otimes_{f^*\mathcal{O}_Y}\mathcal{O}_X$ where this tensor is defined in [[Important Adjunctions for Sheaves#^4952e8|Tensor-Hom $\mathcal{O}_X$-modules]]. This gives the composite of adjunctions
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%26%26%20%7B%5Cmathsf%7BSh%7D_%7Bf%5E*%5Cmathcal%7BO%7D_Y%7D(X)%7D%20%5C%5C%0A%09%7B%5Cmathsf%7BSh%7D_%7B%5Cmathcal%7BO%7D_X%7D(X)%7D%20%26%26%26%26%20%7B%5Cmathsf%7BSh%7D_%7B%5Cmathcal%7BO%7D_Y%7D(Y)%7D%20%5C%5C%0A%09%26%26%20%7B%5Cmathsf%7BSh%7D_%7Bf_*%5Cmathcal%7BO%7D_X%7D(X)%7D%0A%09%5Carrow%5B%22%7B-%5Cotimes_%7Bf%5E*%5Cmathcal%7BO%7D_Y%7D%5Cmathcal%7BO%7D_X%7D%22'%2C%20bend%20right%20%3D%2010%2C%20from%3D1-3%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bf_*%5Ccirc%20%5Ciota%7D%22'%2C%20bend%20right%20%3D%2010%2C%20from%3D2-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7Bf%5E*%7D%22'%2C%20bend%20right%20%3D%2010%2C%20from%3D2-5%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B-%5Ccirc%20f%5E%5C%23%7D%22'%2C%20bend%20right%20%3D%2010%2C%20from%3D3-3%2C%20to%3D2-5%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	&amp;&amp; {\mathsf{Sh}_{f^*\mathcal{O}_Y}(X)} \\
	{\mathsf{Sh}_{\mathcal{O}_X}(X)} &amp;&amp;&amp;&amp; {\mathsf{Sh}_{\mathcal{O}_Y}(Y)} \\
	&amp;&amp; {\mathsf{Sh}_{f_*\mathcal{O}_X}(X)}
	\arrow[&quot;{-\otimes_{f^*\mathcal{O}_Y}\mathcal{O}_X}&quot;', bend right = 10, from=1-3, to=2-1]
	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1-3, to=3-3]
	\arrow[&quot;{f_*\circ \iota}&quot;', bend right = 10, from=2-1, to=3-3]
	\arrow[&quot;{f^*}&quot;', bend right = 10, from=2-5, to=1-3]
	\arrow[&quot;{-\circ f^\#}&quot;', bend right = 10, from=3-3, to=2-5]
\end{tikzcd}
" /></p>
which represents **change of scalars** for $\mathcal{O}_X$ modules.

An important fact is that the category of sheaves of abelian groups on a space $X$ forms an abelian category, and similarly for the category of $\mathcal{O}_X$-modules on a ringed space $(X,\mathcal{O}_X)$. 
### Slice Categories and Relative Adjunctions

## Tensor-Hom Adjunctions

The category of sheaves on a site, $\mathsf{Sh}(\mathcal{C},J)$, as a topos, comes naturally equipped with a cartesian closed structure (and in fact a locally cartesian closed structure).

>[!def] Presheaf Hom
>Let $\mathcal{F},\mathcal{G}\in \mathsf{Ps}(\mathcal{C})$ be pre-sheaves on a category $\mathcal{C}$. Then we can form their internal hom $\mathscr{Hom}(\mathcal{F},\mathcal{G})$ which is a presheaf given on an object $C \in \mathcal{C}$ by
>$$\mathscr{Hom}(\mathcal{F},\mathcal{G})(C) = \mathsf{Ps}(\mathcal{F}\times y^C,\mathcal{G})$$
>where a map $f:C\to C'$ is sent to pre-composition by $1_\mathcal{F}\times y^f:\mathcal{F}\times y^C\Rightarrow \mathcal{F}\times y^{C'}$.

We begin by showing that this construction forms an adjunction on pre-sheaves with the product of pre-sheaves

>[!proposition] Presheaf-Tensor Adjunction
>For any presheaf $\mathcal{F}$ on $\mathcal{C}$ we have an adjunction
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BPs%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathscr%7BHom%7D(%5Cmathcal%7BF%7D%2C-)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B-%5Ctimes%5Cmathcal%7BF%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Ps}(X)} &amp;&amp; {\mathsf{Ps}(X)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathscr{Hom}(\mathcal{F},-)}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{-\times\mathcal{F}}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>

`\begin{proof}`
We prove the claim by showing the existence of co-universal pairs. First, for $\mathcal{G}$ a presheaf on $\mathcal{C}$ we define a map $\epsilon_\mathcal{G}:\mathscr{Hom}(\mathcal{F},\mathcal{G})\times \mathcal{F}\Rightarrow \mathcal{G}$. On an object $C$ of $\mathcal{C}$ we set $\epsilon_{\mathcal{G},C}$ to be the map that sends $(\alpha:\mathcal{F}\times y^C\Rightarrow \mathcal{G},s \in \mathcal{F}(C))$ to $\alpha_C(s,1_C)$. Observe that if $f:C\to C'$ is a map in $\mathcal{C}$ we have the commutative diagram:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D(%5Cmathcal%7BF%7D%5Ctimes%20y%5E%7BC'%7D%2C%5Cmathcal%7BG%7D)%5Ctimes%20%5Cmathcal%7BF%7D(C')%7D%20%26%26%20%7B%5Cmathsf%7BPs%7D(%5Cmathcal%7BF%7D%5Ctimes%20y%5EC%2C%5Cmathcal%7BG%7D)%5Ctimes%20%5Cmathcal%7BF%7D(C)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(C')%7D%20%26%26%20%7B%5Cmathcal%7BG%7D(C)%7D%0A%09%5Carrow%5B%22%7B(1_%5Cmathcal%7BF%7D%5Ctimes%20y%5Ef)%5E*%5Ctimes%20%5Cmathcal%7BF%7D(f)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon_%7B%5Cmathcal%7BG%7D%2CC'%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Cepsilon_%7B%5Cmathcal%7BG%7D%2CC%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BG%7D(f)%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathsf{Ps}(\mathcal{F}\times y^{C'},\mathcal{G})\times \mathcal{F}(C')} &amp;&amp; {\mathsf{Ps}(\mathcal{F}\times y^C,\mathcal{G})\times \mathcal{F}(C)} \\
	\\
	{\mathcal{G}(C')} &amp;&amp; {\mathcal{G}(C)}
	\arrow[&quot;{(1_\mathcal{F}\times y^f)^*\times \mathcal{F}(f)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\epsilon_{\mathcal{G},C'}}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{\epsilon_{\mathcal{G},C}}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\mathcal{G}(f)}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>
which going the top route sends $(\alpha:\mathcal{F}\times y^{C'}\Rightarrow \mathcal{G},s \in \mathcal{F}(C'))$ is sent to $(\alpha\circ (1_\mathcal{F}\times y^f):\mathcal{F}\times y^C\Rightarrow \mathcal{G},\mathcal{F}(f)(s) \in \mathcal{F}(C))$ before mapping to 
$$\alpha_C(\mathcal{F}(f)(s),y^f(1_C)) = \alpha_C(\mathcal{F}(f)(s),f)$$
and going the bottom route sends $(\alpha:\mathcal{F}\times y^{C'}\Rightarrow \mathcal{G},s \in \mathcal{F}(C'))$ to $\alpha_{C'}(s,1_{C'})$ before mapping it to $$\mathcal{G}(f)(\alpha_{C'}(s,1_{C'}))$$
However, these two expressions agree by naturality of $\alpha$, so $\epsilon_\mathcal{G}$ is natural. Now, suppose we have a pre-sheaf $\mathcal{H}$ on $\mathcal{C}$ together with a natural transformation $\beta:\mathcal{H}\times \mathcal{F}\Rightarrow \mathcal{G}$. Then we define a natural transformation $\beta^\flat:\mathcal{H}\Rightarrow \mathscr{Hom}(\mathcal{F},\mathcal{G})$ by defining the map at $C$, $\beta^\flat_C:\mathcal{H}(C)\to \mathsf{Ps}(\mathcal{F}\times y^C,\mathcal{G})$ to be given by sending a section $s \in \mathcal{H}(s)$ to the natural transformation $\beta^\flat_C(s):\mathcal{F}\times y^C\Rightarrow \mathcal{G}$ which at an object $C'$ is given by the map $\beta^\flat_C(s)_{C'}:\mathcal{F}(C')\times y^C(C')\to \mathcal{G}(C')$ which sends $(t\in \mathcal{F}(C'),f:C'\to C)$ to $\beta_{C'}(\mathcal{H}(f)(s),t)$. By construction this map will make our triangle commute and is unique/specified by this property, so it suffices to prove naturality.

Observe that if $g:C''\to C'$ is a map in $\mathcal{C}$, then we have the commutative diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BF%7D(C')%5Ctimes%20y%5EC(C')%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(C'')%5Ctimes%20y%5EC(C'')%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(C')%7D%20%26%26%20%7B%5Cmathcal%7BG%7D(C'')%7D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BF%7D(g)%5Ctimes%20y%5EC(g)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cbeta%5E%5Cflat_C(s)_%7BC'%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Cbeta%5E%5Cflat_C(s)_%7BC''%7D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BG%7D(g)%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{F}(C')\times y^C(C')} &amp;&amp; {\mathcal{F}(C'')\times y^C(C'')} \\
	\\
	{\mathcal{G}(C')} &amp;&amp; {\mathcal{G}(C'')}
	\arrow[&quot;{\mathcal{F}(g)\times y^C(g)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\beta^\flat_C(s)_{C'}}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{\beta^\flat_C(s)_{C''}}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\mathcal{G}(g)}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>
where by naturality of $\beta$ we have that 
$$\mathcal{G}(g)(\beta_{C'}(\mathcal{H}(f)(s),t))) = \beta_{C''}(\mathcal{H}(g)\mathcal{H}(f)(s),\mathcal{F}(g)(t))$$
so the square commutes, completing the proof.
`\end{proof}`
To motivate the definition of $\mathscr{Hom}(\mathcal{F},\mathcal{G})$ we can use the adjunction and Yoneda lemmas to specify its value at an object $C$:
$$
\begin{align*}
\mathscr{Hom}(\mathcal{F},\mathcal{G})(C) &\cong \mathsf{Ps}(y^C,\mathscr{Hom}(\mathcal{F},\mathcal{G})) \cong \mathsf{Ps}(\mathcal{F}\times y^C,\mathcal{G})
\end{align*}
$$


Next, we will show that when $\mathcal{G}$ is a sheaf this construction outputs a sheaf.

>[!proposition] Sheaf Hom
>If $\mathcal{G}$ is a sheaf on the site $(\mathcal{C},J)$ and $\mathcal{F}$ is any pre-sheaf on $\mathcal{C}$, then $\mathscr{Hom}(\mathcal{F},\mathcal{G})$ is a sheaf on $(\mathcal{C},J)$.

`\begin{proof}`
Recall that the statement that $\mathcal{G}$ is a sheaf on the site is the condition that for any object $C$ and any covering sieve $S$ on $C$ with natural transformation $\alpha:S\Rightarrow \mathcal{G}$, we have a unique lift to the maximal presheaf:
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09S%20%26%26%20%7B%5Cmathcal%7BG%7D%7D%20%5C%5C%0A%09%7By%5EC%7D%0A%09%5Carrow%5B%22%5Calpha%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Ciota_S%7D%22'%2C%20tail%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7B%5Cexists%20!%5Chat%7B%5Calpha%7D%7D%22'%2C%20dashed%2C%20from%3D2-1%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	S &amp;&amp; {\mathcal{G}} \\
	{y^C}
	\arrow[&quot;\alpha&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\iota_S}&quot;', tail, from=1-1, to=2-1]
	\arrow[&quot;{\exists !\hat{\alpha}}&quot;', dashed, from=2-1, to=1-3]
\end{tikzcd}
" /></p>
Now suppose we have such a covering sieve $S$ on $C$ with a natural transformation $\alpha:S\Rightarrow \mathscr{Hom}(\mathcal{F},\mathcal{G})$. Then for every $f:C'\to C$ in $S(C')$ we have $\alpha_{C'}(f):\mathcal{F}\times y^{C'}\Rightarrow \mathcal{G}$, and for every $g:C''\to C'$ we have $$\alpha_{C''}(f\circ g)=\alpha_{C''}\circ S(g)(f) = \mathscr{Hom}(\mathcal{F},\mathcal{G})(g)\circ \alpha_{C'}(f) = \alpha_{C'}(f)\circ 1_\mathcal{F}\times y^g$$
Now, for any $k:D\to C'$, and $x \in \mathcal{F}(D)$, we have $\alpha_{C'}(f)_D(x,k) \in \mathcal{G}(D)$, where naturality says that for ay $h:E\to D$ we have that 
$$\mathcal{G}(h)(\alpha_{C'}(f)_D(x,k)) = \alpha_{C'}(f)_E(\mathcal{F}(h)(x),k\circ h)$$
The previous naturality then gives
$$\alpha_{C''}(f\circ g)_D(x',k') = \alpha_{C'}(f)_D(x',g\circ k')$$
Then, fix $k:C'\to C$ and $x \in \mathcal{F}(C')$. Then we define a natural transformation $\omega:k^*S\Rightarrow \mathcal{G}$, where $k^*S \subseteq y^{C'}$ is a covering sieve by the functoriality of a Grothendieck topology, by setting for $D \in \mathcal{C}$, and $g:D\to C'$ in $k^*S$.
$$\omega_D(g) = \alpha_{D}(k\circ g)_D(\mathcal{F}(g)(x),1_D)  \in \mathcal{G}(D)$$
To show this is natural let $h:E\to D$ be a map in $\mathcal{C}$, and consider the diagram
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bk%5E*S(D)%7D%20%26%26%20%7Bk%5E*S(E)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(D)%7D%20%26%26%20%7B%5Cmathcal%7BG%7D(E)%7D%0A%09%5Carrow%5B%22%7B-%5Ccirc%20h%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Comega_D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Comega_E%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BG%7D(h)%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{k^*S(D)} &amp;&amp; {k^*S(E)} \\
	\\
	{\mathcal{G}(D)} &amp;&amp; {\mathcal{G}(E)}
	\arrow[&quot;{-\circ h}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\omega_D}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{\omega_E}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\mathcal{G}(h)}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>

Then for $g:D\to C'$ in $k^*S$, we have that 
$$
\begin{align*}
\mathcal{G}(h)(\omega_D(g)) &= \mathcal{G}(h)(\alpha_{D}(k\circ g)_D(\mathcal{F}(g)(x),1_D)) \\
&= \alpha_D(k\circ g)_E(\mathcal{F}(g\circ h)(x), h) \\
&= \alpha_E(k\circ g\circ h)_E(\mathcal{F}(g\circ h)(x),1_E) \\
&= \omega_E(g\circ h)
\end{align*}
$$
so our diagram commutes. Since $\mathcal{G}$ is a sheaf we have a unique lift
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7Bk%5E*S%7D%20%26%26%20%7B%5Cmathcal%7BG%7D%7D%20%5C%5C%0A%09%5C%5C%0A%09%7By%5E%7BC'%7D%7D%0A%09%5Carrow%5B%22%5Comega%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Ciota_%7Bk%5E*S%7D%7D%22'%2C%20tail%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Chat%7B%5Comega%7D%7D%22'%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{k^*S} &amp;&amp; {\mathcal{G}} \\
	\\
	{y^{C'}}
	\arrow[&quot;\omega&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\iota_{k^*S}}&quot;', tail, from=1-1, to=3-1]
	\arrow[&quot;{\hat{\omega}}&quot;', dashed, from=3-1, to=1-3]
\end{tikzcd}
" /></p>
Moving forward, let the $\hat{\omega}$ constructed in this way be denoted by $\hat{\omega}^{k,x}$. We define $\hat{\alpha}:y^C\Rightarrow \mathscr{Hom}(\mathcal{F},\mathcal{G})$ by setting $\hat{\alpha}_{C}(1_C):\mathcal{F}\times y^C\Rightarrow \mathcal{G}$ to be the natural transformation given at $C'$ by the map that sends $x\in \mathcal{F}(C')$ and $k:C'\to C$ to
$$\hat{\alpha}_C(1_C)_{C'}(x,k) = \hat{\omega}^{k,x}_{C'}(1_{C'}) \in \mathcal{G}(C')$$
Let $g:D\to C'$ be a map in $\mathcal{C}$. Then we have the square
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BF%7D(C')%5Ctimes%20y%5EC(C')%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(D)%5Ctimes%20y%5EC(D)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(C')%7D%20%26%26%20%7B%5Cmathcal%7BG%7D(D)%7D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BF%7D(g)%5Ctimes%20y%5EC(g)%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Chat%7B%5Calpha%7D_C(1_C)_%7BC'%7D%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%5Chat%7B%5Calpha%7D_C(1_C)_D%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BG%7D(g)%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{F}(C')\times y^C(C')} &amp;&amp; {\mathcal{F}(D)\times y^C(D)} \\
	\\
	{\mathcal{G}(C')} &amp;&amp; {\mathcal{G}(D)}
	\arrow[&quot;{\mathcal{F}(g)\times y^C(g)}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\hat{\alpha}_C(1_C)_{C'}}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{\hat{\alpha}_C(1_C)_D}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\mathcal{G}(g)}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>
Going the bottom path we obtain $\mathcal{G}(g)(\hat{\omega}^{k,x}_{C'}(1_{C'})) = \hat{\omega}^{k,x}_D(g)$, while going the top way gives $\hat{\omega}^{k\circ g,\mathcal{F}(g)(x)}_D(1_D)$. Note that $\hat{\omega}_D^{k\circ g,\mathcal{F}(g)(x)}$ is determined by its action on elements of $(k\circ g)^*S = g^*k^*S$, so we need only it agrees with $\hat{\omega}_D^{k,x}\circ y^g$ on the maps in this space. Thus, let $\varphi:E\to D$ be a map in $g^*k^*S$, so $k\circ g \circ \varphi \in S$. Then we have that 
$$\hat{\omega}_D^{k,x}(g\circ \varphi) = \omega_D^{k,x}(g\circ \varphi) = \alpha_D(k\circ g\circ \varphi)_D(\mathcal{F}(g\circ \varphi)(x),1_D)$$
while
$$\hat{\omega}^{k\circ g,\mathcal{F}(g)(x)}_D(\varphi) = \omega^{k\circ g,\mathcal{F}(g)(x)}_D(\varphi) = \alpha_D(k\circ g\circ \varphi)_D(\mathcal{F}(g\circ \varphi)(x),1_D)$$
so they agree, and hence by uniqueness we have that our square commutes, and so $\hat{\alpha}_C(1_C)$ is natural, and we obtain a natural transformation $\hat{\alpha}:y^C\Rightarrow \mathscr{Hom}(\mathcal{F},\mathcal{G})$. Finally, for $f:C'\to C$ in $S$, we have that for $k:C''\to C'$ and $x \in \mathcal{F}(C'')$, we have $$\hat{\alpha}_{C'}(f) = \mathscr{Hom}(\mathcal{F},\mathcal{G})(f)(\hat{\alpha}_C(1_C)) =  \hat{\alpha}_C(1_C)\circ 1_\mathcal{F}\times y^f$$
is a natural transformation $\mathcal{F}\times y^{C'}\Rightarrow \mathcal{G}$ given by
$$\hat{\alpha}_{C'}(f)_{C''}(x,k) = \hat{\alpha}_C(1_C)_{C''}(x,f\circ k) = \hat{\omega}^{f\circ k,x}_{C''}(1_{C''})$$
Note that for any $g:D\to C'' \in (f\circ k)^*S$ we have 
$$\hat{\omega}_{D}^{f\circ k,x}(g) = \alpha_{D}(f\circ k \circ g)_{D}(\mathcal{F}(g)(x),1_{D}) = \alpha_{C'}(f)_{D}(\mathcal{F}(g)(x),k\circ g) = \mathcal{G}(g)(\alpha_{C'}(f)_{C''}(x,k))$$
so by uniqueness we must have that $\hat{\omega}_{C''}^{f\circ k,x}(1_{C''}) = \alpha_{C'}(f)_{C''}(x,k)$, as desired, and completing existence.

Finally, by construction this is unique since its restrictions are all uniquely determined by commutivity of our triangle.
`\end{proof}`
**TODO: Provide Intuitive Description of This**

Now we can play the same game as for the push-pull adjunction in [[Important Adjunctions for Sheaves#^48a080]] to obtain the following hom-product adjunction for sheaves

>[!theorem] Sheaf Hom-Product Adjunction
>For a sheaf $\mathcal{F}$ on a site $(\mathcal{C},J)$, we have the following hom-product adjunction
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D(%5Cmathcal%7BC%7D%2CJ)%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D(%5Cmathcal%7BC%7D%2CJ)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathscr%7BHom%7D(%5Cmathcal%7BF%7D%2C-)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%5Ccirc%20(-%5Ctimes%5Cmathcal%7BF%7D)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Sh}(\mathcal{C},J)} &amp;&amp; {\mathsf{Sh}(\mathcal{C},J)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathscr{Hom}(\mathcal{F},-)}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\mathfrak{a}\circ (-\times\mathcal{F})}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>


### Sheaves on Spaces

In the case of a space $X$ with pre-sheaves $\mathcal{F},\mathcal{G}$ on $X$, we have a simpler description of sheaf-hom. Namely, an element of $\mathscr{Hom}(\mathcal{F},\mathcal{G})(U) = \mathsf{Ps}(\mathcal{F}\times y^U,\mathcal{G})$ is a natural transformation $\alpha:\mathcal{F}\times y^U\Rightarrow \mathcal{G}$. But, for $V \nsubseteq U$ we have that $y^U(V) = \emptyset$, so $\alpha$ is a family of maps $\alpha_V:\mathcal{F}(V)\to \mathcal{G}(V)$ for $V \subseteq U$, and natural in $V$. However, this is exactly the data of a natural transformation $\alpha:\mathcal{F}\vert_U\Rightarrow \mathcal{G}\vert_U$, where formally $\mathcal{F}\vert_U = \iota_U^*\mathcal{F}$, for $\iota_U:U\hookrightarrow X$ the inclusion of the open. Additionally, in this case we have a simpler proof that when $\mathcal{G}$ is a sheaf the sheaf-hom yields a sheaf.

`\begin{proof}[Proof of Sheaf Hom for Spaces]`
Let $U \subseteq X$ be an open and let $U = \bigcup_{i \in I}U_i$ be an open cover of $U$. Suppose $s_i \in \mathscr{Hom}(\mathcal{F},\mathcal{G})(U_i)$ for each $i \in I$, and such that $s_i\vert_{U_i\cap U_j} = s_j\vert_{U_i\cap U_j}$ for each $i,j \in I$. Then let $t \in \mathcal{F}(V)$ for $V \subseteq U$. It follows that $\{s_{i,U_i\cap V}(t)\}_{i \in I}$ forms a matching family in $\mathcal{G}$, so as $\mathcal{G}$ is a sheaf there exists a unique $s_V(t) \in \mathcal{G}(V)$ which restricts to these points. We define $s:\mathcal{F}\vert_U\Rightarrow \mathcal{G}\vert_U$ using these unique amalgamations. To show that the definition is natural let $W\subseteq V \subseteq U$ and let $t \in \mathcal{F}(V)$. Then we want to consider the diagram ^562c83
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BF%7D(V)%7D%20%26%26%20%7B%5Cmathcal%7BF%7D(W)%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathcal%7BG%7D(V)%7D%20%26%26%20%7B%5Cmathcal%7BG%7D(W)%7D%0A%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7BV%2CW%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7Bs_V%7D%22'%2C%20from%3D1-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7Bs_W%7D%22%2C%20from%3D1-3%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Ctext%7Bres%7D_%7BV%2CW%7D%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{F}(V)} &amp;&amp; {\mathcal{F}(W)} \\
	\\
	{\mathcal{G}(V)} &amp;&amp; {\mathcal{G}(W)}
	\arrow[&quot;{\text{res}_{V,W}}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{s_V}&quot;', from=1-1, to=3-1]
	\arrow[&quot;{s_W}&quot;, from=1-3, to=3-3]
	\arrow[&quot;{\text{res}_{V,W}}&quot;', from=3-1, to=3-3]
\end{tikzcd}
" /></p>
But for any $i \in I$ we have that 
$$s_V(t)\vert_{W}\vert_{W\cap U_i} = s_V(t)\vert_{V\cap U_i}\vert_{W\cap U_i} = s_{i,V\cap U_i}(t\vert_{V\cap U_i})\vert_{W\cap U_i} = s_{i,W\cap U_i}(t\vert_{W\cap U_i}) = s_W(t\vert_W)\vert_{W\cap U_i}$$
so by the fact that $\mathcal{G}$ is a sheaf, and hence separable, we have that $s_V(t)\vert_W = s_W(t\vert_W)$, and so $s$ is natural. The uniqueness of the amalgamation follows from the fact that it restricts to the $s_i$ which form a covering family.
`\end{proof}`

In many cases we will be working with sheaves in $R$-modules, in which the same argument applies, but we want our product-hom adjunction becomes a tensor-hom adjunction. Indeed, if $\mathcal{F},\mathcal{G}$ are pre-sheaves of $R$-modules, then we define $\mathcal{F}\otimes_R\mathcal{G}$ to be given component-wise. We define a natural transformation $\epsilon_\mathcal{F}:\mathcal{F}\otimes_R\mathscr{Hom}(\mathcal{F},\mathcal{G})\Rightarrow \mathcal{G}$ is given at an open $U$ by the map
$\epsilon_{\mathcal{F},U}:\mathcal{F}(U)\otimes_R\mathsf{Ps}(\mathcal{F}\vert_U,\mathcal{G}\vert_U)\to \mathcal{G}(U)$ is induced by the $R$-bilinear map that sends $(s,\alpha)$ to $\alpha_U(s)$. Now, let $\beta:\mathcal{F}\otimes_R\mathcal{H}\Rightarrow \mathcal{G}$. We want to obtain a unique $\beta^\#:\mathcal{H}\Rightarrow \mathscr{Hom}(\mathcal{F},\mathcal{G})$ making the diagram 
<p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathcal%7BF%7D%5Cotimes_R%5Cmathscr%7BHom%7D(%5Cmathcal%7BF%7D%2C%5Cmathcal%7BG%7D)%7D%20%26%26%20%7B%5Cmathcal%7BG%7D%7D%20%5C%5C%0A%09%5C%5C%0A%09%7B%5Cmathcal%7BF%7D%5Cotimes_R%20%5Cmathcal%7BH%7D%7D%0A%09%5Carrow%5B%22%7B%5Cepsilon_%7B%5Cmathcal%7BF%7D%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cmathcal%7BF%7D%5Cotimes_R%5Cbeta%5E%5C%23%7D%22%2C%20dashed%2C%20from%3D3-1%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cbeta%22'%2C%20from%3D3-1%2C%20to%3D1-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="
\begin{tikzcd}[white]
	{\mathcal{F}\otimes_R\mathscr{Hom}(\mathcal{F},\mathcal{G})} &amp;&amp; {\mathcal{G}} \\
	\\
	{\mathcal{F}\otimes_R \mathcal{H}}
	\arrow[&quot;{\epsilon_{\mathcal{F}}}&quot;, from=1-1, to=1-3]
	\arrow[&quot;{\mathcal{F}\otimes_R\beta^\#}&quot;, dashed, from=3-1, to=1-1]
	\arrow[&quot;\beta&quot;', from=3-1, to=1-3]
\end{tikzcd}
" /></p>
Namely, at an open set $U$ we define $\beta^\#_U:\mathcal{H}(U)\to \mathsf{Ps}(\mathcal{F}\vert_U,\mathcal{G}\vert_U)$ by sending $s \in \mathcal{H}(U)$ to the natural transformation $\beta^\#_U(s):\mathcal{F}\vert_U\Rightarrow \mathcal{G}\vert_U$, where at an open $V \subseteq U$ the map $\beta^\#_U(s)_V:\mathcal{F}(V)\to \mathcal{G}(V)$ given by sending $t \in \mathcal{F}(V)$ to $\beta_V(t\otimes s\vert_V)$, which is natural by naturality of $\beta$. Further, we have that at $U$ open in $X$ and for a simple tensor $s \otimes t \in \mathcal{F}(U)\otimes_R\mathcal{H}(U)$, we have the composite
$$\epsilon_{\mathcal{F},U}(s\otimes \beta_U^\#(t)) = \beta^\#_U(t)_U(s) = \beta_U(s\otimes t)$$
For uniqueness suppose we have another natural transformation $\alpha:\mathcal{H}\Rightarrow \mathscr{Hom}(\mathcal{F},\mathcal{G})$ making the diagram commute. Then at an open $U \subseteq X$, $\alpha_U(s):\mathcal{F}\vert_U\Rightarrow \mathcal{G}\vert_U$ is a natural transformation satisfying $\alpha_U(s)_U(t) = \beta_U(t\otimes s)$. If $V \subseteq U$, we have that 
$$\alpha_U(s)_V(t\vert_V) = \alpha_U(s)_U(t)\vert_V = \beta_U(t\otimes s)$$
so $\alpha_U(s)$ is specified on diagonals and restrictions. On the other hand, $\alpha_V(s\vert_V) = \alpha_U(s)\vert_V$, so for any $t \in \mathcal{F}(V)$ we have that
$$\alpha_U(s)_V(t) = \alpha_V(s\vert_V)_V(t) = \beta_V(t\otimes s\vert_V) = \beta^\#_U(s)_V(t)$$
as desired.
`\end{proof}`
This gives the following result:

>[!theorem] Pre-Sheaf Tensor Hom adjunction
>If $\mathcal{F}$ is a pre-sheaf of $R$-modules on $X$, then we obtain the adjunction
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D_R(X)%7D%20%26%26%20%7B%5Cmathsf%7BPs%7D_R(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathscr%7BHom%7D(%5Cmathcal%7BF%7D%2C-)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B-%5Cotimes_R%5Cmathcal%7BF%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Ps}_R(X)} &amp;&amp; {\mathsf{Ps}_R(X)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathscr{Hom}(\mathcal{F},-)}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{-\otimes_R\mathcal{F}}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>



Additionally, as in previous cases we can compose with the associated sheaf adjunction to obtain an adjunction on sheaf categories.

>[!theorem] Sheaf Tensor-Hom Adjunction
>If $\mathcal{F}$ is a sheaf of $R$-modules on $X$, then we obtain the adjunction
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D_R(X)%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D_R(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathscr%7BHom%7D(%5Cmathcal%7BF%7D%2C-)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathfrak%7Ba%7D%5Ccirc%20(-%5Cotimes_R%5Cmathcal%7BF%7D)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Sh}_R(X)} &amp;&amp; {\mathsf{Sh}_R(X)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathscr{Hom}(\mathcal{F},-)}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{\mathfrak{a}\circ (-\otimes_R\mathcal{F})}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>

### Sheaves of $\mathcal{O}_X$-Modules

^4952e8

To begin adjusting the adjunctions in the previous sections we need to introduce suitable notions of internal sheaf hom and tensor of $\mathcal{O}_X$-modules. For the sheaf hom we just use the normal hom with the one change being that all sections must be maps of $\mathcal{O}_X\vert_U$-modules. For the sheaf tensor we first define it for pre-sheaves.

>[!def] Pre-sheaf Tensor of $\mathcal{O}_X$-modules
>Let $\mathcal{F}$ and $\mathcal{G}$ be pre-sheaf $\mathcal{O}_X$-modules. Then we define $\mathcal{F}\otimes_{\mathcal{O}_X}^{pre}\mathcal{G}$ to be the pre-sheaf given by taking tensors component-wise.

The argument that this assignment is part of an adjunction $\mathcal{F}\otimes_{\mathcal{O}_X}^{pre}-\dashv \mathscr{Hom}_{\mathcal{O}_X}(\mathcal{F},-)$ follows mutatis mutandis to the argument in the [[Important Adjunctions for Sheaves#^562c83|proof of sheaf hom for spaces]]. Thus we obtain the following result

>[!theorem] Pre-sheaf $\mathcal{O}_X$-module tensor-hom adjunction
>If $\mathcal{F}$ is a pre-sheaf $\mathcal{O}_X$-module, we obtain an adjunction
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BPs%7D_%7B%5Cmathcal%7BO%7D_X%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BPs%7D_%7B%5Cmathcal%7BO%7D_X%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathscr%7BHom%7D_%7B%5Cmathcal%7BO%7D_X%7D(%5Cmathcal%7BF%7D%2C-)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B-%5Cotimes_%7B%5Cmathcal%7BO%7D_X%7D%5E%7Bpre%7D%5Cmathcal%7BF%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Ps}_{\mathcal{O}_X}(X)} &amp;&amp; {\mathsf{Ps}_{\mathcal{O}_X}(X)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathscr{Hom}_{\mathcal{O}_X}(\mathcal{F},-)}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{-\otimes_{\mathcal{O}_X}^{pre}\mathcal{F}}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>

Performing the same tricks as usual we can upgrade this to an adjunction of sheaves of $\mathcal{O}_X$ modules.

>[!theorem] Sheaf $\mathcal{O}_X$-module tensor-hom adjunction
>If $\mathcal{F}$ is a sheaf $\mathcal{O}_X$-module, then we obtain an adjunction
><p align="center"><img align="center"src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathsf%7BSh%7D_%7B%5Cmathcal%7BO%7D_X%7D(X)%7D%20%26%26%20%7B%5Cmathsf%7BSh%7D_%7B%5Cmathcal%7BO%7D_X%7D(X)%7D%0A%09%5Carrow%5B%22%22%7Bname%3D0%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B%5Cmathscr%7BHom%7D_%7B%5Cmathcal%7BO%7D_X%7D(%5Cmathcal%7BF%7D%2C-)%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%22%7Bname%3D1%2C%20anchor%3Dcenter%2C%20inner%20sep%3D0%7D%2C%20%22%7B-%5Cotimes_%7B%5Cmathcal%7BO%7D_X%7D%5Cmathcal%7BF%7D%7D%22'%2C%20bend%20right%20%3D%2030%2C%20from%3D1-3%2C%20to%3D1-1%5D%0A%09%5Carrow%5B%22%5Cdashv%22%7Banchor%3Dcenter%2C%20rotate%3D-90%7D%2C%20draw%3Dnone%2C%20from%3D1%2C%20to%3D0%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]	{\mathsf{Sh}_{\mathcal{O}_X}(X)} &amp;&amp; {\mathsf{Sh}_{\mathcal{O}_X}(X)}	\arrow[&quot;&quot;{name=0, anchor=center, inner sep=0}, &quot;{\mathscr{Hom}_{\mathcal{O}_X}(\mathcal{F},-)}&quot;', bend right = 30, from=1-1, to=1-3]	\arrow[&quot;&quot;{name=1, anchor=center, inner sep=0}, &quot;{-\otimes_{\mathcal{O}_X}\mathcal{F}}&quot;', bend right = 30, from=1-3, to=1-1]	\arrow[&quot;\dashv&quot;{anchor=center, rotate=-90}, draw=none, from=1, to=0]\end{tikzcd}" /></p>
>

Where $-\otimes_{\mathcal{O}_X}\mathcal{F} = \mathfrak{a}(-\otimes_{\mathcal{O}_X}^{pre}\mathcal{F})$. 


#### References

[^1]: The Rising Sea in nLab. (n.d.). https://ncatlab.org/nlab/show/The+Rising+Sea. Accessed 20 May 2024
