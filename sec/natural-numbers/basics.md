---
title: Natural Numbers
---



Iterative Sets
--------------

Let's define another kind of algebra.

::: definition :::
Let $A$ be a set with a distinguished element $e \in A$ and a map $\varphi : A \rightarrow A$. Then we say the triple $\langle A, e, \varphi \rangle$ is an _iterative set_.
::::::::::::::::::

This is not so different from our definition of semigroup. Yes, semigroups have a _binary_ function while here we have only a unary function, and semigroups also satisfy a law. But the basic setup of a set with some functions is the same. All that is to say, iterative sets are a class of algebras.

There's not much we can do with one besides construct a list of successive values: $$e, \varphi(e), \varphi(\varphi(e)), \varphi(\varphi(\varphi(e))), \ldots$$ We might call this list of values the _iterates_ of $e$ under $\varphi$.

In general, not all of these values have to be distinct. As an example, we can enumerate the iterative sets which have two elements.

::: example :::
Let $B = \{t,f\}$. Describe the iterative sets over $B$ and, for each one, find the first few iterates of the distinguished element.

::: proof :::
We've [shown](@thm-func-two-elts) that there are four functions on $B$: $$g_1 = \begin{pmatrix} t & f \\ t & t \end{pmatrix}, g_2 = \begin{pmatrix} t & f \\ t & f \end{pmatrix}, g_3 = \begin{pmatrix} t & f \\ f & t \end{pmatrix}, g_4 = \begin{pmatrix} t & f \\ f & f \end{pmatrix}.$$ Since there are no restrictions on what functions can form iterative set, choosing one of these, and one element $e \in B$, gives 8 cases. We list them and the first few iterates $e$, $\varphi(e)$, $\varphi(\varphi(e))$ (et cetera) below.

1. $\langle B, t, g_1 \rangle$: $t$, $t$, $t$, $t$, $t$, $\ldots$
2. $\langle B, t, g_2 \rangle$: $t$, $t$, $t$, $t$, $t$, $\ldots$
3. $\langle B, t, g_3 \rangle$: $t$, $f$, $t$, $f$, $t$, $\ldots$
4. $\langle B, t, g_4 \rangle$: $t$, $f$, $f$, $f$, $f$, $\ldots$
5. $\langle B, f, g_1 \rangle$: $f$, $t$, $t$, $t$, $t$, $\ldots$
6. $\langle B, f, g_2 \rangle$: $f$, $f$, $f$, $f$, $f$, $\ldots$
7. $\langle B, f, g_3 \rangle$: $f$, $t$, $f$, $t$, $f$, $\ldots$
8. $\langle B, f, g_4 \rangle$: $f$, $f$, $f$, $f$, $f$, $\ldots$
:::::::::::::
:::::::::::::::

Iterative sets have a kind of structure, and it makes sense for a function to preserve that structure.

::: definition :::
Let $\langle A, e, \varphi \rangle$ and $\langle B, f, \psi \rangle$ be iterative sets, and let $\theta : A \rightarrow B$ be a function. We say that $\theta$ is an _iterative homomorphism_ if the following hold.

1. $\theta(e) = f$.
2. $\theta \circ \varphi = \psi \circ \theta$.
::::::::::::::::::

As usual, the identity function is a homomorphism:

::: theorem :::
[@thm-id-iterative-hom]()
Let $\langle A, e, \varphi \rangle$ be an iterative set. Then $\mathsf{id}_A$ is an iterative homomorphism.

::: proof :::
We have $\mathsf{id}_A(e) = e$ and $$\mathsf{id}_A \circ f = f = f \circ \mathsf{id}_A$$ as needed.
:::::::::::::
:::::::::::::::

And the composite of iterative homomorphisms is again a homomorphism.

::: theorem :::
[@thm-comp-iterative-hom]()
Let $\langle A, e, \varphi \rangle$, $\langle B, f, \psi \rangle$, and $\langle C, g, \chi \rangle$ be iterative sets, with iterative homomorphisms $\theta : A \rightarrow B$ and $\zeta : B \rightarrow C$. Then $\zeta \circ \theta : A \rightarrow C$ is an iterative homomorphism.

