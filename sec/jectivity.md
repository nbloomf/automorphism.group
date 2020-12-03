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
[@thm-comp-surjective]()
Let $f : A \rightarrow B$ and $g : B \rightarrow C$ be functions. If $f$ and $g$ are surjective, then $g \circ f$ is surjective.

::: proof :::
Let $c \in C$. Since $g$ is surjective, there is a $b \in B$ such that $g(b) = c$. Similarly, since $f$ is surjective, there is an $a \in A$ with $f(a) = b$. Now $$(g \circ f)(a) = g(f(a)) = g(b) = c.$$ Since $c$ was arbitrary in $C$, $g \circ f$ is surjective as claimed.
:::::::::::::
:::::::::::::::

We have two alternative characterizations of surjectivity which are sometimes useful.

::: theorem :::
Let $f : A \rightarrow B$ be a function. Then the following are equivalent:

1. $f$ is surjective.
2. For all sets $C$ and functions $h$ and $k$ with signature $B \rightarrow C$, if $h \circ f = k \circ f$, then $h = k$.

::: proof :::
First we show (1) implies (2). To this end, suppose $f : A \rightarrow B$ is surjective, and that we have functions $h$ and $k$ with signature $B \rightarrow C$ such that $h \circ f = k \circ f$. Now let $b \in B$. Since $f$ is surjective, we have $b = f(a)$ for some $a \in A$. Now

$$\begin{eqnarray*}
h(b)
 & = & h(f(a)) \\
 & = & (h \circ f)(a) \\
 & = & (k \circ f)(a) \\
 & = & k(f(a)) \\
 & = & k(b).
\end{eqnarray*}$$

Since $b$ was arbitrary in $B$, we have $h = k$ as needed.

Next we show (2) implies (1). To this end, suppose that for all sets $C$ and all functions $h$ and $k$ with signature $B \rightarrow C$, if $h \circ f = k \circ f$ then $h = k$. We now choose a specific $C$; let $C = \{ \circ, \star \}$. We define a subset $h \subseteq B \times C$ as follows.

$$\begin{eqnarray*}
h & = & \{ (b,\circ) \in B \times C \mid b = f(a)\ \mathrm{for\ some}\ a \in A \} \\
  &   & \cup \{ (b,\star) \in B \times C \mid b \neq f(a)\ \mathrm{for\ all}\ a \in A \}.
\end{eqnarray*}$$

We claim that $h$ is a function. To see this, we need to establish it is both total and well-defined.

- To see that $h$ is total, let $b \in B$. Now either $b = f(a)$ for some $a \in A$, or we have $b \neq f(a)$ for all $a \in A$. In the first case we have $(b,\circ) \in h$, and in the second we have $(b,\star) \in h$. In either case, $(b,c) \in h$ for some $c \in C$. Since $b$ was arbitrary, $h$ is total.
- To see that $h$ is well-defined, suppose we have $b \in B$ and $c_1, c_2 \in C$ such that $(b,c_1) \in h$ and $(b,c_2) \in h$. We have two possibilities for $b$; either $b = f(a)$ for some $a \in A$ or $b \neq f(a)$ for all $a \in A$. In the first case, by definition we have $c_1 = \circ = c_2$, and in the second case, we have $c_1 = \star = c_2$. In either case we have $c_1 = c_2$, and so $h$ is well-defined.

Now note that for all $a \in A$, we have

$$\begin{eqnarray*}
(h \circ f)(a)
 & = & h(f(a)) \\
 & = & \circ \\
 & = & \mathsf{const}_{\circ}(f(a)) \\
 & = & (\mathsf{const}_{\circ} \circ f)(a).
\end{eqnarray*}$$

Since $a$ was arbitrary, we have $h \circ f = \mathsf{const}_{\circ} \circ f$. By our hypothesis (2), then, we have $h = \mathsf{const}_{\circ}$. In particular, if $b \in B$, we have $h(b) = \circ$ and so (by the definition of $h$) $b = f(a)$ for some $a \in A$. Since $b$ was arbitrary, $f$ is surjective.
:::::::::::::
:::::::::::::::

In other words, surjective functions are precisely those which can be "cancelled" from the right.



Injectivity
-----------

Where surjectivity was dual to totality, well-definedness also has a dual, called _injectivity_. These are functions which send distinct inputs to distinct outputs.

