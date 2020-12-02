---
title: Functions
---

Functions
---------

This is one of the most fundamental definitions in algebra. Intutitively, a function is a thing that "transforms" objects of one type into objects of another type.

::: definition :::
[@def-total]()[@def-well-defined]()[@def-function]()
Let $A$ and $B$ be sets, with a subset $f \subseteq A \times B$.

1. We say that $f$ is _total_ when for every $a \in A$, there exists a $b \in B$ such that $(a,b) \in f$.
2. We say that $f$ is _well-defined_ when for all $a \in A$ and $b_1, b_2 \in B$, if $(a,b_1) \in f$ and $(a,b_2) \in f$, then $b_1 = b_2$. 
3. We say $f$ is a _function_ if it is both total and well-defined.
::::::::::::::::::

We have some special notation for working with functions. Although a function is literally a set, we will usually express the statement "$f \subseteq A \times B$ is a function" using the notation $f : A \rightarrow B$, pronounced "$f$ maps $A$ to $B$". In this notation, $A \rightarrow B$ is called the _signature_ of $f$.

The total and well-definedness conditions together imply that for every $a \in A$, there is a _unique_ $b \in B$ with $(a,b) \in f$. Whenever this kind of thing happens -- an object with some property exists and is unique -- it is often useful to give it a name. We refer to this unique $b$ as $f(a)$, called the _image_ of $f$ _at_ $a$.

Now we'll establish some concrete examples of functions.

::: example :::
[@def-identity-function]()
Let $A$ be a set. The diagonal subset $\Delta \subseteq A \times A$ given by $$\Delta = \{(a,a) \mid a \in A\}$$ is a function. We call this the _identity function_ on $A$, and denote it $\mathsf{id}_A$. By definition, $\mathsf{id}_A(a) = a$ for all $a \in A$.

::: proof :::
We need to show that $\Delta$ is total and well-defined.

1. First we show that $\Delta$ is total. Let $a \in A$; then we have $(a,a) \in \Delta$, and in particular $a$ itself witnesses the totality of $\Delta$ at $a$. Since $a$ was arbitrary, $\Delta$ is total.
2. Next we show that $\Delta$ is well-defined. To this end, suppose we have $a \in A$ and $b_1, b_2 \in A$ such that $(a,b_1) \in \Delta$ and $(a,b_2) \in \Delta$. then we have $b_1 = a = b_2$ as required. So $\Delta$ is well-defined.

Since $\Delta$ is both total and well-defined, it is a function.
:::::::::::::
:::::::::::::::

The identity function is an atypical example of a function in one respect -- the "input" set and the "output" set are the same. (This is not usually the case.) This is a good time to define "input" set and "output" sets more precisely.

::: definition :::
[@def-domain]()[@def-codomain]()
Let $f : A \rightarrow B$ be a function. We say that $A$ is the _domain_ of $f$, denoted $\mathsf{dom}(f)$, and that $B$ is the _codomain_ of $f$, denoted $\mathsf{cod}(f)$.
::::::::::::::::::

Another boring but useful class of functions are those which always output the same thing. Such functions are called _constant_.

::: example :::
Let $A$ and $B$ be sets, and fix $b \in B$. Then the subset $$K \subseteq A \times B = \{ (a,b) \mid a \in A \}$$ is a function. We call this the _constant_ function on $A$ with image $b$, and denote it $\mathsf{const}_b$. By definition, $\mathsf{const}_b(a) = b$ for all $a \in A$.

::: proof :::
We need to show that $K$ is total and well-defined.

1. First we show that $K$ is total. Let $a \in A$; by definition, we have $(a,b) \in K$. Since $a$ was arbitrary, $K$ is total.
2. Next we show that $K$ is well-defined. To this end, suppose we have $a \in A$ and $b_1, b_2 \in B$ such that $(a,b_1) \in K$ and $(a,b_2) \in K$. Again by definition, we have $b_1 = b = b_2$.

Since $K$ is both total and well-defined, it is a function.
:::::::::::::
:::::::::::::::

In the long run we won't often be working with functions as sets; in some sense the set-based machinery behind functions is an implementation detail. However it does pop up from time to time. So for the sake of the exercise, and to get a taste of pain, we'll characterize all of the subsets of a particular $A \times B$ by their totality or well-definedness.

