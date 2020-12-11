---
title: Multiplication
---



Multiplication
--------------

Now we'll try to define the usual product of natural numbers, $\mult$. Like $\plus$, this operation has signature $\nats \times \nats \rightarrow \nats$, so we might hope to define it in terms of $\simprec_{\varphi,\mu}$ for some $\varphi$ and $\mu$. For example, the product of zero with any natural number should again be zero. So
$$\begin{eqnarray*}
\zero
 & = & \simprec_{\varphi,\mu}(\zero,m) \\
 & = & \varphi(m)
\end{eqnarray*}$$
for any $m$; evidently then $\varphi = \const_\zero$. Similarly, we want
$$\begin{eqnarray*}
 &   & n \cdot m + m \\
 & = & (n + 1) \cdot m \\
 & = & \simprec_{\varphi,\mu}(\next(n),m) \\
 & = & \mu(n,m,\simprec_{\varphi,\mu}(n,m)) \\
 & = & \mu(n,m,n \cdot m),
\end{eqnarray*}$$
and evidently $\mu(-,m,k) = \plus(k,m)$. With that in mind we define $\mult$ as follows.

::: definition :::
Let $\mu : \nats \times \nats \times \nats \rightarrow \nats$ be given by $\mu(-,a,b) = \plus(b,a)$. We define $\mult : \nats \times \nats \rightarrow \nats$ by $$\mult = \simprec_{\const_\zero,\mu}.$$ 
::::::::::::::::::

As with $\plus$, we can characterize $\mult$ as the unique solution to a system of functional equations. This is handy for a couple of reasons. One, it represents properties of $\mult$. But more broadly, once we have isomorphic copies of $\nats$ giving different representations of numbers (like the fixed radix notation we usually expect), we can use it to show that different _implementations_ of $\mult$ are really correct as long as they "behave" like $\mult$.

::: corollary :::
$\mult$ is the unique function $f$ having signature $\nats \times \nats \rightarrow \nats$ satisfying the following system of functional equations for all $a,b \in \nats$.

