---
type: nota
course: Statistica
topic: 
tags: STAT
---

Prev: [[Statistica (STAT)]]

# Indipendenza Stocastica
---
i indipendenza stocastica dice che lo conoscenza della avvenuta del evento $A$ non cambia la probabilità di un evento $B$ ed è definita in formula come

$$
\mathbf{P}(A\cap B) =\mathbf{P}(A) \times\mathbf{P}(B)
$$

- se $A$ e $B$ sono indipendenti, sono indipendenti anche $A^c$ e $B$, $A$  e $B^c$, $A^c$ e $B^c$
- se $\mathbf{P}(A) =0$ oppure $\mathbf{P}(A) = 1$, $A$ è indipendente da qualsiasi altro evento;
- due eventi $inccompatibili$ (cioè che hanno intersezione vuota) non possono essere indipendenti, a meno che uno dei due sia trascurabile.

### Indipendenza di più eventi

Assegnati $n$  eventi $A_1,\dots,A_n$, questi si dicono $indipendenti$ se per ogni intero $k$ con $2 \leq k \leq n$ e per ogni scelta di $1 \leq i_1 < i_2 < \dots < i_k \leq n$  , vale l’eguaglianza

$$
\mathbf{P}(A_{i_1} \cap \cdots \cap A_{i_k}) = \mathbf{P}(A_{i_1}) \dots \mathbf{P}(A_{i_k})
$$
