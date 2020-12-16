---
title: The Division Algorithm
---



The Division Algorithm
----------------------

Finally we come to the first power tool for the natural numbers: the division algorithm. This theorem states that for any $a$ and $b$ with $b$ not zero, there exist $q$ and $r$ such that $a = qb + r$ and $r$ is not "too big". This $q$ is called the _quotient_ and $r$ the _remainder_.

The division algorithm ties together the three basic operations -- $\next$, $\plus$, and $\mult$ -- and has two conclusions, one equality and one inequality. It also has some really powerful applications, like computing the greatest common divisor of two numbers and constructing fixed radix representations.

We'd like to define $\divalg$ recursively, and the basic recursion operator we've been using is $\simprec$, so it would be nice to express the division algorithm in those terms. Let's see if we can make the function signatures work out.

Note that the division algorithm will take two numbers and return two numbers, so its signature looks like $$\divalg : \nats \times \nats \rightarrow \nats \times \nats.$$ The signature of $\simprec$, on the other hand, is $$\simprec_{\varphi,\mu} : \nats \times A \rightarrow B,$$ where $\varphi : A \rightarrow B$ and $\mu : \nats \times A \times B \rightarrow B$. Letting $A = \nats$ and $B = \nats \times \nats$, we're looking for $$\varphi : \nats \rightarrow \nats \times \nats$$ and $$\mu : \nats \times \nats \times (\nats \times \nats) \rightarrow \nats \times \nats$$ so that $\simprec_{\varphi,\mu}$ "behaves like" the division algorithm. But how does the division algorithm behave?

Let's look at some specific cases. For instance, if $a = \zero$, then we want $$\varphi(b) = \simprec_{\varphi,\mu}(\zero,b) = (q,r)$$ such that $\zero = \plus(\mult(q,b),r)$. Evidently $q = r = \zero$.

Now consider $\divalg(\next(a),b)$. Switching to more familiar notation for a moment, suppose we've already found the quotient and remainder of $a$ by $b$ as $a = qb+r$. Now $$a+1 = qb+r+1;$$ so $q$ and $r+1$ satisfy the equality constraint, but possibly not the inequality constraint. If $r+1 < b$ we're ok. And since $r < b$, the worst that the strict inequality $r+1 < b$ can fail is when $r+1 = b$; in this case we can simply "increment" $q$ and "reset" $r$ to zero.

With these observations in mind, we define the division algorithm like so.