::: definition :::
[@def-injective]()
Let $f : A \rightarrow B$ be a function. We say $f$ is _injective_ if whenever $a_1, a_2 \in A$ such that $f(a_1) = f(a_2)$, we have $a_1 = a_2.$
::::::::::::::::::

This property is sometimes called _one-to-one_, but again I'll prefer injective. (Even _two-to-two_ would be better than one-to-one, since that more accurately reflects what it means.) Showing that a function is injective usually involves setting up an equality $f(x) = f(y)$ for arbitrary $x$ and $y$ and showing that $x = y.$

::: theorem :::
[@thm-id-injective]()
The identity function $\mathsf{id}_A$ is injective.

::: proof :::
Let $a_1, a_2 \in A$ with $\mathsf{id}_A(a_1) = \mathsf{id}_A(a_2).$ Using the definition of $\mathsf{id}_A$, we have $$a_1 = \mathsf{id}_A(a_1) = \mathsf{id}_A(a_2) = a_2.$$ Since $a_1$ and $a_2$ were arbitrary, $\mathsf{id}_A$ is injective as claimed.
:::::::::::::
:::::::::::::::

The composite of injective functions is again injective.

::: theorem :::
[@thm-comp-injective]()
Let $f : A \rightarrow B$ and $g : B \rightarrow C$ be functions. If $f$ and $g$ are injective, then $g \circ f$ is also injective.

::: proof :::
Let $a_1, a_2 \in A$ such that $(g \circ f)(a_1) = (g \circ f)(a_2).$ Now $$g(f(a_1)) = (g \circ f)(a_1) = (g \circ f)(a_2) = g(f(a_2)).$$ Since $g$ is injective, we have $f(a_1) = f(a_2)$, and because $f$ is injective, we have $a_1 = a_2.$ Since $a_1$ and $a_2$ were arbitrary in $A$, $g \circ f$ is injective as claimed.
:::::::::::::
:::::::::::::::

Like surjectivity, we have an alternative characterization of injectivity. This one is a little richer, though; in addition to being "cancellable", injective functions are "left undoable".

::: theorem :::
[@thm-injective-cancel]()
Let $f : A \rightarrow B$ be a function with $A$ not empty. Then the following are equivalent.

1. $f$ is injective.
2. There is a function $g : B \rightarrow A$ such that $g \circ f = \mathsf{id}_A.$
3. If $h$ and $k$ are functions with signature $C \rightarrow A$ such that $f \circ h = f \circ k$, then $h = k.$

::: proof :::
Note the condition that $A$ is not empty. We haven't been very concerned about what happens if the domain or codomain of a function is empty because it hasn't mattered; however it does matter here, at least for the proof we're going to write.

First we show that (1) implies (2). To this end, note that since $A$ is not empty, it contains at least one element; say $z \in A$. We now define a subset $g \subseteq B \times A$ as follows.

$$\begin{eqnarray*}
g & = & \{ (b,a) \in B \times A \mid f(a) = b \} \\
  &   & \cup \{ (b,z) \in B \times A \mid b \neq f(a)\ \mathrm{for\ all}\ a \in A \}.
\end{eqnarray*}$$

We claim that $g$ is a function. To see this, we need to show that $g$ is both total and well-defined.

- To see that $g$ is total, let $b \in B$. There are two possibilities for $b$; either $b = f(a)$ for some $a \in A$, or $b \neq f(a)$ for all $a \in A$. If $b = f(a)$, we have $$(b,a) \in \{ (b,a) \mid b = f(a) \} \subseteq g$$ as needed. If instead we have $b \neq f(a)$ for all $a \in A$, we have $$(b,z) \in \{ (b,z) \mid b \neq f(a)\ \mathrm{for\ all}\ a \in A \} \subseteq g.$$ In either case, we have $(b,a) \in g$ for some $a \in A$. Since $b$ was arbitrary, $g$ is total.
- Next we show that $g$ is well-defined. To that end, suppose we have $b \in B$ and $a_1, a_2 \in A$ such that $(b,a_1) \in g$ and $(b,a_2) \in g$. We again have two possibilities for $b$. First suppose $b = f(a)$ for some $a \in A$. Then we necessarily have $$(b,a_1) \in \{ (b,a) \mid b = f(a) \},$$ so that $b = f(a_1)$. Similarly, $b = f(a_2)$, and so $f(a_1) = f(a_2)$. Since $f$ is injective, we have $a_1 = a_2$. Now suppose that $b \neq f(a)$ for all $a \in A$. This time we have $(b,a_1) \in \{ (b,z) \mid b \neq f(a)\ \mathrm{for\ all}\ a \in A \}$ so that $a_1 = z$. Similarly, $a_2 = z$, and we have $a_1 = a_2$. In either case, we have $a_1 = a_2$, and so $g$ is well-defined.

