---
title: Semigroups
---



::: definition :::
Let $S$ be a set and $t : S \times S \rightarrow S$ a function. We say that $\langle S, t \rangle$ is a _semigroup_ if the following holds:

- For all $a,b,c \in S$, $t(t(a,b),c) = t(a,t(b,c))$.

Typically functions with signature $S \times S \rightarrow S$ are called _binary operators_ and written using infix notation. In that case, the associative property is written $(a \cdot b) \cdot c = a \cdot (b \cdot c)$.
::::::::::::::::::

::: example :::
Let $A$ be a set. We define the set of all functions on $A$ by $$\mathsf{Map}(A) = \{ f \subseteq A \times A \mid f : A \rightarrow A \}.$$ Then $\langle \mathsf{Map}(A), \circ \rangle$ is a semigroup.

::: proof :::
We [already showed](@thm-composition-assoc) that composition of arbitrary functions is associative.
:::::::::::::
:::::::::::::::



Subsemigroups
-------------

::: theorem :::
Let $\langle S, t \rangle$ be a semigroup, with $T \subseteq S$ be a nonempty subset, and define $$u = \{ (a,b) \in t \mid a \in T \times T \}.$$ Then the following are equivalent.

1. For all $a,b \in T$, $u(a,b)$ is also in $T$.
2. $u$ is a function with signature $T \times T \rightarrow T$.
3. $\langle T, u \rangle$ is a semigroup.

When these conditions hold, we say that $T$ is a _subsemigroup_ of $S$. When condition (1) holds specifically we say that $T$ is _closed_ under $t$.

::: proof :::
First we show that (1) implies (2). We'll need to show three things: that $u$ is a subset of $(T \times T) \times T$, that $u$ is total, and that $u$ is well-defined.

- Let $(a,b) \in u$. By definition, we have $a = (x,y)$ for some $x,y \in T$, and $b = t(x,y)$. Condition (1) yields that $b = t(x,y) \in T$, and so we have $(a,b) \in (T \times T) \times T$. Thus $u \subseteq (T \times T) \times T$ as needed.
- Next we show that $u$ is total. To this end, let $a \in T \times T \subseteq S \times S$. Because $t$ is total, we have $(a,b) \in t$, for some $b \in S$, and thus $(a,b) \in u$.
- Finally we show that $u$ is well-defined. To this end, suppose we have $a \in T \times T$ and $b_1, b_2 \in T$ such that $(a,b_1) \in u$ and $(a,b_2) \in u$. Buy definition, we also have $(a,b_1) \in t$ and $(a,b_2) \in t$. Since $t$ is a function, it is well-defined, and so $b_1 = b_2$ as needed.

Thus $u$ is a function with signature $T \times T \rightarrow T$.

Next we show that (2) implies (3). It suffices to show that $u$ is associative. Note that, by definition, for all $x,y \in T$ we have $u(x,y) = t(x,y)$. Thus for all $x,y,z \in T$, we have

$$\begin{eqnarray*}
u(u(x,y),z)
 & = & t(t(x,y),z) \\
 & = & t(x,t(y,z)) \\
 & = & u(x,u(y,z))
\end{eqnarray*}$$

as needed; thus $\langle T, u \rangle$ is a semigroup.

Finally we show that (3) implies (1). If $\langle T, u \rangle$ is a semigroup, then $u$ is a function with signature $T \times T \rightangle T$; in particular, if $(a,b) \in T \times T$, then $u(a,b) \in T$ as needed.
:::::::::::::
:::::::::::::::

We don't usually go to the trouble of using a distinct symbol for the "restricted" operation on a subsemigroup, although in principle it is a different function (since it has a different signature).

We've already got some examples of subsemigroups.

::: example :::
Let $A$ be a set. Then the following subsets of $\mathsf{Map}(A)$ are also subsemigroups of $\langle \mathsf{Map}, \circ \rangle$.

1. $\mathsf{Inj}(A) = \{ f \in \mathsf{Map}(A) \mid f\ \mathrm{is\ injective} \}$
2. $\mathsf{Surj}(A) = \{ f \in \mathsf{Map}(A) \mid f\ \mathrm{is\ surjective} \}$
3. $\mathsf{Sym}(A) = \{ f \in \mathsf{Map}(A) \mid f\ \mathrm{is\ bijective} \}$

::: proof :::
We've already shown that the composite of [injective](@thm-comp-injective), [surjective](@thm-comp-surjective), and [bijective](@thm-comp-bijective) functions retain the jectivity of their arguments.
:::::::::::::
:::::::::::::::
