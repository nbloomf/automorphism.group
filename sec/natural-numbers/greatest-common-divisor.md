---
title: Greatest Common Divisor
---



Divisors and Common Divisors
----------------------------

We've defined two _arithmetic_ orders on natural numbers, which have very similar characterizations: $\leq$ and $|$. We were also able to turn $\leq$ into two _operations_ on $\nats$, specifically, $\min$ and $\max$. There's an analogous way to turn divisibility into an operator, which we'll explore in this section. We need a definition first.

::: definition :::
Let $a$, $b$, and $c$ be natural numbers. We say $c$ is a _common divisor_ of $a$ and $b$ if it is simultaneously a divisor of $a$ and $b$; that is, both $c | a$ and $c | b$.
::::::::::::::::::

Given two numbers $a$ and $b$, there is always at least one common divisor because $\next(\zero) |a$ and $\next(\zero) | b$. In some sense $\next(\zero)$ is the "least" common divisor of any two natural numbers because, given any other common divisor $c$, we have $\next(\zero) | c$. Turning this around, we can define greatest common divisors as follows.

::: definition :::
Let $a$ and $b$ be natural numbers. Suppose we have $d \in \nats$ satisfying the following.

1. $d$ is a common divisor of $a$ and $b$.
2. If $c$ is a common divisor of $a$ and $b$, then $c | d$.

Then $d$ is called a _greatest common divisor_ of $a$ and $b$.
::::::::::::::::::

Note that this definition doesn't say anything about whether such a $d$ _exists_; a priori it could be that two specific numbers don't have a greatest common divisor. (We will see that they do.) However, from the definition we can show that _if_ a greatest common divisor exists, then it is unique.

::: theorem :::
Let $a,b \in \nats$. If we have $u,v \in \nats$ such that both $u$ and $v$ are greatest common divisors of $a$ and $b$, then $u = v$.

::: proof :::
Because $u$ is a common divisor of $a$ and $b$ and $v$ is a greatest common divisor, we have $u | v$. Similarly, because $v$ is a common divisor and $u$ a greatest common divisor, $v | u$. As we've [shown](@thm-nat-divides-antisymmetric), we then have $u = v$ as claimed.
:::::::::::::
:::::::::::::::

It's not obvious from the definition (to me anyway) that any two given natural numbers should have a greatest common divisor; but as we'll show, they do.



Greatest Common Divisors
------------------------

We're going to define a function $f : \nats \times \nats \rightarrow \nats$ with the property that $f(a,b)$ is a greatest common divisor of $a$ and $b$; we'll define this $f$ by iterative norm recursion. With that in mind, we need an iterative norm.