::: proof :::
We have $$(\zeta \circ \theta)(e) = \zeta(\theta(e)) = \zeta(f) = g$$ and
$$\begin{eqnarray*}
(\zeta \circ \theta) \circ \varphi
 & = & \zeta \circ (\theta \circ \varphi) \\
 & = & \zeta \circ (\psi \circ \theta) \\
 & = & (\zeta \circ \psi) \circ \theta \\
 & = & (\chi \circ \zeta) \circ \theta \\
 & = & \chi \circ (\zeta \circ \theta)
\end{eqnarray*}$$
as needed.
:::::::::::::
:::::::::::::::



Natural Numbers
---------------

We define the natural numbers to be a very special iterative set. We take the existence of this set as an axiom; it's possible it could be proven to exist in terms of more primitive machinery, but we have to start somewhere, and this is as good a place as any.

::: axiom :::
There is an iterative set $\langle \nats, \zero, \next \rangle$ which has the following _universal property_: if $\langle A, e, \varphi \rangle$ is an iterative set, then there is a unique iterative homomorphism $\Theta : \nats \rightarrow A$.

We denote this unique map $\natrec_{e,\varphi}$.
:::::::::::::

If you're not used to it, that might seem like a weird way to define numbers! However it turns out to be very useful for thory building and workable (if inefficient) for computations. The key is the uniqueness of homomorphisms from $\nats$. Like any iterative set, the iterates of $\zero$ look sort of like numbers, assuming they are all distinct. But the unique map $\natrec_{e,\varphi}$ mean that in some sense $\nats$ is the "smallest most general" iterative set.

$\natrec_{e,\varphi}$ captures the essential pattern of _recursion_ on natural numbers, and it does so in a very well-behaved way. Reasoning about recursion with $\natrec_{e,\varphi}$ can be very simple.

You might also be wondering how this formulation of $\nats$ compares to the usual Peano axioms. It turns out that we can (and we will) derive them as theorems. For example, we can prove a version of the induction principle.

::: theorem :::
[@thm-nat-induction]()
Let $A$ be a set and suppose we have a function (not a homomorphism!) $f : \nats \rightarrow A$. Suppose now that we have a subset $B \subseteq A$ satisfying the following:

1. $f(\zero) \in B$.
2. If $n \in \nats$ and $f(n) \in B$, then $f(\next(n)) \in B$.

Then we have $f(n) \in B$ for all $n \in \nats$. When using this theorem we say we are proceeding _by induction_; (1) is called the _base case_, and (2) is called the _inductive step_.

::: proof :::
We define a subset $T \subseteq \nats$ as follows: $$T = \{ n \in \nats \mid f(n) \in B \}.$$ Next we define a set $g \subseteq T \times T$ by $$g = \next \cap (T \times T).$$ We claim that $g$ is a function; to see this we need to show it is total and well defined.

- To see that $g$ is total, let $a \in T$; that is, $f(a) \in B$. From (2), we also have $f(\next(a)) \in B$, so that $\next(a) \in T$. So $(a,\next(a)) \in \next \cap (T \times T) = g$, and since $a$ was arbitrary, $g$ is total.
- To see that $g$ is well-defined, suppose we have $a \in T$ and $b_1,b_2 \in T$ such that $(a,b_1) \in g$ and $(a,b_2) \in g$. We then have $b_1 = \next(a) = b_2$ (since $\next$ is a function).

So $g$ is a function with signature $T \rightarrow T$. By (1) we also have $\zero \in T$, so $\langle T, \zero, g \rangle$ is an iterative set. The universal property of $\nats$ now applies; we let $\Theta = \natrec_{\zero,g}$ be the unique iterative homomorphism $\nats \rightarrow T$.

Now consider the inclusion map $\iota : T \rightarrow \nats$. In particular, $\iota(\zero) = \zero$, and we have
$$\begin{eqnarray*}
(\iota \circ g)(n)
 & = & \iota(g(n)) \\
 & = & g(n) \\
 & = & \next(n) \\
 & = & \next(\iota(n)) \\
 & = & (\next \circ \iota)(n);
