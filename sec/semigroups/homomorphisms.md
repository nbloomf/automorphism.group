---
title: Semigroup Homomorphisms
---



Homomorphisms
-------------

The concept of "semigroup" represents a kind of structure. As we'll see, anytime we have a kind of structure, the structure-preserving functions are typically useful. These are called _homomorphisms_.

::: definition :::
[@def-semigroup-homomorphism]()
Let $\langle S, \cdot \rangle$ and $\langle T, \star \rangle$ be semigroups and $f : S \rightarrow T$ a function. We say that $f$ is a _semigroup homomorphism_ if the following holds:

- $f(a \cdot b) = f(a) \star f(b)$ for all $a,b \in S$.

If in addition $f$ is bijective, we say that $f$ is a _semigroup isomorphism_ and that $S$ and $T$ are _isomorphic_, written $S \cong T$.
::::::::::::::::::

I like to think of a homomorphism $f : S \rightarrow T$ as projecting a shadow of $S$ into $T$.

Homomorphisms interact with the basic algebra of functions as we'd hope; the identity is a homomorphism:

::: theorem :::
Let $S$ be a semigroup. The identity function $\mathsf{id}_S$ is an isomorphism.

::: proof :::
We've already [shown](@thm-id-bijective) that $\mathsf{id}_S$ is a bijection, so we just need to show it is a homomorphism. To see this, let $a,b \in S$. Now
$$\begin{eqnarray*}
\mathsf{id}_S(a \cdot b)
 & = & a \cdot b \\
 & = & \mathsf{id}_S(a) \cdot \mathsf{id}_S(b)
\end{eqnarray*}$$
as required.
:::::::::::::
:::::::::::::::

And the composite of two homomorphisms is a homomorphism:

::: theorem :::
Let $S$, $T$, and $U$ be semigroups, and suppose $f : S \rightarrow T$ and $g : T \rightarrow U$ are homomorphisms. Then $g \circ f : S \rightarrow U$ is a homomorphism. If $f$ and $g$ are isomorphisms, then $g \circ f$ is an isomorphism.

::: proof :::
Let $a,b \in S$. Then we have
$$\begin{eqnarray*}
(g \circ f)(a \cdot b)
 & = & g(f(a \cdot b)) \\
 & = & g(f(a) \cdot f(b)) \\
 & = & g(f(a)) \cdot g(f(b)) \\
 & = & (g \circ f)(a) \cdot (g \circ f)(b)
\end{eqnarray*}$$
as required. The isomorphism part follows because, as we've already [shown](@thm-comp-bijective), the composite of bijections is a bijection.
:::::::::::::
:::::::::::::::

There is a unique homomorphism from any given semigroup to a semigroup with one element.

::: theorem :::
Let $S$ be a semigroup, and let $\langle \{e\}, \cdot \rangle$ be the unique semigroup on the singleton set $\{e\}$. Then there is a unique semigroup homomorphism $f : S \rightarrow \{e\}$.

::: proof :::
Let $f = \mathsf{const}_e$. To see that $f$ is a homomorphism, let $a,b \in S$. Then $$f(a \cdot b) = e = e \cdot e = f(a) \cdot f(e)$$ as required. To see that $f$ is unique, suppose $g : S \rightarrow \{e\}$ is another homomorphism; then for all $a \in S$ we have $g(a) = e = f(a)$. So $g = f$.
:::::::::::::
:::::::::::::::



Isomorphisms
------------

_Isomorphism_ is an especially important concept. It is very rare for two given semigroups to be equal; equality is simply too strict. However an isomorphism between semigroups means that the two are essentially the same _up to a renaming of the elements_. It captures the _meaning_ while throwing away unimportant information. For this reason, we often end up trying to characterize some class of semigroups (or any alebras, for that matter) _up to isomorphism_. For this reason, it is handy to have some criteria which can demonstrate when two semigroups are _not_ isomorphic.

::: theorem :::
[@thm-semigroup-zero-identity-transfer]()
Let $\langle S, \cdot \rangle$ and $\langle T, \star \rangle$ be semigroups and $f : S \rightarrow T$ a surjective semigroup homomorphism.

1. If $z \in S$ is a left (right) zero, then $f(z) \in T$ is a left (right) zero.
2. If $z \in S$ is a zero element, then $f(z) \in T$ is a zero element.
3. If $u \in S$ is a left (right) identity, then $f(u) \in T$ is a left (right) identity.
4. If $u \in S$ is an identity element, then $f(u) \in T$ is an identity element.

