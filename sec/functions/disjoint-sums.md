---
title: Disjoint Sums
---



Disjoint Sums of Sets
---------------------

In this section we nail down the properties of a useful operation on sets, called _disjoint sum_.

::: definition :::
Let $A$ and $B$ be sets. Then we define a set $A + B$, called the _disjoint sum_ of $A$ and $B$, by $$A + B = (\{\star\} \times A) \cup (\{\bullet\} \times B).$$ We also define functions $\iota_A : A \rightarrow A + B$ and $\iota_B : B \rightarrow A + B$ by $$\iota_A(a) = (\star,a)\ \mathrm{and}\ \iota_B(b) = (\bullet,b),$$ called the _canonical injections_ into $A + B$.
::::::::::::::::::

The canonical injections are injective.

::: theorem :::
Let $A$ and $B$ be sets. The canonical injections $\iota_A : A \rightarrow A + B$ and $\iota_B : B \rightarrow A + B$ are injective.

::: proof :::
To see that $\iota_A$ is injective, let $a_1, a_2 \in A$ and suppose $\iota_A(a_1) = \iota_A(a_2)$. Then $(\star,a_1) = (\star,a_2)$, and so $a_1 = a_2$ as needed. $\iota_B$ is injective by a similar argument.
:::::::::::::
:::::::::::::::

We can think of $A + B$ together with the injections $\iota_A$ and $\iota_B$ as an example of a kind of (really boring!) structure: sets equipped with distinguished maps from $A$ and $B$. Among such structures, $A+B$ is special, as in the following theorem.

::: theorem :::
Let $A$, $B$, and $Z$ be sets, and suppose we have functions $\alpha : A \rightarrow Z$ and $\beta : B \rightarrow Z$. Then there is a unique function $\theta : A + B \rightarrow Z$ such that $\alpha = \theta \circ \iota_A$ and $\beta = \theta \circ \iota_B$. That is, there is a unique $\theta$ such that the following diagram commutes.

~~~ tikzcd
A \arrow[r, "\iota_A"] \arrow[dr, "\alpha"'] & A + B \arrow[d, dotted, "\theta"] & B \arrow[l, "\iota_B"'] \arrow[dl, "\beta"] \\
& Z &
~~~~~~~~~~

We denote this unique $\theta$ by $\alpha + \beta$.

::: proof :::
This is a "there exists a unique" theorem, so we need to show that (1) such a $\theta$ exists and (2) it is unique.

We define $$\theta = \{ ((\star,a),\alpha(a)) \mid a \in A \} \cup \{ ((\bullet,b),\beta(b)) \mid b \in B \}.$$ First we show that $\theta$ is a function.

- To see that $\theta$ is total, suppose $x \in A + B$. By definition, either $x = (\star,a)$ for some $a \in A$ or $x = (\bullet,b)$ for some $b \in B$; in the first case we have $(x,\alpha(a)) \in \theta$ for some $a \in A$, and in the second we have $(x,\beta(b)) \in \theta$ for some $b \in B$. So $\theta$ is total.
- To see that $\theta$ is well-defined, suppose we have $x \in A+B$ and $z_1,z_2 \in Z$ such that $(x,z_1),(x,z_2) \in \theta$. We have two possibilities for $x$. If $x = (\star,a)$ with $a \in A$, then $z_1 = \alpha(a) = z_2$; similarly, if $x = (\bullet,b)$ with $b \in B$ then $z_1 = \beta(b) = z_2$. So $\theta$ is well-defined.

So $\theta$ is a function with signature $A + B \rightarrow Z$. Next we show that $\theta$ factors through $\iota_A$ and $\iota_B$. To this end, first suppose $a \in A$. Now
$$\begin{eqnarray*}
 &   & \alpha(a) \\
 & = & \theta(\star,a) \\
 & = & \theta(\iota_A(a)) \\
 & = & (\theta \circ \iota_A)(a),
\end{eqnarray*}$$
so that $\alpha = \theta \circ \iota_A$. Similarly, if $b \in B$ then
$$\begin{eqnarray*}
 &   & \beta(b) \\
 & = & \theta(\bullet,b) \\
 & = & \theta(\iota_B(b)) \\
 & = & (\theta \circ \iota_B)(b)
\end{eqnarray*}$$
so that $\beta = \theta \circ \iota_B$.

Finally, we need to show that $\theta$ is unique. To this end, suppose we have $\psi : A + B \rightarrow Z$ which also factors through $\iota_A$ and $\iota_B$; that is, $\alpha = \psi \circ \iota_A$ and $\beta = \psi \circ \iota_B$. Now let $x \in A + B$. We have two possibilities. If $x = (\star,a)$ with $a \in A$, then
$$\begin{eqnarray*}
 &   & \psi(x) \\
 & = & \psi(\star,a) \\
 & = & \psi(\iota_A(a)) \\
 & = & (\psi \circ \iota_A)(a) \\
 & = & \alpha(a) \\
 & = & (\theta \circ \iota_A)(a) \\
 & = & \theta(\iota_A(a)) \\
 & = & \theta(\star,a) \\
 & = & \theta(x).
\end{eqnarray*}$$
Similarly, if $x = (\bullet,b)$ with $b \in B$, then
$$\begin{eqnarray*}
 &   & \psi(x) \\
 & = & \psi(\bullet,b) \\
 & = & \psi(\iota_B(b)) \\
 & = & (\psi \circ \iota_B)(b) \\
 & = & \beta(b) \\
 & = & (\theta \circ \iota_B)(b) \\
 & = & \theta(\iota_B(b)) \\
 & = & \theta(\bullet,b) \\
 & = & \theta(x).
\end{eqnarray*}$$
Thus $\psi = \theta$, and $\theta$ is unique.
:::::::::::::
:::::::::::::::
