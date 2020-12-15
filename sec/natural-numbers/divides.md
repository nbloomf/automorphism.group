---
title: Divisibility
---



Divisibility
------------

Recall that we said $<$ is an _additive_ order relation on natural numbers because it is defined in terms of $\plus$. There is an analogous relation defined in terms of $\mult$ called _divisibility_.

::: definition :::
Given $a,b \in \nats$, we say $a | b$, pronounced $a$ _divides_ $b$, if there exists a $c \in \nats$ such that $\mult(a,c) = b$.
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
Let $a,b,c,d \in \nats$. Then we have the following.

1. $a | \mult(a,b)$.
2. If $c \neq \zero$, $\mult(a,b) = \mult(c,d)$, and $c|a$, then $b|d$.
3. If $c|a$ and $c|b$, then $c | \plus(a,b)$.
4. If $b \neq \zero$ and $a|b$, then $a \leq b$.

::: proof :::
To see (1), note that $\mult(a,b) = \times(a,b)$.

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