::: proof :::
First we show (1). To this end, first suppose $z$ is a left zero in $S$. Now let $t \in T$. Since $f$ is surjective, there exists $s \in S$ with $f(s) = t$. Now
$$\begin{eqnarray*}
f(z) \star t
 & = & f(z) \star f(s) \\
 & = & f(z \cdot s) \\
 & = & f(z)
\end{eqnarray*}$$
since $z$ is a left zero element in $S$. Since $t$ was arbitray in $T$, $f(z)$ is a left zero. The proof for $z$ a right zero is analogous. Now (2) follows from (1) and the [uniqueness](@thm-semigroup-zero-unique) of simultaneous one-sided zeros because every zero is both a left and a right zero.

We can show (3) similarly. Suppose $u \in S$ is a left identity and let $t \in T$. Since $f$ is surjective, there exists $s \in S$ with $f(s) = t$. Now
$$\begin{eqnarray*}
f(u) \star t
 & = & f(u) \star f(s) \\
 & = & f(u \cdot s) \\
 & = & f(s) \\
 & = & t;
\end{eqnarray*}$$
we similarly have $t \star f(u) = t$. Since $t$ was arbitrary in $T$, $f(u)$ is a left identity. The proof for $u$ a right identity is analogous. Now (4) follows from (3) and the [uniqueness](@thm-semigroup-identity-unique) of simultaneous one-sided identities because every identity is both a left and a right identity.
:::::::::::::
:::::::::::::::

This theorem can be used to show that two semigroups are _not_ isomorphic; for instance, if we know that one has a zero but the other does not.

We can also use isomorphisms to justify referring to _the_ left or right zero semigroup on a set.

::: theorem :::
Let $\langle S, \cdot \rangle$ be a semigroup.

1. If every element of $S$ is a left zero, then $S \cong \mathsf{LZ}(S)$.
2. If every element of $S$ is a right zero, then $S \cong \mathsf{RZ}(S)$.

::: proof :::
First we show (1). Denote by $\star$ the operation on the left zero semigroup $\mathsf{LZ}(S)$. To show that two semigroups are isomorphic, we must first exhibit a function from one to the other, then show it is a homomorphism, and finally show that it is bijective.

Recall that as sets we have $S = \mathsf{LZ}(S)$. So we define $f : S \rightarrow \mathsf{LZ}(S)$ by $f = \mathsf{id}_S$. To see that $f$ is a homomorphism, let $s,t \in S$ and note that

$$\begin{eqnarray*}
f(s \cdot t)
 & = & f(s) \\
 & = & f(s) \star f(t).
\end{eqnarray*}$$

(Here we used the fact that $s$ is a left zero in $S$ and $f(s)$ is a left zero in $\mathsf{LZ}(S)$.) Since $s$ and $t$ were arbitrary in $S$, $f$ is a homomorphism. Finally, we have [shown](@thm-id-bijective) that the identity function is bijective. So we have $S \cong \mathsf{LZ}(S)$ as claimed.

The proof of (2) is analogous.
:::::::::::::
:::::::::::::::

Isomorphisms also interact with zero and identity adjunction.

::: theorem :::
Let $\langle S, \cdot \rangle$ and $\langle T, \star \rangle$ be semigroups, and suppose we have elements $h \notin S$ and $k \notin T$. Suppose further that $f : S \rightarrow T$ is an isomorphism. Then we have the following.

1. $g = f \cup \{ (h,k) \}$ is a bijective function with signature $S \cup \{h\} \rightarrow T \cup \{k\}$.
2. $g$ is an isomorphism $\mathsf{Z}_h(S) \rightarrow \mathsf{Z}_k(T)$.
3. $g$ is an isomorphism $\mathsf{U}_h(S) \rightarrow \mathsf{U}_k(T)$.

::: proof :::
First we show (1). Certainly we have $g \subseteq (S \cup \{h\}) \times (T \cup \{k\})$. To see that $g$ is a function we show it is total and well-defined.

