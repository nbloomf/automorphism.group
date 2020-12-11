---
title: Addition
---

Another Recursion Operator
--------------------------

At this point we've defined (as an axiom) the natural numbers $\nats$ as an inductive set from which there is a unique inductive homomorphism $\natrec$. It may be surprising that this is all we need; from here we could directly define the usual arithmetic. It will be handy, though, to have some more specialized tools first.

We can think of $\natrec$ as a _recursion operator_. It takes some very basic data, $e$ and $\varphi$, and bundles it into a very well-behaved function $\nats \rightarrow A$. Notably, the proof that $\natrec$ is well-behaved only needs to be written once. Whenever we sit down to design a recursive function on $\nats$, it may be handy to see if there is a more general recursion operator hiding in the details.

Here we will establish the existence and uniqueness of a handy operator called _simple recursion with a parameter_. This is handy for defining functions with signature $\nats \times A \rightarrow B$.

::: theorem :::
[@thm-simple-recursion]()
Let $A$ and $B$ be sets, and suppose we have functions $\varphi : A \rightarrow B$ and $\mu : \nats \times A \times B \rightarrow B$. Then there is a unique function $\Theta : \nats \times A \rightarrow B$ satisfying the following:

1. $\Theta(\zero,a) = \varphi(a)$ for all $a \in A$.
2. $\Theta(\next(n),a) = \mu(n,a,\Theta(n,a))$ for all $a \in A$ and $n \in \nats$.

This function $\Theta$ will be denoted $\mathsf{simprec}_{\varphi,\mu}$, called _simple recursion with a parameter_.

::: proof :::
This is a "there exists a unique" theorem, so we have to things to show: that such a $\Theta$ exists, and that it is unique. First we show existence.

Define $\varepsilon : A \rightarrow \nats \times B$ by $$\varepsilon(a) = (\zero, \varphi(a)),$$ and define $\chi : A \rightarrow (\nats \times B)^{\nats \times B}$ by $$\chi(a)(n,b) = (\next(n),\mu(n,a,b)).$$

Now for each $a \in A$, $\langle \nats \times B, \varepsilon(a), \mu(a) \rangle$ is an iterative set. We then define $\Omega : \nats \rightarrow (\nats \times B)^A$ by $$\Omega(n)(a) = \natrec_{\varepsilon(a),\chi(a)}(n).$$ Finally we define $\Theta : \nats \times A \rightarrow B$ by $$\Theta(n,a) = \pi_2(\Omega(n)(a)),$$ where $\pi_2 : \nats \times B \rightarrow B$ is the second "coordinate projection -- that is, $\pi_2(n,b) = b$. We claim that this $\Theta$ satisfies properties (1) and (2).

To see that $\Theta$ satisfies (1), let $a \in A$. Now we have
$$\begin{eqnarray*}
\Theta(\zero,a)
 & = & \pi_2(\Omega(n)(a)) \\
 & = & \pi_2(\natrec_{\varepsilon(a),\chi(a)}(\zero)) \\
 & = & \pi_2(\varepsilon(a)) \\
 & = & \pi_2(\mathsf{zero},\varphi(a)) \\
 & = & \varphi(a)
\end{eqnarray*}$$
as needed. Before we show that $\Theta$ satisfies (2), we'll use induction to show that for all $a \in A$ and $n \in \nats$, $$\Omega(\next(n))(a) = (\next(n),\mu(n,a,\Theta(n,a))).$$

For the base case, suppose $n = \zero$. Now
$$\begin{eqnarray*}
 &   & \Omega(\next(\zero))(a) \\
 & = & \natrec_{\varepsilon(a),\chi(a)}(\next(\zero)) \\
 & = & \chi(a)(\natrec_{\varepsilon(a),\chi(a)}(\zero)) \\
 & = & \chi(a)(\varepsilon(a)) \\
 & = & \chi(a)(\zero,\varphi(a)) \\
 & = & (\next(\zero),\mu(\zero,a,\varphi(a))) \\
 & = & (\next(\zero),\mu(\zero,a,\Theta(\zero,a)))