::: example :::
Let $B = \{ \circ, \star \}$. Determine which subsets of $B \times B$ are total and which are well-defined.

::: proof :::
Note that $B \times B$ contains four elements: $$B \times B = \{ (\circ,\circ), (\circ,\star), (\star,\circ), (\star,\star) \}.$$ Given an arbitrary subset of $B \times B$, every element is either in or out, so there are $2^4 = 16$ different subsets.

- $\{\}$: **Not total** because there is no $b \in B$ with $(\star, b) \in f$. Vacuously **well defined**, since the antecedent in the definition of well defined, that is, "$(a,b_1) \in f$ and $(a,b_2) \in f$", is false.
- $\{(\circ,\circ)\}$: **Not total** because there is no $b \in B$ with $(\star, b) \in f$. **Well-defined**.
- $\{(\circ,\star)\}$: **Not total** because there is no $b \in B$ with $(\star, b) \in f$. **Well-defined**.
- $\{(\circ,\circ), (\circ,\star)\}$: **Not total** because there is no $b \in B$ with $(\star, b) \in f$. **Not well-defined** since there exist $b_1,b_2 \in B$ with $(\circ,b_1) \in f$ and $(\circ,b_2) \in f$ but $b_1 \neq b_2$.
- $\{(\star,\circ)\}$: **Not total** because there is no $b \in B$ with $(\circ, b) \in f$. **Well-defined**.
- $\{(\circ,\circ), (\star,\circ)\}$: **Total** and **well-defined**.
- $\{(\circ,\star), (\star,\circ)\}$: **Total** and **well-defined**.
- $\{(\circ,\circ), (\circ,\star), (\star,\circ)\}$: **Total**. **Not well-defined** since there exist $b_1,b_2 \in B$ with $(\circ,b_1) \in f$ and $(\circ,b_2) \in f$ but $b_1 \neq b_2$.
- $\{(\star,\star)\}$: **Not total** because there is no $b \in B$ with $(\circ, b) \in f$. **Well-defined**.
- $\{(\circ,\circ), (\star,\star)\}$: **Total** and **well-defined**.
- $\{(\circ,\star), (\star,\star)\}$: **Total** and **well-defined**.
- $\{(\circ,\circ), (\circ,\star), (\star,\star)\}$: **Total**. **Not well-defined** since there exist $b_1,b_2 \in B$ with $(\circ,b_1) \in f$ and $(\circ,b_2) \in f$ but $b_1 \neq b_2$.
- $\{(\star,\circ), (\star,\star)\}$: **Not total** because there is no $b \in B$ with $(\circ, b) \in f$. **Not well-defined** since there exist $b_1,b_2 \in B$ with $(\star,b_1) \in f$ and $(\star,b_2) \in f$ but $b_1 \neq b_2$.
- $\{(\circ,\circ), (\star,\circ), (\star,\star)\}$: **Total**. **Not well-defined** since there exist $b_1,b_2 \in B$ with $(\star,b_1) \in f$ and $(\star,b_2) \in f$ but $b_1 \neq b_2$.
- $\{(\circ,\star), (\star,\circ), (\star,\star)\}$: **Total**. **Not well-defined** since there exist $b_1,b_2 \in B$ with $(\star,b_1) \in f$ and $(\star,b_2) \in f$ but $b_1 \neq b_2$.
- $\{(\circ,\circ), (\circ,\star), (\star,\circ), (\star,\star)\}$: **Total**. **Not well-defined** since there exist $b_1,b_2 \in B$ with $(\circ,b_1) \in f$ and $(\circ,b_2) \in f$ but $b_1 \neq b_2$.

To summarize, among the subsets of $B \times B$,

- 2 elements are neither total nor well-defined.
- 5 elements are total but not well-defined.
- 5 elements are not total, but are well-defined.
- 4 elements are both total and well-defined (e.g., are functions).

:::::::::::::
:::::::::::::::



Composition
-----------

