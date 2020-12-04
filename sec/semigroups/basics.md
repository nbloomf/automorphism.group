---
title: Semigroups
---



Semigroups
----------

To a first approximation, algebra is all about studying sets equipped with functions satisfying some fixed set of properties. One of the simplest interesting examples of such a property is _associativity_; here we define a kind of algebra which has this and nothing else.

::: definition :::
Let $S$ be a set and $t : S \times S \rightarrow S$ a function. We say that $\langle S, t \rangle$ is a _semigroup_ if the following holds:

- $t(t(a,b),c) = t(a,t(b,c))$ for all $a,b,c \in S$.

Typically functions with signature $S \times S \rightarrow S$ are called _binary operators_ and written using infix notation. In that case, the associative property is written $(a \cdot b) \cdot c = a \cdot (b \cdot c)$.
::::::::::::::::::

At this stage we've only got one example, but it's a good one.

::: example :::
Let $A$ be a set. We define the set of all functions on $A$ by $$\mathsf{Map}(A) = \{ f \subseteq A \times A \mid f : A \rightarrow A \}.$$ Then $\langle \mathsf{Map}(A), \circ \rangle$ is a semigroup.

::: proof :::
We [already showed](@thm-composition-assoc) that composition of arbitrary functions is associative.
:::::::::::::
:::::::::::::::

We can also define a semigroup structure on singleton sets.

::: example :::
Let $S = \{a\}$ be a singleton set, and define $$\cdot = \{((a,a),a)\}.$$ Then $\langle S, \cdot \rangle$ is a semigroup; in fact this $\cdot$ is the _only_ operation such that $\langle S, \cdot \rangle$ is a semigroup.

::: proof :::
We should mention that $\cdot$ is a function, although the proof is trivial. It is also associative since we have $$(a \cdot a) \cdot a = a = a \cdot (a \cdot a)$$ as needed. Uniqueness follows because there is only one binary operation on a singleton set.
:::::::::::::
:::::::::::::::

We'll save a study of semigroups with two elements for later.



Subsemigroups
-------------

One of the Big Questions in algebra is this: given a class of algebras, how do we find examples? Examples are precious gems among a vast universe of logical garbage. To guide the search, it is often useful to find systematic ways of constructing _new_ examples out of existing ones. There are many examples of this phenomenon at work, and we describe one of the simplest here: taking subsets.

::: theorem :::
[@thm-subsemigroup]()
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

Finally we show that (3) implies (1). If $\langle T, u \rangle$ is a semigroup, then $u$ is a function with signature $T \times T \rightarrow T$; in particular, if $(a,b) \in T \times T$, then $u(a,b) \in T$ as needed.
:::::::::::::
:::::::::::::::

We don't usually go to the trouble of using a distinct symbol for the "restricted" operation on a subsemigroup, although in principle it is a different function (since it has a different signature).

We've already got some examples of subsemigroups.

::: example :::
[@thm-jection-semigroups]()
Let $A$ be a set. Then the following subsets of $\mathsf{Map}(A)$ are also subsemigroups of $\langle \mathsf{Map}, \circ \rangle$.

1. $\mathsf{Inj}(A) = \{ f \in \mathsf{Map}(A) \mid f\ \mathrm{is\ injective} \}$
2. $\mathsf{Surj}(A) = \{ f \in \mathsf{Map}(A) \mid f\ \mathrm{is\ surjective} \}$
3. $\mathsf{Sym}(A) = \{ f \in \mathsf{Map}(A) \mid f\ \mathrm{is\ bijective} \}$

::: proof :::
We've already shown that the composite of [injective](@thm-comp-injective), [surjective](@thm-comp-surjective), and [bijective](@thm-comp-bijective) functions retain the jectivity of their arguments.
:::::::::::::
:::::::::::::::

As a more concrete example, we've already enumerated the bijections on $A = \{1,2\}$.

::: example :::
Let $A = \{1,2\}$. Then $$\mathsf{Sym}(A) = \left\{ \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix}, \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \right\}$$ is a semigroup.