\end{eqnarray*}$$
as claimed. For the inductive step, suppose the equality holds for all $a \in A$ for some $n \in \nats$. Now let $a \in A$; we have
$$\begin{eqnarray*}
 &   & \Omega(\next(\next(n)))(a) \\
 & = & \natrec_{\varepsilon(a),\chi(a)}(\next(\next(n))) \\
 & = & \chi(a)(\natrec_{\varepsilon(a),\chi(a)}(\next(n))) \\
 & = & \chi(a)(\Omega(\next(n))(a)) \\
 & = & \chi(a)(\next(n),\mu(n,a,\Theta(n,a))) \\
 & = & (\next(\next(n)),\mu(\next(n),a,\mu(n,a,\Theta(n,a)))) \\
 & = & (\next(\next(n)), \\
 &   & \quad \mu(\next(n),a,\pi_2(\next(n),\mu(n,a,\Theta(n,a))))) \\
 & = & (\next(\next(n)),\mu(\next(n),a,\pi_2(\Omega(\next(n))(a)))) \\
 & = & (\next(\next(n)),\mu(\next(n),a,\Theta(\next(n),a))). \\
\end{eqnarray*}$$
By induction, and since $a$ was arbitrary in $A$, the equality holds. But now for all $a \in A$ and $n \in \nats$, we have
$$\begin{eqnarray*}
 &   & \Theta(\next(n),a) \\
 & = & \pi_2(\Omega(\next(n))(a)) \\
 & = & \pi_2(\next(n),\mu(n,a,\Theta(n,a))) \\
 & = & \mu(n,a,\Theta(n,a))
\end{eqnarray*}$$
as claimed.

To see that $\Theta$ is unique, we again use induction. Suppose $\Psi : \nats \times A \rightarrow B$ is another function satisfying both (1) and (2). For the base case, we have
$$\begin{eqnarray*}
\Psi(\zero,a)
 & = & \varphi(a) \\
 & = & \Theta(\zero,a)
\end{eqnarray*}$$
for all $a \in A$. For the inductive step, if $n \in \nats$ such that $\Psi(n,a) = \Theta(n,a)$ for all $a \in A$, then we have
$$\begin{eqnarray*}
\Psi(\next(n),a)
 & = & \mu(n,a,\Psi(n,a)) \\
 & = & \mu(n,a,\Theta(n,a)) \\
 & = & \Theta(\next(n),a)
\end{eqnarray*}$$
for all $a \in A$. So we have $\Psi = \Theta$ as claimed.
:::::::::::::
:::::::::::::::

This proof might look like a significant jump in sophistication over what we've been doing up to this point because it uses functions which output other functions. But the core of the argument is very simple: we defined $\Theta$, showed it has the desired properties (by induction), and showed it is unique with those properties (by induction).

As with $\natrec$, what's handy about this operator is it only needs two pieces of data, $\varphi$ and $\mu$, which are not subject to any restrictions other than their signatures.



Addition
--------

We're going to use $\mathsf{simprec}$ to define addition on natural numbers. Rather than just writing down the definition, it's instructive to see where it comes from. $\simprec$ has the right signature; $\simprec : \nats \times A \rightarrow B$ with $A = B = \nats$. We just need to find appropriate $\varphi : \nats \rightarrow \nats$ and $mu : \nats \times \nats \times \nats \rightarrow \nats$. For instance, we'd like $\next$ to behave like $+1$, and $$n = \zero + n = \simprec_{\varphi,\mu}(\zero,n) = \varphi(n),$$ so maybe $\varphi = \id$. Similarly, we want
$$\begin{eqnarray*}
 &   & (m + n) + 1 \\
 & = & (m + 1) + n \\
 & = & \simprec_{\varphi,\mu}(\next(m), n) \\
 & = & \mu(m,n,\simprec_{\varphi,\mu}(m,n)) \\
 & = & \mu(m,n,m+n).
