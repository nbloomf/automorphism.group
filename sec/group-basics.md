---
title: Groups
---

Abstract Groups
---------------

::: definition :::
Let $G$ be a set with a distinguished element $e \in G$, a mapping $\circ^{-1} : G \rightarrow G$, and an operation $\star : G \times G \rightarrow G$. We say the tuple $\langle G, e, \circ^{-1}, \star \rangle$ is a _group_ if the following properties hold.

1. $(a \star b) \star c = a \star (b \star c)$ for all $a,b,c \in G$; that is, $\star$ is _associative_.
2. $a \star e = a$ and $e \star a = a$ for all $a \in G$; that is, $e$ is _neutral_ with respect to $\star$ from both the right and the left.
3. $a \star a^{-1} = e$ and $a^{-1} \star a = e$ for all $a \in G$; that is, $a$ and $a^{-1}$ are _mutual inverses_ with respect to $\star$.
::::::::::::::::::