\end{eqnarray*}$$
so $\iota$ is an iterative homomorphism. As we've [shown](@thm-comp-iterative-hom), the composite $\iota \circ \Theta$ is also an iterative homomorphism with signature $\nats \rightarrow \nats$. Since [we also know](@thm-id-iterative-hom) that $\mathsf{id}_{\nats}$ is an iterative homomorphism, by uniqueness, we must have $\iota \circ \Theta = \mathsf{id}_{\nats}$. If $n \in \nats$, we have $$n = \mathsf{id}_{\nats}(n) = (\iota \circ \Theta)(n) = \iota(\Theta(n)) = \Theta(n);$$ in particular, $n \in T$. So we have $f(n) \in B$. Since $n$ was arbitrary in $\nats$, the conclusion follows.
:::::::::::::
:::::::::::::::

A more traditional version of the induction principle follows as a corollary.

::: corollary :::
Suppose we have a subset $B \subseteq \nats$ satisfying the following properties:

1. $\zero \in B$.
2. For all $n \in \nats$, if $n \in B$ then $\next(n) \in B$.

Then $B = \nats$.

::: proof :::
This is a special case of the [induction principle](@thm-nat-induction) with $A = \nats$ and $f : \nats \rightarrow \nats$ the identity map.
:::::::::::::
:::::::::::::::::

The induction principle is a powerful technique for showing that some property holds for all natural numbers. We can extend it slightly to any set whose elements can be "measured" by natural numbers.

::: theorem :::
[@thm-induction-on-f]()
Let $f : A \rightarrow \nats$ be a function. Suppose we have $B \subseteq A$ satisfying the following.

1. $f(a) = \zero$ implies $a \in B$ for all $a \in A$.
2. For all $n \in \nats$, if $$f(a) = n\ \mathrm{implies}\ a \in B\ \mathrm{for\ all}\ a \in A,$$ then $$f(a) = \next(n)\ \mathrm{implies}\ a \in B\ \mathrm{for\ all}\ a \in A.$$

Then we have $B = A$. When using this theorem we say we are proceeding by induction _on_ $f$; (1) is called the _base case_, and (2) is called the _inductive step_.

::: proof :::
Define a subset $T \subseteq \nats$ as follows. $$T = \{ n \in \nats \mid f(a) = n\ \mathrm{implies}\ a \in B\ \mathrm{for\ all}\ a \in A \}.$$ We show that $T = \nats$ using induction with the identity map $g : \mathsf{id}_{\nats}$.

- To see the base case, note that $\mathsf{id}_{\nats}(\zero) = \zero \in T$ by (1).
- To see the inductive step, suppose we have $n \in \nats$ such that $n \in T$. By definition, we have $f(a) = n$ implies $a \in B$ for all $a \in A$. By (2), we have $f(a) \next(n)$ implies $a \in B$ for all $a \in A$, and so $\next(n) \in T$.

By induction, we have $T = \nats$. Now let $a \in A$. We have $f(a) = n$ for some $n \in \nats$. Since $n \in T$, we also have $a \in B$. So $A \subseteq B$, and thus $B = A$ as claimed.
:::::::::::::
:::::::::::::::

Note that this theorem does not require any structure on $A$ beyond the "measurement" function $f : A \rightarrow \nats$; this makes it very useful. If all the elements of $A$ have "finite size", then we can induct on the size. Whenever we see words like _finite dimension_, _finitely generated_, _finite length_, et cetera, odds are good that this theorem (or something like it) can be applied.

The induction principle is the most complicated among the Peano axioms; to show that $\nats$ really does act how we expect the natural numbers to, we'll also establish the  other two "important" axioms: that $\zero$ is not equal to $\next(n)$ for any $n$, and that $\next$ is injective. For both of these we need a utility function.