- To see that $g$ is total, let $x \in S \cup \{h\}$. if $x \in S$, then since $f$ is total, we have $y \in T$ such that $(x,y) \in f \subseteq g$. If $x = h$ then $(h,k) \in g$. So $g$ is total.
- To see that $g$ is well-defined, suppose we have $x \in S \cup \{h\}$ and $y_1,y_2 \in T \cup \{k\}$ such that $(x,y_1) \in g$ and $(x,y_2) \in g$. We have two possibilities for $x$. If $x \in S$, then in fact $(x,y_1) \in f$ and $(x,y_2) \in f$; since $f$ is well-defined we have $y_1 = y_2$. Suppose instead that $x = h$. Then we have $y_1 = k = y_2$. So $g$ is well-defined.

So $g$ is a function. To see that $g$ is bijective, define $u = f^{-1} \cup \{(k,h)\}$. The argument showing that $g$ is a function also applies to $u$, so we have $u : T \cup \{k\} \rightarrow S \cup \{h\}$. Moreover, we have $u \circ g = \mathsf{id}_{S \cup \{h\}}$ and $g \circ u = \mathsf{id}_{T \cup \{k\}}$, and [so](@thm-bij-inverses) $g$ is bijective.

Now we show (2). To this end, let $a,b \in \mathsf{Z}_h(S)$. We have four possibilities for $a$ and $b$.

- If $a \in S$ and $b \in S$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & f(a \cdot b) \\
 & = & f(a) \star f(b) \\
 & = & g(a) \star g(b).
\end{eqnarray*}$$
- If $a \in S$ and $b = h$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & g(a \cdot h) \\
 & = & g(h) \\
 & = & k \\
 & = & g(a) \star k \\
 & = & g(a) \star g(h) \\
 & = & g(a) \star g(b).
\end{eqnarray*}$$
- If $a = h$ and $b \in S$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & g(h \cdot b) \\
 & = & g(h) \\
 & = & k \\
 & = & k \star g(b) \\
 & = & g(h) \star g(b) \\
 & = & g(a) \star g(b).
\end{eqnarray*}$$
- If $a = h$ and $b = h$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & g(h \cdot h) \\
 & = & g(h) \\
 & = & k \\
 & = & k \star k \\
 & = & g(h) \star g(k).
\end{eqnarray*}$$
So $g$ is a homomorphism, and thus an isomorphism.

Finally we show (3). To this end, let $a,b \in \mathsf{U}_h(S)$. We have four possibilities for $a$ and $b$.

- If $a \in S$ and $b \in S$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & f(a \cdot b) \\
 & = & f(a) \star f(b) \\
 & = & g(a) \star g(b).
\end{eqnarray*}$$
- If $a \in S$ and $b = h$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & g(a \cdot h) \\
 & = & g(a) \\
 & = & g(a) \star k \\
 & = & g(a) \star g(h) \\
 & = & g(a) \star g(b).
\end{eqnarray*}$$
- If $a = h$ and $b \in S$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & g(h \cdot b) \\
 & = & g(b) \\
 & = & k \star g(b) \\
 & = & g(h) \star g(b) \\
 & = & g(a) \star g(b).
\end{eqnarray*}$$
- If $a = h$ and $b = h$, we have
$$\begin{eqnarray*}
g(a \cdot b)
 & = & g(h \cdot h) \\
 & = & g(h) \\
 & = & k \\
 & = & k \star k \\
 & = & g(h) \star g(k).
\end{eqnarray*}$$
So $g$ is a homomorphism, and thus an isomorphism.
:::::::::::::
:::::::::::::::

And there is essentially only one null semigroup on a given set.

::: theorem :::
[@thm-null-semigroup-isomorpic]()
Let $S$ be a nonempty set, and suppose we have $u,v \in S$ with $u \neq v$. Define $f \subseteq \mathsf{K}_u(S) \times \mathsf{K}_v(S)$ by $$f = \{ (x,x) \mid x \in S, x \neq u,\ \mathrm{and}\ x \neq v \} \cup \{ (u,v), (v,u) \}.$$ Then $f$ is an isomorphism $\mathsf{K}_u(S) \rightarrow \mathsf{K}_v(S)$.

::: proof :::
First we need to show that $f$ is a function; total and well-defined.

- To see that $f$ is total, let $a \in S$. If $a = u$ then $(a,v) \in f$. If $a = v$ then $(a,u) \in f$. If $a \neq u$ and $a \neq v$, then $(a,a) \in f$.
- To see that $f$ is well-defined, suppose we have $x \in S$ and $y_1,y_2 \in S$ such that $(x,y_1) \in f$ and $(x,y_2) \in f$. If $x = u$, then $y_1 = v = y_2$. If $x = v$, then $y_1 = u = y_2$. Suppose then that $x \neq u$ and $x \neq v$; then we have $y_1 = x = y_2$. So $f$ is well-defined.

