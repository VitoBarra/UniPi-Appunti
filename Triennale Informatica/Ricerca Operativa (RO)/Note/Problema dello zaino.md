---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---
# Problema dello zaino
---
Il [[Problema dello zaino|problema dello zaino]] consiste, dati $n$ oggetti di valore $v_1,\dots,v_n$ e peso $p_1,\dots,p_n$, e dato un contenitore di capacità $C$, nel determinare quali oggetti inserire nel contenitore rispettando il vincolo di capacità e massimizzando il valore totale.

Si introducono variabili binarie
$$
x_i=\begin{cases}1 & \text{se l'oggetto } i \text{ viene inserito}\\0 & \text{altrimenti}\end{cases}
$$

La formulazione come [[Programmazione lineare Intera|PLI]] è
$$
\begin{cases}
\max \sum\limits_{i=1}^n v_ix_i\\
\sum\limits_{i=1}^n p_ix_i\leq C\\
x_i\in\{0,1\}\qquad i=1,\dots,n
\end{cases}
$$

## Rilassamento continuo

Il rilassamento continuo si ottiene sostituendo i vincoli di interezza con $0\leq x_i\leq 1$:
$$
\begin{cases}
\max \sum\limits_{i=1}^n v_ix_i\\
\sum\limits_{i=1}^n p_ix_i\leq C\\
0\leq x_i\leq 1\qquad i=1,\dots,n
\end{cases}
$$

La soluzione ottima del rilassamento continuo si calcola ordinando gli oggetti in ordine decrescente di rendimento $\dfrac{v_i}{p_i}$, determinando l'indice $h$ tale che $\sum_{i=1}^h p_i\leq C$ e $\sum_{i=1}^{h+1} p_i>C$, e ponendo
$$
\bar{x}_1=1,\dots,\bar{x}_h=1,\qquad \bar{x}_{h+1}=\frac{C-\sum_{i=1}^h p_i}{p_{h+1}},\qquad \bar{x}_{h+2}=\dots=\bar{x}_n=0.
$$

## Algoritmo euristico

Una soluzione ammissibile può essere costruita con la seguente euristica:
- ordina gli oggetti in ordine decrescente di rendimento $\dfrac{v_i}{p_i}$
- poni $\bar{C}=C$, dove $\bar{C}$ rappresenta la capacità residua
- per $i=1,\dots,n$, se $p_i\leq \bar{C}$ poni $x_i=1$ e aggiorna $\bar{C}=\bar{C}-p_i$, altrimenti poni $x_i=0$

Questa procedura produce rapidamente una soluzione ammissibile, ma non garantisce in generale l'ottimalità.

## Relazione con il Branch and Bound

Il [[Problema dello zaino|problema dello zaino]] si presta a essere risolto con [[Branch and Bound]]. In questo caso:
- il bound superiore è dato dal rilassamento continuo
- il branch è binario e si effettua istanziando un'eventuale variabile frazionaria della soluzione ottima del rilassamento continuo
- la visita dell'albero decisionale può essere eseguita, ad esempio, in ampiezza

Se la soluzione ottima del rilassamento continuo è intera, allora essa è già ottima anche per il problema intero. Se invece compare una variabile frazionaria, si generano due sottoproblemi imponendo rispettivamente $x_i=0$ e $x_i=1$ per una variabile frazionaria $x_i$.

Il [[Problema dello zaino|problema dello zaino]] può inoltre essere risolto con un algoritmo di [[Programmazione Dinamica]].
