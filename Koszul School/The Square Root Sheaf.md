---
date: 2024-05-16T14:41:00
tags:
  - AlgebraicGeometry
  - LocalSystems
  - Sheaves
type: Notes
summary:
---
## Introduction

In these notes we wish to study the (equivariant) local system known as the square root sheaf.

## The Goal

Throughout we let $X = \mathbb{C}^\times$ and $G = \mathbf{GL}_1$. We have the square action $G\times X\to X$ given by $(t,x)\mapsto t^2x$. Now, consider the following result of Achar [Prop 6.2.13](zotero://open-pdf/library/items/6IX3KWCC?page=274&annotation=X3DGWV8N)  

>[!proposition|6.2.13]
>%% display: Prop 6.2.13 %%
>Let $G$ be a algebraic group, and let $X$ be a homogeneous space with point $x$. There is an equivalence of categories: $$\mathcal{L}oc_{G}^{ft}(X,\mathbb{C}) \cong \mathbb{C}[G^x/(G^x)^\circ]-\text{mod}$$
>where $G^x$ is the stabilizer of $x$ under the action of $G$ and $(G^x)^\circ$ is its connected component at the identity.

^9c947c

`\begin{proof}[Proof Idea.]`
Since $X$ is a Homogenous space we have an isomorphism $X \cong G/G^x$. Now, we have the natural quotient $$G/(G^x)^\circ \twoheadrightarrow G/G^x$$
Further, this quotient is a covering map, with the Galois group of the covering being $G^\times/(G^\times)^\circ$. It follows that we have a surjection $$\pi_{1}(X,x)\twoheadrightarrow G^x/(G^x)^\circ$$
`\end{proof}`
Let us consider an example for the concepts in Proposition [[The Square Root Sheaf#^9c947c|Prop 6.2.13]].  

>[!example]
>In the context of the square action $G\times X\to X$, as given above, we have the following:
>-The bijection $X \cong G/G^\times$ is given by a map $\mathbb{C}^\times/\langle \pm 1\rangle \xrightarrow{\cong} \mathbb{C}^\times$ given by $t\mapsto t^2$. 

## The Theory

Let us now return to a simpler setting before discussing equivariance, which is [Theorem 1.7.9](zotero://open-pdf/library/items/6IX3KWCC?page=44&annotation=F3MFF747) in [@acharPramodAcharPerverse2021].

>[!theorem|1.7.9]
>Suppose  $(X,x_{0}) \in \mathsf{Top}$ is a connected, locally path connected, and semi-locally simply connected space (i.e.  triply connected). Then there is an equivalence of categories given by Monodromy  $$\text{Mon}_{x_{0}}:\mathcal{L}oc(X,R)\to R[\pi_{1}(X,x_{0})]-\mathsf{mod}$$

`\begin{proof}[Proof Idea.]`
We will construct the map in the opposite direction. To begin let $M \in R[\pi_1(X,x_0)]$ denote a representation of the fundamental group and denote the action by $\rho$. 
- For each point $x \in X$ choose a path $\alpha_x:[0,1]\to X$ such that $\alpha_x(0) = x_0$ and $\alpha_x(1) = x$, and fixing $\alpha_{x_0} = c_{x_0}$, the constant path, we define a pre-sheaf (in fact a local system) $\mathcal{F}_{M}$ on $X$ given by $$\mathcal{F}_{M}(U) := \left\{s:U\to M\,\vert\,\forall \gamma :[0,1]\to U,\;s(\gamma(0)) = \rho(\alpha_{\gamma(0)}\cdot \gamma \cdot \overline{\alpha_{\gamma(1)}})\bullet s(\gamma(1))\right\}$$
`\end{proof}`

Lets return to the case of the square root sheaf, which we denote by $\mathcal{F}$. Then $$\mathcal{F}(U) = \left\{g:U\to \mathbb{C}\,\vert\,g \text{ holomorphic, } z\frac{dg}{dz}-\frac{1}{2}g=0 \right\}$$ We claim that the square root sheaf is a local system. Consider the opens given by branch-cuts $U_1 = \mathbb{C}^\times\backslash(-\infty,0)$ and $U_2 = \mathbb{C}^\times\backslash (0,\infty)$. Note that the $U_i$ are simply connected. Further, we can define branches of the logarithm $\log_i$ given by argument functions $\arg_1(z) \in (-\pi,\pi)$ and $\arg_2(z) \in (0,2\pi)$, respectively. Since the $U_i$ are connected domains, then, if we fix $g \in \mathcal{F}(U_i)$, it follows that $\left(\frac{g}{f_i}\right)' = 0$ for $f_i = e^{\log_i(z)/2}$ implies $g = \lambda_gf_i$ for some constant $\lambda_g$. 

Therefore, we have a natural isomorphism $\mathcal{F}\vert_{U_i}\to \underline{\mathbb{C}}\vert_{U_i}$ given by sending $g$ to $\frac{g}{f_i}$. 

**Q.** Why in general is $\mathcal{F}$ not a constant sheaf?

Note that $\mathcal{F}$, as all sheaves with sheaf restrictions, can be realized as a gluing of its sub-sheaves for an open cover. In particular, this implies that we can realize $\mathcal{F}$ as a gluing of $\underline{\mathbb{C}}\vert_{U_1}$ and $\underline{\mathbb{C}}\vert_{U_2}$ along $U_1\cap U_2 = V_1 \amalg V_2$ where $V_1 = \{z \in \mathbb{C}:\text{Im}(z) > 0\}$ and $V_2 = \{z \in \mathbb{C}:\text{Im}(z) < 0\}$, so in particular this is a disconnected space. Here our isomorphism is
$$
\underline{\mathbb{C}}\vert_{U_{1}}\vert_{U_{1}\cap U_{2}}\xrightarrow{\cong}\underline{\mathbb{C}}\vert_{U_{2}}\vert_{U_{1}\cap U_{2}}
$$
We can represent the left as being sections on the connected components, $(\lambda_{1} f_1\vert_{V_1},\lambda_{2} f_1\vert_{V_2})$ and $(\lambda_{1} f_2\vert_{V_1},\lambda_{2} f_2\vert_{V_2})$. Since our arguments differ by $\pi$ in the lower half plane, but agree in the upper half plane, we map $(\lambda_{1} f_1\vert_{V_1},\lambda_{2} f_1\vert_{V_2})$ to $(\lambda_{1} f_2\vert_{V_1}, -\lambda_{2} f_2\vert_{V_2})$. 
