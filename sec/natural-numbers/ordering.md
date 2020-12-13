---
title: Ordering Natural Numbers
---



Less Than
---------

We're now prepared to define the usual order relations on natural numbers, starting with "less than". We might call these _additive_ order relations, since they are defined in terms of $\plus$.

::: definition :::
We define a relation $<$ on $\nats$ (pronounced _less than_) as follows. Given $a,b \in \nats$, we say $a < b$ if there exists $c \in \nats$ such that $\plus(a,\next(c)) = b$.
::::::::::::::::::

Showing that $a < b$ is straightforward enough; we just have to exhibit a specific $c$ such that $\plus(a,\next(c)) = b$. Showing that $a \not\lt b$ is different, though, because we have to show that no such $c$ exists. This will usually come down to showing that such an equation leads to something we know is absurd, like $\zero = \next(m)$.

::: example :::
For all $m \in \nats$ we have the following.

1. $\zero < \next(m)$.
2. $\next(m) \not\lt \zero$.

::: proof :::
To see (1), note that $$\plus(\zero,\next(m)) = \next(m)$$ as needed.

To see (2), suppose to the contrary we have $c \in \nats$ with $\plus(\next(m),c) = \zero$. But then
$$\begin{eqnarray*}
 &   & \next(\plus(m,c)) \\
 & = & \plus(\next(m),c) \\
 & = & \zero,
\end{eqnarray*}$$
which is absurd.
:::::::::::::
:::::::::::::::

No natural number is less than itself.

::: theorem :::
If $a \in \nats$, then $a \not\lt a$.

Relations satisfying this property are called _antireflexive_.

::: proof :::
Suppose we have $a < a$. That is, that for some $c \in \nats$ we have $\plus(a,\next(c)) = a$. Note than that
$$\begin{eqnarray*}
 &   & \plus(a,\zero) \\
 & = & a \\
 & = & \plus(a,\next(c)).
\end{eqnarray*}$$
Since $\plus$ is cancellative, we have $\zero = \next(c)$; however this is absurd. So we have $a \not\lt a$.
:::::::::::::
:::::::::::::::

Two natural numbers cannot be simultaneously less than each other.

::: theorem :::
If $a,b \in \nats$ such that $a < b$, then $b \not\lt a$.

Relations satisfying this property are called _asymmetric_.

