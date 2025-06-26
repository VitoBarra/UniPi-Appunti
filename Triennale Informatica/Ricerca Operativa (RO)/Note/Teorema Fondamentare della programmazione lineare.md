---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags:
  - RO
---
# Teorema Fondamentale della programmazione lineare
---

Consideriamo un problema di [[Programmazione lineare|PL]] in forma canonica

$$
\begin{cases}
\max c^Tx \\
x \in P =\{x \in \mathbb{R}^n \ | \ Ax \leq b\}
\end{cases}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
(\mathcal{P})
$$

## **Teorema fondamentale della PL**

Supponiamo che la regione ammissibile $P$ sia [[Decomposizione dei poliedri|decomposta]] nel modo seguente:

$P = conv\{v_1, \dots , v_m\} + cono\{d_1, \dots, d_q\}$

- Il valore ottimo di $(\mathcal{P})$ è finito se e solo se $c^T d_j \leq 0 \ \  \forall j = 1, \dots, q$, cioè nessuna [[Poliedro#Direzione di recessione|direzione di recessione]] di $P$ è una [[Direzioni di crescita e di decrescita|direzione di crescita]].
- Se il valore ottimo di $(\mathcal{P})$ e finito, allora esiste un indice $i \in \{1, \dots, m\}$ tale che $v^i$ è una soluzione ottima di $(\mathcal{P})$.


> [!Abstract] #### Corollario
>Se il poliedro $P$ è limitato allora un suo vertice è una soluzione ottima di $(\mathcal{P})$

### Esistenza delle soluzioni

1. se esiste una direzione di recessione di $P$ che è anche una direzione di crescita, allora il valore ottimo è $+\infty$ e non esiste nessuna soluzione ottima.
2. altrimenti il valore ottimo $v$ è finito ed esiste almeno una soluzione ottima.
    1. la soluzione ottima è unica
    2. se esistono due soluzioni ottime $x$ e $x'$ diverse allora anche $ax+(1-a)x'$ è ottima per ogni $a\in(0,1)$. Infatti $ax+(1-a)x'$ è ammissibile perché fa parte di $conv(V)$ e

    $$
    c^T[ax+(1-a)x']=ac^Tx+(1-a)c^Tx'=av+(1-a)v=v
    $$


quindi esistono infinite soluzioni ottime