Thus $f$ is a function. Next we need to show that $f$ is bijective; to this end, we claim that $f \circ f = \mathsf{id}_S$. To see this we consider three cases for $x \in S$.

- If $x = u$ then
$$\begin{eqnarray*}
(f \circ f)(x)
 & = & (f \circ f)(u) \\
 & = & f(f(u)) \\
 & = & f(v) \\
 & = & u \\
 & = & \mathsf{id}_S(u) \\
 & = & \mathsf{id}_S(x).
\end{eqnarray*}$$
- If $x = v$, then
$$\begin{eqnarray*}
(f \circ f)(x)
 & = & (f \circ f)(v) \\
 & = & f(f(v)) \\
 & = & f(u) \\
 & = & v \\
 & = & \mathsf{id}_S(v) \\
 & = & \mathsf{id}_S(x).
\end{eqnarray*}$$
- If $x \neq u$ and $x \neq v$, then
$$\begin{eqnarray*}
(f \circ f)(x)
 & = & f(f(x)) \\
 & = & f(x) \\
 & = & x \\
 & = & \mathsf{id}_S(x).
\end{eqnarray*}$$

So we have $f \circ f = \mathsf{id}_S$. Since $f$ has a left and a right inverse, it is bijective.

Finally we need to show that $f$ is a homomorphism. To this end, let $a,b \in S$. Then $$f(a \cdot b) = f(u) = v = f(a) \cdot f(b)$$ as required.
:::::::::::::
:::::::::::::::

Suppose we have a set $S$ and a binary operation $\cdot : S \times S \rightarrow S$, but we don't know if $\cdot$ is associative. The naive way to check this is to look at all possible triples $a,b,c \in S$ and see if $(a \cdot b) \cdot c$ is equal to $a \cdot (b \cdot c)$. When $S$ is finite (whatever that means) the number of cases to check grows with the cube of the size of $S$. There is another strategy we can use that brings the amount of work down to the square of the size of $S$; show that $S$ is related to some other known semigroup.

::: theorem :::
[@thm-set-assoc-transfer]()
Let $S$ be a set and $\cdot : S \times S \rightarrow S$ a (not necessarily associative!) binary operation on $S$. Suppose we have a semigroup $\langle T, \star \rangle$.

1. If we have an injective function $f : S \rightarrow T$ such that for all $a,b \in S$, $f(a \cdot b) = f(a) \star f(b)$, then $\langle S, \cdot \rangle$ is a semigroup and $f$ a homomorphism.
2. If we have a surjective function $g : T \rightarrow S$ such that for all $a,b \in T$, $f(a \star b) = f(a) \cdot f(b)$, then $\langle S, \cdot \rangle$ is a semigroup and $f$ a homomorphism.

::: proof :::
First we show (1). It suffices to show that $\cdot$ is associative; that $f$ is a homomorphism follows trivially. To this end, let $a,b,c \in S$. Now we have

$$\begin{eqnarray*}
f((a \cdot b) \cdot c)
 & = & f(a \cdot b) \star f(c) \\
 & = & (f(a) \star f(b)) \star f(c) \\
 & = & f(a) \star (f(b) \star f(c)) \\
 & = & f(a) \star f(b \cdot c) \\
 & = & f(a \cdot (b \cdot c)).
\end{eqnarray*}$$

Because $f$ is injective, we have $(a \cdot b) \cdot c = a \cdot (b \cdot c)$. Since $a$, $b$, and $c$ were arbitrary in $S$, $\cdot$ is associative, and so $\langle S, \cdot \rangle$ is a semigroup.

Next we show (2); again it suffices to show that $\cdot$ is associative. To this end, let $a,b,c \in S$. Because $f$ is surjective, there exist $x,y,z \in T$ such that $f(x) = a$, $f(y) = b$, and $f(z) = c$. Now we have

$$\begin{eqnarray*}
(a \cdot b) \cdot c
 & = & (f(x) \cdot f(y)) \cdot f(z) \\
 & = & f(x \star y) \cdot f(z) \\
 & = & f((x \star y) \star z) \\
 & = & f(x \star (y \star z)) \\
 & = & f(x) \cdot f(y \star z) \\
 & = & f(x) \cdot (f(y) \cdot f(z)) \\
 & = & a \cdot (b \cdot c).
