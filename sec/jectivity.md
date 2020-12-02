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
[@thm-comp-injective]()
Let $f : A \rightarrow B$ and $g : B \rightarrow C$ be functions. If $f$ and $g$ are injective, then $g \circ f$ is also injective.

::: proof :::
Let $a_1, a_2 \in A$ such that $(g \circ f)(a_1) = (g \circ f)(a_2)$. Now $$g(f(a_1)) = (g \circ f)(a_1) = (g \circ f)(a_2) = g(f(a_2)).$$ Since $g$ is injective, we have $f(a_1) = f(a_2)$, and because $f$ is injective, we have $a_1 = a_2$. Since $a_1$ and $a_2$ were arbitrary in $A$, $g \circ f$ is injective as claimed.
:::::::::::::
:::::::::::::::



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
- To see that $g$ is well-defined, suppose we have $b \in B$ and $a_1, a_2 \in A$ such that $(b,a_1) \in g$ and $(b, a_2) \in g$. By definition, we then have $f(a_1) = b = f(a_2)$. Since $f$ is injective, we then have $a_1 = a_2$. Since $b$, $a_1$, and $a_2$ were arbitrary, $g$ is well-defined

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