::: proof :::
Suppose $a < b$; then we have $m \in \nats$ such that $\plus(a,\next(m)) = b$. Now suppose we also have $b < a$, with $n \in \nats$ such that $plus(b,\next(n)) = a$. Now
$$\begin{eqnarray*}
 & = & \plus(a,\plus(\next(m),\next(n))) \\
 & = & \plus((\plus(a,\next(m)),\next(n)) \\
 & = & \plus(b,\next(n)) \\
 & = & a.
\end{eqnarray*}$$
As we've [shown](@thm-plus-neutral), then $$\plus(\next(m),\next(n)) = \zero.$$ But now we have
$$\begin{eqnarray*}
 &   & \zero \\
 & = & \plus(\next(m),\next(n)) \\
 & = & \plus(\plus(m,\next(n)),\next(n)) \\
 & = & \next(\plus(\plus(m,\next(n)),n)),
\end{eqnarray*}$$
which is absurd. So $b \not\lt a$.
:::::::::::::
:::::::::::::::

We can collapse chains of less-than relationships.

::: theorem :::
Let $a,b,c \in \nats$. If $a < b$ and $b < c$, then $a < c$.

Relations satisfying this property are called _transitive_.

::: proof :::
Suppose $a < b$ and $b < c$. Then we have $m,n \in \nats$ such that $$\plus(a,\next(m)) = b$$ and $$\plus(b,\next(n)) = c.$$ Note that
$$\begin{eqnarray*}
 &   & \plus(a,\next(\plus(m,\next(n)))) \\
 & = & \plus(a,\plus(\next(m),\next(m))) \\
 & = & \plus(\plus(a,\next(m)),\next(n)) \\
 & = & \plus(b,\next(n)) \\
 & = & c,
\end{eqnarray*}$$
so that $a < c$.
:::::::::::::
:::::::::::::::

Less than is compatible with $\next$, $\plus$, and $\mult$ (almost).

::: theorem :::
[@thm-lt-equivalents]()
Let $a,b,c \in \nats$. Then the following are equivalent.

1. $a < b$
2. $\next(a) < \next(b)$.
3. $\plus(a,c) < \plus(b,c)$.
4. $\mult(a,\next(c)) < \mult(b,\next(c))$.

::: proof :::
First we show that (1) implies (2). Suppose $a < b$; then there exists $c \in \nats$ such that $\plus(a,\next(c)) = b$. But then we have
$$\begin{eqnarray*}
 &   & \plus(\next(a),\next(c)) \\
 & = & \next(\plus(a,\next(c))) \\
 & = & \next(b),
\end{eqnarray*}$$
so that $\next(a) < \next(b)$.

To see (2) implies (1), suppose we have $c$ such that $\plus(\next(a),\next(c) = \next(b)$. Then
$$\begin{eqnarray*}
 &   & \next(\plus(a,\next(c))) \\
 & = & \plus(\next(a),\next(c)) \\
 & = & \next(b);
\end{eqnarray*}$$
since $\next$ is injective, we have $\plus(a,\next(c)) = b$ and thus $a < b$ as needed.

Next we show that (1) implies (3). To that end suppose $a < b$; then there exists $m \in \nats$ such that $\plus(a,\next(m)) = b$. Now
$$\begin{eqnarray*}
 &   & \plus(\plus(a,c),\next(m)) \\
 & = & \plus(a,\plus(c,\next(m))) \\
 & = & \plus(a,\plus(\next(m),c)) \\
 & = & \plus(\plus(a,\next(m)),c) \\
 & = & \plus(b,c)
\end{eqnarray*}$$
so that $\plus(a,c) < \plus(b,c)$.

Next we show that (3) implies (1). To that end suppose $\plus(a,c) < \plus(b,c)$; then there exists $m \in \nats$ such that $$\plus(\plus(a,c),\next(m)) = \plus(b,c).$$ Now
$$\begin{eqnarray*}
 &   & \plus(\plus(a,\next(m)),c) \\
 & = & \plus(a,\plus(\next(m),c)) \\
 & = & \plus(a,\plus(c,\next(m))) \\
 & = & \plus(\plus(a,c),\next(m)) \\
 & = & \plus(b,c).
\end{eqnarray*}$$
Since $\plus$ is cancellative, we have $\plus(a,\next(m)) = b$, so that $a < b$ as needed.

Now we show that (1) implies (4). To that end, suppose $a < b$; then there exists $m \in \nats$ such that $\plus(a,\next(m)) = b$. Now
$$\begin{eqnarray*}
 &   & \mult(b,\next(c)) \\
 & = & \mult(\plus(a,\next(m)),\next(c)) \\
 & = & \plus(\mult(a,\next(c)),\mult(\next(m),\next(c))) \\
 & = & \plus(\mult(a,\next(c)), \\
 &   & \quad \plus(\mult(m,\next(c)),\next(c))) \\
 & = & \plus(\mult(a,\next(c)), \\
 &   & \quad \next(\plus(\mult(m,\next(c)),c))),
\end{eqnarray*}$$
and so $\mult(a,\next(c)) < \mult(b,\next(c))$.

Next we show that (4) implies (1), proceeding by induction on $a$. For the base case $a = \zero$, we consider two possibilities for $b$. If $b = \zero$, then we have
$$\begin{eqnarray*}
 &   & \mult(a,\next(c)) \\
 & = & \mult(\zero,\next(c)) \\
 & = & \mult(b,\next(c)),
\end{eqnarray*}$$
so that $\mult(a,\next(c)) \not\lt \mult(b,\next(c))$. Then (4) is false, so the implication (4) implies (1) holds vacuously. If $b = \next(m)$ for some $m$, then we have
$$\begin{eqnarray*}
 &   & \mult(a,\next(c)) \\
 & = & \mult(\zero,\next(c)) \\
 & = & \zero \\
 & < & \next(\plus(\mult(m,\next(c)),c)) \\
 & = & \plus(\mult(m,\next(c)),\next(c)) \\
 & = & \mult(\next(m),\next(c)) \\
 & = & \mult(b,\next(c))
\end{eqnarray*}$$
and $$a = \zero < \next(m) = b,$$ so (4) implies (1) holds.

For the inductive step, suppose we have $a \in \nats$ such that for all $b$ and $c$, if $\mult(a,\next(c)) < \mult(b,\next(c))$ then $a < b$. We wish now to show that this statement also holds for $\next(a)$. To that end we consider two possibilities for $b$.

If $b = \zero$, we have
$$\begin{eqnarray*}
 &         & \mult(\next(a),\next(c)) \\
 & =       & \plus(\mult(a,\next(c)),\next(c)) \\
 & =       & \next(\plus(\mult(a,\next(c)),c)) \\
 & \not\lt & \zero \\
 & =       & \mult(\zero,\next(c)) \\
 & =       & \mult(b,\next(c));
\end{eqnarray*}$$
So (4) does not hold for $b = \zero$, and thus (4) implies (1) holds vacuously in this case.

Suppose instead we have $b = \next(m)$ for some $m \in \nats$, and suppose further that $$\mult(\next(a),\next(c)) < \mult(b,\next(c)).$$ Now
$$\begin{eqnarray*}
 & = & \plus(\mult(a,\next(c)),\next(c)) \\
 & = & \mult(\next(a),\next(c)) \\
 & < & \mult(b,\next(c)) \\
 & = & \mult(\next(m),\next(c)) \\
 & = & \plus(\mult(m,\next(c)),\next(c)).
\end{eqnarray*}$$
We've already shown that (3) implies (1) over all natural numbers, so this implies $$\mult(a,\next(c)) < \mult(m,\next(c)).$$ By the induction hypothesis on $a$, we have $a < m$, and because (1) implies (2) over all natural numbers, we have $$\next(a) < \next(m) = b$$ as needed. So (4) implies (1) for all $b$ and $c$ for all $a$ by induction, and so (4) implies (1) over all natural numbers as needed.
:::::::::::::
:::::::::::::::



...Or Equal To
--------------

It's typical to generalize $<$ just a bit to make it reflexive.

::: definition :::
We define a relation $\leq$ on $\nats$ as follows: $a \leq b$ if either $a < b$ or $a = b$.
::::::::::::::::::

Less than or equal to satisfies most of the properties less than does (or very nearly so).

::: theorem :::
The following are equivalent for all $a,b,c \in \nats$.

1. $a \leq b$.
2. There exists $m \in \nats$ such that $\plus(a,m) = b$.
3. $\next(a) \leq \next(b)$.
4. $\plus(a,c) \leq \plus(b,c)$.
5. $\mult(a,\next(c)) \leq \mult(b,\next(c))$.

::: proof :::
First we show that (1) implies (2). If $a \leq b$, either $a = b$ or $a < b$. If $a = b$, then $$\plus(a,\zero) = \plus(b,\zero) = b.$$ If $a < b$, then by definition there is a $c$ with $\plus(a,\next(c)) = b$. So (1) implies (2).

Now we show that (2) implies (1). Suppose we have $m \in \nats$ with $\plus(a,m) = b$. There are two possibilities for $m$. If $m = \zero$, then
$$\begin{eqnarray*}
 &   & a \\
 & = & \plus(a,\zero) \\
 & = & \plus(a,m) \\
 & = & b,
\end{eqnarray*}$$
so $a \leq b$. If $m = \next(n)$, then $\plus(a,\next(n)) = b$, so $a < b$ and thus $a \leq b$. So (2) implies (1).

Now we show (1) implies (3). If $a \leq b$, then either $a = b$ or $a < b$. In the first case we have $\next(a) = \next(b)$, and in the second case, as we've [shown](@thm-lt-equivalents), $\next(a) < \next(b)$. In either case $\next(a) \leq \next(b)$ as needed.

(3) implies (1) is shown similarly. If $\next(a) \leq \next(b)$, then either $\next(a) = \next(b)$ or $\next(a) < \next(b)$. In the first case we have $a = b$ because $\next$ is injective, and in the second case we've [shown](@thm-lt-equivalents) that $a < b$. In either case $a \leq b$ as needed.

Now we show (1) implies (4). If $a \leq b$ then either $a = b$ or $a < b$. If $a = b$, we have $\plus(a,c) = \plus(b,c)$, and if $a < b$, we've [shown](@thm-lt-equivalents) that $\plus(a,c) < \plus(b,c)$. In either case, $\plus(a,c) \leq \plus(b,c)$.

(4) implies (1) is shown similarly. If $\plus(a,c) \leq \plus(b,c)$ then either $\plus(a,c) = \plus(b,c)$ or $\plus(a,c) < \plus(b,c)$. In the first case, because $\plus$ is cancellative we have $a = b$. In the second case, we've [shown](@thm-lt-equivalents) that $a < b$. In either case we have $a \leq b$ as needed.

Next we show (1) implies (5). If $a \leq b$, then either $a = b$ or $a < b$. If $a = b$ we have $$\mult(a,\next(c)) = \mult(b,\next(c)).$$ If $a < b$, then as we've [shown](@thm-lt-equivalents) we have $$\mult(a,\next(c)) < \mult(b,\next(c)).$$ In either case we have $$\mult(a,\next(c)) \leq \mult(b,\next(c)).$$

Finally we show (5) implies (1). If $$\mult(a,\next(c)) \leq \mult(a,\next(b)),$$ then either $$\mult(a,\next(c)) = \mult(b,\next(c))$$ or $$\mult(a,\next(c)) < \mult(b,\next(c)).$$ In the first case we have $a = b$ because $\mult$ is (almost) [cancellative](@thm-mult-cancellative), and in the second case we've [shown](@thm-lt-equivalents) that $a < b$. In either case $a \leq b$.
:::::::::::::
:::::::::::::::

As expected, $\leq$ is reflexive, antisymmetric, and transitive.

::: theorem :::
The following hold for all $a,b,c \in \nats$.

1. $a \leq a$.
2. If $a \leq b$ and $b \leq a$, then $a = b$.
3. If $a \leq b$ and $b \leq c$, then $a \leq c$.

::: proof :::
If $a \in \nats$ then $a = a$, so $a \leq a$ by definition.

Suppose $a \leq b$ and $b \leq a$. Then there exist $m,n \in \nats$ such that $\plus(a,m) = b$ and $\plus(b,n) = a$. Now
$$\begin{eqnarray*}
 &   & \plus(a,\plus(m,n)) \\
 & = & \plus(\plus(a,m),n) \\
 & = & \plus(b,n) \\
 & = & a;
\end{eqnarray*}$$
so we have $\plus(m,n) = \zero$, and then $m = n = \zero$. So $$a = \plus(b,m) = \plus(b,\zero) = b$$ as claimed.

Now suppose $a \leq b$ and $b \leq c$; then there are $m,n \in \nats$ with $\plus(a,m) = b$ and $\plus(b,n) = c$. Then
$$\begin{eqnarray*}
 &   & \plus(a,\plus(m,n)) \\
 & = & \plus(\plus(a,m),n) \\
 & = & \plus(b,n) \\
 & = & c,
\end{eqnarray*}$$
so $a \leq c$.
:::::::::::::
:::::::::::::::

We can also solve some inequalities.

::: example :::
If $m \in \nats$ such that $m \leq \zero$, then $m = \zero$.

::: proof :::
Suppose $m \leq \zero$. There are two possibilities for $m$; either $m = \zero$ or $m = \next(n)$ for some $n$. We've shown that $\next(n) \not\lt \zero$, and also that $\zero \not\lt \zero$; in either case we have $m \not\lt \zero$. So it must be that $m = \zero$.
:::::::::::::
:::::::::::::::

We can split a $\leq$ inequality with a $\next$ into an $=$ part and a $<$ part with no $\next$; this is handy for induction proofs.

::: theorem :::
Let $k,n \in \nats$. If $k \leq \next(n)$, then either $k \leq n$ or $k = \next(n)$.

::: proof :::
Suppose $k \leq \next(n)$; then we have $m$ such that $\plus(k,m) = \next(n)$. There are two possibilities for $m$. If $m = \zero$, then $$k = \plus(k,\zero) = \plus(k,m) = \next(n).$$ Suppose instead that $m = \next(u)$ for some $u$. Then
$$\begin{eqnarray*}
 &   & \next(n) \\
 & = & \plus(k,m) \\
 & = & \plus(k,\next(u)) \\
 & = & \next(\plus(k,u)).
\end{eqnarray*}$$
Since $\next$ is injective, we have $\plus(k,u) = n$, and so $k \leq n$ as needed.
:::::::::::::
:::::::::::::::



Greater Than
------------

It's convenient to name the inverses of $<$ and $\leq$.

::: definition :::
We define a relation $>$ on $\nats$ (pronounced _greater than_) as follows. Given $a,b \in \nats$, $a > b$ means the same as $a < b$.

Similarly we define $\geq$ such that $a \geq b$ means the same as $b \leq a$.
::::::::::::::::::

$>$ has analogous properties to those of $<$ whose proofs are all trivial.

::: corollary :::
For all $a,b,c \in \nats$ we have the following.

1. $\next(a) > \zero$.
2. $\zero \not\gt \next(a)$.
3. $a \not\gt a$.
4. If $a > b$, then $b \not\gt a$.
5. If $a > b$ and $b > c$, then $a > c$.
:::::::::::::::::

$>$ interacts with $\next$, $\plus$, and $\mult$.

::: corollary :::
For all $a,b,c \in \nats$, the following are equivalent.

1. $a > b$.
2. $\next(a) > \next(b)$.
3. $\plus(a,c) > \plus(b,c)$.
4. $\mult(a,\next(c)) > \mult(b,\next(c))$.
:::::::::::::::::

Likewise $\geq$.

::: corollary :::
For all $a,b,c \in \nats$ we have the following.

1. $a \geq a$.
2. If $a \geq b$ and $b \geq a$, then $a = b$.
3. If $a \geq b$ and $b \geq c$, then $a \geq c$.
:::::::::::::::::

And $\geq$ interacts with $\next$, $\plus$, and $\mult$.

::: corollary :::
For all $a,b,c \in \nats$, the following are equivalent.

1. $a \geq b$.
2. There exists $m \in \nats$ such that $\plus(b,m) = a$.
2. $\next(a) \geq \next(b)$.
3. $\plus(a,c) \geq \plus(b,c)$.
4. $\mult(a,\next(c)) \geq \mult(b,\next(c))$.
:::::::::::::::::

The additive order relations are handy for lots of reasons. A particularly good one is the following result, which gives a proof template for doing case analysis on $\nats$.

::: theorem :::
Let $a,b \in \nats$. Then one and only one of the following holds.

1. $a < b$
2. $a = b$
3. $a > b$

We call this the _trichotomy property_ of the natural numbers.

::: proof :::
First we show the "one" part; that any two natural numbers satisfy _at least_ one of these relations. We proceed by induction on $a$. For the base case $a = \zero$, note that there are two possibilities for $b$. If $b = \zero$, then we have $$a = \zero = b.$$ If $b = \next(m)$ for some $m$, then we've shown that $$a = \zero < \next(m) = b,$$ so that $a < b$.

For the inductive step, suppose the claim holds for all $b$ for some $a$, and consider $\next(a)$. Let $b \in \nats$. By the inductive hypothesis we have three possibilities.

If $a < b$, we have $\plus(a,\next(c)) = b$ for some $c$. Thus $$\plus(\next(a),c) = b.$$ There are two possibilities for $c$; if $c = \zero$, then we have $\next(a) = b$ as needed, and if $c = \next(d)$ for some $d$ then $\next(a) < b$ as needed.

If $a = b$, we have
$$\begin{eqnarray*}
 &   & \plus(b,\next(\zero)) \\
 & = & \plus(a,\next(\zero)) \\
 & = & \next(\plus(a,\zero)) \\
 & = & \next(a),
\end{eqnarray*}$$
so $b < \next(a)$.

If $a > b$, we have $\plus(b,\next(c)) = a$ for some $c$. Now
$$\begin{eqnarray*}
 &   & \next(a) \\
 & = & \next(\plus(b,\next(c))) \\
 & = & \plus(b,\next(\next(c))),
\end{eqnarray*}$$
so that $b < \next(a)$.

In all cases, either $\next(a) < b$, $\next(a) = b$, or $\next(a) > b$, as needed. By induction the claim holds for all $a,b \in \nats$.

We still need to check the "only one" part of this claim. If $a = b$, we've shown we cannot also have $a < b$, and similarly cannot have $a > b$. If $a < b$, then (by definition) $b > a$ and we cannot also have $a > b$.

And so _at least_ one of $a < b$, $a = b$, or $a > b$ holds, but also _at most_ one holds.
:::::::::::::
:::::::::::::::

The order relations also allow us to express an alternative form of the induction principle. Recall that with ordinary induction, a property holds for all natural numbers if it holds for $\zero$ and also for $\next(n)$ when it holds for $n$. It turns out we can "weaken" the inductive hypothesis a bit to all $k$ such that $k \leq n$. This form of induction is not actually stronger in deductive power than normal induction, but it is sometimes easier to use, and we call it _strong_ induction to distinguish it from normal induction.

::: theorem :::
Let $A$ be a set and suppose we have a function $f : \nats \rightarrow A$. Suppose now that we have a subset $B \subseteq A$ satisfying the following:

1. $f(\zero) \in B$.
2. If $n \in \nats$ and $f(k) \in B$ for all $k \leq n$, then $f(\next(n)) \in B$.

Then we have $f(n) \in B$ for all $n \in \nats$. When using this theorem we say we are proceeding by _strong induction_; (1) is called the _base case_ and (2) is called the _inductive step_.

::: proof :::
Let $B$ be such a subset. We define an auxiliary subset $T \subseteq \nats$ as follows: $$T = \{ n \mid \mathrm{if}\ k \leq n\ \mathrm{then}\ f(k) \in B\ \mathrm{for\ all}\ k \}.$$ We first will show that $T = \nats$ by induction.

For the base case, consider $n = \zero$. If $k \leq \zero$, then $k = \zero$. We have $f(k) = f(\zero) \in B$ by definition, and thus $\zero \in T$ as needed.

For the inductive step, suppose we have $n \in T$. Now suppose $k \leq \next(n)$. We need to show that $f(k) \in B$. There are two possibilities: either $k \leq n$ or $k = \next(n)$. Suppose first that $k \leq n$; since $n \in T$, we have $f(k) \in B$. Now suppose $k = \next(n)$. Again we have $n \in T$, and note that the condition for membership in $T$ is precisely the hypothesis of (2). So we have $f(\next(n)) \in B$. In either case we have $f(k) \in B$, and so $\next(n) \in T$. By induction we thus have $T = \nats$.

Finally we can show that $f(n) \in B$ for all $n$. To this end let $n \in \nats$. We have $n \in T$, and in particular, since $n \leq n$, we have $f(n) \in B$. Since $n$ was arbitrary the theorem is proved.
:::::::::::::
:::::::::::::::

The most common variant of strong induction is that having $A = \nats$ and $f = \id$.

::: corollary :::
Suppose we have a subset $B \subseteq \nats$ satisfying the following properties.

1. $\zero \in B$.
2. For all $n \in \nats$, if $k \in B$ whenever $k \leq n$, then $\next(n) \in B$.

Then $B = \nats$.
:::::::::::::::::

Strong induction also has an analogous "measure" variety.

::: theorem :::
Let $f : A \rightarrow \nats$ be a function. Suppose we have $B \subseteq A$ satisfying the following.

1. $f(a) = \zero$ implies $a \in B$ for all $a \in A$.
2. For all $n \in \nats$, if $f(a) = k$ and $k \leq n$ imply $a \in B$ for all $k \in \nats$ and $a \in A$, then $f(a) = \next(n)$ implies $a \in B$ for all $a \in A$.

Then we have $B = A$. When using this theorem we say we are proceeding by _strong induction on_ $f$; (1) is called the _base case_, and (2) the _inductive step_.

::: proof :::
Let $B$ be such a subset. We define an auxiliary subset $T \subseteq \nats$ by $$T = \{ n \mid \mathrm{if}\ f(a) = n\ \mathrm{then}\ a \in B\ \mathrm{for\ all}\ a \in A \}.$$ We first will show that $T = \nats$ by strong induction.

For the base case $n = \zero$, note that for all $a \in A$, if $f(a) = \zero$ then $a \in b$ by (1). So we have $\zero \in T$.

For the inductive step, let $n \in \nats$ and suppose we have $k \in T$ for all $k \leq n$. We want to show that $\next(n) \in T$. First note the following: if $a \in A$ and $k \leq n$, since $k \in T$, we have that if $f(a) = k$ then $a \in B$. This is precisely the hypothesis of (2). And so, whenever $f(a) = \next(n)$, we have $a \in B$. Thus $\next(n) \in T$, and by induction we have $T = \nats$.

Finally, let $a \in A$. Now $f(a) \in \nats \subseteq T$, so we have $a \in B$. Thus $B = A$ as claimed.
:::::::::::::
:::::::::::::::
