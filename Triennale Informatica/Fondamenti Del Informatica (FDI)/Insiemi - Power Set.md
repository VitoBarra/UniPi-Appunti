---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

## Insiemi - Power Set  
---
Il **power set** (o **insieme delle parti**) di un [[Insiemi Matematici|insieme]] $A$, indicato con $\mathcal{P}(A)$ o anche $2^{A}$, è l’insieme di **tutti i sottoinsiemi possibili** di $A$, compreso l’insieme vuoto $\varnothing$ e l’insieme stesso $A$. Formalmente:  $$
\mathcal{P}(A) = \{\, X \mid X \subseteq A \,\}
$$Se $A$ ha [[Insiemi - Cardinalita|cardinalita]] $n$ elementi distinti, allora il suo power set contiene $2^n$ sottoinsiemi.  
In simboli:  $$
|\mathcal{P}(A)| = 2^{|A|}
$$


### Esempio
Se $A = \{1, 2\}$, allora:  
$$
\mathcal{P}(A) = \{\varnothing, \{1\}, \{2\}, \{1,2\}\}
$$

L’insieme $\mathcal{P}(A)$ è quindi sempre un insieme di insiemi, rappresentando tutte le combinazioni possibili degli elementi di $A$.