::: proof :::
We have already [enumerated](@thm-bijections-two-elts) the elements of $\mathsf{Sym}(A)$ as shown, and we just [established](@thm-jection-semigroups) that $\mathsf{Sym}(A)$ is a subsemigroup of $\mathsf{Map}(A)$ (and thus also a semigroup).
:::::::::::::
:::::::::::::::

The subsets of a set come equipped with a structure of their own, which we can take advantage of.

::: theorem :::
[@thm-subsemigroup-intersection]()
Let $\langle S, \cdot \rangle$ be a semigroup, and let $T_1$ and $T_2$ be subsemigroups of $S$. If $T_1 \cap T_2$ is not empty, then $T_1 \cap T_2$ is also a subsemigroup of $S$.

::: proof :::
Suppose $T_1 \cap T_2$ is not empty. (This condition is important, since in general the intersection of subsemigroups may be trivial!) Of course we have $T_1 \cap T_2 \subseteq S$.

Using our [definition](@thm-subsemigroup) of subsemigroup, it suffices to show that $T_1 \cap T_2$ is closed under $\cdot$. To this end, let $a,b \in T_1 \cap T_2$. Now $a,b \in T_1$, and since $T_1$ is a subsemigroup of $S$, we have $a \cdot b \in T_1$. Similarly, $a \cdot b \in T_2$. Thus we have $a \cdot b \in T_1 \cap T_2$, and so $T_1 \cap T_2$ is a subsemigroup of $S$ as claimed.
:::::::::::::
:::::::::::::::

The union of two subsemigroups is generally not also a subsemigroup. There is a universal way to turn the union of semigroups into a (generally larger) subsemigroup, however. We will examine that concept later.



Special Elements, Special Semigroups
------------------------------------

We'll often refer to the operation on a semigroup as its "product" or "multiplication", by analogy with multiplication of numbers. Recall that there are two particular numbers which exhibit extreme behavior under multiplication: zero and one. These extreme behaviors can have analogs among semigroup elements as well.

::: definition :::
[@def-semigroup-zero-element]()
Let $\langle S, \cdot \rangle$ be a semigroup with $z \in Z$.

- $z$ is called a _left zero_ if we have $z \cdot s = z$ for all $s \in S$.
- $z$ is called a _right zero_ if we have $s \cdot z = z$ for all $s \in S$.
- $z$ is called a _zero_ if it is both a left and a right zero.
::::::::::::::::::

Not every semigroup has a zero element. However, given a semigroup we can always add a zero element to it.

::: theorem :::
Let $\langle S, t \rangle$ be a semigroup, and let $z$ be an element not in $S$. Define $\mathsf{Z}_z(S) = S \cup \{ z \}$ and define

$$\begin{eqnarray*}
u
 & = & t \cup \{ ((z,s),z) \mid s \in S \} \\
 &   & \cup \{ ((s,z),s) \mid s \in S \} \cup \{ ((z,z),z) \}.
\end{eqnarray*}$$

Then $\langle \mathsf{Z}_z(S), u \rangle$ is a semigroup and $S$ is a subsemigroup of $\mathsf{Z}_z(S)$. We say that $\mathsf{Z}_z(S)$ is obtained from $S$ by _adjoining a zero_.

::: proof :::
Since we defined $u$ as a set, we'll first establish that it is a function. To that end we need to show it is total and well-defined.

- To see that $u$ is total, note that there are four possibilities for an element $x \in \mathsf{Z}_z(S) \times \mathsf{Z}_z(S)$, which are distinct since $z \not\in S$. If $x = (s_1,s_2)$ with $s_1, s_2 \in S$, then (since $t$ is total) we have $w \in S \subseteq \mathsf{Z}_z(S)$ such that $((s_1,s_2),w) \in t \subseteq u$. If $x = (s,z)$ with $s \in S$, then $((s,z),z) \in u$. If $x = (z,s)$ with $s \in S$, then $((z,s),s) \in u$, and finally if $x = (z,z)$ then $((z,z),z) \in u$. So $u$ is total.
- To see that $u$ is well-defined, suppose we have $x \in \mathsf{Z}_z(S) \times \mathsf{Z}_z(S)$ and $w_1, w_2 \in \mathsf{Z}_z(S)$ such that $(x,w_1) \in u$ and $(x,w_2) \in u$. Again there are four possibilities for $x$. If $x \in S \times S$, then $w_1 = w_2$ because $t$ is total. In the other three cases we have $w_1 = z = w_2$ as needed. So $u$ is total.