::: definition :::
Let $f : A \rightarrow B$ and $g : B \rightarrow C$ be functions. Note that for all $a \in A$, $f(a) \in B$, and so $g(f(a)) \in C$. Then the set $$g \circ f = \{ (a, g(f(a))) \mid a \in A \} \subseteq A \times C$$ is a function, called the _composite_ of $g$ and $f$. By definition, $(g \circ f)(a) = g(f(a))$ for all $a \in A$.

::: proof :::
We need to show that $g \circ f$ is total and well defined.

1. First we show that $g \circ f$ is total. Let $a \in A$; by definition we have $(a, g(f(a))) \in g \circ f$. Since $a$ was arbitrary, $g \circ f$ is total.
2. Next we show that $g \circ f$ is well-defined. To this end, suppose we have $a \in A$ and $c_1, c_2 \in C$ such that $(a, c_1) \in g \circ f$ and $(a, c_2) \in g \circ f$. By definition, we have $c_1 = g(f(a)) = c_2$ as required.

Since $g \circ f$ is both total and well-defined, it is a function.
:::::::::::::
::::::::::::::::::

Since functions are sets, to show that two functions are equal we can use the usual strategy of showing that each is a subset of the other. However, there is an equivalent strategy that is often simpler: show that they have the same _images_.

::: theorem :::
[@thm-function-eq]()
Let $A$ and $B$ be sets with $f : A \rightarrow B$ and $g : A \rightarrow B$. Then the following are equivalent.

1. $f = g$.
2. For all $a \in A$, $f(a) = g(a)$.

::: proof :::
First we show that (1) implies (2). Suppose $f = g$, and let $a \in A$. We have $(a, f(a)) \in f$, so that $(a, f(a)) \in g$. Recall that $g(a)$ is precisely the _unique_ $b \in B$ such that $(a,b) \in g$, so we have $g(a) = f(a)$ as needed. Since $a$ was arbitrary, (2) holds.

Next we show that (2) implies (1); to this end suppose (2) holds. We need to show that $f = g$, and to do that we'll show that an arbitrary element of $f$ is also in $g$ and vice versa. Suppose we have $(a,b) \in f$. Recall that $f(a)$ is the unique $z \in B$ such that $(a,z) \in f$; that is, $f(a) = b$. So we have $$(a,b) = (a,f(a)) = (a,g(a)) \in g,$$ and thus $f \subseteq g$. A similar argument shows that $g \subseteq f$, and so $f = g$ as needed.
:::::::::::::
:::::::::::::::

With this proof strategy for equality in hand we can now establish some useful theorems about composition. First, identity functions are "neutral" with respect to composition.

::: theorem :::
Let $f : A \rightarrow B$ be a function. Then we have the following.

1. $f \circ \mathsf{id}_A = f$
2. $\mathsf{id}_B \circ f = f$

::: proof :::
First we show (1). Let $a \in A$. Now $$(f \circ \mathsf{id}_A)(a) = f(\mathsf{id}_A(a)) = f(a).$$ Since $a$ was arbitrary, we have $f \circ \mathsf{id}_A = f$ as claimed.

To see (2), likewise let $a \in A$. Now $$(\mathsf{id}_B \circ f)(a) = \mathsf{id}_b(f(a)) = f(a),$$ so that $\mathsf{id}_B \circ f = f$ as claimed.
:::::::::::::
:::::::::::::::

Constant functions are "absorptive" on the left, and also kind of on the right.

::: theorem :::
Let $f : A \rightarrow B$ be a function, $a \in A$, and $C$ a set with $c \in C$. Then we have the following.

1. $\mathsf{const}_c \circ f = \mathsf{const}_c$.
2. $f \circ \mathsf{const}_a = \mathsf{const}_{f(a)}$.

::: proof :::
First we show (1). Note that the notation $\mathsf{const}_b$ is playing two roles in this equation; on the left it has signature $B \rightarrow C$, and on the right it has signature $A \rightarrow C$. Let $a \in A$. Then we have $(\mathsf{const}_c \circ f)(a) = \mathsf{const}_c(f(a)) = c = \mathsf{const}_c(a)$. Since $a$ was arbitrary, we have $\mathsf{const}_c \circ f = \mathsf{const}_c$ as claimed.

