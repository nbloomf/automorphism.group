---
title: Semigroups
---



::: definition :::
Let $S$ be a set and $t : S \times S \rightarrow S$ a function. We say that $\langle S, \cdot \rangle$ is a _semigroup_ if the following holds:

- For all $a,b,c \in S$, $f(f(a,b),c) = f(a,f(b,c))$.

Typically functions with signature $S \times S \rightarrow S$ are called _binary operators_ and written using infix notation. In that case, the associative property is written $(a \cdot b) \cdot c = a \cdot (b \cdot c)$.
::::::::::::::::::

::: example :::
Let $A$ be a set. We define the set of all functions on $A$ by $$\mathsf{Map}(A) = \{ f \subseteq A \times A \mid f : A \rightarrow A \}.$$ Then $\langle \mathsf{Map}(A), \circ \rangle$ is a semigroup.

::: proof :::
We [already showed](@thm-composition-assoc) that composition of arbitrary functions is associative.
:::::::::::::
:::::::::::::::