Since $g$ is total and well-defined, it is a function. Next we need to show that $g \circ f = \mathsf{id}_A$. To this end, let $a \in A$. then $$(g \circ f)(a) = g(f(a)) = a = \mathsf{id}_A(a),$$ since by definition $(f(a),a) \in g$. Since $a$ was arbitrary, we have $g \circ f = \mathsf{id}_A$ as claimed.

Next, we show (2) implies (3). To this end, suppose $g$ exists with $g \circ f = \mathsf{id}_A$, and suppose further we have functions $h$ and $k$ with $f \circ h = f \circ k$. Now

$$\begin{eqnarray*}
h
 & = & \mathsf{id}_A \circ h \\
 & = & (g \circ f) \circ h \\
 & = & g \circ (f \circ h) \\
 & = & g \circ (f \circ k) \\
 & = & (g \circ f) \circ k \\
 & = & \mathsf{id}_A \circ k \\
 & = & k
\end{eqnarray*}$$

as needed.

Finally, we show that (3) implies (1). We need to show that $f$ is injective. To this end, let $a_1, a_2 \in A$ and suppose $f(a_1) = f(a_2)$. Let $C = \{\star\}$, and define $h = \mathsf{const}_{a_1}$ and $h = \mathsf{const}_{a_2}$ as functions with signature $C \rightarrow A$. Now let $c \in C$, and note that

$$\begin{eqnarray*}
(f \circ h)(c)
 & = & f(h(c)) \\
 & = & f(\mathsf{const}_{a_1}(c)) \\
 & = & f(a_1) \\
 & = & f(a_2) \\
 & = & f(\mathsf{const}_{a_2}(c)) \\
 & = & f(k(c)) \\
 & = & (f \circ k)(c).
\end{eqnarray*}$$

Since $c$ was arbitrary, we have $f \circ h = f \circ k$, and thus $h = k$. But now note that

$$\begin{eqnarray*}
a_1
 & = & \mathsf{const}_{a_1}(\star) \\
 & = & h(\star) \\
 & = & k(\star) \\
 & = & \mathsf{const}_{a_2}(\star) \\
 & = & a_2.
\end{eqnarray*}$$

Since $a_1$ and $a_2$ were arbitrary in $A$, $f$ is injective as claimed.
:::::::::::::
:::::::::::::::

This characterization of injective functions is very similar to the analogous result for surjective functions, except that surjectivity did not have an analogue of statement (2). There is a reason for this; it turns out the existence of a right inverse implies surjectivity, but the converse statement is equivalent to the axiom of choice. My personal preference is to avoid using AC because it is nonconstructive. We can get pretty far without it, and what we gain is the ability to turn proofs into algorithms, which is a pretty big win. We could argue that there's no _harm_ in assuming AC, since we can simply try to find proofs that don't use it, and it does make lots of things much simpler. This is certainly true. However, the equivalence of "surjective implies right invertible" and AC demonstrates that it can easily creep in when we're not looking. So we'll just do without for as long as possible.



Bijectivity
-----------

Functions which are both injective and surjective end up being especially important, so we give them a name.

::: definition :::
A function $f$ is called _bijective_ if it is both injective and surjective.
::::::::::::::::::

Bijective functions basically come in two flavors:

- those with signature $A \rightarrow B$ with $B \neq A$. We can think of these as _renamings_.
- those with signature $A \rightarrow A$. These are called _permutations_, and will get more attention later.

In any case, what makes bijective functions really interesting is that each one has a corresponding "undo" function, as characterized in the following result.

::: theorem :::
Let $f : A \rightarrow B$ be a function. If $f$ is bijective, then there is a unique function $g : B \rightarrow A$ such that $g \circ f = \mathsf{id}_A$ and $f \circ g = \mathsf{id}_B$. We denote this function $f^{-1}$, pronounced $f$-_inverse_.

::: proof :::
Thinking of functions as sets, define a _set_ $$g = \{ (f(a), a) \mid a \in A \}.$$ We need to show four things:

1. $g$ is a function (which is not at all obvious from the definition);
2. $g \circ f = \mathsf{id}_A$ and $f \circ g = \mathsf{id}_B$; and
3. $g$ is unique among the objects having properties (1) and (2).