\end{eqnarray*}$$

Since $a$, $b$, and $c$ were arbitrary in $S$, $\cdot$ is associative, so that $\langle S, \cdot \rangle$ is a semigroup, and moreover $f$ is a homomorphism, as claimed.
:::::::::::::
:::::::::::::::

We will now embark on a quest to determine all of the semigroup operations on a set with two elements by brute force. This will be painful. With the tools we have available, we won't be able to avoid some amount of brute force case analysis. More or less, that means examining each of the 16 binary operations on a two-element set and determining which ones are associative. The main goal of proving a result like this is to motivate the development of more powerful tools. :)

::: example :::
Let $S = \{a,b\}$ be a set with $a \neq b$. Find the operations $\cdot$ on $S$ such that $\langle S, \cdot \rangle$ is a semigroup, and determine which of these are distinct up to isomorphism.

::: proof :::
We start by considering the two possible values of $a \cdot a$.

First, suppose $a \cdot a = b$. Now suppose $a \cdot b$ and $b \cdot a$ are not equal; then we have
$$\begin{eqnarray*}
(a \cdot a) \cdot a
 & = & b \cdot a \\
 & \neq & a \cdot b \\
 & = & a \cdot (a \cdot a);
\end{eqnarray*}$$
so that $\cdot$ is not associative. Thus we must have $a \cdot b = b \cdot a$. There are four possibilities for this common value along with $b \cdot b$.

- Suppose $a \cdot b = b \cdot a = a$ and $b \cdot b = a$. But now we have
$$\begin{eqnarray*}
(a \cdot a) \cdot b
 & = & b \cdot b \\
 & = & a \\
 & \neq & b \\
 & = & a \cdot a \\
 & = & a \cdot (a \cdot b)
\end{eqnarray*}$$
so $\cdot$ is not associative.
- Suppose $a \cdot b = b \cdot a = a$ and $b \cdot b = b$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & b & a \\
b & a & b
\end{array}$$
We claim that this operation is associative. To see why, define $f : S \rightarrow \mathsf{Sym}(\{1,2\})$ by $$f = \left\{ \left(a, \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix}\right), \left(b, \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix} \right) \right\}.$$ It is clear that $f$ is total and well-defined, and moreover as a function is bijective. We also claim that $f(x \cdot y) = f(x) \circ f(y)$ for all $x,y \in S$; we can brute force this with four cases.
$$\begin{eqnarray*}
f(a \cdot a)
 & = & f(b) \\
 & = & \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix} \\
 & = & \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \circ \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \\
 & = & f(a) \circ f(a), \\
 &   & \\
f(a \cdot b)
 & = & f(a) \\
 & = & \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \\
 & = & \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \circ \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix} \\
 & = & f(a) \circ f(b), \\
 &   & \\
f(b \cdot a)
 & = & f(a) \\
 & = & \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \\
 & = & \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix} \circ \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \\
 & = & f(b) \circ f(a),\ \mathrm{and} \\
 &   & \\
f(b \cdot b)
 & = & f(b) \\
 & = & \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix} \\
 & = & \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix} \circ \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix} \\
 & = & f(b) \circ f(b).
\end{eqnarray*}$$
Since $\mathsf{Sym}(\{1,2\})$ is a [semigroup](@thm-jection-semigroups), as we established in the [previous result](@thm-set-assoc-transfer), this means that $\cdot$ is associative, $S$ is a semigroup, and in fact $f$ is a homomorphism. But we have a bit more: since $f$ is bijective, it is an _isomorphism_, so we have $S \cong \mathsf{Sym}(\{1,2\})$. I did warn that this would be painful.
- Suppose $a \cdot b = b \cdot a = b$ and $b \cdot b = a$. But now we have
$$\begin{eqnarray*}
(a \cdot b) \cdot b
 & = & a \cdot b \\
 & = & a \\
 & \neq & b \\
 & = & a \cdot a \\
 & = & a \cdot (b \cdot b)
\end{eqnarray*}$$
so $\cdot$ is not associative.
- Suppose $a \cdot b = b \cdot a = b$ and $b \cdot b = b$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & b & b \\
b & b & b
\end{array}$$
Then we have $S = \mathsf{K}_b(S)$.

Now suppose $a \cdot a = a$.

