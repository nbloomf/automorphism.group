---
title: Iterative Norms
---



Another Recursion Operator
--------------------------

The recursion operators $\natrec$ and $\simprec$ act like _program skeletons_: we can fill in the "slots" with any functions having the right signatures and get a computable function out. In this post we'll define another recursion operator called _bailout recursion_.

::: theorem :::
Let $A$ and $B$ be sets, and let $\bool = \{\true,\false\}$. Suppose we have functions with the following signatures.
$$\begin{array}{l}
\beta : \nats \times A \rightarrow \bool \\
\omega : \nats \times A \rightarrow A \\
\psi : \nats \times A \rightarrow B
\end{array}$$
Then there is a unique function $\Theta : \nats \times A \rightarrow B$ satisfying the following:

1. $\Theta(\zero,a) = \psi(\zero,a)$ for all $a \in A$.
2. For all $a \in A$ and $n \in \nats$,

$$\begin{array}{l} \Theta(\next(n),a) \\ \ = \left\{\begin{array}{ll} \psi(\next(n),a) & \mathrm{if}\ \beta(\next(n),a) = \true \\ \Theta(n,\omega(\next(n),a)) & \mathrm{otherwise}. \end{array}\right. \end{array}$$ This function $\Theta$ will be denoted $\bailrec_{\beta,\omega,\psi}$, called _bailout recursion_.

::: proof :::
This is a "there exists a unique" theorem, so we have two things to show: that such a $\Theta$ exists, and that it is unique. As usual for the recursion operators on $\nats$, we'll define this in terms of natural recursion on an appropriate iterative set.

To this end, define $\chi : (\nats \times A)^{\nats \times A} \rightarrow (\nats \times A)^{\nats \times A}$ by $$\chi(h)(n,a) = \left\{\begin{array}{l} (n,a) & \mathrm{if}\ \beta(n,a) = \true \\ h(\prev(n),\omega(n,a)) & \mathrm{otherwise}. \end{array}\right.$$

Now $\langle (\nats \times A)^{\nats \times A}, \id, \chi \rangle$ is an iterative set. We define $\Theta : \nats \times A \rightarrow B$ by $$\Theta(n,a) = \psi(\natrec_{\id,\chi}(n)(n,a)).$$

First, note that if $a \in A$ we have
$$\begin{eqnarray*}
 &   & \Theta(\zero,a) \\
 & = & \psi(\natrec_{\id,\chi}(\zero)(\zero,a)) \\
 & = & \psi(\id(\zero,a)) \\
 & = & \psi(\zero,a)
\end{eqnarray*}$$
as claimed.

Now suppose $\beta(\next(n),a) = \true$. Then
$$\begin{eqnarray*}
 &   & \Theta(\next(n),a) \\
 & = & \psi(\natrec_{\id,\chi}(\next(n))(\next(n),a)) \\
 & = & \psi(\chi(\natrec_{\id_chi}(n))(\next(n),a)) \\
 & = & \psi(\next(n),a)
\end{eqnarray*}$$
as claimed. Suppose instead that $\beta(\next(n),a) = \false$. Then
$$\begin{eqnarray*}
 &   & \Theta(\next(n),a) \\
 & = & \psi(\natrec_{\id,\chi}(\next(n))(\next(n),a)) \\
 & = & \psi(\chi(\natrec_{\id_chi}(n))(\next(n),a)) \\
 & = & \psi(\natrec_{\id,\chi}(n)(\prev(\next(n)),\omega(\next(n),a))) \\
 & = & \psi(\natrec_{\id,\chi}(n)(n,\omega(\next(n),a))) \\
 & = & \Theta(n,\omega(\next(n),a))
\end{eqnarray*}$$
as claimed. So such a function exists.

Finally we show that $\Theta$ exists. To this end, suppose we have another function $\Omega$ satisfying conditions (1) and (2); we need to show that $\Theta(n,a) = \Omega(n,a)$ for all $a \in A$ and $n \in \nats$. We proceed by induction on $n$.

For the base case $n = \zero$. If $a \in A$ we have
$$\begin{eqnarray*}
 &   & \Theta(n,a) \\
 & = & \Theta(\zero,a) \\
 & = & \psi(\zero,a) \\
 & = & \Omega(\zero,a) \\
 & = & \Omega(n,a).
\end{eqnarray*}$$
Now suppose we have $\Theta(n,a) = \Omega(n,a)$ for all $a \in A$ for some $n \in \nats$. We consider two possibilities. First suppose $\beta(\next(n),a) = \true$. Then
$$\begin{eqnarray*}
 &   & \Theta(\next(n),a) \\
 & = & \psi(\next(n),a) \\
 & = & \Omega(\next(n),a).
\end{eqnarray*}$$
Suppose instead that $\beta(\next(n),a) = \false$. Then, using the induction hypothesis,
$$\begin{eqnarray*}
 &   & \Theta(\next(n),a) \\
 & = & \Theta(n,\omega(\next(n),a)) \\
 & = & \Omega(n,\omega(\next(n),a)) \\
 & = & \Omega(\next(n),a).
\end{eqnarray*}$$
So we have $\Theta(n,a) = \Omega(n,a)$ for all $a$ and $n$, $\Omega = \Theta$, and thus $\Theta$ is unique.
:::::::::::::
:::::::::::::::

Bailout recursion does some cool things that simple recursion does not: the $\omega$ map lets us "mutate" the initial parameter $a$ at each step in the recursion, and the boolean function $\beta$ lets us short-circuit the evaluation. Compare this to $\simprec$, which uses the same $a$ at each step and _must_ count its natural number argument all the way to zero.

Simple and bailout recursion do share an important property, though. Both are carefully chosen to have tail recursive evaluation strategies. Intuitively, a recursive function -- one defined in terms of itself -- is called _tail recursive_ if there is "nothing left to do" after the recursive call. For example, suppose we tried to define a recursive function on $\nats$ like $$f(n+1) = 1 + f(n).$$ This is a recursive equation in $f$, but it is not _tail_ recursive, because on the right hand side there is something waiting for the result of the recursive call; namely, the $1+$.^[I think it's helpful to compare the difference between arbitrary recursion and tail recursion to that between arbitrary `GOTO`s and structured loops. In both cases we take a simple but dangerous primitive and hide it behind a safer and more semantic interface.]

Arbitrary recursion can be dangerous and tricky to reason about if each recursive call leaves a mess to be cleaned up. In contrast, tail recursive functions do not leave anything to be cleaned up and so can be evaluated using only a constant amount of space. Our recursion operators, $\simprec$ and $\bailrec$, are designed to be tail recursive.



Iterative Norms
---------------

The essence of recursion is to solve problems by combining solutions to smaller instances of the same problem. The recursion patterns we've defined so far take a very specific and limited view of what "smaller instance" means; the instance smaller than $\next(n)$ is just $n$. We can think of this as the recursion pattern embodied by the induction principle.

We have another (equivalent in power, but sometimes easier to use) induction principle, called the _strong_ induction principle. 

::: definition :::
Let $\langle A, \varepsilon, \varphi \rangle$ be an iterative set, and $\eta : A \rightarrow \nats$ a function. We say $\eta$ is an _iterative norm_ if the following hold for all $a \in A$ and $n \in \nats$.

1. If $\eta(a) = \zero$, then $\eta(\varphi(a)) = \zero$.
2. If $\eta(a) = \next(n)$, then $\eta(\varphi(a)) \leq n$.
::::::::::::::::::

We can think of an iterative norm as a kind of _measurement_ on the elements of the iterative set with the property that the measure of successive iterates is shrinking.

::: theorem :::
Let $\langle A, \varepsilon, \varphi \rangle$ be an iterative set and $\eta : A \rightarrow \nats$ an iterative norm. Let $B$ be a set and $\chi : A \rightarrow B$ a function. There is a unique function $\Theta : A \rightarrow B$ such that, for all $a \in A$, we have $$\Theta(a) = \left\{\begin{array}{ll} \chi(a) & \mathrm{if}\ \eta(a) = \zero \\ \Theta(\varphi(a)) & \mathrm{otherwise}. \end{array}\right.$$ This $\Theta$ is denoted $\normrec_{\varphi,\eta,\chi}$, pronounced _norm recursion_.

::: proof :::
This is a "there exists a unique" theorem, so we'll need to show that such a $\Theta$ exists and then show it is unique. First define $\beta : \nats \times A \rightarrow \bool$ by $$\beta(-,a) = \left\{\begin{array}{ll} \true & \mathrm{if}\ \eta(a) = \zero \\ \false & \mathrm{otherwise}, \end{array}\right.$$ define $\omega : \nats \times A \rightarrow A$ by $$\omega(-,a) = \varphi(a),$$ and define $\psi : \nats \times A \rightarrow B$ by $$\psi(-,a) = \chi(a).$$ We define a helper function $\Omega : \nats \times A \rightarrow B$ by $$\Omega = \bailrec_{\beta,\omega,\psi}.$$

As a lemma, we need the following intermediate result about $\Omega$: for all $a \in A$ and $k \in \nats$, we have $$\Omega(\plus(\eta(\varphi(a)),k),\varphi(a)) = \Omega(\eta(\varphi(a)),\varphi(a)).$$ We prove this by strong induction on $\eta(\varphi(a))$. For the base case $\eta(\varphi(a)) = \zero$, we proceed by induction on $k$. For the base case $k = \zero$, note that
$$\begin{eqnarray*}
 &   & \Omega(\plus(\eta(\varphi(a)),k),\varphi(a)) \\
 & = & \Omega(\plus(\eta(\varphi(a)),\zero),\varphi(a)) \\
 & = & \Omega(\eta(\varphi(a)),\varphi(a))
\end{eqnarray*}$$
as needed. For the inductive step, suppose the equality holds for some $k$. Now, because $\eta(\varphi(a)) = \zero$, we have $$\beta(-,\varphi(a)) = \true.$$ Then
$$\begin{eqnarray*}
 &   & \Omega(\plus(\eta(\varphi(a)),\next(k)),\varphi(a)) \\
 & = & \Omega(\next(\plus(\eta(\varphi(a)),k)),\varphi(a)) \\
 & = & \psi(\next(\plus(\eta(\varphi(a)),k)),\varphi(a)) \\
 & = & \chi(\varphi(a)) \\
 & = & \psi(\eta(\varphi(a)),\varphi(a)) \\
 & = & \Omega(\eta(\varphi(a)),\varphi(a)).
\end{eqnarray*}$$
By induction (on $k$), when $\eta(\varphi(a)) = \zero$, for all $k$ we have $$\Omega(\plus(\eta(\varphi(a)),k),\varphi(a)) = \Omega(\eta(\varphi(a)),\varphi(a)).$$ Now for the strong inductive step (on $\eta(\varphi(a))$, suppose we have $m \in \nats$ such that for all $k \in \nats$ and $a \in A$ such that $\eta(\varphi(a)) \leq m$, we have $$\Omega(\plus(\eta(\varphi(a)),k),\varphi(a)) = \Omega(\eta(\varphi(a)),\varphi(a)).$$ We need to show that this equality also for all $k$ and all $a$ such that $\eta(\varphi(a)) = \next(m)$. We proceed by induction on $k$.

For the base case $k = \zero$, note that
$$\begin{eqnarray*}
 &   & \Omega(\plus(\eta(\varphi(a)),k),\varphi(a)) \\
 & = & \Omega(\plus(\eta(\varphi(a)),\zero),\varphi(a)) \\
 & = & \Omega(\eta(\varphi(a)),\varphi(a))
\end{eqnarray*}$$
as needed. For the inductive step, suppose the equality holds for some $k$. Recall that $\eta(\varphi(a)) = \next(m)$, so that $$\beta(-,\varphi(a)) = \false.$$ Now we have
$$\begin{eqnarray*}
 &   & \Omega(\plus(\eta(\varphi(a)),\next(k)),\varphi(a)) \\
 & = & \Omega(\next(\plus(\eta(\varphi(a)),k)),\varphi(a)) \\
 & = & \Omega(\plus(\eta(\varphi(a)),k),\varphi(\varphi(a))) \\
 & = & Q.
\end{eqnarray*}$$
Note that since $\eta$ is an iterative norm, we have $\eta(\varphi(\varphi(a))) \leq m$; in particular $\plus(\eta(\varphi(\varphi(a))),u) = m$ for some $u$. Then
$$\begin{eqnarray*}
 &   & \plus(\eta(\varphi(a)),k) \\
 & = & \plus(\next(m),k) \\
 & = & \plus(m,\next(k)) \\
 & = & \plus(\plus(\eta(\varphi(\varphi(a))),u),\next(k)) \\
 & = & \plus(\eta(\varphi(\varphi(a))),\plus(u,\next(k))).
\end{eqnarray*}$$
Using the strong induction hypothesis on $\eta(\varphi(\varphi(a)) \leq m$, and since $\eta(\varphi(a)) = \next(m)$, we have
$$\begin{eqnarray*}
 &   & Q \\
 & = & \Omega(\plus(\eta(\varphi(\varphi(a))),\plus(u,\next(k))),\varphi(\varphi(a))) \\
 & = & \Omega(\eta(\varphi(\varphi(a))),\varphi(\varphi(a))) \\
 & = & \Omega(\plus(\eta(\varphi(\varphi(a))),u),\varphi(\varphi(a))) \\
 & = & \Omega(m,\varphi(\varphi(a))) \\
 & = & \Omega(\next(m),\varphi(a)) \\
 & = & \Omega(\eta(\varphi(a)),\varphi(a)).
\end{eqnarray*}$$
So the equality holds for all $k$. By strong induction, the lemma holds for all $k$ and all $a$.

We're finally prepared to define $\Theta : A \rightarrow B$ by $$\Theta(a) = \Omega(\eta(a),a).$$ To see that $\Theta$ satisfies our claimed equation, consider two possibilities for $\eta(a)$. If $\eta(a) = \zero$, we have
$$\begin{eqnarray*}
 &   & \Theta(a) \\
 & = & \Omega(\eta(a),a) \\
 & = & \Omega(\zero,a) \\
 & = & \psi(\zero,a) \\
 & = & \chi(a)
\end{eqnarray*}$$
as claimed. Suppose instead that $\eta(a) = \next(m)$ for some $m$. Since $\eta$ is an iterative norm, we have $\eta(\varphi(a)) \leq m$; say we have $u$ such that $$\plus(\eta(\varphi(a)),u) = m.$$ Using the lemma, we now have
$$\begin{eqnarray*}
 &   & \Theta(a) \\
 & = & \Omega(\eta(a),a) \\
 & = & \Omega(\next(m),a) \\
 & = & \Omega(m,\varphi(a)) \\
 & = & \Omega(\plus(\eta(\varphi(a)),u),\varphi(a)) \\
 & = & \Omega(\eta(\varphi(a)),\varphi(a)) \\
 & = & \Theta(\varphi(a))
\end{eqnarray*}$$
as claimed.

Finally, we show that $\Theta$ is unique; to do this we'll show that if $\Pi : A \rightarrow B$ also satisfies the equation then $\Pi(a) = \Theta(a)$ for all $a$. We proceed by strong induction on $\eta(a)$. For the base case $\eta(a) = \zero$, we have $\Pi(a) = \chi(a) = \Theta(a)$ as needed. For the inductive step, suppose we have $m \in \nats$ such that $\Pi(a) = \Theta(a)$ whenever $\eta(a) \leq m$, and suppose $\eta(a) = \next(m)$. Since $\eta$ is an iterative norm we have $\eta(\varphi(a)) \leq m$, and so $$\Pi(a) = \Pi(\varphi(a)) = \Theta(\varphi(a)) = \Theta(a)$$ as needed.
:::::::::::::
:::::::::::::::

Norm recursion is interesting because it allows us to define recursive functions on any set which has an appropriate normed iterative structure. If we can measure the "size" of the elements in a set, and if we can step from one element to the next so that the size is decreasing, then we can define recursive functions.
