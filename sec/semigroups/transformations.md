---
title: Semigroups of Transformations
---



Transformation Semigroups
-------------------------

We've already [shown](@ex-map-semigroup) that the set $\Map(S)$ of all functions from a set $S$ to itself forms a semigroup; in fact it's a monoid with identity $\id_A$. If $S$ is also a _semigroup_ then $\Map(A)$ has some interesting subsemigroups.

::: corollary :::
Let $S$ be a semigroup, and define subsets $$\End_\Sem(S) = \{ f : S \rightarrow S \mid f\ \mathrm{is\ a\ homomorphism} \}$$ and $$\Aut_\Sem(S) = \{ f : S \rightarrow S \mid f\ \mathrm{is\ an\ isomorphism} \}.$$ Then both $\End_\Sem(S)$ and $\Aut_\Sem(S)$ are subsemigroups of $\langle \Map(S), \circ \rangle$.

::: proof :::
We've already shown that these sets are closed under composition and that the identity function is an isomorphism.
:::::::::::::
:::::::::::::::::

These two semigroups somehow encode the structure of $S$, and so can be used to better understant $S$ itself.

There's another way to turn a set of functions into a semigroup.

::: theorem :::
Let $A$ be a set and $\langle S, \cdot \rangle$ a semigroup, and let $$\Map(A,S) = \{ f \subseteq A \times B \mid f : A \rightarrow S \}.$$ Define a binary operation $\psi$ on $\Map(A,S)$ by $$\psi(f,g)(a) = f(a) \cdot g(a).$$ Then we have the following.

1. $\langle \Map(A,S), \psi \rangle$ is a semigroup.
2. If $e \in S$ is a left (right) identity, then $\const_e \in \Map(A,S)$ is a left (right) identity.
3. If $S$ is a monoid, then $\Map(A,S)$ is a monoid.
4. If $z \in S$ is a left (right) zero, then $\const_z \in \Map(A,S)$ is a left (right) zero.

This is sometimes called the _pointwise_ product on $\Map(A,S)$.

::: proof :::
To see (1), we need to show that $\psi$ is associative. To this end let $f,g,h \in \Map(A,S)$. If $a \in A$, we have
$$\begin{eqnarray*}
 &   & \psi(f,\psi(g,h))(a) \\
 & = & f(a) \cdot \psi(g,h)(a) \\
 & = & f(a) \cdot (g(a) \cdot h(a)) \\
 & = & (f(a) \cdot g(a)) \cdot h(a) \\
 & = & \psi(f,g)(a) \cdot h(a) \\
 & = & \psi(\psi(f,g),h)(a).
\end{eqnarray*}$$
Since $a$ was arbitrary, we have $$\psi(f,\psi(g,h)) = \psi(\psi(f,g),h)$$ as needed.

To see (2), suppose $e \in S$ is a left identity; that is, $e \cdot s = s$ for all $s \in S$. Now let $f : A \rightarrow B$ and $a \in A$. We have
$$\begin{eqnarray*}
 &   & \psi(\const_e,f)(a) \\
 & = & \const_e(a) \cdot f(a) \\
 & = & e \cdot f(a) \\
 & = & f(a). \\
\end{eqnarray*}$$
Since $a$ is arbitrary, we have $\psi(\const_e,f) = f$, and since $f$ is arbitrary, $\const_e$ is a left identity. A similar argument shows that if $e$ is a right identity then $\const_e$ is a right identity. (3) then follows because every identity is both a left and a right identity.

The argument for (4) is very similar to that for (2). Suppose $z \in S$ is a left zero and let $f : A \rightarrow S$ and $a \in A$. Then
$$\begin{eqnarray*}
 &   & \psi(\const_z,f)(a) \\
 & = & \const_z(a) \cdot f(a) \\
 & = & z \cdot f(a) \\
 & = & z \\
 & = & \const_z(a).
\end{eqnarray*}$$
Since $a$ is arbitrary, $\psi(\const_z,f) = \const_z$, and since $f$ is arbitrary, $\const_z$ is a left zero. A similar argument shows that $\const_z$ is a right zero.
:::::::::::::
:::::::::::::::

The pointwise product doesn't encode the structure of $S$ quite like $\End$ and $\Aut$ do, but it does have uses.



Semigroup Actions
-----------------

Let's take a small detour to define yet another kind of algebra.

::: definition :::
Let $\langle S, \cdot \rangle$ be a semigroup and $A$ a set. Suppose we have a function $\star : S \times A \rightarrow A$. Then we say $\langle A, \star \rangle$ is a (left) _semigroup action_ of $S$ if for all $s,t \in S$ and $a \in A$ we have $$(s \cdot t) \star a = s \star (t \star a).$$