Next we need to show that $u$ is associative. To that end, note first that $u(z,x) = u(x,z) = z$ for all $x \in \mathsf{Z}_z(S)$. Now suppose we have $a,b,c \in \mathsf{Z}_z(S)$; we consider four possibilities.

- If $a = z$, we have $$\begin{eqnarray*} u(u(a,b),c) & = & u(u(z,b),c) \\ & = & u(z,c) \\ & = & z \\ & = & u(z,u(b,c)) \\ & = & u(a,u(b,c)). \end{eqnarray*}$$
- If $b = z$, we have $$\begin{eqnarray*} u(u(a,b),c) & = & u(u(a,z),c) \\ & = & u(z,c) \\ & = & z \\ & = & u(a,z) \\ & = & u(a,u(z,c)) \\ & = & u(a,u(b,c)). \end{eqnarray*}$$
- If $c = z$, we have $$\begin{eqnarray*} u(u(a,b),c) & = & u(u(a,b),z) \\ & = & z \\ & = & u(a,z) \\ & = & u(a,u(b,z)) \\ & = & u(a,u(b,c)). \end{eqnarray*}$$
- Suppose now that $a,b,c \neq z$; then we have $a,b,c \in S$. Since $t$ is associative, we then have $$\begin{eqnarray*} u(u(a,b),c) & = & u(t(a,b),c) \\ & = & t(t(a,b),c) \\ & = & t(a,t(b,c)) \\ & = & u(a,t(b,c)) \\ & = & u(a,u(b,c)). \end{eqnarray*}$$

Since $a$, $b$, and $c$ were arbitrary in $\mathsf{Z}_z(S)$, $u$ is associative, and so $\langle \mathsf{Z}_z(S), u \rangle$ is a semigroup.

To see that $S \subseteq \mathsf{Z}_z(S)$ is a subsemigroup it [suffices](@thm-subsemigroup) to show that $S$ is closed under $u$. But of course if $a,b \in S$, then $u(a,b) = t(a,b) \in S$ as needed.
:::::::::::::
:::::::::::::::

Note that not every semigroup that _has_ a zero is obtained from some other semigroup by _adjoining_ a zero. Adjunction (adjoinment?) can only produce very special semigroups where the product of two nonzero elements is never zero.

Also note that there were no restrictions on the semigroups $S$ to which we can adjoin a zero. So we can adjoin _two_ zeros, like $\mathsf{Z}_w(\mathsf{Z}_z(S))$. We need to be very careful, however, because only the outermost adjoined "zero" is actually a zero _element_ in the whole semigroup; for instance in this example we have $w \cdot z = z \cdot w = w$, so $z$ is not a zero element even though it was adjoined to $S$ as a zero. More generally, if $S$ has a zero element already it will not be one anymore in $\mathsf{Z}_z(S)$.

The zero element of a semigroup, if it exists, is unique.

::: theorem :::
[@thm-semigroup-zero-unique]()
Let $S$ be a semigroup with $a,b \in S$. If $a$ is a left zero and $b$ a right zero, then $a = b$. In particular, if $S$ has a zero element then it is unique.

::: proof :::
We have $$a = a \cdot b = b;$$ the first equality since $a$ is a left zero and the second because $b$ is a right zero. The "in particular" follows because every zero element is both a left and a right zero by definition.
:::::::::::::
:::::::::::::::

Note that this result says nothing about the uniqueness of one-sided zeros, and indeed they need not be unique. In fact left and right zeros can fail to be unique in the worst possible way.

::: theorem :::
Let $S$ be a nonempty set, and define $u \subseteq (S \times S) \times S$ by $$u = \{((s,t),s) \mid s,t \in S \}.$$ Then we have the following.

1. $u$ is a function with signature $S \times S \rightarrow S$.
2. $\langle S, u \rangle$ is a semigroup.
3. Every element of $S$ is a left zero.

