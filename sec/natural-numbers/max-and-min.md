---
title: Max and Min
---



Maximum and Minimum
-------------------

The trichotomy property essentially says that any two natural numbers can be put in order, with one being "larger" and the other "smaller". (If the numbers happen to be the same, then "larger" and "smaller" collapse into the same concept.)

We can bundle this intuition into binary operators which single out these larger and smaller numbers.

::: definition :::
We define an operation $\max : \nats \times \nats \rightarrow \nats$ by $$\max(a,b) = \left\{\begin{array}{ll} a & \mathrm{if}\ b \leq a \\ b & \mathrm{otherwise} \end{array}\right.$$ and $\min : \nats \times \nats \rightarrow \nats$ by $$\min(a,b) = \left\{\begin{array}{ll} b & \mathrm{if}\ b \leq a \\ a & \mathrm{otherwise}. \end{array}\right.$$
::::::::::::::::::

First we establish some special cases.

::: theorem :::
Let $a \in \nats$. Then the following hold.

1. $\max(\zero,a) = a$.
2. $\max(a,a) = a$.
3. $\min(\zero,a) = \zero$.
4. $\min(a,a) = a$.

::: proof :::
First we show (1). For all $a \in \nats$ we have $\zero \leq a$, so that $\max(\zero,a) = a$. (2) is similar; we have $a \leq a$ for all $a$ so that $\max(a,a) = a$. This also shows (4), that $\min(a,a) = a$.

Showing (3) is a little more involved; we need to consider two possibilities for $a$. If $a = \zero$, then $a \leq \zero$ and so $\min(\zero,a) = \zero$. If $a = \next(m)$ for some $m$, we have $\next(m) \not\leq \zero$, so that $\min(\zero,a) = \zero$.
:::::::::::::
:::::::::::::::

$\max$ and $\min$ are commutative.

::: theorem :::
For all $a,b \in \nats$, we have the following.

1. $\max(a,b) = \max(b,a)$.
2. $\min(a,b) = \min(b,a)$.

::: proof :::
First we show (1). Let $a,b \in \nats$. By the trichotomy property, we have three possibilities. If $a < b$, then $b \not\leq a$, so $\max(a,b) = b$. Similarly, $a \leq b$, so that $\max(b,a) = b$. If $a = b$, then both $a \leq b$ and $b \leq a$, so that $\max(a,b) = a = \max(b,a)$. If $a > b$, then $b \leq a$, so $\max(a,b) = a$. Similarly, $a \not\leq b$, so $\max(b,a) = a$. In any case we have $\max(a,b) = \max(b,a)$ as claimed.

(2) is proved similarly. Given $a,b \in \nats$, there are three possibilities. If $a < b$, then $b \not\leq a$, so that $\min(a,b) = a$, and $a \leq b$, so that $\min(b,a) = a$. If $a = b$ then both $a \leq b$ and $b \leq a$ so that $\min(a,b) = a = \min(b,a)$. If $a > b$, then $a \not\leq b$, so that $\min(b,a) = b$, and $b \leq a$, so that $\min(a,b) = b$. In any case we have $\min(a,b) = \min(b,a)$.
:::::::::::::
:::::::::::::::

Before going too much further, we establish an alternative characterization of $\min$ that is sometimes useful.

::: theorem :::
Let $a,b \in \nats$. Suppose we have $d \in \nats$ satisfying the following:

1. $d \leq a$ and $d \leq b$.
2. If $c \in \nats$ such that $c \leq a$ and $c \leq b$, then $c \leq d$.

Then $d = \min(a,b)$.

::: proof :::
First we show that $\min(a,b)$ satisfies conditions (1) and (2). Given $a$ and $b$ we consider two possibilities. If $b \leq a$ then $\min(a,b) = b$, and we have $\min(a,b) \leq a$ and $\min(a,b) \leq b$. If $b \not\leq a$ then $a < b$ and $\min(a,b) = a;$ now $\min(a,b) \leq a$ and $\min(a,b) \leq b$. In either case, $\min(a,b)$ satisfies condition (1).

Next we show that $\min(a,b)$ satisfies condition (2). To this end suppose $c \leq a$ and $c \leq b$. By definition, $\min(a,b)$ is equal to either $a$ or $b$, and in either case we have $c \leq \min(a,b)$.

Finally suppose $d \in \nats$ also satisfies (1) and (2). Since $\min(a,b)$ satisfies (1) and $d$ satisfies (2), we have $\min(a,b) \leq d$. But since $d$ also satisfies (1) and $\min(a,b)$ satisfies (2), $d \leq \min(a,b)$. So $d = \min(a,b)$.
:::::::::::::
:::::::::::::::

There is an analogous characterization of $\max$.

::: theorem :::
[@thm-max-lub]()
Let $a,b \in \nats$. Suppose we have $d \in \nats$ satisfying the following:

1. $a \leq d$ and $b \leq d$.
2. If $c \in \nats$ such that $a \leq c$ and $b \leq c$, then $d \leq c$.

Then $d = \max(a,b)$.

::: proof :::
First we show that $\max(a,b)$ satisfies conditions (1) and (2). Given $a$ and $b$ we consider two possibilities. If $b \leq a$, then $\max(a,b) = a$, and we have $a \leq \max(a,b)$ and $b \leq \max(a,b)$. If $b \not\leq a$, then $b > a$ and $\max(a,b) = b;$ now $b \leq \max(a,b)$ and $a \leq \max(b)$. In either case, $a \leq \max(a,b)$ and $b \leq \max(a,b)$.

Next we show that $\max(a,b)$ satisfies condition (2). To this end suppose $a \leq c$ and $b \leq c$. By definition, $\max(a,b)$ is equal to either $a$ or $b$, and in either case we have $\max(a,b) \leq c$.

Finally suppose $d \in \nats$ also satisfies (1) and (2). Since $\max(a,b)$ satisfies (1) and (d) satisfies (2), we have $d \leq \max(a,b)$. But since $d$ also satisfies (1) and $\max(a,b)$ satisfies (2), we have $\max(a,b) \leq d$. So $d = \max(a,b)$.
:::::::::::::
:::::::::::::::

Both $\next$ and $\plus$ distribute over $\min$ and $\max$.

::: theorem :::
Let $a,b,c \in \nats$. Then we have the following.

1. $\next(\max(a,b)) = \max(\next(a),\next(b))$.
2. $\plus(c,\max(a,b)) = \max(\plus(c,a),\plus(c,b))$.
3. $\next(\min(a,b)) = \min(\next(a),\next(b))$.
4. $\plus(c,\min(a,b)) = \min(\plus(c,a),\plus(c,b))$.

::: proof :::
First we show (1). We consider two possibilities. If $b \leq a$, then $\max(a,b) = a$ and $\next(b) \leq \next(a)$, so we have
$$\begin{eqnarray*}
 &   & \max(\next(a),\next(b)) \\
 & = & \next(a) \\
 & = & \next(\max(a,b)).
\end{eqnarray*}$$
If $b \not\leq a$, then $\max(a,b) = b$ and $\next(b) \not\leq \next(a)$, so we have
$$\begin{eqnarray*}
 &   & \max(\next(a),\next(b)) \\
 & = & \next(b) \\
 & = & \next(\max(a,b)).
\end{eqnarray*}$$

Next we show (2). We have two possibilities. If $b \leq a$, then $\max(a,b) = a$ and $\plus(c,b) \leq \plus(c,a)$, so we have
$$\begin{eqnarray*}
 &   & \max(\plus(c,a),\plus(c,b)) \\
 & = & \plus(c,a) \\
 & = & \plus(c,\max(a,b)).
\end{eqnarray*}$$
If $b \not\leq a$, then $\max(a,b) = b$ and $\plus(b,c) \not\leq \plus(a,c)$, so we have
$$\begin{eqnarray*}
 &   & \max(\plus(c,a),\plus(c,b)) \\
 & = & \plus(c,b) \\
 & = & \plus(c,\max(a,b)).
\end{eqnarray*}$$

Proofs of (3) and (4) are similar.
:::::::::::::
:::::::::::::::

$\mult$ also distributes over $\min$ and $\max$.

::: theorem :::
For all $a,b,c \in \nats$ we have the following.

1. $\mult(c,\max(a,b)) = \max(\mult(c,a),\mult(c,b))$.
2. $\mult(c,\min(a,b)) = \min(\mult(c,a),\mult(c,b))$.

::: proof :::
First we show (1). Let $a,b \in \nats$; we have two possibilities. If $b \leq a$ then $\max(a,b) = a$ and also $\mult(c,b) \leq \mult(c,a)$. Now
$$\begin{eqnarray*}
 &   & \max(\mult(c,a),\mult(c,b)) \\
 & = & \mult(c,a) \\
 & = & \mult(c,\max(a,b)).
\end{eqnarray*}$$
Suppose instead that $b \not\leq a$. Then $\mult(c,b) \not\leq \mult(c,a)$, and we have
$$\begin{eqnarray*}
 &   & \max(\mult(c,a),\mult(c,b)) \\
 & = & \mult(c,b) \\
 & = & \mult(c,\max(a,b)).
\end{eqnarray*}$$

The proof for (2) is similar to that for (1).
:::::::::::::
:::::::::::::::

$\min$ and $\max$ are associative.

::: theorem :::
For all $a,b,c \in \nats$ we have the following.

1. $\max(a,\max(b,c)) = \max(\max(a,b),c)$.
2. $\min(a,\min(b,c)) = \min(\min(a,b),c)$.

::: proof :::
First we show (1). To save some pencil inches, let $U = \max(a,\max(b,c))$ and $V = \max(\max(a,b),c)$. We start by showing that $U \leq V$. First note that $$a \leq \max(a,b) \leq V.$$ Similarly, we have $b \leq V$. We also have $c \leq V$; as we've [seen](@thm-max-lub), this implies that $\max(b,c) \leq V$. Using the least upper bound property again, we have $U \leq V$.

Next we show that $V \leq U$. Note that $a \leq U$ and $$b \leq \max(b,c) \leq U;$$ similarly $c \leq U$. Now $\max(a,b) \leq U$, and likewise $V \leq U$. So we have $U = V$ as claimed.

The proof of (2) is analogous.
:::::::::::::
:::::::::::::::

We can expand $\plus$ and $\mult$ in terms of $\min$ and $\max$.

::: theorem :::
For all $a,b \in \nats$ we have the following.

1. $\min(a,b) \leq \max(a,b)$.
2. $\plus(\min(a,b),\max(a,b)) = \plus(a,b)$.
3. $\mult(\min(a,b),\max(a,b)) = \mult(a,b)$.

::: proof :::
First we show (1). Given $a,b \in \nats$, we consider two possibilities. If $b \leq a$, then $$\min(a,b) = b \leq a = \max(a,b)$$ as claimed. If $b \not\leq a$ then $$\min(a,b) = a < b = \max(a,b),$$ so that $\min(a,b) \leq \max(a,b)$ as claimed.

Now we show (2). Given $a,b \in \nats$, we have three possibilities. If $a < b$, we have
$$\begin{eqnarray*}
 &   & \plus(\min(a,b),\max(a,b)) \\
 & = & \plus(a,\max(a,b)) \\
 & = & \plus(a,b)
\end{eqnarray*}$$
as claimed. If $a = b$, we have
$$\begin{eqnarray*}
 &   & \plus(\min(a,b),\max(a,b)) \\
 & = & \plus(b,a) \\
 & = & \plus(a,b)
\end{eqnarray*}$$
as claimed. If $a > b$, we have
$$\begin{eqnarray*}
 &   & \plus(\min(a,b),\max(a,b)) \\
 & = & \plus(b,a) \\
 & = & \plus(a,b)
\end{eqnarray*}$$
as claimed.

The proof for (3) is similar to that for (2).
:::::::::::::
:::::::::::::::

$\min$ and $\max$ distribute over each other from both sides.

::: theorem :::
For all $a,b,c \in \nats$ we have the following.

1. $\max(c,\min(a,b)) = \min(\max(c,a),\max(c,b))$.
2. $\max(\min(a,b),c) = \min(\max(a,c),\max(b,c))$.
3. $\min(c,\max(a,b)) = \max(\min(c,a),\min(c,b))$.
4. $\min(\max(a,b),c) = \max(\min(a,c),\min(b,c))$.

::: proof :::
First we show (1). Note that $$\min(a,b) \leq a \leq \max(c,a)$$ and $c \leq \max(c,a)$, so that $$\max(c,\min(a,b)) \leq \max(c,a).$$ Similarly we have $$\min(a,b) \leq b \leq \max(c,b)$$ and $c \leq \max(c,b)$ so that $$\max(c,\min(a,b)) \leq \max(c,b).$$ Thus $$\max(c,\min(a,b)) \leq \min(\max(c,a),\max(c,b)).$$

Now we consider two possibilities for $\min(a,b)$. First suppose $\min(a,b) = a$. Now $$\max(c,a) \leq \max(c,\min(a,b)),$$ and $$\min(\max(c,a),\max(c,b)) \leq \max(c,a),$$ and because $\leq$ is transitive we have $$\min(\max(c,a),\max(c,b)) \leq \max(c,\min(a,b)).$$ Suppose instead that $\min(a,b) = b$. Now $$\max(c,b) \leq \max(c,\min(a,b)),$$ and $$\min(\max(c,a),\max(c,b)) \leq \max(c,b),$$ and because $\leq$ is transitive we have $$\min(\max(c,a),\max(c,b)) \leq \max(c,(\min(a,b)).$$ In either case we have $$\min(\max(c,a),\max(c,b)) \leq \max(c,(\min(a,b)),$$ and so $$\min(\max(c,a),\max(c,b)) = \max(c,(\min(a,b))$$ as claimed.

(2) follows from (1) because $\max$ is commutative.

The proofs of (3) and (4) are analogous.
:::::::::::::
:::::::::::::::