Suppose further that $b \cdot b = a$. Now suppose $a \cdot b$ and $b \cdot a$ are not equal; then we have
$$\begin{eqnarray*}
(b \cdot b) \cdot b
 & = & a \cdot b \\
 & \neq & b \cdot a \\
 & = & b \cdot (b \cdot b);
\end{eqnarray*}$$
so that $\cdot$ is not associative. Thus we must have $a \cdot b = b \cdot a$. There are two possibilities for this common value.

- Suppose $a \cdot b = b \cdot a = a$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & a & a \\
b & a & a
\end{array}$$
Then we have $S = \mathsf{K}_a(S)$.
- Suppose instead that $a \cdot b = b \cdot a = b$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & a & b \\
b & b & a
\end{array}$$
We claim that this operation is associative. To see why, define $f : S \rightarrow \mathsf{Sym}(\{1,2\})$ by $$f = \left\{ \left(a, \begin{pmatrix} 1 & 2 \\ 1 & 2 \end{pmatrix}\right), \left(b, \begin{pmatrix} 1 & 2 \\ 2 & 1 \end{pmatrix} \right) \right\}.$$ Similarly to a previous case, this function satisfies $f(x \cdot y) = f(x) \circ f(y)$ for all $x, y \in S$, so that $S$ is a semigroup and $f$ is an isomorphism. Thus $S \cong \mathsf{Sym}(\{1,2\})$.

Now suppose (in addition to $a \cdot a = a$) that $b \cdot b = b$. There are four possibilities for the values of $a \cdot b$ and $b \cdot a$.

- Suppose $a \cdot b = a$ and $b \cdot a = a$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & a & a \\
b & a & b
\end{array}$$
Then we have $S = \mathsf{Z}_a(\{b\})$.
- Suppose $a \cdot b = a$ and $b \cdot a = b$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & a & a \\
b & b & b
\end{array}$$
Then we have $S = \mathsf{LZ}(S)$.
- Suppose $a \cdot b = b$ and $b \cdot a = a$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & a & b \\
b & a & b
\end{array}$$
Then we have $S = \mathsf{RZ}(S)$.
- Suppose $a \cdot b = b$ and $b \cdot a = b$; that is, the multiplication table of $S$ looks like this:
$$\begin{array}{c|cc}
  & a & b \\ \hline
a & a & b \\
b & b & b
\end{array}$$
Then we have $S = \mathsf{Z}_b(\{a\})$.

Among the binary operations on $S$, we've shown that each one is either not associative or _is_ associative and either equal to or isomorphic to one of $\mathsf{Sym}(\{1,2\})$, $\mathsf{K}_b(S)$, $\mathsf{K}_a(S)$, $\mathsf{Z}_a(\{b\})$, $\mathsf{LZ}(S)$, $\mathsf{RZ}(S)$, and $\mathsf{Z}_b(\{a\})$. Not all of these are distinct up to isomorphism, though; we have already [seen](@thm-null-semigroup-isomorpic) that $\mathsf{K}_a(S) \cong \mathsf{K}_b(S)$ and because $\{a\} \cong \{b\}$ as one-element semigroups, $\mathsf{Z}_a(\{b\}) \cong \mathsf{Z}_b(\{a\})$.

This cuts our list down to five: $$\mathsf{Sym}(\{1,2\}), \mathsf{K}_a(S), \mathsf{Z}_b(\{a\}), \mathsf{LZ}(S),\ \mathrm{and}\ \mathsf{RZ}(S).$$ We claim that these five are mutually nonisomorphic.

- $\mathsf{Sym}(\{1,2\})$ has an identity element, while the other four do not; so it is distinct up to isomorphism.
- $\mathsf{K}_a(S)$ is null, while the other four are not; so it is distinct up to isomorphism.
- $\mathsf{Z}_b(\{a\})$ has a zero element, while $\mathsf{LZ}(S)$ and $\mathsf{RZ}(S)$ do not; so it is not isomorphic to them.
- $\mathsf{LZ}(S)$ has a left zero but $\mathsf{RZ}(S)$ does not, so these two are distinct.

So a semigroup containing two elements is isomorphic to one of these 5.
:::::::::::::
:::::::::::::::

Okay! So we've classified the semigroups with two elements up to isomorphism. Is this interesting? I mean, sort of? Realistically semigroups are such weak structures that they end up being extremely numerous, so building complete tables of them like this is computationally very difficult. What's really interesting about this classification theorem is the machinery we developed to prove it.

This is a common pattern in mathematics; the journey is sometimes more interesting than the destination. :)