::: definition :::
Define $\varphi : \nats \rightarrow \nats \times \nats$ by $\varphi(n) = (\zero,\zero)$, and define $\mu : \nats \times \nats \times (\nats \times \nats) \rightarrow \nats \times \nats$ by $$\mu(\ast,m,(q,r)) = \left\{\begin{array}{ll} (\next(q),\zero) & \mathrm{if}\ \zero < m \leq \next(r) \\ (q,\next(r)) & \mathrm{otherwise}. \end{array}\right.$$ We then define the function $\divalg : \nats \times \nats \rightarrow \nats \times \nats$ by $$\divalg = \simprec{\varphi,\mu},$$ pronounced the _division algorithm_. For convenience we also define $\quo,\rem : \nats \times \nats \rightarrow \nats$ by $\quo(a,b) = q$ and $\rem(a,b) = r$ where $\divalg(a,b) = (q,r)$.
::::::::::::::::::

First of all, we need to prove that $\divalg$ acts like the division algorithm.

::: theorem :::
[@thm-divalg-nat]()
Let $a,b \in \nats$ and let $(q,r) = \divalg(a,\next(b))$. Then we have the following.

1. $a = \plus(\mult(q,\next(b)),r)$.
2. $r < \next(b)$.

::: proof :::
We proceed by induction on $a$. For the base case $a = \zero$, note that
$$\begin{eqnarray*}
 &   & \divalg(a,\next(b)) \\
 & = & \divalg(\zero,\next(b)) \\
 & = & \varphi(\next(b)) \\
 & = & (\zero, \zero).
\end{eqnarray*}$$
Now
$$\begin{eqnarray*}
 &   & \plus(\mult(q,\next(b)),r) \\
 & = & \plus(\mult(\zero,\next(b)),\zero) \\
 & = & \plus(\zero,\zero) \\
 & = & \zero \\
 & = & a
\end{eqnarray*}$$
and $r = \zero < \next(b)$ as needed.

For the inductive step, suppose both (1) and (2) hold for all $b$ for some $a$, and let $(q_1,r_1) = \divalg(a,\next(b))$. Now we have
$$\begin{eqnarray*}
 &   & \divalg(\next(a),\next(b)) \\
 & = & \mu(a,\next(b),\divalg(a,\next(b))) \\
 & = & \mu(a,\next(b),(q_1,r_1)) \\
 & = & Q.
\end{eqnarray*}$$
We have two possibilities to consider: either $\next(r_1) \geq \next(b)$ or $\next(r_1) < \next(b)$.

Suppose first that $\next(r_1) \geq \next(b)$. By our definition of $\mu$ we have $Q = (\next(q_1),\zero)$. Now we have
$$\begin{eqnarray*}
 &   & \plus(\mult(\next(q_1),\next(b)),\zero) \\
 & = & \mult(\next(q_1),\next(b)) \\
 & = & \plus(\mult(q_1,\next(b)),\next(b)) \\
 & = & \plus(\mult(q_1,\next(b)),\next(r_1)) \\
 & = & \next(\plus(\mult(q_1,\next(b)),r_1)) \\
 & = & \next(a)
\end{eqnarray*}$$
as well as $\zero < \next(b)$. So $\divalg(\next(a),\next(b))$ satisfies (1) and (2) for all $b$.

Now suppose $\next(r_1) < \next(b)$. By our definition of $\mu$ we have $Q = (q_1,\next(r_1))$. In this case we have
$$\begin{eqnarray*}
 &   & \plus(\mult(q_1,\next(b)),\next(r_1)) \\
 & = & \next(\plus(\mult(q_1,\next(b)),r_1)) \\
 & = & \next(a),
\end{eqnarray*}$$
and of course $\next(r_1) < \next(b)$. So $\divalg(\next(a),\next(b))$ satisfies (1) and (2) for all $b$.

By induction, $\divalg(a,\next(b))$ satisfies (1) and (2) for all $a$ and $b$.
:::::::::::::
:::::::::::::::

It turns out that the previous theorem characterizes the division algorithm.

::: theorem :::
Let $a,b \in \nats$, and suppose we have $q,r \in \nats$ such that the following hold:

1. $a = \plus(\mult(q,\next(b)),r)$.
2. $r < \next(b)$.

Then $(q,r) = \divalg(a,\next(b))$.

::: proof :::
It suffices to show that if both $(q_1,r_1)$ and $(q_2,r_2)$ satisfy conditions (1) and (2), then $q_1 = q_2$ and $r_1 = r_2$. To that end, suppose (1) and (2) are both satisfied. By the trichotomy property, we can assume without loss of generality that $r_1 \leq r_2$; say $r_1 = \plus(r_1,k)$. Now
$$\begin{eqnarray*}
 &   & \plus(\mult(q_1,\next(b)),r_1) \\
 & = & a \\
 & = & \plus(\mult(q_2,\next(b)),r_2) \\
 & = & \plus(\mult(q_2,\next(b)),\plus(r_1,k)) \\
 & = & \plus(\mult(q_2,\next(b)),\plus(k,r_1)) \\
 & = & \plus(\plus(\mult(q_2,\next(b)),k),r_1). \\
\end{eqnarray*}$$
Because $\plus$ is cancellative, we have $$\mult(q_1,\next(b)) = \plus(\mult(q_2,\next(b)),k).$$ Note also that $k \leq r_2 < \next(b)$, so that $k < \next(b)$. As we've shown, $k = \zero$. Thus $$\mult(q_1,\next(b)) = \mult(q_2,\next(b)),$$ and since $\mult$ is (almost) cancellative, $q_1 = q_2$. Then
$$\begin{eqnarray*}
 &   & \plus(\mult(q_1,\next(b)),r_1) \\
 & = & \plus(\mult(q_2,\next(b)),r_2) \\
 & = & \plus(\mult(q_1,\next(b)),r_2),
\end{eqnarray*}$$
and since $\plus$ is cancellative, $r_1 = r_2$.
:::::::::::::
:::::::::::::::

The last two theorems essentially say that the output of $\divalg(a,b)$ is the unique solution of a particular system of equations so long as $b$ is not zero. But what if $b$ is zero? We frankly won't usually be interested in this case, since in the $b = \zero$ case the system of equations does not have a unique solution and the particular one given by $\divalg$ is a quirk of our definition. However it does show up as the base case in some induction proofs. So we consider it along with some other special cases.

::: theorem :::
If $a \in \nats$, we have the following.

1. $\divalg(a,\zero) = (\zero,a)$.
2. $\divalg(a,\next(\zero)) = (a,\zero)$.
3. If $a < \next(b)$, then $\divalg(a,\next(b)) = (\zero,a)$.
4. $\divalg(\next(a),\next(a)) = (\next(\zero),\zero)$.

::: proof :::
To see (1), we proceed by induction on $a$. For the base case $a = \zero$, we have
$$\begin{eqnarray*}
 &   & \divalg(a,\zero) \\
 & = & \divalg(\zero,\zero) \\
 & = & \simprec_{\varphi,\mu}(\zero,\zero) \\
 & = & \varphi(\zero) \\
 & = & (\zero,\zero) \\
 & = & (\zero,a)
\end{eqnarray*}$$
as claimed. For the inductive step, suppose $\divalg(a,\zero) = (\zero,a)$ for some $a$. Now
$$\begin{eqnarray*}
 &   & \divalg(\next(a),\zero) \\
 & = & \simprec_{\varphi,\mu}(\next(a),\zero) \\
 & = & \mu(a,\zero,\simprec_{\varphi,\mu}(a,\zero)) \\
 & = & \mu(a,\zero,\divalg(a,\zero)) \\
 & = & \mu(a,\zero,(\zero,a)) \\
 & = & (\zero,\next(a))
\end{eqnarray*}$$
as needed. By induction, $\divalg(a,\zero) = (\zero,a)$ for all $a$.

To see (2), note that $$a = \plus(\mult(\next(\zero),a),\zero)$$ and $\zero < \next(\zero)$. By the uniqueness of quotients and divisors by a nonzero dividend, we have $\divalg(a,\next(\zero)) = (\next(\zero),\zero)$.

To see (3), note that $$a = \plus(\mult(\zero,\next(b)),a)$$ and $a < \next(b)$. Again by the uniqueness of quotients and divisors by a nonzero dividend, we have $\divalg(a,\next(b)) = (0,a)$ as claimed.

To see (4), note that $$\next(a) = \plus(\mult(\next(\zero),\next(a)),\zero)$$ and $\zero < \next(a)$. Again by uniqueness we have $\divalg(\next(a),\next(a)) = (\next(\zero),\zero)$.
:::::::::::::
:::::::::::::::

The previous theorem also demonstrates a handy witness property for the division algorithm. In order to demonstrate that $\divalg(a,b) = (q,r)$ when $b \neq \zero$, it's enough to show that $a$, $b$, $q$, and $r$ satisfy the unique property of $\divalg$. This also applies in the following result on products.

::: theorem :::
If $a,b\in \nats$, then $$\divalg(\mult(a,\next(b)),\next(b)) = (a,\zero).$$

::: proof :::
Note that $$\mult(a,\next(b)) = \plus(\mult(a,\next(b)),\zero)$$ and $\zero < \next(b)$. By the uniqueness of quotients and divisors by a nonzero dividend, $$\divalg(\mult(a,\next(b)),\next(b)) = (a,\zero)$$ as claimed.
:::::::::::::
:::::::::::::::
