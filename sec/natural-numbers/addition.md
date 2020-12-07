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

We're going to use $\mathsf{simprec}$ to define addition on natural numbers. Rather than just writing down the definition, it's instructive to see where it comes from. $\simprec$ has the right signature; $\simprec : \nats \times A \rightarrow B$ with $A = B = \nats$. We just need to find appropriate $\varphi : \nats \rightarrow \nats$ and $mu : \nats \times \nats \times \nats \rightarrow \nats$. For instance, we'd like $\next$ to behave like $+1$, and $$n = \zero + n = \simprec_{\varphi,\mu}(\zero,n) = \varphi(n),$$ so maybe $\varphi = \mathsf{id}$. Similarly, we want
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
Define $\mu : \nats \times \nats \times \nats \rightarrow \nats$ by $\mu(-,-,b) = \next(b)$. We then define $\plus : \nats \times \nats \rightarrow \nats$ by $$\plus = \simprec_{\mathsf{id},\mu}.$$ We'll usually prefer the infix symbol $+$ rather than the prefix $\plus$ for this function.
::::::::::::::::::

The remainder of this section is all about showing that this $\plus$ acts like we expect it to. First, $\plus$ interacts with $\next$.

::: theorem :::
The following hold for all $a,b \in \nats$.

1. $\plus(\zero,a) = a$.
2. $\plus(\next(a),b) = \next(\plus(a,b))$.
3. $\plus(a,\zero) = a$.
4. $\plus(a,\next(b)) = \next(\plus(a,b))$.

::: proof :::
Throughout this proof, we use $\mu$ as defined with $\plus$. To see (1), note that
$$\begin{eqnarray*}
 &   & \plus(\zero,a) \\
 & = & \simprec_{\mathsf{id},\mu}(\zero,a) \\
 & = & \mathsf{id}(a) \\
 & = & a
\end{eqnarray*}$$
as claimed.

To see (2), note that
$$\begin{eqnarray*}
 &   & \plus(\next(a),b) \\
 & = & \simprec_{\mathsf{id},\mu}(\next(a),b) \\
 & = & \mu(a,b,\simprec_{\mathsf{id},\mu}(a,b)) \\
 & = & \next(\simprec_{\mathsf{id},\mu}(a,b)) \\
 & = & \next(\plus(a,b))
\end{eqnarray*}$$
as claimed.

To show (3) we proceed by induction on $a$. For the base case $a = \zero$, we have
$$\begin{eqnarray*}
 &   & \plus(a,\zero) \\
 & = & \plus(\zero,\zero) \\
 & = & \simprec_{\mathsf{id},\mu}(\zero,\zero) \\
 & = & \mathsf{id}(\zero) \\
 & = & \zero \\
 & = & a
\end{eqnarray*}$$
as needed. For the inductive step, suppose that for some $a \in \nats$ we have $\plus(a,\zero) = a$. Now
$$\begin{eqnarray*}
 &   & \plus(\next(a),\zero) \\
 & = & \next(\plus(a,\zero)) \\
 & = & \next(a).
\end{eqnarray*}$$
By induction, (3) holds for all $a \in \nats$.

We also show (4) by induction on $a$. For the base case, let $a = \zero$; we then have
$$\begin{eqnarray*}
 &   & \plus(a,\next(b)) \\
 & = & \plus(\zero,\next(b)) \\
 & = & \simprec_{\mathsf{id},\mu}(\zero,\next(b)) \\
 & = & \mathsf{id}(\next(b)) \\
 & = & \next(b) \\
 & = & \next(\mathsf{id}(b)) \\
 & = & \next(\simprec_{\mathsf{id},\mu}(\zero,b)) \\
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
By induction, the (4) holds for all $a,b \in \nats$.
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
