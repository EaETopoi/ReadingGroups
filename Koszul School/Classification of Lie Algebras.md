---
date: 2024-05-16T13:05:00
tags:
  - LieAlgebras
  - RepresentationTheory
type: Notes
summary:
---
## Introduction
These notes are part of a reading group on representation theory and the use of Lie algebras.

## Lie Algebras

Lie algebras are classically associated with Lie groups (i.e. group objects in the category of smooth manifolds) by taking the tangent space at the identity. However, we can consider Lie algebras more generally purely algebraically. 

>[!def] Lie Algebras
>A **Lie algebra** $\mathfrak{g}$ over a field $\mathbb{F}$ is an $\mathbb{F}$-vector space with a linear map $$[,]:\mathfrak{g}\otimes_\mathbb{F}\mathfrak{g}\to \mathfrak{g}$$
>satisfying the following properties (where we write $\otimes$ simply for $\otimes_\mathbb{F}$)
>- (**Alternating**) The following diagram commutes
><p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathfrak%7Bg%7D%7D%20%26%26%20%7B%5Cmathfrak%7Bg%7D%5Cotimes%20%5Cmathfrak%7Bg%7D%7D%20%5C%5C%0A%09%26%20%7B%5Cmathfrak%7Bg%7D%7D%0A%09%5Carrow%5B%22%5CDelta%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%220%22'%2C%20from%3D1-1%2C%20to%3D2-2%5D%0A%09%5Carrow%5B%22%7B%5B%2C%5D%7D%22%2C%20from%3D1-3%2C%20to%3D2-2%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{\mathfrak{g}} &amp;&amp; {\mathfrak{g}\otimes \mathfrak{g}} \\&amp; {\mathfrak{g}}\arrow[&quot;\Delta&quot;, from=1-1, to=1-3]\arrow[&quot;0&quot;', from=1-1, to=2-2]\arrow[&quot;{[,]}&quot;, from=1-3, to=2-2]\end{tikzcd}" /></p>
>- (**Jacobi Identity**) If $c:-\otimes -\xrightarrow{\cong} -\otimes -$ is the swap isomorphism for the tensor and $a:(-\otimes-)\otimes-\xrightarrow{\cong}-\otimes(-\otimes-)$ denotes the associator, we have the following commuting diagram
><p align="center"><img align="center" src="https://i.upmath.me/svg/%0A%5Cbegin%7Btikzcd%7D%5Bwhite%5D%0A%09%7B%5Cmathfrak%7Bg%7D%5Cotimes%20(%5Cmathfrak%7Bg%7D%5Cotimes%20%5Cmathfrak%7Bg%7D)%7D%20%26%26%20%7B%5Cmathfrak%7Bg%7D%7D%20%5C%5C%0A%09%7B%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%7D%20%26%26%20%7B%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%7D%20%5C%5C%0A%09%7B%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%7D%20%26%26%20%7B%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%5Coplus%20%5Cmathfrak%7Bg%7D%5E%7B%5Cotimes%203%7D%7D%0A%09%5Carrow%5B%22%7B%5Cmathbbm%7B0%7D%7D%22%2C%20from%3D1-1%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5CDelta_3%7D%22'%2C%20from%3D1-1%2C%20to%3D2-1%5D%0A%09%5Carrow%5B%22%7B%5Cmathbbm%7B1%7D%5Coplus%20c_%7B%5Cmathfrak%7Bg%7D%2C%5Cmathfrak%7Bg%7D%5Cotimes%5Cmathfrak%7Bg%7D%7D%5Coplus%20c_%7B%5Cmathfrak%7Bg%7D%2C%5Cmathfrak%7Bg%7D%5Cotimes%5Cmathfrak%7Bg%7D%7D%7D%22'%2C%20from%3D2-1%2C%20to%3D3-1%5D%0A%09%5Carrow%5B%22%7B%2B%7D%22'%2C%20from%3D2-3%2C%20to%3D1-3%5D%0A%09%5Carrow%5B%22%7B%5Cmathbbm%7B1%7D%5Coplus%20a_%7B%5Cmathfrak%7Bg%7D%2C%5Cmathfrak%7Bg%7D%2C%5Cmathfrak%7Bg%7D%7D%20%5Coplus%20a_%7B%5Cmathfrak%7Bg%7D%2C%5Cmathfrak%7Bg%7D%2C%5Cmathfrak%7Bg%7D%7D%7D%22'%2C%20from%3D3-1%2C%20to%3D3-3%5D%0A%09%5Carrow%5B%22%7B%5Cmathbbm%7B1%7D%5Coplus%20%5Cmathbbm%7B1%7D%5Coplus%20(%5Cmathbbm%7B1%7D%5Cotimes%20c_%7B%5Cmathfrak%7Bg%7D%2C%5Cmathfrak%7Bg%7D%7D)%7D%22'%2C%20from%3D3-3%2C%20to%3D2-3%5D%0A%5Cend%7Btikzcd%7D%0A" alt="\begin{tikzcd}[white]{\mathfrak{g}\otimes (\mathfrak{g}\otimes \mathfrak{g})} &amp;&amp; {\mathfrak{g}} \\{\mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}} &amp;&amp; {\mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}} \\{\mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}} &amp;&amp; {\mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}\oplus \mathfrak{g}^{\otimes 3}}\arrow[&quot;{\mathbbm{0}}&quot;, from=1-1, to=1-3]\arrow[&quot;{\Delta_3}&quot;', from=1-1, to=2-1]\arrow[&quot;{\mathbbm{1}\oplus c_{\mathfrak{g},\mathfrak{g}\otimes\mathfrak{g}}\oplus c_{\mathfrak{g},\mathfrak{g}\otimes\mathfrak{g}}}&quot;', from=2-1, to=3-1]\arrow[&quot;{+}&quot;', from=2-3, to=1-3]\arrow[&quot;{\mathbbm{1}\oplus a_{\mathfrak{g},\mathfrak{g},\mathfrak{g}} \oplus a_{\mathfrak{g},\mathfrak{g},\mathfrak{g}}}&quot;', from=3-1, to=3-3]\arrow[&quot;{\mathbbm{1}\oplus \mathbbm{1}\oplus (\mathbbm{1}\otimes c_{\mathfrak{g},\mathfrak{g}})}&quot;', from=3-3, to=2-3]\end{tikzcd}" /></p>
>
>A map of lie algebras is an $\mathbb{F}$-vector space homomorphism that preserves the bracket.