$$\left\{\begin{array}{l}
f(\zero,b) = \zero \\
f(\next(a),b) = \plus(f(a,b),b).
\end{array}\right.$$
:::::::::::::::::

We now embark upon an arduous journey to show that this $\mult$ behaves the way we think it does.

::: theorem :::
The following hold for all $a,b \in \nats$.

1. $\mult(a,\zero) = \zero$.
2. $\mult(a,\next(b)) = \plus(\mult(a,b),a)$.

::: proof :::
In this proof, $\mu$ will be as given in the definition of $\mult$. We show (1) by induction. For the base case, suppose $a = \zero$. Then we have
$$\begin{eqnarray*}
 &   & \mult(a,\zero) \\
 & = & \mult(\zero,\zero) \\
 & = & \zero
\end{eqnarray*}$$
as needed. For the inductive step, suppose we have $a \in \nats$ such that $\mult(a,\zero) = \zero$. Now
$$\begin{eqnarray*}
 &   & \mult(\next(a),\zero) \\
 & = & \plus(\mult(a,\zero),\zero) \\
 & = & \plus(\zero,\zero) \\
 & = & \zero
\end{eqnarray*}$$
as needed. So (1) holds for all $a \in \nats$ by induction.

We also show (2) by induction on $a$. For the base case $a = \zero$, we have
$$\begin{eqnarray*}
 &   & \mult(a,\next(b)) \\
 & = & \mult(\zero,\next(b)) \\
 & = & \zero \\
 & = & \mult(\zero,b) \\
 & = & \plus(\mult(\zero,b),\zero) \\
 & = & \plus(\mult(a,b),a)
\end{eqnarray*}$$
as claimed. For the inductive step, suppose we have $a \in \nats$ with $$\mult(a,\next(b)) = \plus(\mult(a,b),a)$$ for all $b \in \nats$. Then
$$\begin{eqnarray*}
 &   & \mult(\next(a),\next(b)) \\
 & = & \plus(\mult(a,\next(b)),\next(b)) \\
 & = & \next(\plus(\mult(a,\next(b)),b)) \\
 & = & \next(\plus(\plus(\mult(a,b),a),b)) \\
 & = & \next(\plus(\mult(a,b),\plus(a,b))) \\
 & = & \next(\plus(\mult(a,b),\plus(b,a))) \\
 & = & \next(\plus(\plus(\mult(a,b),b),a)) \\
 & = & \next(\plus(\mult(\next(a),b),a)) \\
 & = & \plus(\mult(\next(a),b),\next(a))
\end{eqnarray*}$$
for all $b \in \nats$. By induction, then, (2) holds for all $a,b \in \nats$.
:::::::::::::
:::::::::::::::

We've seen that the output of $\mult$ is $\zero$ if either input is zero. In fact this is the _only_ way $\mult$ can produce $\zero$.

::: theorem :::
If $a,b \in \nats$ such that $\mult(a,b) = \zero$, then either $a = \zero$ or $b = \zero$.

::: proof :::
[@thm-nat-no-zero-divisors]()
Suppose $\mult(a,b) = \zero$. Recall that if $a \in \nats$, then either $a = \zero$ or $a = \next(n)$ for some $n$. Similarly, either $b = \zero$ or $b = \next(m)$ for some $m$. Suppose we have $a = \next(n)$ and $b = \next(m)$. Now
$$\begin{eqnarray*}
 &   & \zero
 & = & \mult(a,b) \\
 & = & \mult(\next(n),\next(m)) \\
 & = & \plus(\mult(n,\next(m)),\next(m)) \\
 & = & \next(\plus(\mult(n,\next(m)),m)).
\end{eqnarray*}$$
However there does not exist $k \in \nats$ with $\next(k) = \zero$; so we must have either $a = \zero$ or $b = \zero$.
:::::::::::::
:::::::::::::::

$\next(\zero)$ acts like 1.

::: theorem :::
For all $a \in \nats$, we have the following.

1. $\mult(\next(\zero),a) = a$.
2. $\mult(a,\next(\zero)) = a$.

::: proof :::
To see (1), note that for all $a \in \nats$ we have
$$\begin{eqnarray*}
 &   & \mult(\next(\zero),a) \\
 & = & \plus(\mult(\zero,a),a) \\
 & = & \plus(\zero,a) \\
 & = & a
\end{eqnarray*}$$
as claimed.

To see (2), we proceed by induction on $a$. For the base case $a = \zero$, note that
$$\begin{eqnarray*}
 &   & \mult(a,\next(\zero)) \\
 & = & \mult(\zero,\next(\zero)) \\
 & = & \zero \\
 & = & a
\end{eqnarray*}$$
as needed. For the inductive step, suppose the equality holds for some $a \in \nats$. Now
$$\begin{eqnarray*}
 &   & \mult(\next(a),\next(\zero)) \\
 & = & \plus(\mult(a,\next(\zero)),\next(\zero)) \\
 & = & \plus(a,\next(\zero)) \\
 & = & \next(\plus(a,\zero)) \\
 & = & \next(a).
\end{eqnarray*}$$
By induction, (2) holds for all $a$.
:::::::::::::
:::::::::::::::

As a special case, multiplying by "two" is equivalent to adding a number to itself.

::: example :::
For all $a \in \nats$, $$\mult(\next(\next(\zero)),a) = \plus(a,a).$$

::: proof :::
We have
$$\begin{eqnarray*}
 &   & \mult(\next(\next(\zero)),a) \\
 & = & \plus(\mult(\next(\zero),a),a) \\
 & = & \plus(a,a)
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::

$\mult$ is commutative.

::: theorem :::
For all $a,b \in \nats$, we have $$\mult(a,b) = \mult(b,a).$$

::: proof :::
We proceed by induction on $a$. For the base case $a = 0$, we have
$$\begin{eqnarray*}
 &   & \mult(a,b) \\
 & = & \mult(\zero,b) \\
 & = & \zero \\
 & = & \mult(b,\zero) \\
 & = & \mult(b,a)
\end{eqnarray*}$$
as needed. For the inductive step, suppose we have $a \in \nats$ such that $\mult(a,b) = \mult(b,a)$ for all $b \in \nats$. Now
$$\begin{eqnarray*}
 &   & \mult(\next(a),b) \\
 & = & \plus(\mult(a,b),b) \\
 & = & \plus(\mult(b,a),b) \\
 & = & \mult(b,\next(a))
\end{eqnarray*}$$
for all $b$. By induction, the conclusion holds for all $a,b \in \nats$.
:::::::::::::
:::::::::::::::

$\mult$ distributes over $\plus$.

::: theorem :::
For all $a,b,c \in \nats$, we have the following:

1. $\mult(a,\plus(b,c)) = \plus(\mult(a,b),\mult(a,c))$.
2. $\mult(\plus(a,b),c) = \plus(\mult(a,c),\mult(b,c))$.

::: proof :::
We first show (1) by induction on $a$. For the base case $a = \zero$, we have
$$\begin{eqnarray*}
 &   & \mult(a,\plus(b,c)) \\
 & = & \mult(\zero,\plus(b,c)) \\
 & = & \zero \\
 & = & \plus(\zero,\zero) \\
 & = & \plus(\mult(\zero,b),\mult(\zero,c)) \\
 & = & \plus(\mult(a,b),\mult(a,c))
\end{eqnarray*}$$
as needed. For the inductive step, suppose (1) holds for all $b$ and $c$ for some $a$. Now
$$\begin{eqnarray*}
 &   & \mult(\next(a),\plus(b,c)) \\
 & = & \plus(\mult(a,\plus(b,c)),\plus(b,c)) \\
 & = & \plus(\plus(\mult(a,b),\mult(a,c)),\plus(b,c)) \\
 & = & \plus(\mult(a,b),\plus(\mult(a,c),\plus(b,c))) \\
 & = & \plus(\mult(a,b),\plus(\plus(\mult(a,c),b),c)) \\
 & = & \plus(\mult(a,b),\plus(\plus(b,\mult(a,c)),c)) \\
 & = & \plus(\mult(a,b),\plus(b,\plus(\mult(a,c),c))) \\
 & = & \plus(\plus(\mult(a,b),b),\plus(\mult(a,c),c)) \\
 & = & \plus(\mult(\next(a),b),\plus(\mult(a,c),c)) \\
 & = & \plus(\mult(\next(a),b),\mult(\next(a),c)).
\end{eqnarray*}$$
By induction, (1) holds for all $a,b,c \in \nats$.

To see (2), note that
$$\begin{eqnarray*}
 &   & \mult(\plus(a,b),c) \\
 & = & \mult(c,\plus(a,b)) \\
 & = & \plus(\mult(c,a),\mult(c,b)) \\
 & = & \plus(\mult(c,a),\mult(b,c)) \\
 & = & \plus(\mult(a,c),\mult(b,c))
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::

$\mult$ is associative.

::: theorem :::
For all $a,b,c \in \nats$, we have $$\mult(\mult(a,b),c) = \mult(a,\mult(b,c)).$$

::: proof :::
We also show (2) by induction on $a$. For the base case $a = \zero$ we have
$$\begin{eqnarray*}
 &   & \mult(\mult(a,b),c) \\
 & = & \mult(\mult(\zero,b),c) \\
 & = & \mult(\zero,c) \\
 & = & \zero \\
 & = & \mult(\zero,\mult(b,c))
\end{eqnarray*}$$
as needed. For the inductive step, suppose (2) holds for all $b$ and $c$ for some $a$. Then
$$\begin{eqnarray*}
 &   & \mult(\mult(\next(a),b),c) \\
 & = & \mult(\plus(\mult(a,b),b),c) \\
 & = & \plus(\mult(\mult(a,b),c),\mult(b,c)) \\
 & = & \plus(\mult(a,\mult(b,c)),\mult(b,c)) \\
 & = & \mult(\next(a),\mult(b,c)).
\end{eqnarray*}$$
By induction, the conclusion holds for all $a,b,c \in \nats$.
:::::::::::::
:::::::::::::::

Finally, $\mult$ is almost cancellative.

::: theorem :::
For all $a,b,c \in \nats$ we have the following.

1. If $\mult(\next(a),b) = \mult(\next(a),c)$, then $b = c$.
2. If $\mult(b,\next(a)) = \mult(c,\next(a))$, then $b = c$.

::: proof :::
We will prove (1) using _nested_ induction; first on $b$, then on $c$. Let $B$ be the set of all $b \in \nats$ such that for all $a$ and $c$, if $$\mult(\next(a),b) = \mult(\next(a),c),$$ then $b = c$. We want to show that $B = \nats$ by induction. For the base case $b = \zero$, suppose we have $$\mult(\next(a),b) = \mult(\next(a),c).$$ Now
$$\begin{eqnarray*}
 &   & \zero \\
 & = & \mult(\next(a),\zero) \\
 & = & \mult(\next(a),b) \\
 & = & \mult(\next(a),c).
\end{eqnarray*}$$
As we've [shown](@thm-nat-no-zero-divisors), either $\next(a) = \zero$ or $c = \zero$; however the first case cannot happen, so $c = \zero = b$ as needed.

For the inductive step, suppose we have $b \in \nats$ such that $b \in B$. We now want to show that $\next(b) \in B$. Let $C$ be the set of all natural numbers such that for all $a$, if $$\mult(\next(a),\next(b)) = \mult(\next(a),c),$$ then $\next(b) = c$. We will show that $C = \nats$ by induction on $c$. To that end, for the base case, let $c = \zero$ and suppose we have $$\mult(\next(a),\next(b)) = \mult(\next(a),c).$$ Then we have
$$\begin{eqnarray*}
 &   & \zero \\
 & = & \mult(\next(a),\zero) \\
 & = & \mult(\next(a),c) \\
 & = & \mult(\next(a),\next(b)) \\
 & = & \plus(\mult(a,\next(b)),\next(b)) \\
 & = & \next(\plus(\mult(a,\next(b)),b)).
\end{eqnarray*}$$
However this is not possible, so we have $\zero \in C$ _vacuously_. For the inductive step, suppose we have $c \in C$. Now let $a \in A$, and suppose $$\mult(\next(a),\next(b)) = \mult(\next(a),\next(c)).$$ Now we have
$$\begin{eqnarray*}
 &   & \next(\plus(\plus(\mult(a,c),c),a)) \\
 & = & \next(\plus(\mult(a,c),\plus(c,a))) \\
 & = & \next(\plus(\mult(a,c),\plus(a,c))) \\
 & = & \next(\plus(\plus(\mult(a,c),a),c)) \\
 & = & \next(\plus(\plus(\mult(c,a),a),c)) \\
 & = & \next(\plus(\mult(\next(c),a),c)) \\
 & = & \next(\plus(\mult(a,\next(c)),c)) \\
 & = & \plus(\mult(a,\next(c)),\next(c)) \\
 & = & \mult(\next(a),\next(c)) \\
 & = & \mult(\next(a),\next(b)) \\
 & = & \plus(\mult(a,\next(b)),\next(b)) \\
 & = & \next(\plus(\mult(a,\next(b)),b)) \\
 & = & \next(\plus(\mult(\next(b),a),b)) \\
 & = & \next(\plus(\plus(\mult(b,a),a),b)) \\
 & = & \next(\plus(\plus(\mult(a,b),a),b)) \\
 & = & \next(\plus(\mult(a,b),\plus(a,b))) \\
 & = & \next(\plus(\mult(a,b),\plus(b,a))) \\
 & = & \next(\plus(\plus(\mult(a,b),b),a)).
\end{eqnarray*}$$
(That's a mouthful.) Since $\next$ is injective, we have
$$\begin{eqnarray*}
 &   & \plus(\plus(\mult(a,c),c),a) \\
 & = & \plus(\plus(\mult(a,b),b),a),
\end{eqnarray*}$$
and since $\plus$ is cancellative, we have $$\plus(\mult(a,c),c) = \plus(\mult(a,b),b),$$ and thus
$$\begin{eqnarray*}
 &   & \mult(\next(a),b) \\
 & = & \plus(\mult(a,b),b) \\
 & = & \plus(\mult(a,c),c) \\
 & = & \mult(\next(a),c).
\end{eqnarray*}$$
Since $b \in B$, we have $b = c$, and thus $\next(b) = \next(c)$. Since $a$ was arbitrary, we have $\next(c) \in C$, so $C = \nats$ by induction. Then $\next(b) \in B$, so $B = \nats$ by induction, and so (1) holds for all $a,b,c \in \nats$.

After all that, showing (2) is straightforward. Suppose $a,b,c \in \nats$ such that $$\mult(b,\next(a)) = \mult(c,\next(a)).$$ Then we have
$$\begin{eqnarray*}
 &   & \mult(\next(a),b) \\
 & = & \mult(b,\next(a)) \\
 & = & \mult(c,\next(a)) \\
 & = & \mult(\next(a),c).
\end{eqnarray*}$$
Then $b = c$ as claimed.
:::::::::::::
:::::::::::::::
