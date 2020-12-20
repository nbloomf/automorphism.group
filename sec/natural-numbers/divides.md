---
title: Divisibility
---



Divisibility
------------

Recall that we said $<$ is an _additive_ order relation on natural numbers because it is defined in terms of $\plus$. There is an analogous relation defined in terms of $\mult$ called _divisibility_.

::: definition :::
Given $a,b \in \nats$, we say $a | b$, pronounced $a$ _divides_ $b$, if there exists a $c \in \nats$ such that $\mult(a,c) = b$. If $a$ divides $b$ we say $a$ is a _divisor_ of $b$.
::::::::::::::::::

We start with some basic examples.

::: theorem :::
Let $a \in \nats$. Then we have the following.

1. $a | \zero$.
2. If $\zero | a$, then $a = \zero$.
3. $\next(\zero) | a$.
4. If $a | \next(\zero)$, then $a = \next(\zero)$.

::: proof :::
To see (1), note that $\mult(a,\zero) = \zero$. To see (2), note that if $\zero | a$ then by definition we have $c \in \nats$ such that $$a = \mult(\zero,c) = \zero.$$ To see (3), note that $\mult(a,\next(\zero)) = a$. To see (4), note that we've shown if $\mult(a,c) = \next(\zero)$ then $a = c = \next(\zero)$.
:::::::::::::
:::::::::::::::

Divisibility on natural numbers is reflexive, antisymmetric, and transitive.

::: theorem :::
[@thm-nat-divides-reflexive]()[@thm-nat-divides-antisymmetric]()[@thm-nat-divides-transitive]()
Let $a,b,c \in \nats$. Then we have the following.

1. $a | a$.
2. If $a | b$ and $b | a$, then $a = b$.
3. If $a | b$ and $b | c$, then $a | c$.

::: proof :::
To see (1), note that $a = \mult(a,\next(\zero))$.

Suppose $a|b$ and $b|a$. By definition, we have $m,n \in \nats$ such that $\mult(a,m) = b$ and $\mult(b,n) = a$. Then
$$\begin{eqnarray*}
 &   & \mult(a,\mult(m,n)) \\
 & = & \mult(\mult(a,m),n) \\
 & = & \mult(b,n) \\
 & = & a,
\end{eqnarray*}$$
so we have $m = n = \next(\zero)$. But then $$a = \mult(b,\next(\zero)) = b$$ as claimed.

Suppose $a|b$ and $b|c$; by definition we have $m,n \in \nats$ such that $\mult(a,m) = b$ and $\mult(b,n) = c$. Now
$$\begin{eqnarray*}
 &   & \mult(a,\mult(m,n)) \\
 & = & \mult(\mult(a,m),n) \\
 & = & \mult(b,n) \\
 & = & c,
\end{eqnarray*}$$
so $a|c$, as claimed.
:::::::::::::
:::::::::::::::

The next theorem is a grab bag of results linking divisibility with the rest of our arithmetic so far.

::: theorem :::
[@thm-nat-div-plus]()
Let $a,b,c,d \in \nats$. Then we have the following.

1. $a | \mult(a,b)$.
2. If $c \neq \zero$, $\mult(a,b) = \mult(c,d)$, and $c|a$, then $b|d$.
3. If $c|a$ and $c|b$, then $c | \plus(a,b)$.
4. If $b \neq \zero$ and $a|b$, then $a \leq b$.

::: proof :::
To see (1), note that $\mult(a,b) = \mult(a,b)$.

To see (2), say $a = \mult(c,u)$. Now
$$\begin{eqnarray*}
 &   & \mult(c,d) \\
 & = & \mult(a,b) \\
 & = & \mult(\mult(c,u),b) \\
 & = & \mult(c,\mult(u,b)).
\end{eqnarray*}$$
Since $c \neq \zero$ and $\mult$ is (almost) cancellative, we have $d = \mult(u,b)$, and thus $b | d$ as claimed.

Next we show (3). Say $a = \mult(c,h)$ and $b = \mult(c,k)$. Using distributivity, we have
$$\begin{eqnarray*}
 &   & \plus(a,b) \\
 & = & \plus(\mult(c,h),\mult(c,k)) \\
 &= & \mult(c,\plus(h,k))
\end{eqnarray*}$$
so that $c | \plus(a,b)$ as claimed.

Next we show (4). Say $b = \mult(a,k)$. Since $b \neq \zero$, we must also have $k \neq \zero$; say $k = \next(m)$. Now
$$\begin{eqnarray*}
 &   & b \\
 & = & \mult(k,a) \\
 & = & \mult(\next(m),a) \\
 & = & \plus(\mult(m,a),a),
\end{eqnarray*}$$
so that $a \leq b$.
:::::::::::::
:::::::::::::::

We'll eventually be able to say a lot more interesting stuff using divisibility, but we need some more tools first.

With our order relations, an interesting problem is how to demonstrate that they are or are not satisfied. To show that $a < b$, for instance, it's enough to exhibit a specific $c$ such that $\plus(a,\next(c)) = b$. Thanks to the trichotomy theorem, we can similarly show that $a \not\lt b$ by exhibiting a specific $c$ such that $\plus(b,c) = a$. In these problems, we might call $c$ a _witness_ to the ordering of $a$ and $b$.

The divides relation is similarly easy to prove in the positive; to show that $a|b$ it's enough to find $c$ such that $\mult(a,c) = b$. There is no analog of the trichotomy property for divisibility, however we can still prove a "witness theorem" giving a shortcut for showing that one number _doesn't_ divide another.

::: theorem :::
Let $a,b \in \nats$ with $b \neq \zero$. If there exists an $m \in \nats$ such that $\mult(a,m) < b$ and $b < \mult(a,\next(m))$, then $a \not\vert b$.

::: proof :::
Suppose we have $n \in \nats$ such that $\mult(a,n) = b$. In particular, we must have $a \neq \zero$ since $b \neq \zero$. Now $$\mult(a,m) < \mult(a,n),$$ and since $a \neq \zero$ we have $m < n$. Similarly, $$\mult(a,n) < \mult(a,\next(m))$$ so that $n < \next(m)$. However, we've shown that this is not possible, so no such $n$ exists. Thus $a \not\vert b$.
:::::::::::::
:::::::::::::::