If a semigroup satisfies condition (3), we say it is a _left zero_ semigroup. When $S$ is equipped with this operation we refer to it as $\mathsf{LZ}(S)$, pronounced "left zero semigroup on $S$".

::: proof :::
First we show (1); that $u$ is a function. This requires showing that $u$ is total and well-defined.

- To see that $u$ is total, note that if $a,b \in S$ then by definition $((a,b),a) \in u$ as needed.
- To see that $u$ is well-defined, suppose we have $(a,b) \in S \times S$ and $c_1, c_2 \in S$ such that $((a,b),c_1) \in u$ and $((a,b),c_2) \in u$. By definition, we have $c_1 = a = c_2$ as needed.

Next we show (2); for this it suffices to show that $u$ is associative. To this end, let $a,b,c \in S$. Now $$\begin{eqnarray*} u(u(a,b),c) & = & u(a,b) \\ & = & a \\ & = & u(a,u(b,c)) \end{eqnarray*}$$ as needed.

Finally we show (3). To this end let $a \in S$. We want to show that $a$ is a left zero. To do that, let $b \in S$; from the definition of $u$ we have $u(a,b) = a$. Since $b$ was arbitrary, $a$ is a left zero, and since $a$ was arbitrary, _every_ element of $S$ is a left zero.
:::::::::::::
:::::::::::::::

That is, it's possible that _every_ element of a semigroup is a left zero. We have an analogous theorem for right zeros.

::: theorem :::
Let $S$ be a nonempty set, and define $u \subseteq (S \times S) \times S$ by $$u = \{((s,t),t) \mid s,t \in S \}.$$ Then we have the following.

1. $u$ is a function with signature $S \times S \rightarrow S$.
2. $\langle S, u \rangle$ is a semigroup.
3. Every element of $S$ is a right zero.

If a semigroup satisfies condition (3), we say it is a _right zero_ semigroup. When $S$ is equipped with this operation we refer to it as $\mathsf{RZ}(S)$, pronounced "right zero semigroup on $S$".

::: proof :::
This proof is entirely analogous to the corresponding theorem about left zero semigroups.
:::::::::::::
:::::::::::::::

We have another pathological example: constant functions $S \times S \rightarrow S$ also yield a semigroups.

::: theorem :::
Let $S$ be a nonempty set with $z \in S$, and let $\cdot : S \times S \rightarrow S$ be $\cdot = \mathsf{const}_{z}$. Then $\langle S, \cdot \rangle$ is a semigroup. Semigroups of this form are called _null_ semigroups, and the null semigroup on $S$ with constant $z$ is denoted $\mathsf{K}_z(S)$ (k for constant).

::: proof :::
It suffices to show that this product is associative. To that end, let $a,b,c \in S$. Now $$(a \cdot b) \cdot c = z = a \cdot (b \cdot c);$$ since $a$, $b$, and $c$ were arbitrary, $\cdot$ is associative as needed.
:::::::::::::
:::::::::::::::

We've seen what can happen when a semigroup element acts like zero. Interesting things also happen when elements act like one.

::: definition :::
Let $\langle S, \cdot \rangle$ be a semigroup with $u \in S$.

1. $u$ is called a _left unit_ if we have $u \cdot s = s$ for all $s \in S$.
2. $u$ is called a _right unit_ if we have $s \cdot u = s$ for all $s \in S$.
3. $u$ is called a _unit_ if it is both a left and a right unit.
::::::::::::::::::

Again, not every semigroup has a unit, but we can always add a unit to an existing semigroup.

::: theorem :::
Let $\langle S, t \rangle$ be a semigroup, and let $e$ be an element not in $S$. Define $\mathsf{U}_e(S) = S \cup \{e\}$ and define $$\begin{eqnarray*} u & = & t \cup \{ ((e,s),s) \mid s \in S \} \\ & & \cup \{ ((s,e),s) \mid s \in S \} \cup \{((e,e),e)\}. \end{eqnarray*}$$

Then $\langle \mathsf{U}_e(S), u \rangle$ is a semigroup and $S$ is a subsemigroup of $\mathsf{U}_e(S)$. We say that $\mathsf{U}_e(S)$ is obtained from $S$ by _adjoining a unit_.