::: theorem :::
Define $\varphi : \nats \times \nats \rightarrow \nats \times \nats$ by $$\varphi(a,b) = \left\{\begin{array}{ll} (a,\zero) & \mathrm{if}\ b = \zero \\ (b,\rem(a,b)) & \mathrm{otherwise}, \end{array}\right.$$ and $\eta : \nats \times \nats \rightarrow \nats$ given by $\eta(a,b) = b$. Then $\eta$ is an iterative norm on $\langle \nats \times \nats, (\zero,\zero), \varphi \rangle$.

::: proof :::
Suppose $\eta(a,b) = \zero$; we need to show that $\eta(\varphi(a,b)) = \zero$. Note that $b = \eta(a,b) = \zero$, and we have $$\eta(\varphi(a,b)) = \eta(\varphi(a,\zero)) = \eta(a,\zero) = \zero$$ as needed.

Now suppose $\eta(a,b) = \next(m)$ for some $m$; we thus have $b = \eta(a,b) = \next(m)$. In particular $b \neq \zero$, so that $\varphi(a,b) = (b,\rem(a,b))$ and $\rem(a,b) < b$. We now have two possibilities for $\rem(a,b)$. If $\rem(a,b) = \zero$, then
$$\begin{eqnarray*}
 &      & \eta(\varphi(a,b)) \\
 & =    & \eta(b,\rem(a,b)) \\
 & =    & \eta(b,\zero) \\
 & =    & \zero \\
 & \leq & m.
\end{eqnarray*}$$
Suppose $\rem(a,b) = \next(u)$ for some $u$. Becuase $$\rem(a,b) < b = \next(m),$$ we have $\rem(a,b) \leq m$. Then
$$\begin{eqnarray*}
 &      & \eta(\varphi(a,b)) \\
 & =    & \eta(b,\rem(a,b)) \\
 & =    & \rem(a,b) \\
 & \leq & m.
\end{eqnarray*}$$
In either case, if $\eta(a,b) = \next(m)$ then $\eta(\varphi(a,b)) \leq m$. So $\eta$ is an iterative norm.
:::::::::::::
:::::::::::::::

We can now define the $\gcd$ function.

::: definition :::
Let $\varphi$ and $\eta$ be as defined in the previous theorem. Define a map $\gcd : \nats \times \nats \rightarrow \nats$ by $$\gcd = \normrec_{\varphi,\eta,\pi_1},$$ where $\pi_1 : \nats \times \nats \rightarrow \nats$ is the first coordinate projection.
::::::::::::::::::

First, we compute some special cases.

::: theorem :::
For all $a,b \in \nats$ we have the following.

1. $\gcd(a,\zero) = a$.
2. $\gcd(\zero,a) = a$.
3. $\gcd(a,\next(b)) = \gcd(\next(b),\rem(a,\next(b)))$.

::: proof :::
To see (1), note that $\eta(a,\zero) = \zero$, so that
$$\begin{eqnarray*}
 &   & \gcd(a,\zero) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(a,\zero) \\
 & = & \pi_1(a,\zero) \\
 & = & a
\end{eqnarray*}$$
as claimed. To see (2) we consider two possibilities. If $a = \zero$, then $$\gcd(\zero,a) = \gcd(\zero,\zero) = \zero = a$$ by (1). Suppose instead that $a = \next(m)$ for some $m$. Note that $\eta(\zero,a) = a \neq \zero$ and $\rem(\zero,a) = \zero$. Then we have
$$\begin{eqnarray*}
 &   & \gcd(\zero,a) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(\zero,a) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(a,\rem(\zero,a)) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(a,\zero) \\
 & = & \pi_1(a,\zero) \\
 & = & a
\end{eqnarray*}$$
as claimed.

To see (3), note that $\eta(a,\next(b)) = \next(b) \neq \zero$. So we have
$$\begin{eqnarray*}
 &   & \gcd(a,\next(b)) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(a,\next(b)) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(\varphi(a,\next(b))) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(\next(b),\rem(a,\next(b))) \\
 & = & \gcd(\next(b),\rem(a,\next(b)))
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::

Of course defining $\gcd$ is one thing, but showing that it yields greatest common divisors is another. We'll do that now.

::: theorem :::
For all $a,b \in \nats$, $\gcd(a,b)$ is a greatest common divisor of $a$ and $b$. That is, we have the following.

1. $\gcd(a,b) | a$ and $\gcd(a,b) | b$.
2. If $c \in \nats$ such that $c | a$ and $c | b$, then $c | \gcd(a,b)$.

::: proof :::
First we show (1), proceeding by strong induction on $b$. For the base case $b = \zero$, note that $$\gcd(a,b) = \gcd(a,\zero) = a,$$ and we have $a | a$ and $a | \zero$. So if $b = \zero$ then $\gcd(a,b)$ is a common divisor of $a$ and $b$.

For the inductive step, suppose that for some $m$, whenever $b \leq m$, $\gcd(a,b)$ is a common divisor of $a$ and $b$. We now consider $\gcd(a,\next(m))$. In this case we have $\eta(a,\next(m)) \neq \zero$, so that
$$\begin{eqnarray*}
 &   & \gcd(a,\next(m)) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(a,\next(m)) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(\varphi(a,\next(m))) \\
 & = & \normrec_{\varphi,\eta,\pi_1}(\next(m),\rem(a,\next(m))) \\
 & = & \gcd(\next(m),\rem(a,\next(m))).
\end{eqnarray*}$$
By the strong induction hypothesis, since $\rem(a,\next(m)) \leq m$, $\gcd(a,\next(m))$ is a common divisor of $\next(m)$ and $\rem(a,\next(m))$. Since divisibility is transitive, $\gcd(a,\next(m))$ also divides $\mult(\quo(a,\next(m)),\next(m))$, and so as we've [shown](@thm-nat-div-plus), $\gcd(a,\next(m))$ must also divide $$\plus(\mult(\quo(a,\next(m)),\next(m)),\rem(a,\next(m))) = a.$$ So $\gcd(a,\next(m))$ is a common divisor of $a$ and $\next(m)$, as needed. By strong induction $\gcd(a,b)$ is a common divisor of $a$ and $b$ for all $a$ and $b$.

Now we show (2), again proceeding by strong induction on $b$. For the base case $b = \zero$, suppose we have $c$ a common divisor of $a$ and $b$. Now $$\gcd(a,b) = \gcd(a,\zero) = a$$ and $c | a = \gcd(a,b)$ as needed. For the inductive step, suppose that for some $m$, if $b \leq m$ then $\gcd(a,b)$ is a greatest common divisor of $a$ and $b$ for all $a$. We now consider $b = \next(m)$.  Suppose $c$ is a common divisor of $a$ and $\next(m)$. Now $$a = \plus(\mult(\quo(a,\next(m)),\next(m)),\rem(a,\next(m))),$$ so that, as we've [shown](@thm-div-sum), $c$ divides $\rem(a,\next(m))$. Note that $\gcd(a,\next(m)) = \gcd(\next(m),\rem(a,\next(m)))$. Using the strong induction hypothesis, $$c | \gcd(\next(m),\rem(a,\next(m))),$$ and so $c | \gcd(a,b)$ as needed. By strong induction, (2) holds for all $a$ and $b$.

Combining (1) and (2), $\gcd(a,b)$ is a greatest common divisor of $a$ and $b$ for all $a,b \in \nats$ as claimed.
:::::::::::::
:::::::::::::::

The uniqueness property of greatest common divisors makes it possible to prove things about $\gcd$ without digging into the definition.

::: theorem :::
We have the following for all $a,b \in \nats$.

1. $\gcd(a,a) = a$.
2. $\gcd(a,b) = \gcd(b,a)$.
3. $\gcd(a,\next(\zero)) = \next(\zero)$.
4. If $\gcd(a,b) = \zero$, then $a = b = \zero$.

::: proof :::
To see (1), suppose $c$ is a common divisor of $a$ and $a$ (just go with it). Then $c$ divides $a$. Since $a|a$, $a$ is a greatest common divisor of $a$ and $a$, and $since greatest common divisors are unique, $\gcd(a,a) = a$.

To see (2), note that since $\gcd(a,b)$ is a common divisor of $b$ and $a$, we have $\gcd(a,b) | \gcd(b,a)$; similarly $\gcd(b,a) | \gcd(a,b)$, and so $\gcd(a,b) = \gcd(b,a)$.

To see (3), suppose $c$ is a common divisor of $a$ and $\next(\zero)$. We've [seen](@thm-times-eq-one) that the only divisor of $\next(\zero)$ is $\next(\zero)$, so $c = \next(\zero)$. Of course $\next(\zero)$ is itself a common divisor of $a$ and $\next(\zero)$, so $\gcd(a,\next(\zero)) = \next(\zero)$ by the uniqueness property of greatest common divisors.

To see (4), note that if $\zero | a$ then $a = \zero$; similarly $b = \zero$.
:::::::::::::
:::::::::::::::

Greatest common divisors detect divisibility.

::: theorem :::
Let $a,b \in \nats$. Then $\gcd(a,b) = a$ if and only if $a|b$.

::: proof :::
If $\gcd(a,b) = a$, then as a common divisor of $a$ and $b$ we have $a|b$. Conversely, suppose $a|b$. Now $a|a$ and $a|b$, so $a|\gcd(a,b)$, and again as a common divisor of $a$ and $b$ we have $\gcd(a,b)|a$. So $\gcd(a,b) = a$.
:::::::::::::
:::::::::::::::

As an operation, $\gcd$ is associative.

::: theorem :::
For all $a,b,c \in \nats$, we have $$\gcd(a,\gcd(b,c)) = \gcd(\gcd(a,b),c).$$

::: proof :::
For brevity, let $u = \gcd(a,\gcd(b,c))$ and $v = \gcd(\gcd(a,b),c)$. Note that $u | a$ and $u | \gcd(b,c)$, and since $\gcd(b,c)$ is a common divisor of $b$ and $c$, $u | b$ and $u | c$. Now $u | \gcd(a,b)$ and $u | c$, so $u | v$. Similarly, $v | \gcd(a,b)$ and $v | c$, and since $\gcd(a,b)$ is a common divisor of $a$ and $b$, $v | a$ and $v | b$. So $v | \gcd(b,c)$, and then $v | u$. So $u = v$ as claimed.
:::::::::::::
:::::::::::::::

As an operation, $\gcd$ distributes over $\mult$ in both directions.

::: theorem :::
Let $a,b,c \in \nats$. Then we have the following.

1. $\gcd(\mult(a,c),\mult(b,c)) = \mult(\gcd(a,b),c)$.
2. $\gcd(\mult(c,a),\mult(c,b)) = \mult(c,\gcd(a,b))$.

::: proof :::
First we show (1). We consider two possibilities. If $c = \zero$, then
$$\begin{eqnarray*}
 &   & \mult(\gcd(a,b),c) \\
 & = & \mult(\gcd(a,b),\zero) \\
 & = & \zero \\
 & = & \gcd(\zero,\zero) \\
 & = & \gcd(\mult(a,\zero),\mult(b,\zero)) \\
 & = & \gcd(\mult(a,c),\mult(b,c))
\end{eqnarray*}$$
as claimed. Suppose instead that $c \neq \zero$. Because $\gcd(a,b) | a$, we have $$\mult(\gcd(a,b),c) | \mult(a,c).$$ Similarly, as $\gcd(a,b) | b$, we have $$\mult(\gcd(a,b),c) | \mult(b,c).$$ Thus $$\mult(\gcd(a,c),\gcd(b,c)) | \gcd(\mult(a,c),\mult(b,c)).$$

Now note that $c | \mult(a,c)$ and $c | \mult(b,c)$, so that $$c | \gcd(\mult(a,c),\mult(b,c)).$$ Let $u$ be such that $$\mult(c,u) = \gcd(\mult(a,c),\mult(b,c)).$$ Then $\mult(u,c) | \mult(a,c)$, and (because $c \neq \zero$) $u | a$. Likewise we have $\mult(u,c) | \mult(b,c)$ and so $u | b$. Thus $u | \gcd(a,b)$, and we have $$\mult(u,c) | \mult(\gcd(a,b),c).$$ Thus $$\gcd(\mult(a,c),\mult(b,c)) | \mult(\gcd(a,b),c).$$ Since divisibility on natural numbers is antisymmetric, we have $$\gcd(\mult(a,c),\mult(b,c)) = \mult(\gcd(a,b),c)$$ for $c \neq \zero$, and thus for all $c$.

To see (2), note that
$$\begin{eqnarray*}
 &   & \gcd(\mult(c,a),\mult(c,b)) \\
 & = & \gcd(\mult(a,c),\mult(b,c)) \\
 & = & \mult(\gcd(a,b),c) \\
 & = & \mult(c,\gcd(a,b))
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::

As an operation, $\gcd$ is compatible with divisibility.

::: theorem :::
For all $a,b,c \in \nats$, if $a|b$ then $\gcd(a,c) | \gcd(b,c)$.

::: proof :::
Since $a | b$, we have $\gcd(a,b) = a$. Now
$$\begin{eqnarray*}
 &   & \gcd(\gcd(a,c),\gcd(b,c)) \\
 & = & \gcd(\gcd(\gcd(a,c),b),c) \\
 & = & \gcd(\gcd(a,\gcd(c,b)),c) \\
 & = & \gcd(\gcd(a,\gcd(b,c)),c) \\
 & = & \gcd(\gcd(\gcd(a,b),c),c) \\
 & = & \gcd(\gcd(a,b),\gcd(c,c)) \\
 & = & \gcd(a,c),
\end{eqnarray*}$$
and thus $\gcd(a,c) | \gcd(b,c)$ as claimed.
:::::::::::::
:::::::::::::::

$\gcd$ interacts with quotients.

::: theorem :::
Let $a,b,c \in \nats$ with $c|a$, $c|b$, and $c \neq \zero$. Then $$\quo(\gcd(a,b),c) = \gcd(\quo(a,c),\quo(b,c)).$$

::: proof :::
Write $a = \mult(u,c)$ and $b = \mult(v,c)$. Now
$$\begin{eqnarray*}
 &   & \quo(\gcd(a,b),c) \\
 & = & \quo(\gcd(\mult(u,c),\mult(v,c)),c) \\
 & = & \quo(\mult(\gcd(u,v),c),c) \\
 & = & \gcd(u,v) \\
 & = & \gcd(\quo(a,c),\quo(b,c))
\end{eqnarray*}$$
as claimed.
:::::::::::::
:::::::::::::::