Next we show (2). There is a fourth set $D$ here playing the role of domain for both $\mathsf{const}_a$ and $\mathsf{const}{f(a)}$. Let $d \in D$. Now $(f \circ \mathsf{const}_a)(d) = f(\mathsf{const}_a(d)) = f(a) = \mathsf{const}_{f(a)}(d)$. Since $d$ was arbitrary, we have $f \circ \mathsf{const}_a = \mathsf{const}_{f(a)}$ as claimed. 
:::::::::::::
:::::::::::::::

This one's really important: function composition is associative.

::: theorem :::
Let $f : A \rightarrow B$, $g : B \rightarrow C$, and $h : C \rightarrow D$ be functions. Then $$h \circ (g \circ f) = (h \circ g) \circ f.$$

::: proof :::
We usually gloss over this, but it's important to convince ourselves that all the compositions here make sense -- for instance, $g \circ f$ has signature $A \rightarrow C$, so that $h \circ (g \circ f)$ exists.

Now to show the claimed equality holds, let $a \in A$. Now

$$\begin{eqnarray*}
(h \circ (g \circ f))(a)
 & = & h((g \circ f)(a)) \\
 & = & h(g(f(a))) \\
 & = & (h \circ g)(f(a)) \\
 & = & ((h \circ g) \circ f)(a).
\end{eqnarray*}$$

Since $a$ was arbitrary, we have $h \circ (g \circ f) = (h \circ g) \circ f$ as claimed.
:::::::::::::
:::::::::::::::

It's important to get really comfortable with function composition; we're going to use it a lot. :)



Roster Notation
---------------

Notation is how we turn abstract concepts into computational objects. Here we'll define a notation now for working with functions on finite sets. Let $f : A \rightarrow B$ be a function with $A$ finite; for our purposes a set is finite if its elements can be indexed by natural numbers (what are those!) as $a_1$, $a_2$, up to $a_n$ for some $n$. For each $a_i$ the corresponding image $f(a_i)$ is unique, and we can simply list the pairs vertically like so:

$$\begin{pmatrix} a_1 & a_2 & \cdots & a_n \\ f(a_1) & f(a_2) & \cdots & f(a_n) \end{pmatrix}$$

We'll call this _roster notation_. What makes this handy as notation is that composition can be carried out mechanically. For instance, here are the four functions on $\{\circ,\star\}$ we found earlier, this time in roster form.

$$\begin{pmatrix}
\circ & \star \\ \circ & \circ
\end{pmatrix}, \begin{pmatrix}
\circ & \star \\ \circ & \star
\end{pmatrix}, \begin{pmatrix}
\circ & \star \\ \star & \circ
\end{pmatrix}, \begin{pmatrix}
\circ & \star \\ \star & \star
\end{pmatrix}$$

To compute the composite of two functions, say $g \circ f$, we can write the roster of $f$ above the roster of $g$ and then chase the symbols downward. For example, if $$f = \begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} \ \mathrm{and}\ g = \begin{pmatrix} \circ & \star \\ \star & \circ \end{pmatrix},$$ we can compute the composite $g \circ f$ by drawing $f$ above $g$ and tracing the "flow" of symbols downward, matching the output of $f$ to the input of $g$.

$$g \circ f = \begin{matrix}
\begin{pmatrix}
\circ & \star \\ \circ & \circ
\end{pmatrix} \\
\begin{pmatrix}
\circ & \star \\ \star & \circ
\end{pmatrix}
\end{matrix} = \begin{pmatrix}
\circ & \star \\ \star & \star
\end{pmatrix}$$

Taking this a step further, any two functions on $\{\circ,\star\}$ can be composed with one another. We can compute these products and compile them into a table like so; note that in the product $g \circ f$, $g$ is the row label and $f$ the column label.

$$\begin{array}{c|cccc}
 &
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix} \\ \hline
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} \\
\begin{pmatrix} \circ & \star \\ \circ & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix} \\
\begin{pmatrix} \circ & \star \\ \star & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \circ \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \circ & \circ \end{pmatrix} \\
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix} &
\begin{pmatrix} \circ & \star \\ \star & \star \end{pmatrix}
\end{array}$$

Roster notation is only practical for hand calculation on functions with small domains. However it is a nice example of a notation allowing us to turn an otherwise awkward computation into a mechanical symbol-pushing exercise.