\end{eqnarray*}$$
With that in mind, we define $\plus$ as follows.

::: definition :::
[@def-nat-plus]()
Define $\mu : \nats \times \nats \times \nats \rightarrow \nats$ by $\mu(-,-,b) = \next(b)$. We then define $\plus : \nats \times \nats \rightarrow \nats$ by $$\plus = \simprec_{\id,\mu}.$$ We'll usually prefer the infix symbol $+$ rather than the prefix $\plus$ for this function.
::::::::::::::::::

Defining $\plus$ in terms of $\simprec$ has a nice side effect; we can characterize $\plus$ as the unique solution to a particular set of functional equations. This gives a natural way to show that some function is really $\plus$; show it satisfies these equations.

::: corollary :::
$\plus$ is the unique function $f$ having signature $\nats \times \nats \rightarrow \nats$ satisfying the following system of functional equations for all $a,b \in \nats$.

$$\left\{\begin{array}{l}
f(\zero,b) = b \\
f(\next(a),b) = \next(f(a,b)).
\end{array}\right.$$
:::::::::::::::::

The remainder of this section is all about showing that this $\plus$ acts like we expect it to. First, $\plus$ interacts with $\next$.

::: theorem :::
The following hold for all $a,b \in \nats$.

1. $\plus(a,\zero) = a$.
2. $\plus(a,\next(b)) = \next(\plus(a,b))$.
3. $\plus(\next(a),b) = \plus(a,\next(b))$.

::: proof :::
Throughout this proof, we use $\mu$ as defined with $\plus$. To show (1) we proceed by induction on $a$. For the base case $a = \zero$, we have
$$\begin{eqnarray*}
 &   & \plus(a,\zero) \\
 & = & \plus(\zero,\zero) \\
 & = & \simprec_{\id,\mu}(\zero,\zero) \\
 & = & \id(\zero) \\
 & = & \zero \\
 & = & a
\end{eqnarray*}$$
as needed. For the inductive step, suppose that for some $a \in \nats$ we have $\plus(a,\zero) = a$. Now
$$\begin{eqnarray*}
 &   & \plus(\next(a),\zero) \\
 & = & \next(\plus(a,\zero)) \\
 & = & \next(a).
\end{eqnarray*}$$
By induction, (1) holds for all $a \in \nats$.

We also show (2) by induction on $a$. For the base case, let $a = \zero$; we then have
$$\begin{eqnarray*}
 &   & \plus(a,\next(b)) \\
 & = & \plus(\zero,\next(b)) \\
 & = & \simprec_{\id,\mu}(\zero,\next(b)) \\
 & = & \id(\next(b)) \\
 & = & \next(b) \\
 & = & \next(\id(b)) \\
 & = & \next(\simprec_{\id,\mu}(\zero,b)) \\
 & = & \next(\plus(\zero,b)) \\
 & = & \next(\plus(a,b))
\end{eqnarray*}$$
as needed. For the inductive step, suppose we have $\plus(a,\next(b)) = \next(\plus(a,b))$ for all $b \in A$ for some $a \in A$. Now
$$\begin{eqnarray*}
 &   & \plus(\next(a),\next(b)) \\
 & = & \next(\plus(a,\next(b))) \\
 & = & \next(\next(\plus(a,b))) \\
 & = & \next(\plus(\next(a),b)).
\end{eqnarray*}$$
By induction, the (2) holds for all $a,b \in \nats$.

To see (3), note that
$$\begin{eqnarray*}
 &   & \plus(\next(a),b) \\
 & = & \next(\plus(a,b)) \\
 & = & \plus(a,\next(b))
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::

Next, $\plus$ is associative.

::: theorem :::
[@thm-plus-associative]()
For all $a,b,c \in \nats$, we have $$\plus(\plus(a,b),c) = \plus(a,\plus(b,c)).$$

::: proof :::
We proceed by induction on $a$. For the base case $a = 0$, note that
$$\begin{eqnarray*}
 &   & \plus(\plus(a,b),c) \\
 & = & \plus(\plus(\zero,b),c) \\
 & = & \plus(b,c) \\
 & = & \plus(\zero,\plus(b,c)) \\
 & = & \plus(a,\plus(b,c))
\end{eqnarray*}$$
as needed. For the inductive step, suppose we have $$\plus(\plus(a,b),c) = \plus(a,\plus(b,c))$$ for all $b,c \in \nats$ for some $a$. Now
$$\begin{eqnarray*}
 &   & \plus(\plus(\next(a),b),c) \\
 & = & \plus(\next(\plus(a,b)),c) \\
 & = & \next(\plus(\plus(a,b),c)) \\
 & = & \next(\plus(a,\plus(b,c))) \\
 & = & \plus(\next(a),\plus(b,c)).
\end{eqnarray*}$$
By induction, we thus have $$\plus(\plus(a,b),c) = \plus(a,\plus(b,c))$$ for all $a,b,c \in \nats$.
:::::::::::::
:::::::::::::::

This gives us our first interesting example of a semigroup.

::: corollary :::
$\langle \nats, \plus \rangle$ is a semigroup.
:::::::::::::::::

$\plus$ is also commutative.

::: theorem :::
For all $a,b \in \nats$, we have $\plus(a,b) = \plus(b,a)$.

::: proof :::
We proceed by induction on $a$. For the base case $a = \zero$, we have
$$\begin{eqnarray*}
 &   & \plus(\zero,b) \\
 & = & b \\
 & = & \plus(b,\zero)
\end{eqnarray*}$$
for all $b$. For the inductive step, suppose $\plus(a,b) = \plus(b,a)$ for all $b \in \nats$ for some $a$. Now
$$\begin{eqnarray*}
 &   & \plus(\next(a),b) \\
 & = & \next(\plus(a,b)) \\
 & = & \next(\plus(b,a)) \\
 & = & \plus(b,\next(a)).
\end{eqnarray*}$$
By induction, $\plus(a,b) = \plus(b,a)$ for all $a,b \in \nats$.
:::::::::::::
:::::::::::::::

Finally, $\plus$ is cancellative.

::: theorem :::
For all $a,b,c \in \nats$, we have the following.

1. If $\plus(c,a) = \plus(c,b)$, then $a = b$.
2. If $\plus(a,c) = \plus(b,c)$, then $a = b$.

A binary operation (like $\plus$) that satisfies (1) is called _left cancellative_, and one satisfying (2) is called _right cancellative_. Operations which satisfy both (like $\plus$) are simply called _cancellative_.

::: proof :::
To see (1), we proceed by induction on $c$. For the base case, suppose $$\plus(\zero,a) = \plus(\zero,b).$$ Then we have
$$\begin{eqnarray*}
 &   & a \\
 & = & \plus(\zero,a) \\
 & = & \plus(\zero,b) \\
 & = & b
\end{eqnarray*}$$
as needed. For the inductive step, suppose (1) holds for all $a$ and $b$ for some $c$. Now suppose $$\plus(\next(c),a) = \plus(\next(c),b).$$ Then we have
$$\begin{eqnarray*}
 &   & \next(\plus(c,a)) \\
 & = & \plus(\next(c),a) \\
 & = & \plus(\next(c),b) \\
 & = & \next(\plus(c,b)).
\end{eqnarray*}$$
Since $\next$ is [injective](@thm-next-injective), we have $\plus(c,a) = \plus(c,b)$. By the induction hypothesis, we have $a = b$. By induction, then, (1) holds for all $a,b,c \in \nats$.

To see (2), suppose $$\plus(a,c) = \plus(b,c).$$ Then we have
$$\begin{eqnarray*}
 &   & \plus(c,a) \\
 & = & \plus(a,c) \\
 & = & \plus(b,c) \\
 & = & \plus(c,b).
\end{eqnarray*}$$
Using (1), then, we have $a = b$ as claimed.
:::::::::::::
:::::::::::::::

We've shown that $\plus$ is associative, commutative, and cancellative, as we expect. However it may not be clear how to get from $\zero$ and $\next$ to the usual base 10 notation for numbers, which I've been careful to avoid. In a nutshell, what we've defined here is a _unary_ representation for natural numbers; the "size" of the number is just the number of times $\next$ is applied to $\zero$. As an example, let's compute the sum of "2" and "3".

$$\begin{eqnarray*}
 &   & \plus(\next(\next(\zero)),\next(\next(\next(\zero)))) \\
 & = & \plus(\next(\zero),\next(\next(\next(\next(\zero)))) \\
 & = & \plus(\zero,\next(\next(\next(\next(\next(\zero))))) \\
 & = & \next(\next(\next(\next(\next(\zero)))) \\
\end{eqnarray*}$$

$\plus$ works by peeling $\next$s off of one argument and moving it to the other, until the argument reaches zero. This is extremely inefficient, but it is very convenient for proving lots of theorems.

What's happening here is that, as we've defined it here, $\nats$ is simply one possible _representation_ of the natural numbers -- one which is amenable to some problems but not others. Later on we will construct alternative representations that are better for different kinds of problems. The benefit of defining $\nats$ in terms of its universal property is that showing different representations are really "the same" is very straightforward.

::: theorem :::
Let $\langle A, e, \varphi \rangle$ be an iterative set, and suppose $A$ has the property that for any iterative set $B$, there is a unique iterative set homomorphism $\Theta : A \rightarrow B$. Then we have $A \cong \nats$.

::: proof :::
Let $\Theta : A \rightarrow \nats$ be the unique iterative homomorphism. By the uniqueness property, we must have $\Theta \circ \natrec = \id_\nats$ and $\natrec \circ \Theta = \id_A$; thus $A \cong \nats$ via $\Theta$.
:::::::::::::
:::::::::::::::



Solving Equations
-----------------

We can solve some basic addition problems now.

::: example :::
[@thm-plus-neutral]()
Let $a,b \in \nats$. Then we have the following.

1. If $\plus(a,b) = a$, then $b = \zero$.
2. If $\plus(b,a) = a$, then $b = \zero$.

::: proof :::
To see (1), note that
$$\begin{eqnarray*}
 &   & \plus(a,b) \\
 & = & a \\
 & = & \plus(a,\zero).
\end{eqnarray*}$$
Since $\plus$ is left cancellative, we have $b = \zero$ as claimed. (2) is proved similarly, using the fact that $\plus$ is right cancellative.
:::::::::::::
:::::::::::::::

If $\plus(-,b)$ acts like $\next$, then $b = 1$.

::: theorem :::
Let $a,b \in \nats$. Then we have the following.

1. If $\plus(a,b) = \next(a)$, then $b = \next(\zero)$.
2. If $\plus(a,b) = \next(b)$, then $a = \next(\zero)$.

::: proof :::
First we show (1). There are two possitibilities for $b$. If $b = \zero$, then
$$\begin{eqnarray*}
 &   & \next(a) \\
 & = & \plus(a,b) \\
 & = & \plus(a,\zero) \\
 & = & a;
\end{eqnarray*}$$
however we've [shown](@thm-next-no-fixpoint) this cannot happen. So we must have $b = \next(m)$ for some $m$. Now
$$\begin{eqnarray*}
 &   & \next(a) \\
 & = & \plus(a,b) \\
 & = & \plus(a,\next(m)) \\
 & = & \next(\plus(a,m)).
\end{eqnarray*}$$
Since $\next$ is injective, we have $a = \plus(a,m)$, and so $m = \zero$ by the previous theorem. Then $b = \next(\zero)$ as claimed.

To see (2), suppose $\plus(a,b) = \next(b)$. Then
$$\begin{eqnarray*}
 &   & \next(b) \\
 & = & \plus(a,b) \\
 & = & \plus(b,a),
\end{eqnarray*}$$
and using (1), we have $a = \next(\zero)$ as claimed.
:::::::::::::
:::::::::::::::

The next theorem solves $a + b = 0$, $a + b = 1$, and $a + b = 2$ over the natural numbers. Baby steps!

::: example :::
[@thm-nats-plus-eq-zero]()[@thm-nats-plus-eq-one]()[@thm-nats-plus-eq-two]()
Let $a,b \in \nats$.

1. If $\plus(a,b) = \zero$, then $a = b = \zero$.
2. If $\plus(a,b) = \next(\zero)$, then either $a = \zero$ and $b = \next(\zero)$, or $a = \next(\zero)$ and $b = \zero$.
3. If $\plus(a,b) = \next(\next(\zero))$, then either $a = \zero$ and $b = \next(\next(\zero))$, or $a = \next(\zero)$ and $b = \next(\zero)$, or $a = \next(\next(\zero))$ and $b = \zero$.

::: proof :::
First we show (1). Suppose $\plus(a,b) = \zero$. We've [shown](@thm-nat-case) that $a$ is either $\zero$ or $\next(n)$ for some $n$. If $a = \next(n)$, then we have
$$\begin{eqnarray*}
 &   & \zero \\
 & = & \plus(a,b) \\
 & = & \plus(\next(n),b) \\
 & = & \next(\plus(n,b));
\end{eqnarray*}$$
however we've also [shown](@thm-nat-zero-not-next) that $\zero$ cannot be equal to $\next(-)$. So we must have $a = \zero$. But now
$$\begin{eqnarray*}
 &   & b \\
 & = & \plus(\zero,b) \\
 & = & \plus(a,b) \\
 & = & \zero
\end{eqnarray*}$$
as claimed.

Next we show (2). Suppose $\plus(a,b) = \next(\zero)$. Again, either $a = \zero$ or $a = \next(n)$ for some $n$. If $a = \zero$, we have
$$\begin{eqnarray*}
 &   & b \\
 & = & \plus(\zero,b) \\
 & = & \plus(a,b) \\
 & = & \next(\zero).
\end{eqnarray*}$$
Suppose instead that $a = \next(n)$. Now we have
$$\begin{eqnarray*}
 &   & \next(\zero) \\
 & = & \plus(a,b) \\
 & = & \plus(\next(n),b) \\
 & = & \next(\plus(n,b)).
\end{eqnarray*}$$
Since $\next$ is injective, we have $\plus(n,b) = \zero$; by (1), we have $n = b = \zero$, and so $a = \next(\zero)$.

Finally we show (3). Suppose $\plus(a,b) = \next(\next(\zero))$. Again, either $a = \zero$ or $a = \next(n)$ for some $n$. If $a = \zero$, then
$$\begin{eqnarray*}
 &   & b \\
 & = & \plus(\zero,b) \\
 & = & \plus(a,b) \\
 & = & \next(\next(\zero)).
\end{eqnarray*}$$
Suppose instead that $a = \next(n)$; then
$$\begin{eqnarray*}
 &   & \next(\next(\zero)) \\
 & = & \plus(a,b) \\
 & = & \plus(\next(n),b) \\
 & = & \next(\plus(n,b)).
\end{eqnarray*}$$
Since $\next$ is injective, we have $\plus(n,b) = \next(\zero)$. By (2) we have two possibilities: $n = \zero$ (so $a = \next(\zero)$) and $b = \next(\zero)$, or $n = \next(\zero)$ (so $a = \next(\next(\zero))$) and $b = \zero$.
:::::::::::::
:::::::::::::::
