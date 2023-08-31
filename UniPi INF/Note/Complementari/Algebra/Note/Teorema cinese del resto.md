---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Teorema cinese del resto 
---
_Sia_ un il sistema di congruenze:
$$
\begin{cases}
x &\equiv a_{1} \mod{n_{1}} \\
  & \vdots  \\ 
x &\equiv a_{k} \mod{n_{k}} \\
\end{cases}
$$
dove $a_{1},\dots a_{k}\in \mathbb{N}$ con $n_{1},\dots ,n_{k} > 0$, e $N=\prod_{i=1}^{k}n_{i}$
_se_ 
- il [[Massimo comun divisore|massimo comun divisione]] $\text{MCD}(n_{i}, n_{j}) = 1 \forall i\not=j$ ovvero sono [[Insieme dei coprimi|coprimi]] a _due a due_
- vale che $0 \leq a_{i} <n_{i}$
_allora_  
1. Esiste una _soluzione_ $x_{0}$ tale che $0 \leq x_{0} <N$ e il resto delle [[Teorema della divisione|divisione]] intera (_divisione euclidea_) $\cfrac{x_{0}}{n_{i}}$ è $a_{i}\ \forall i$ 
2. la soluzione generale è della forma $x=x_{0}+rN \mod N$

quindi prese due soluzioni $x_{0}$ e $x_{1}$ varra che $x_{0}\equiv x_{1} \mod  N$


#### Dimostrazione