First we show (1): that $g \subseteq B \times A$ is a function. Recall that this has two sub-parts: showing that $g$ is both total and well-defined.

- To see that $g$ is total, first let $b \in B$. Since $f$ is surjective, there exists $a \in A$ such that $b = f(a)$. By definition, then, we have $$(b,a) = (f(a),a) \in g.$$ Since $b$ is arbitrary, $g$ is total.
- To see that $g$ is well-defined, suppose we have $b \in B$ and $a_1, a_2 \in A$ such that $(b,a_1) \in g$ and $(b, a_2) \in g$. By definition, we then have $f(a_1) = b = f(a_2)$. Since $f$ is injective, we then have $a_1 = a_2$. Since $b$, $a_1$, and $a_2$ were arbitrary, $g$ is well-defined.

So $g$ is total and well-defined, and thus a function with signature $B \rightarrow A$. In particular, it now makes sense to use $g(\star)$ notation, and we have $g(f(a)) = a$.

Next we show (2). Let $a \in A$; note that $$(g \circ f)(a) = g(f(a)) = a = \mathsf{id}_A(a).$$ Since $a$ is arbitrary, we have $g \circ f = \mathsf{id}_A$. Now let $b \in B$; since $f$ is surjective, we have $b = f(a)$ for some $a$. Now note that $$(f \circ g)(b) = f(g(b)) = f(g(f(a))) = f(a) = b.$$ Since $b$ was arbitrary we have $f \circ g = \mathsf{id}_B$ as claimed.

Finally we show (3), that $g$ is unique among functions $B \rightarrow A$ that compose with $f$ as in (2). To this end, let $h : B \rightarrow A$ be a function such that $h \circ f = \mathsf{id}_A$ and $f \circ h = \mathsf{id}_B$. We want to show that $h = g$, and to do so we'll show each is a subset of the other.

First suppose $(b,a) \in h$. Now $$b = \mathsf{id}_B(b) = (f \circ h)(b) = f(h(b)) = f(a),$$ so we have $(b,a) = (f(a),a) \in g$ by definition, and thus $h \subseteq g$. Next let $(f(a),a) \in g$. Of course $h(f(a)) = (h \circ f)(a) = \mathsf{id}_A(a) = a$ so that $(f(a),a) \in h$ and $g \subseteq h$. Thus $h = g$ as claimed.
:::::::::::::
:::::::::::::::

This theorem is interesting because it defines $f^{-1}$ using a _uniqueness property_. We don't just show that $f^{-1}$ exists or that it satisfies some property; we show that it is _unique_ with that property. This gives a handy strategy for showing that a given function $g$ is equal to $f^{-1}$; just show that $g$ satisfies the _properties_ of the inverse. This is a subtle but very powerful point.

To see the uniqueness strategy in action, we can try it out on a few concrete examples. First, the inverse of a bijective function is again bijective.

::: theorem :::
Let $f : A \rightarrow B$ be a bijective function. Then $f^{-1}$ is also bijective, and moreover $(f^{-1})^{-1} = f$.

::: proof :::
First we show that $f^{-1}$ is bijective -- that is, both injective and surjective. To see that $f^{-1}$ is injective, suppose we have $b_1, b_2 \in B$ such that $f^{-1}(b_1) = f^{-1}(b_2)$. Then we also have

$$\begin{eqnarray*}
b_1
 & = & \mathsf{id}_B(b_1) \\
 & = & (f \circ f^{-1})(b_1) \\
 & = & f(f^{-1}(b_1)) \\
 & = & f(f^{-1}(b_2)) \\
 & = & (f \circ f^{-1})(b_2) \\
 & = & \mathsf{id}_B(b_2) \\
 & = & b_2.
\end{eqnarray*}$$

Since $b_1$ and $b_2$ were arbitrary, $f^{-1}$ is injective. To see that $f^{-1}$ is surjective, let $a \in A$, thinking of $A$ as the codomain of $g$. Since $f$ is a function of course $f(a)$ exists in $B$ and $f^{-1}(f(a)) = a$; since $a$ was arbitrary, $f^{-1}$ is surjective, and thus bijective as claimed.

Now the previous theorem applies. Note that $f : A \rightarrow B$ is a function, and that $f \circ f^{-1} = \mathsf{id}_B$ and $f^{-1} \circ f = \mathsf{id}_A$. By the uniqueness property of inverse functions, then, we have $(f^{-1})^{-1} = f$ as claimed.
:::::::::::::
:::::::::::::::

