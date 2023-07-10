---
type: nota
course: Statistica
topic: 
tags: STAT
---

Prev: [[Statistica (STAT)]]

# Probabilità
---

si parla di probabilità quando si analizza un evento il cui esito non è sicuro e vogliamo misurare quanto spesso un dato esito capita

### Eventi:

l universo di cui analizziamo gli eventi è l insieme $\Omega$ chiamato spazio dei campioni è gli eventi sono una famiglia di sottoinsiemi di $\Omega$

### Esempi:

dove lo spazio dei campioni sono i valori della roulette quindi   $\Omega = \{0,1,2,\dots,36\}$

e i suoi Eventi quindi sottoinsiemi sono

- pari $P =\{2,4,\dots,36\}$
- dispari $D = \{1,3,\dots,35\}$
- maggiori di 10 $A = \{11,12,\dots,36\}$
- minori di 10 $A^c= \{0,1,\dots,9\}$
- pari e maggiori di 10 $P \cap A = \{12,14,\dots,36\}$
- pari o maggiori di 10 $P \cup A = \{2,4,\dots,8,11,12,\dots,36\}$
- l’evento sicuro $\Omega$
- l’evento impossibile $\emptyset$

### Algebra Delle parti:

la famiglia dei sottoinsieme chiamata “eventi” è stabile per operazioni di

- unione (finita)
- intersezione
- complementazione

ed è quindi detta un Algebra delle parti

## Probabilità Finitamente Additiva

sia $\mathcal{F}$ un algebra delle parti di $\Omega$ è definita come  Probabilità Finitamente Additiva

$$
\mathbf{P} : \mathcal{F}\rightarrow[0,1]
$$

è soddisfa le seguenti proprietà

- se $A,B  \in \mathcal{F}$ e $A \cap B = \emptyset \implies \mathbf{P}(A \cup B) = \mathbf{P}(A)+\mathbf{P}(B)$
- $\mathbf{P}(\Omega) =1$

alcune conseguenza sono

1. $\mathbf{P}(\emptyset)=0$
2. $\mathbf{P}(A^c) =1-\mathbf{P}(A)$
3. se $B \subset A,\mathbf{P}(A\backslash B) =\mathbf{P}(A)-\mathbf{P}(B)$, dove si è posto $A \backslash B = A \cap B^c$
4. $\mathbf{P}(A\cup B) =\mathbf{P}(A)+\mathbf{P}(B) -\mathbf{P}(A\cap B)$
5. $\mathbf{P}(A\cup B \cup C) =\mathbf{P}(A)+\mathbf{P}(B) +\mathbf{P}(C) -\mathbf{P}(A\cap B)-\mathbf{P}(A\cap C)-\mathbf{P}(B\cap C) + \mathbf{P}(A\cap B \cap C)$

questa algebra pero ha un limite tecnico non permettere di fare il limite

### $\sigma$-Algebra:

se la famiglia delle parti è stabile per operazioni

- di unione numerabile
- intersezione numerabile
- complementazione

ed è quindi detta un $\sigma$-algebra

## Additività Numerabile o $\sigma$-additività

Definizione assiomatica di probabilità secondo Kolmogorov

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 11.png]]

![[Raccolta UniPi INF/Note/2° Anno/Statistica/-STAT Media/Untitled 1 1.png]]

### Probabilità in casi uniformemente probabili

![[Raccolta UniPi INF/Note/2° Anno/Statistica/-STAT Media/Untitled 2 1.png]]