If $S$ is a monoid with identity $e$, we say further that $\langle A, \star \rangle$ is a (left) _monoid action_ if for all $a \in A$ we have $$e \star a = a.$$

Sometimes if we're discussing multiple semigroup actions, and definitely if we have multiple actions of the same semigroup on some set, we'll say $S$ acts on $A$ _via_ $\star$ to be explicit.
::::::::::::::::::

As usual, this algebra has a corresponding concept of _homomorphism_.

::: definition :::
Let $\langle S, \cdot \rangle$ be a semigroup and let $\langle A, \star \rangle$ and $\langle B, \bullet \rangle$ be (left) semigroup actions of $S$. A function $f : A \rightarrow B$ is called a _semigroup action homomorphism_ if for all $s \in S$ and $a \in A$ we have $$f(s \star a) = s \bullet f(a).$$ If $f$ is bijective, we call it a (left) semigroup action isomorphism and write $A \cong B$.
::::::::::::::::::

Also as usual, the identity function is a homomorphism.

::: theorem :::
Let $\langle S, \cdot \rangle$ be a semigroup and $\langle A, \star \rangle$ a semigroup action of $S$. Then $\id_A$ is a semigroup action homomorphism.

::: proof :::
Let $s \in S$ and $a \in A$. Then
$$\begin{eqnarray*}
 &   & \id_A(s \star a) \\
 & = & s \star a \\
 & = & s \star \id_A(a)
\end{eqnarray*}$$
as needed.
:::::::::::::
:::::::::::::::

The composite of homomorphisms is a homomorphism.

::: theorem :::
Let $\langle S, \cdot \rangle$ be a semigroup and $\langle A, \star_A \rangle$, $\langle B, \star_B \rangle$, and $\langle C, \star_C \rangle$ be (left) semigroup actions of $S$, and let $f : A \rightarrow B$ and $g : B \rightarrow C$ be semigroup action homomorphisms. Then $g \circ f : A \rightarrow C$ is a semigroup action homomorphism.

::: proof :::
Let $s \in S$ and $a \in A$. Then we have
$$\begin{eqnarray*}
 &   & (g \circ f)(s \star_A a) \\
 & = & g(f(s \star_A a)) \\
 & = & g(s \star_B f(a)) \\
 & = & s \star_C g(f(a)) \\
 & = & s \star_C (g \circ f)(a)
\end{eqnarray*}$$
as needed.
:::::::::::::
:::::::::::::::

And the inverse of an isomorphism is an isomorphism.

::: theorem :::
Let $\langle S, \cdot \rangle$ be a semigroup and $\langle A, \star \rangle$ and $\langle B, \bullet \rangle$ (left) semigroup actions of $S$, and suppose $f : A \rightarrow B$ is a semigroup action isomorphism. Then $f^{-1} : B \rightarrow A$ is a semigroup action isomorphism.

::: proof :::
Let $s \in S$ and $b \in B$. Since $f$ is bijective, there is an $a \in A$ such that $f(a) = b$ and $f^{-1}(b) = a$. Now
$$\begin{eqnarray*}
 &   & f^{-1}(s \bullet b) \\
 & = & f^{-1}(s \bullet f(a)) \\
 & = & f^{-1}(f(s \star a)) \\
 & = & (f^{-1} \circ f)(s \star a) \\
 & = & \id_A(s \star a) \\
 & = & s \star a \\
 & = & s \star f^{-1}(b)
\end{eqnarray*}$$
as needed.
:::::::::::::
:::::::::::::::

The signature and axiom of a semigroup action looks suspiciously like the semigroup product; it's not too surprising that semigroups are our first example.

::: example :::
Let $\langle S, \cdot \rangle$ be a semigroup; then $\langle S, \cdot \rangle$ is a (left) semigroup action.
:::::::::::::::

We won't have many more examples for a while, which is unfortunate because actions are really where semigroups (and their most interesting subclass, groups) really shine. This is especially so when the object being acted on is not just a _set_, but has structure of its own. A semigroup action represents a structure on the set of endomorphisms of an object. In fact we can make this intuition precise: a semigroup action on $A$ can be turned into a semigroup homomorphism to $\Map(A)$.

::: theorem :::
Let $\langle S, \cdot \rangle$ be a semigroup and let $A$ be a set, and let $\langle A, \star \rangle$ be a left semigroup action of $S$. Define $\theta_\star : S \rightarrow \Map(A)$ by $\theta_\star(s)(a) = s \star a$. Then we have the following.

1. $\theta_\star$ is a semigroup homomorphism.
2. If $S$ is a monoid and $\star$ a monoid action, then $\theta_\star$ is a monoid homomorphism.