::: proof :::
Because we defined $u$ as a set, we should show it is a function. To do this we'll show it is both total and well-defined.

- To see that $u$ is total, note that there are four possibilities for an element $x \in \mathsf{U}_e(S) \times \mathsf{U}_e(S)$, which are distinct since $e \notin S$. If $x = (s_1,s_2)$ with $s_1,s_2 \in S$, then (since $t$ is total) we have $w \in S \subseteq \mathsf{U}_e(S)$ such that $(x,w) \in t \subseteq u$. If $x = (s,e)$ with $s \in S$, then $((s,e),s) \in u$. If $x = (e,s)$ with $s \in S$, then $(x,s) \in u$. Finally, if $x = (e,e)$, then $(x,e) \in u$. So $u$ is total.
- To see that $u$ is well-defined, suppose we have $x \in \mathsf{U}_e(S) \times \mathsf{U}_e(S)$ and $w_1,w_2 \in \mathsf{U}_e(S)$ such that $(x,w_1) \in u$ and $(x,w_2) \in u$. Again there are four possibilities for $x$. If $x \in S \times S$, then $w_1 = w_2$ because $t$ is total. If $x = (e,s)$ with $s \in S$, then $w_1 = s = w_2$. If $x = (s,e)$ with $s \in S$, then $w_1 = s = w_2$. Finally, if $x = (e,e)$, then $w_1 = e = w_2$. So $u$ is well-defined.

Next we need to show that $u$ is associative. To that end, note that $u(e,s) = s$ and $u(s,e) = s$ for all $s \in \mathsf{U}_e(S)$. Now let $a,b,c \in \mathsf{U}_e(S)$. We consider four possibilities.

- If $a = e$, then
$$\begin{eqnarray*}
u(u(a,b),c)
 & = & u(u(e,b),c) \\
 & = & u(b,c) \\
 & = & u(e,u(b,c)) \\
 & = & u(a,u(b,c)).
\end{eqnarray*}$$
- If $b = e$, then
$$\begin{eqnarray*}
u(u(a,b),c)
 & = & u(u(a,e),c) \\
 & = & u(a,c) \\
 & = & u(a,u(e,c)) \\
 & = & u(a,u(b,c)).
\end{eqnarray*}$$
- If $c = e$, then
$$\begin{eqnarray*}
u(u(a,b),c)
 & = & u(u(a,b),e) \\
 & = & u(a,b) \\
 & = & u(a,u(b,e)) \\
 & = & u(a,u(b,c)).
\end{eqnarray*}$$
- Suppose then that $a,b,c \neq e$, so that $a,b,c \in S$. Since $t$ is associative, we have
$$\begin{eqnarray*}
u(u(a,b),c)
 & = & u(t(a,b),c) \\
 & = & t(t(a,b),c) \\
 & = & t(a,t(b,c)) \\
 & = & u(a,t(b,c)) \\
 & = & u(a,u(b,c)).
\end{eqnarray*}$$

Since $a$, $b$, and $c$ were arbitrary in $\mathsf{U}_e(S)$, $u$ is associative, so that $\langle \mathsf{U}_e(S), u \rangle$ is a semigroup.

To see that $S \subseteq \mathsf{U}_e(S)$ is a subsemigroup it [suffices](@thm-subsemigroup) to show that $S$ is closed under $u$. But if $a,b \in S$, then $u(a,b) = t(a,b) \in S$ as needed.
:::::::::::::
:::::::::::::::

Also again, not every semigroup that has a unit is obtained by adjoining a unit, and as with adjoining a zero, we can adjoin multiple units. We can even adjoin both zeros _and_ units! However, if a unit exists, it is unique.

::: theorem :::
[@thm-semigroup-unit-unique]()
Let $S$ be a semigroup with $a,b \in S$. If $a$ is a left unit and $b$ a right unit, then $a = b$. In particular, if $S$ has a unit element then it is unique.

::: proof :::
We have $$b = a \cdot b = a;$$ the first equality since $a$ is a left unit and the second equality since $b$ is a right unit. The "in particular" follows because every unit element is both a left and a right unit by definition.
:::::::::::::
:::::::::::::::