The identity function is bijective.

::: theorem :::
[@thm-id-bijective]()
Let $A$ be a set. Then $\mathsf{id}_A^{-1} = \mathsf{id}_A$.

::: proof :::
We've already shown that $\mathsf{id}_A$ is [surjective](@thm-id-surjective) as well as [injective](@thm-id-injective), so it is bijective.

Now note that $\mathsf{id}_A : A \rightarrow A$ and that $\mathsf{id}_A \circ \mathsf{id}_A = \mathsf{id}_A$. By the uniqueness property of function inverses, we have $\mathsf{id}_A^{-1} = \mathsf{id}_A$, as claimed.
:::::::::::::
:::::::::::::::

And the composite of bijective functions is bijective.

::: theorem :::
Let $f : A \rightarrow B$ and $g : B \rightarrow C$ be bijective functions. Then $g \circ f$ is also bijective, and moreover $(g \circ f)^{-1} = f^{-1} \circ g^{-1}$.

::: proof :::
First we show that $g \circ f$ is bijective. Since $f$ and $g$ are both bijective, they are also surjective; we've [already shown](@thm-comp-surjective) that $g \circ f$ is then also surjective. Likewise $f$ and $g$ are injective, and [so](@thm-comp-injective) $g \circ f$ is injective. Thus $g \circ f$ is bijective as claimed.

Now note that $f^{-1} \circ g^{-1} : C \rightarrow A$. Next, we have

$$\begin{eqnarray*}
(g \circ f) \circ (f^{-1} \circ g^{-1})
 & = & g \circ (f \circ (f^{-1} \circ g^{-1})) \\
 & = & g \circ ((f \circ f^{-1}) \circ g^{-1}) \\
 & = & g \circ (\mathsf{id}_B \circ g^{-1}) \\
 & = & g \circ g^{-1} \\
 & = & \mathsf{id}_C
\end{eqnarray*}$$

and similarly

$$\begin{eqnarray*}
(f^{-1} \circ g^{-1}) \circ (g \circ f)
 & = & f^{-1} \circ (g^{-1} \circ (g \circ f)) \\
 & = & f^{-1} \circ ((g^{-1} \circ g) \circ f) \\
 & = & f^{-1} \circ (\mathsf{id}_B \circ f) \\
 & = & f^{-1} \circ f \\
 & = & \mathsf{id}_A.
\end{eqnarray*}$$

By the uniqueness property of function inverses, we have $(g \circ f)^{-1} = f^{-1} \circ g^{-1}$ as claimed.
:::::::::::::
:::::::::::::::

In some sense, bijective functions are not very interesting as functions; they "only" tell us that two sets are the same "up to a renaming". That may or may not be useful in a given context.

However, bijective functions turn out to be extremely interesting as computational objects, particularly when the domain and codomain are the same.

We wrap up this section with yet another way to characterize bijective functions using the existince of left and right undoers.

::: theorem :::
Let $f : A \rightarrow B$ be a function. Suppose we have functions $g$ and $h$ with signature $B \rightarrow A$ such that $g \circ f = \mathsf{id}_A$ and $f \circ h = \mathsf{id}_B$. Then we have the following.

1. $g = h$.
2. $f$ is bijective and $f^{-1} = g = h$.

::: proof :::
To see (1), let $b \in B$. Now

$$\begin{eqnarray*}
g(b)
 & = & g(\mathsf{id}_B(b)) \\
 & = & g((f \circ h)(b)) \\
 & = & (g \circ (f \circ h))(b) \\
 & = & ((g \circ f) \circ h)(b) \\
 & = & (\mathsf{id}_A \circ h)(b) \\
 & = & h(b).
\end{eqnarray*}$$

Since $b$ was arbitrary, we have $g = h$.

Next we show (2). Since $g \circ f = \mathsf{id}_A$, we've [already shown](@thm-injective-cancel) that $f$ is injective. To see that $f$ is surjective, let $b \in B$ and let $a = h(b)$. Now we have $$f(a) = f(h(b)) = (f \circ h)(b) = \mathsf{id}_B(b) = b;$$ since $b$ was arbitrary, $f$ is surjective. That $f^{-1} = g$ (and so also $f^{-1} = h$) follows from the uniqueness property of inverses.
:::::::::::::
:::::::::::::::

This theorem can be used to show that a given function is bijective when its inverse has two different "presentations" that are easier to work with depending on the direction they are composed.