::: proof :::
First we show (1). To that end, let $s,t \in S$, and let $a \in A$. Now
$$\begin{eqnarray*}
 &   & \theta_\star(s \cdot t)(a) \\
 & = & (s \cdot t) \star a \\
 & = & s \star (t \star a) \\
 & = & \theta_\star(s)(t \star a) \\
 & = & \theta_\star(s)(f_\star(t)(a)) \\
 & = & (\theta_\star(s) \circ \theta_\star(t))(a).
\end{eqnarray*}$$
Since $a$ was arbitrary in $A$, we have $$\theta_\star(s \cdot t) = \theta_\star(s) \circ \theta_\star(t)$$ as needed.

Now we show (2); this requires showing that $\theta_\star$ preserves identity elements. Suppose $S$ is a monoid with identity $e$; then we have $e \star a = a$ for all $a \in A$. Letting $a$ be arbitrary in $A$, we have
$$\begin{eqnarray*}
 &   & \theta_\star(e)(a) \\
 & = & e \star a \\
 & = & a \\
 & = & \id_A(a),
\end{eqnarray*}$$
so that $\theta_\star(e) = \id_A$. Recall that $\id_A$ is the identity element in the monoid $\langle \Map(A), \id_A \rangle$, so $\theta_\star$ is a monoid homomorphism.
:::::::::::::
:::::::::::::::

In fact the correspondence between actions and homomorphisms goes further; actions of $S$ on $A$ are precisely equivalent to homomorphisms $S \rightarrow \Map(A)$.

::: theorem :::
Let $\langle S, \cdot \rangle$ be a semigroup and let $A$ be a set. Let $$\Act_{S,\Sem}(A) = \{ \star : S \times A \rightarrow A \mid \star\ \mathrm{is\ an\ action} \}$$ be the set of all semigroup actions of $S$ on $A$, and let $$\Hom_\Sem(S,\Map(A)) = \{ f : S \rightarrow \Map(A) \mid f\ \mathrm{is\ a\ hom} \}$$ be the set of semigroup homomorphisms $S \rightarrow \Map(A)$. Now define a map $$\Theta : \Act_{S,\Sem}(A) \rightarrow \Hom_\Sem(S,\Map(A))$$ by $\Theta(\star) = \theta_\star.$ Then $\Theta$ is bijective with inverse $\Omega(f)(s,a) = f(s)(a).$

::: proof :::
This theorem involves a function that takes a function and outputs a function that outputs a function. It can be tough to keep track of what's happening, but if we're careful we can get through this. :)

We've already shown that $\theta_\star$ is a homomorphism, so $\Theta$ is well-defined. (It's important to point this out!) So it's enough to check that $\Theta$ and $\Omega$ are mutual inverses. To this end, first let $\star : S \times A \rightarrow A$ be a semigroup action of $S$ on $A$. Let $s \in S$ and $a \in A$. Note that $(\Omega \circ \Theta)(\star)$ is an action; so it has signature $S \times A \rightarrow A$. Now
$$\begin{eqnarray*}
 &   & (\Omega \circ \Theta)(\star)(s,a) \\
 & = & \Omega(\Theta(\star))(s,a) \\
 & = & \Theta(\star)(s)(a) \\
 & = & \theta_\star(s)(a) \\
 & = & s \star a \\
 & = & \star(s,a) \\
 & = & \id(\star)(s,a).
\end{eqnarray*}$$
Since $s$ and $a$ were arbitrary, we have $$(\Omega \circ \Theta)(\star) = \id(\star),$$ and since $\star$ was arbitrary, $\Omega \circ \Theta = \id$ as needed.

Now again let $f : S \rightarrow \Map(A)$ be a semigroup homomorphism and let $s \in S$ and $a \in A$. Now
$$\begin{eqnarray*}
 &   & (\Theta \circ \Omega)(f)(s)(a) \\
 & = & \Theta(\Omega(f))(s)(a) \\
 & = & \theta_{\Omega(f)}(s)(a) \\
 & = & \Omega(f)(s,a) \\
 & = & f(s)(a) \\
 & = & \id(f)(s)(a).
\end{eqnarray*}$$
Since $a$ was arbitrary, we have $$(\Theta \circ \Omega)(f)(s) = \id(f)(s);$$ since $s$ was arbitrary we have $$(\Theta \circ \Omega)(f) = \id(f);$$ and since $f$ was arbitrary we have $\Theta \circ \Omega = \id$ as needed.
:::::::::::::
:::::::::::::::

This theorem essentially says that semigroup actions are a redundant concept -- they are equivalent to homomorphisms $S \rightarrow \Map(A)$.
