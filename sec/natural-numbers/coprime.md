---
title: Coprimality
---



Coprimality
-----------

$\gcd(a,b)$ is in some ways a measure of what $a$ and $b$ have in common. If $a$ and $b$ have "nothing" in common, we say they are _coprime_ (or sometimes _relatively prime_).

::: definition :::
We define a relation $\perp$ on $\nats$ as follows: $$\perp \, = \{ (a,b) \mid \gcd(a,b) = \next(\zero) \}.$$ When $a \perp b$ we say $a$ and $b$ are _coprime_.
::::::::::::::::::

Coprimality has some nice properties, of which we'll prove two for now. The first is a well known result called Euclid's Lemma.

::: theorem :::
(Euclid's Lemma.) Let $a,b,c \in \nats$. If $a \perp b$ and $a | \mult(b,c)$, then $a | c$.

::: proof :::
Suppose $\gcd(a,b) = \next(\zero)$. Then we have
$$\begin{eqnarray*}
 &   & c \\
 & = & \mult(\next(\zero),c) \\
 & = & \mult(\gcd(a,b),c) \\
 & = & \gcd(\mult(a,c),\mult(b,c)).
\end{eqnarray*}$$
Now $a | \mult(a,c)$, and $a | \mult(b,c)$ by our hypothesis. So $$a | \gcd(\mult(a,c),\mult(b,c)) = c$$ by the universal property of greatest common divisors.
:::::::::::::
:::::::::::::::

Next, we show that for any nonzero $a$ and $b$, the quotients obtained by dividing out the greatest common divisor of $a$ and $b$ are coprime.

::: theorem :::
Let a,b,u,v \in \nats$ such that the following hold:

1. $a,b \neq \zero$.
2. $a = \mult(u,\gcd(a,b))$.
3. $b = \mult(v,\gcd(a,b))$.

Then $u \perp v$.

::: proof :::
Let $k = \gcd(u,v)$; say $u = \mult(s,k)$ and $v = \mult(t,v)$. Now
$$\begin{eqnarray*}
 &   & a \\
 & = & \mult(u,\gcd(a,b)) \\
 & = & \mult(\mult(s,k),\gcd(a,b)) \\
 & = & \mult(s,\mult(k,\gcd(a,b))),
\end{eqnarray*}$$
and similarly,
$$\begin{eqnarray*}
 &   & b \\
 & = & \mult(v,\gcd(a,b)) \\
 & = & \mult(\mult(t,k),\gcd(a,b)) \\
 & = & \mult(t,\mult(k,\gcd(a,b))).
\end{eqnarray*}$$
In particular, $\mult(k,\gcd(a,b))$ is a common divisor of $a$ and $b$, so we have $$\mult(k,\gcd(a,b)) | \gcd(a,b) = \mult(\next(\zero),\gcd(a,b)).$$ As we've [shown](@thm-div-mult-cancel), this implies that $k | \next(\zero)$, and so $k = \next(\zero)$ as needed.
:::::::::::::
:::::::::::::::



Least Common Multiple
---------------------

Recall that we defined the concept of greatest common divisor by analogy with $\min$. We can draw a similar analogy to $\max$.

::: definition :::
Let $a$, $b$, and $c$ be natural numbers. We say $c$ is a _common multiple_ of $a$ and $b$ if it is simultaneously a multiple of $a$ and $b$; that is, both $b | c$ and $a | c$.
::::::::::::::::::

Any two numbers have at least one common multiple, since $a$ and $b$ both divide $\mult(a,b)$.

::: definition :::
Let $a,b \in \nats$. Suppose we have $d \in \nats$ satisfying the following.

1. $d$ is a common multiple of $a$ and $b$.
2. If $c$ is a common multiple of $a$ and $b$, then $d | c$.

Then $d$ is called a _least common multiple_ of $a$ and $b$.
::::::::::::::::::

We haven't shown that least common multiples exist yet, but if they do, they are unique.

::: theorem :::
Let $a,b \in \nats$. If we have $u,v \in \nats$ such that both $u$ and $v$ are least common multiples of $a$ and $b$, then $u = v$.

::: proof :::
Because $u$ is a common multiple of $a$ and $b$ and $v$ a least common multiple, we have $v | u$. Similarly, because $v$ is a common multiple and $u$ a least common multiple, $u | v$. Since divisibility is antisymmetric, $u = v$ as claimed.
:::::::::::::
:::::::::::::::

But of course least common multiples do exist, and moreover we can compute them.

::: theorem :::
Let $a,b \in \nats$ and define $\lcm : \nats \times \nats \rightarrow \nats$ by $$\lcm(a,b) = \quo(\mult(a,b),\gcd(a,b)).$$ Then $\lcm(a,b)$ is a least common multiple of $a$ and $b$.

::: proof :::
First we show that $\lcm(a,b)$ is a common multiple of $a$ and $b$. We consider two possibilities. Suppose $\gcd(a,b) = \zero$; then $a = b = \zero$. Now
$$\begin{eqnarray*}
 &   & \lcm(a,b) \\
 & = & \lcm(\zero,\zero) \\
 & = & \quo(\mult(\zero,\zero),\gcd(\zero,\zero)) \\
 & = & \quo(\mult(\zero,\zero),\zero) \\
 & = & \zero,
\end{eqnarray*}$$
and we have $a | \zero$ and $b | \zero$ as needed. Suppose instead that $\gcd(a,b) \neq \zero$. Say $b = \mult(u,\gcd(a,b))$. Now
$$\begin{eqnarray*}
 &   & \lcm(a,b) \\
 & = & \quo(\mult(a,b),\gcd(a,b)) \\
 & = & \quo(\mult(a,\mult(u,\gcd(a,b))),\gcd(a,b)) \\
 & = & \quo(\mult(\mult(a,u),\gcd(a,b)),\gcd(a,b)) \\
 & = & mult(a,u)
\end{eqnarray*}$$
so that $a | \lcm(a,b)$. Similarly, say $a = \mult(v,\gcd(a,b))$. Then
$$\begin{eqnarray*}
 &   & \lcm(a,b) \\
 & = & \quo(\mult(a,b),\gcd(a,b)) \\
 & = & \quo(\mult(\mult(v,\gcd(a,b)),b),\gcd(a,b)) \\
 & = & \quo(\mult(v,\mult(\gcd(a,b),b)),\gcd(a,b)) \\
 & = & \quo(\mult(v,\mult(b,\gcd(a,b))),\gcd(a,b)) \\
 & = & \quo(\mult(\mult(v,b),\gcd(a,b)),\gcd(a,b)) \\
 & = & \mult(v,b),
\end{eqnarray*}$$
so that $b | \lcm(a,b)$. Thus $\lcm(a,b)$ is a common multiple of $a$ and $b$.

Next we show that $\lcm(a,b)$ is a _least_ common multiple. We again consider two possibilities. Suppose first that $\gcd(a,b) = \zero$. Then $a = b = \zero$, and if (for instance) $a | c$ then $c = \zero$ as well, and we have $\lcm(a,b) | c = \zero$.

Now suppose $\gcd(a,b) \neq \zero$. Say we have $c \in \nats$ such that $a | c$ and $b | c$; we need to show that $\lcm(a,b) | c$. To this end, write $c = \mult(a,u)$ and $c = \mult(b,v)$, and write $$a = \mult(h,\gcd(a,b))\ \mathrm{and}\ b = \mult(k,\gcd(a,b))$$ with $h \perp k$. Note that
$$\begin{eqnarray*}
 &   & \mult(\mult(h,u),\gcd(a,b)) \\
 & = & \mult(h,\mult(u,\gcd(a,b))) \\
 & = & \mult(h,\mult(\gcd(a,b),u)) \\
 & = & \mult(\mult(h,\gcd(a,b)),u) \\
 & = & \mult(a,u) \\
 & = & c \\
 & = & \mult(b,v) \\
 & = & \mult(\mult(k,\gcd(a,b)),v) \\
 & = & \mult(k,\mult(\gcd(a,b),v)) \\
 & = & \mult(k,\mult(v,\gcd(a,b))) \\
 & = & \mult(\mult(k,v),\gcd(a,b)).
\end{eqnarray*}$$
Since $\gcd(a,b) \neq \zero$, we have $\mult(h,u) = \mult(k,v)$, and in particular $k | mult(h,u)$. Since $h \perp k$, by Euclid's Lemma we have $k | u$. Now
$$\begin{eqnarray*}
 &   & \lcm(a,b) \\
 & = & \quo(\mult(a,b),\gcd(a,b)) \\
 & = & \quo(\mult(a,\mult(k,\gcd(a,b))),\gcd(a,b)) \\
 & = & \quo(\mult(\mult(a,k),\gcd(a,b)),\gcd(a,b)) \\
 & = & \mult(a,k).
\end{eqnarray*}$$
Because $k | u$ and $\mult$ is compatible with divisibility, we have $$\lcm(a,b) = \mult(a,k) \, | \, \mult(a,u) = c$$ as needed.

Thus $\lcm(a,b)$ is a least common multiple of $a$ and $b$.
:::::::::::::
:::::::::::::::

Now $\lcm$ satisfies lots of properties analogous to $\gcd$.

::: theorem :::
The following hold for all $a,b,c \in \nats$.

1. $\lcm(a,\zero) = \zero$.
2. $\lcm(a,\next(\zero)) = a$.
3. $\lcm(a,a) = a$.
4. $\lcm(a,b) = \lcm(b,a)$.
5. $\lcm(a,\lcm(b,c)) = \lcm(\lcm(a,b),c)$.
6. $\lcm(a,b) = a$ if and only if $b | a$.

::: proof :::
To see (1), note that
$$\begin{eqnarray*}
 &   & \lcm(a,\zero) \\
 & = & \quo(\mult(a,\zero),\gcd(a,\zero)) \\
 & = & \quo(\zero,a) \\
 & = & \zero
\end{eqnarray*}$$
as claimed.

To see (2), note that
$$\begin{eqnarray*}
 &   & \lcm(a,\next(\zero)) \\
 & = & \quo(\mult(a,\next(\zero)),\gcd(a,\next(\zero))) \\
 & = & \quo(a,\next(\zero)) \\
 & = & a
\end{eqnarray*}$$
as claimed.

Next we show (3). We consider two cases. If $a = \zero$, we have
$$\begin{eqnarray*}
 &   & \lcm(a,a) \\
 & = & \lcm(\zero,\zero) \\
 & = & \quo(\mult(\zero,\zero),\gcd(\zero,\zero)) \\
 & = & \quo(\zero,\zero) \\
 & = & \zero \\
 & = & a
\end{eqnarray*}$$
as claimed. If $a \neq \zero$, then
$$\begin{eqnarray*}
 &   & \lcm(a,a) \\
 & = & \quo(\mult(a,a),\gcd(a,a)) \\
 & = & \quo(\mult(a,a),a) \\
 & = & a
\end{eqnarray*}$$
as claimed.

To see (4), note that
$$\begin{eqnarray*}
 &   & \lcm(a,b) \\
 & = & \quo(\mult(a,b),\gcd(a,b)) \\
 & = & \quo(\mult(b,a),\gcd(b,a)) \\
 & = & \lcm(b,a).
\end{eqnarray*}$$

Next we show (5). For brevity, let $u = \lcm(a,\lcm(b,c))$ and $v = \lcm(\lcm(a,b),c)$. First note that $a | u$ and $\lcm(b,c) | u$. Since $b | \lcm(b,c)$ and $c | \lcm(b,c)$, we also have $b | u$ and $c | u$. Since $u$ is a common multiple of $a$ and $b$, we have $\lcm(a,b) | u$, and since $u$ is a common multiple of $\lcm(a,b)$ and $c$, we have $v | u$. Similarly, we have $c | v$ and $\lcm(a,b) | b$, so that $a | v$ and $b | v$, so that $\lcm(b,c) | v$ and thus $u | v$. Now $u = v$ because divisibility is antisymmetric.

Finally we show (6). First suppose $b | a$. Certainly $a$ is a common multiple of $a$ and $b$. Suppose now that $c$ is a common multiple of $a$ and $b$; then $a | c$. By the universal property of least common multiples, we have $a = \lcm(a,b)$. Conversely, suppose we have $\lcm(a,b) = a$; then $a$ is a multiple of $b$ as claimed.
:::::::::::::
:::::::::::::::

Multiplication distributes over $\lcm$.

::: theorem :::
Let $a,b,c \in \nats$. Then we have the following.

1. $\lcm(\mult(c,a),\mult(c,b)) = \mult(c,\lcm(a,b))$.
2. $\lcm(\mult(a,c),\mult(b,c)) = \mult(\lcm(a,b),c)$.

::: proof :::
First we show (1). We consider two cases; first suppose $c = \zero$. Then we have
$$\begin{eqnarray*}
 &   & \lcm(\mult(c,a),\mult(c,b)) \\
 & = & \lcm(\mult(\zero,a),\mult(\zero,b)) \\
 & = & \lcm(\zero,\zero) \\
 & = & \zero \\
 & = & \mult(\zero,\lcm(a,b)) \\
 & = & \mult(c,\lcm(a,b))
\end{eqnarray*}$$
as claimed. Now suppose $c \neq \zero$. Then, noting that $\gcd(a,b) | \mult(a,b)$, we have
$$\begin{eqnarray*}
 &   & \lcm(\mult(c,a),\mult(c,b)) \\
 & = & \quo(\mult(\mult(c,a),\mult(c,b)), \\
 &   & \quad \gcd(\mult(c,a),\mult(c,b))) \\
 & = & \quo(\mult(c,\mult(a,\mult(c,b))),\mult(c,\gcd(a,b))) \\
 & = & \quo(\mult(a,\mult(c,b)),\gcd(a,b)) \\
 & = & \quo(\mult(c,\mult(a,b)),\gcd(a,b)) \\
 & = & \mult(c,\quo(\mult(a,b),\gcd(a,b))) \\
 & = & \mult(c,\lcm(a,b))
\end{eqnarray*}$$
as claimed.

To see (2), note that
$$\begin{eqnarray*}
 &   & \lcm(\mult(a,c),\mult(b,c)) \\
 & = & \lcm(\mult(c,a),\mult(c,b)) \\
 & = & \mult(c,\lcm(a,b)) \\
 & = & \mult(\lcm(a,b),c)
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::

$\lcm$ is compatible with divisibility.

::: theorem :::
Let $a,b,c \in \nats$. If $a | b$, then $\lcm(a,c) | \lcm(b,c)$.

::: proof :::
Suppose $a | b$. Then we have
$$\begin{eqnarray*}
 &   & \lcm(\lcm(a,c),\lcm(b,c)) \\
 & = & \lcm(a,\lcm(c,\lcm(b,c))) \\
 & = & \lcm(a,\lcm(\lcm(c,b),c)) \\
 & = & \lcm(a,\lcm(\lcm(b,c),c)) \\
 & = & \lcm(a,\lcm(b,\lcm(c,c))) \\
 & = & \lcm(\lcm(a,b),\lcm(c,c)) \\
 & = & \lcm(b,c)
\end{eqnarray*}$$
so that $\lcm(a,c) | \lcm(b,c)$ as claimed.
:::::::::::::
:::::::::::::::

Finally, $\lcm$ and $\gcd$ distribute over each other.

::: theorem :::
Let $a,b,c \in \nats$. Then we have the following.

1. $\gcd(c,\lcm(a,b)) = \lcm(\gcd(c,a),\gcd(c,b))$.
2. $\lcm(c,\gcd(a,b)) = \gcd(\lcm(c,a),\lcm(c,b))$.

::: proof :::
First we show (1). First suppose $c = \zero$. Then
$$\begin{eqnarray*}
 &   & \gcd(c,\lcm(a,b)) \\
 & = & \gcd(\zero,\lcm(a,b)) \\
 & = & \lcm(a,b) \\
 & = & \lcm(\gcd(\zero,a),\gcd(\zero,b)) \\
 & = & \lcm(\gcd(c,a),\gcd(c,b)
\end{eqnarray*}$$
as claimed. Now suppose $a = \zero$. Then
$$\begin{eqnarray*}
 &   & \gcd(c,\lcm(a,b)) \\
 & = & \gcd(c,\lcm(\zero,b)) \\
 & = & \gcd(c,\zero) \\
 & = & c \\
 & = & \lcm(c,\gcd(c,b)) \\
 & = & \lcm(\gcd(c,\zero),\gcd(c,b)) \\
 & = & \lcm(\gcd(c,a),\gcd(c,b))
\end{eqnarray*}$$
as claimed. Now suppose $b = \zero$. Then
$$\begin{eqnarray*}
 &   & \gcd(c,\lcm(a,b)) \\
 & = & \gcd(c,\lcm(a,\zero)) \\
 & = & \gcd(c,\zero) \\
 & = & c \\
 & = & \lcm(\gcd(c,a),c) \\
 & = & \lcm(\gcd(c,a),\gcd(c,\zero)) \\
 & = & \lcm(\gcd(c,a),\gcd(c,b))
\end{eqnarray*}$$
as claimed.

We can now assume that $a$, $b$, and $c$ are all nonzero. In the next equation chain, for the sake of readability we're going to make two concessions of notation. First, we write $\mult(x,y)$ by juxtaposition as $xy$, which we're used to anyway but have been avoiding. Second, since both multiplication and $\gcd$ are associative we can write, for instance, $xyz$ rather than $(xy)z$ without ambiguity. Using this notation, we have
$$\begin{eqnarray*}
 &   & \gcd(c \cdot \gcd(a,b), ab) \cdot \gcd(c,a,b) \\
 & = & \gcd(\gcd(ca, cb), ab) \cdot \gcd(c,a,b) \\
 & = & \gcd(ca, cb, ab) \cdot \gcd(c,a,b) \\
 & = & \gcd(ca \cdot \gcd(c,a,b), cb \cdot \gcd(c,a,b), ab \cdot \gcd(c,a,b)) \\
 & = & \gcd(cac, caa, cab, cbc, cba, cbb, abc, aba, abb) \\
 & = & \gcd(cca, cba, aca, aba, ccb, cbb, acb, abb) \\
 & = & \gcd(\gcd(cc, cb, ac, ab) \cdot a, \gcd(cc, cb, ac, ab) \cdot b) \\
 & = & \gcd(cc, cb, ac, ab) \cdot \gcd(a,b) \\
 & = & \gcd(c \cdot \gcd(c,b), a \cdot \gcd(c,b)) \cdot \gcd(a,b) \\
 & = & \gcd(c,a) \cdot \gcd(c,b) \cdot \gcd(a,b).
\end{eqnarray*}$$
Now $\gcd(c,a,b) \neq \zero$ and $\gcd(a,b) \neq \zero$. By the [cross multiplication theorem](@thm-nat-cross-mult), we have
$$\begin{eqnarray*}
 &   & \quo(\gcd(c \cdot \gcd(a,b), ab),\gcd(a,b)) \\
 & = & \quo(\gcd(c,a) \cdot \gcd(c,b),\gcd(a,b,c)).
\end{eqnarray*}$$
Note also that
$$\begin{eqnarray*}
 &   & \gcd(a,b,c) \\
 & = & \gcd(c,a,b) \\
 & = & \gcd(c,a,c,b) \\
 & = & \gcd(\gcd(c,a),\gcd(c,b)).
\end{eqnarray*}$$
Now we have
$$\begin{eqnarray*}
 & = & \gcd(c,\lcm(a,b)) \\
 & = & \gcd(\quo(c \cdot \gcd(a,b),\gcd(a,b)),\quo(ab,\gcd(a,b))) \\
 & = & \quo(\gcd(c \cdot \gcd(a,b), ab),\gcd(a,b)) \\
 & = & \quo(\gcd(c,a) \cdot \gcd(c,b),\gcd(a,b,c)) \\
 & = & \quo(\gcd(c,a), \cdot \gcd(c,b),\gcd(\gcd(c,a),\gcd(c,b))) \\
 & = & \lcm(\gcd(c,a),\gcd(c,b))
\end{eqnarray*}$$
as claimed.

Next we show (2). First suppose $c = \zero$. Then
$$\begin{eqnarray*}
 &   & \lcm(c,\gcd(a,b)) \\
 & = & \lcm(\zero,\gcd(a,b)) \\
 & = & \zero \\
 & = & \gcd(\zero,\zero) \\
 & = & \gcd(\lcm(\zero,a),\lcm(\zero,b)) \\
 & = & \gcd(\lcm(c,a),\lcm(c,b))
\end{eqnarray*}$$
as claimed. Now suppose $a = \zero$. Then
$$\begin{eqnarray*}
 &   & \lcm(c,\gcd(a,b)) \\
 & = & \lcm(c,\gcd(\zero,b)) \\
 & = & \lcm(c,b) \\
 & = & \gcd(\zero,\lcm(c,b)) \\
 & = & \gcd(\lcm(c,\zero),\lcm(c,b)) \\
 & = & \gcd(\lcm(a,c),\lcm(c,b))
\end{eqnarray*}$$
as claimed. Now suppose $b = \zero$. Then
$$\begin{eqnarray*}
 &   & \lcm(c,\gcd(a,b)) \\
 & = & \lcm(c,\gcd(a,\zero)) \\
 & = & \lcm(c,a) \\
 & = & \gcd(\lcm(c,a),\zero) \\
 & = & \gcd(\lcm(c,a),\lcm(c,\zero)) \\
 & = & \gcd(\lcm(c,a),\lcm(c,b))
\end{eqnarray*}$$
as claimed.

We can now assume that $a$, $b$, and $c$ are all nonzero. Note that
$$\begin{eqnarray*}
 &   & \gcd(ca,cb) \cdot \gcd(cc,cb,ac,ab) \\
 & = & \gcd(ca \cdot \gcd(cc,cb,ac,ab), cb \cdot \gcd(cc,cb,ac,ab)) \\
 & = & \gcd(cacc,cacb,caac,caab,cbcc,cbcb,cbac,cbab) \\
 & = & \gcd(cacc,caca,cacb,cabc,caba,cabb, \\
 &   & \quad cbcc,cbca,cbcb,cbac,cbaa,cbab) \\
 & = & \gcd(cac \cdot \gcd(c,a,b), cab \cdot \gcd(c,a,b), \\
 &   & \quad cbc \cdot \gcd(c,a,b), cba \cdot \gcd(c,a,b)) \\
 & = & \gcd(cac,cab,cbc,cba) \cdot \gcd(c,a,b).
\end{eqnarray*}$$
Then using the cross multiplication theorem again we have
$$\begin{eqnarray*}
 &   & \lcm(c,\gcd(a,b)) \\
 & = & \quo(c \cdot \gcd(a,b),\gcd(c,\gcd(a,b))) \\
 & = & \quo(\gcd(ca,cb),\gcd(c,a,b)) \\
 & = & \quo(\gcd(cac,cab,cbc,cba), \\
 &   & \quad \gcd(cc,cb,ac,ab)) \\
 & = & \quo(\gcd(gcd(cac,cab),\gcd(cbc,cba)), \\
 &   & \quad \gcd(c \cdot \gcd(c,b), a \cdot \gcd(c,b))) \\
 & = & \quo(\gcd(ca \cdot \gcd(c,b),cb \cdot \gcd(c,a)), \\
 &   & \quad \gcd(c,a) \cdot \gcd(c,b)) \\
 & = & \gcd(\quo(ca \cdot \gcd(c,b),\gcd(c,a) \cdot \gcd(c,b)), \\
 &   & \quad \quo(cb \cdot \gcd(c,a),\gcd(c,a) \cdot \gcd(c,b))) \\
 & = & \gcd(\quo(ca,\gcd(c,a)),\quo(cb,\gcd(c,b))) \\
 & = & \gcd(\lcm(c,a),\lcm(c,b))
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::