::: definition :::
Let $\star \notin \nats$ and define $A = \nats \cup \{\star\}$. Now define $\varphi : A \rightarrow A$ by $$\varphi(a) = \left\{ \begin{array}{ll} \zero & \mathrm{if}\ a = \star \\ \next(a) & \mathrm{if}\ a \in \nats. \end{array}\right.$$ Thinking of $\langle A, \star, \varphi \rangle$ as an iterative set, we let $$\mathsf{unnext} = \natrec_{\star,\varphi}$$ be the unique iterative homomorphism $\nats \rightarrow \nats \cup \{\star\}$.
::::::::::::::::::

True to its name, $\mathsf{unnext}$ can remove one layer of $\next$ from an element of $\nats$.

::: theorem :::
We have the following.

1. $\mathsf{unnext}(\zero) = \ast$.
2. $\mathsf{unnext}(\next(n)) = n$ for all $n \in \nats$.
3. $\mathsf{unnext}$ is bijective, and $\mathsf{unnext}^{-1}$ is an iterative homomorphism.

::: proof :::
To see (1), note that
$$\begin{eqnarray*}
\mathsf{unnext}(\zero)
 & = & \natrec_{\star,\varphi}(\zero) \\
 & = & \star
\end{eqnarray*}$$
as claimed.

To show (2), we proceed by induction on $n \in \nats$. Since induction is still new in our toolbox, we'll be a little more explicit than we might otherwise. Define $B \subseteq \nats$ by $$B = \{ n \in \nats \mid \mathsf{unnext}(\next(n)) = n \};$$ we want to show that $B = \nats$.

For the base case, suppose $n = \zero$. Then we have
$$\begin{eqnarray*}
\mathsf{unnext}(\next(\zero))
 & = & \natrec_{\star,\varphi}(\next(\zero)) \\
 & = & \varphi(\natrec_{\star,\varphi}(\zero)) \\
 & = & \varphi(\star) \\
 & = & \zero
\end{eqnarray*}$$
as needed. For the inductive step, suppose we have $n \in \nats$ such that $n \in B$; that is, $$\mathsf{unnext}(\next(n)) = n.$$ Now
$$\begin{eqnarray*}
\mathsf{unnext}(\next(\next(n)))
 & = & \natrec_{\star,\varphi}(\next(\next(n))) \\
 & = & \varphi(\natrec_{\star,\varphi}(\next(n))) \\
 & = & \varphi(\mathsf{unnext}(\next(n))) \\
 & = & \varphi(n) \\
 & = & \next(n).
\end{eqnarray*}$$
By induction, we have $\nats \subseteq B$, and thus $\mathsf{unnext}(\next(n)) = n$ for all $n \in \nats$.

Finally we show (3). To this end, define $\Theta : \nats \cup \{\star\} \rightarrow \nats$ by $$\Theta(a) = \left\{ \begin{array}{ll} \zero & \mathrm{if}\ a = \star \\ \next(a) & \mathrm{if}\ a \in \nats. \end{array} \right.$$ We need to show that $\Theta$ is an inductive homomorphism and that $\Theta$ is a two-sided inverse of $\mathsf{unnext}$. First we show $\Theta$ is a homomorphism. To this end, first note that
$\Theta(\star) = \zero$ by definition. Now let $a \in \nats \cup \{\star\}$; we have two possibilities. Let $\varphi$ be the inductive function on $\nats \cup \{\star\}$. If If $a = \star$, we have
$$\begin{eqnarray*}
\Theta(\varphi(a))
 & = & \Theta(\varphi(\star)) \\
 & = & \Theta(\zero) \\
 & = & \next(\zero) \\
 & = & \next(\Theta(\star)).
\end{eqnarray*}$$
If instead $a \in \nats$, we have
$$\begin{eqnarray*}
\Theta(\varphi(a))
 & = & \Theta(\next(a)) \\
 & = & \next(\next(a)) \\
 & = & \next(\Theta(a)).
\end{eqnarray*}$$
So $\Theta$ is an inductive set homomorphism. To see that $\mathsf{unnext}$ is bijective, e show that $\Theta$ is a two sided inverse. First we claim that $(\Theta \circ \mathsf{unnext})(n) = n$ for all $n \in \nats$ by induction. For the base case $n = \zero$, we have
$$\begin{eqnarray*}
(\Theta \circ \mathsf{unnext})(n)
 & = & \Theta(\mathsf{unnext}(n)) \\
 & = & \Theta(\mathsf{unnext}(\zero)) \\
 & = & \Theta(\star) \\
 & = & \zero \\
 & = & n.
\end{eqnarray*}$$
For the inductive step, suppose we have $(\Theta \circ \mathsf{unnext})(n) = n$ for some $n \in \nats$. Now
$$\begin{eqnarray*}
(\Theta \circ \mathsf{unnext})(\next(n))
 & = & \Theta(\mathsf{unnext}(\next(n))) \\
 & = & \Theta(n) \\
 & = & \next(n).
\end{eqnarray*}$$
By induction we have $\Theta \circ \mathsf{unnext} = \mathsf{id}_{\nats}$. (We didn't actually use the induction hypothesis here. This is ok, because we can't yet do case analysis on $\nats$.) Next we need to show that $\mathsf{unnext} \circ \Theta = \mathsf{id}_{\nats \cup \{\star\}}$. To this end, let $a \in \nats \cup \{\star\}$. If $a = \star$, we have
$$\begin{eqnarray*}
(\mathsf{unnext} \circ \Theta)(a)
 & = & \mathsf{unnext}(\Theta(a)) \\
 & = & \mathsf{unnext}(\Theta(\star)) \\
 & = & \mathsf{unnext}(\mathsf{\zero}) \\
 & = & \star \\
 & = & a.
\end{eqnarray*}$$
Now suppose $a \in \nats$; we have
$$\begin{eqnarray*}
(\mathsf{unnext} \circ \Theta)(a)
 & = & \mathsf{unnext}(\Theta(a)) \\
 & = & \mathsf{unnext}(\next(a)) \\
 & = & a.
\end{eqnarray*}$$
as needed. So $\mathsf{unnext}$ is invertible with $\mathsf{unnext}^{-1} = \Theta$.
:::::::::::::
:::::::::::::::

We'll define a version of $\mathsf{unnext}$ with signature $\nats \rightarrow \nats$, which is a little more convenient.

::: theorem :::
[@thm-next-injective]()
Define $\psi : \nats \cup \{\star\} \rightarrow \nats$ by $$\psi(a) = \left\{ \begin{array}{ll} \zero & \mathrm{if}\ a = \star \\ a & \mathrm{if}\ a \in \nats, \end{array} \right.$$ and define $\mathsf{prev} : \nats \rightarrow \nats$ by $$\mathsf{prev} = \psi \circ \mathsf{unnext}.$$ Then we have the following:

1. $\mathsf{prev}(\zero) = \zero$.
2. $\mathsf{prev} \circ \next = \nats$.
3. $\next$ is injective.

::: proof :::
To see (1), note that
$$\begin{eqnarray*}
\mathsf{prev}(\zero)
 & = & (\psi \circ \mathsf{unnext})(\zero) \\
 & = & \psi(\mathsf{unnext}(\zero)) \\
 & = & \psi(\ast) \\
 & = & \zero
\end{eqnarray*}$$
as claimed. To see (2), note that if $n \in \nats$ we have
$$\begin{eqnarray*}
(\mathsf{prev} \circ \next)(n)
 & = & \mathsf{prev}(\next(n)) \\
 & = & (\psi \circ \mathsf{unnext})(\next(n)) \\
 & = & \psi(\mathsf{unnext}(\next(n))) \\
 & = & \psi(n) \\
 & = & n \\
 & = & \mathsf{id}_\nats;
\end{eqnarray*}$$
since $n$ was arbitrary, $\mathsf{prev} \circ \next = \mathsf{id}$ as claimed. Now (3) [follows](@thm-injective-cancel) because $\mathsf{prev}$ is a left inverse of $\next$.
:::::::::::::
:::::::::::::::

We're now prepared to finish off the Peano axioms for $\nats$.

::: theorem :::
We have the following.

1. If $n \in \nats$, then either $n = \zero$ or $n = \next(m)$ for some $m \in \nats$.
2. There does not exist $n \in \nats$ such that $\next(n) = \zero$.

::: proof :::
To see (1), let $n \in \nats$. Now consider $u = \mathsf{unnext}(n) \in \nats \cup \{\star\}$; either $u = \star$ or $u \in \nats$. Note first that $\mathsf{unnext}^{-1}(u) = n$. If $u = \star$, then $$n = \mathsf{unnext}^{-1}(u) = \zero.$$ If $u \in \nats$, then $$n = \mathsf{unnext}^{-1}(u) = \next(u).$$

To see (2), suppose we have $\zero = \next(n)$. But now
$$\begin{eqnarray*}
\star
 & = & \mathsf{unnext}(\zero) \\
 & = & \mathsf{unnext}(\next(n)) \\
 & = & n \\
 & \in & \nats,
\end{eqnarray*}$$
But this is a contradiction.
:::::::::::::
:::::::::::::::
