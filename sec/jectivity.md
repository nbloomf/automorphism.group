---
title: Jectivity
---



Surjectivity
------------

In this section we'll define some special classes of functions. The first consists of functions that "hit" every element of the codomain.

::: definition :::
[@def-surjective]()
Let $f : A \rightarrow B$ be a function. We say that $f$ is _surjective_ if for every $b \in B$, there is an $a \in A$ such that $f(a) = b$.
::::::::::::::::::

Sometimes this property is called _onto_, as in $f : A \rightarrow B$ is _onto_ $B$. This terminology is grammatically dubious, so I prefer to avoid it, but it's common in older literature. It's also instructive to note that surjectivity is "dual" to totality; the total property of a function means that every element of the domain is an input, while surjectivity means that every element in the codomain is an output.

Showing that a function is surjective usually involves choosing an arbitrary element of the codomain and showing it is the image of some element in the domain. Our first example is pretty boring.

::: example :::
[@thm-id-surjective]()
The identity function $\mathsf{id}_A$ on a set $A$ is surjective.

::: proof :::
Let $a \in A$. Note that $a = \mathsf{id}_A(a)$. Since $a$ was arbitrary in $A$, $\mathsf{id}_A$ is surjective.
:::::::::::::
:::::::::::::::

Slightly less trivial, the composite of surjective functions is surjective.

::: theorem :::
Let $f : A \rightarrow B$ and $g : B \rightarrow C$ be functions. If $f$ and $g$ are surjective, then $g \circ f$ is surjective.

::: proof :::
Let $c \in C$. Since $g$ is surjective, there is a $b \in B$ such that $g(b) = c$. Similarly, since $f$ is surjective, there is an $a \in A$ with $f(a) = b$. Now $$(g \circ f)(a) = g(f(a)) = g(b) = c.$$ Since $c$ was arbitrary in $C$, $g \circ f$ is surjective as claimed.
:::::::::::::
:::::::::::::::



Injectivity
-----------

Where surjectivity was dual to totality, well-definedness also has a dual, called _injectivity_. These are functions which send distinct inputs to distinct outputs.

::: definition :::
[@def-injective]()
Let $f : A \rightarrow B$ be a function. We say $f$ is _injective_ if whenever $a_1, a_2 \in A$ such that $f(a_1) = f(a_2)$, we have $a_1 = a_2$.
::::::::::::::::::

This property is sometimes called _one-to-one_, but again I'll prefer injective. (Even _two-to-two_ would be better than one-to-one, since that more accurately reflects what it means.) Showing that a function is injective usually involves setting up an equality $f(x) = f(y)$ for arbitrary $x$ and $y$ and showing that $x = y$.

::: theorem :::
[@thm-id-injective]()
The identity function $\mathsf{id}_A$ is injective.

::: proof :::
Let $a_1, a_2 \in A$ with $\mathsf{id}_A(a_1) = \mathsf{id}_A(a_2)$. Using the definition of $\mathsf{id}_A$, we have $$a_1 = \mathsf{id}_A(a_1) = \mathsf{id}_A(a_2) = a_2.$$ Since $a_1$ and $a_2$ were arbitrary, $\mathsf{id}_A$ is injective as claimed.
:::::::::::::
:::::::::::::::

The composite of injective functions is again injective.

::: theorem :::
Let $f : A \rightarrow B$ and $g : B \rightarrow C$ be functions. If $f$ and $g$ are injective, then $g \circ f$ is also injective.

::: proof :::
Let $a_1, a_2 \in A$ such that $(g \circ f)(a_1) = (g \circ f)(a_2)$. Now $$g(f(a_1)) = (g \circ f)(a_1) = (g \circ f)(a_2) = g(f(a_2)).$$ Since $g$ is injective, we have $f(a_1) = f(a_2)$, and because $f$ is injective, we have $a_1 = a_2$. Since $a_1$ and $a_2$ were arbitrary in $A$, $g \circ f$ is injective as claimed.
:::::::::::::
:::::::::::::::