The bracket also gives us a natural algebra homomorphism for any fixed $X \in \mathfrak{g}$, namely
$$
\text{ad}_{X}:\mathfrak{g}\xrightarrow{X\otimes-}\mathfrak{g}\otimes\mathfrak{g}\xrightarrow{[,]}\mathfrak{g}
$$
In fact, the assignment of elements of the lie algebra to its **adjoint operator** is also a lie algebra homomorphism, 
$$
\text{ad}:\mathfrak{g}\to \text{Der}_{\mathbb{F}}(\mathfrak{g})
$$
This is also beginning to approach the theory of representations of lie algebras. 

>[!def] Representation of Lie algebras
>Given an $\mathbb{F}$-Lie algebra $\mathfrak{g}$ and an $\mathbb{F}$-vector space $V$, a **representation** of $\mathfrak{g}$ on $V$ is a Lie algebra homomorphism $$ \pi:\mathfrak{g}\to\mathfrak{gl}(V)$$

Here $\mathfrak{gl}(V) = \text{End}(V)$ equipped with the bracket $[X,Y] := X\circ Y-Y\circ X$. This is a special case of a general lie algebra structure that can be applied to any ring. The adjoint operator can also be realized as an example of a representation of a lie algebra. Now that we have a lot of definitions, lets give some simple examples.

>[!example]
>Every matrix group over $\mathbb{F} = \mathbb{C}$ or $\mathbb{R}$ is naturally a Lie group, and hence has a corresponding Lie algebra given by its tangent at the identity.
>- For $\mathbf{GL}(n,\mathbb{F})$, $\mathfrak{gl}(n,\mathbb{F})$ is simply the space of all $n\times n$ matrices.
>- For $\mathbf{SL}(n,\mathbb{F})$, $\mathfrak{sl}(n,\mathbb{F})$ is the space of traceless $n\times n$ matrices
>- For $\mathbf{O}(n,\mathbb{R}) = \{A \in \mathbf{GL}(n,\mathbb{R}):\langle A-,A-\rangle = \langle-,-\rangle\}$, and one of its connected components, $\mathbf{SO}(n,\mathbb{R}) = \{A \in \mathbf{O}(n,\mathbb{R}):\det(A)=1\}$, have the same lie algebra $\mathfrak{so}(n,\mathbb{R}) = \{A \in \mathfrak{gl}(n,\mathbb{R}):A^T = -A\}$ 
>- Replacing $\mathbb{R}$ by $\mathbb{C}$ above gives $\mathbf{U}(n,\mathbb{C})$, $\mathbf{SU}(n,\mathbb{C})$, while the Lie algebras differ as $\mathfrak{u}(n,\mathbb{C})$ consists of those $X \in \mathfrak{gl}(n,\mathbb{C})$ such that $X^\dagger = -X$, while $\mathfrak{su}(n,\mathbb{C})$ is the subspace of $\mathfrak{u}(n,\mathbb{C})$ consisting of traceless matrices.

As in rings we have notions of **ideals** in Lie algebras which are identical to rings but with multiplication requirements replaced by the Bracket. A classical example of an ideal is $\mathscr{D}(\mathfrak{g})$ consisting of all elements in the image of the bracket. When this ideal is trivial the Lie algebra is said to be **abelian**. 

As in the case of groups and modules, the classification of Lie algebras hinges on a clear understanding of subobjects and quotients.

>[!def] Simple
>A Lie algebra is said to be **simple** if it has no non-trivial ideals. A Lie algebra is said to be **semi-simple** if it has no non-trivial **abelian ideals**. (i.e. ideals which are abelian as Lie algebras in their own right.)

