---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Problemi di selezione di sottoinsiemi
---
I [[Problemi di selezione di sottoinsiemi|problemi di selezione di sottoinsiemi]] consistono nel selezionare una sottofamiglia di sottoinsiemi a partire da un [[Insiemi Matematici|insieme]] finito $I=\{1,\dots,m\}$ e da una famiglia $S_1,\dots,S_n\subseteq I$, dove ogni sottoinsieme $S_j$ ha costo o valore $c_j$.

## Struttura generale

L'obiettivo cambia in base al tipo di vincolo imposto sugli elementi di $I$:
- nel problema di copertura ogni elemento deve appartenere ad almeno un sottoinsieme selezionato
- nel problema di partizione ogni elemento deve appartenere esattamente a un sottoinsieme selezionato
- nel problema di riempimento ogni elemento deve appartenere ad al più un sottoinsieme selezionato

## Variabili e matrice di incidenza

Si definisce la matrice di incidenza $a_{ij}$ come
$$
a_{ij}=\begin{cases}1 & \text{se } i\in S_j \\ 0 & \text{altrimenti}\end{cases}
$$

Si introduce inoltre una variabile binaria per ogni sottoinsieme:
$$
x_j=\begin{cases}1 & \text{se } S_j \text{ è selezionato} \\ 0 & \text{altrimenti}\end{cases}
$$

## Problema di copertura

Il [[Problemi di selezione di sottoinsiemi|problema di copertura]] consiste nel determinare una sottofamiglia di costo minimo tale che ogni elemento di $I$ appartenga ad almeno un sottoinsieme selezionato.

$$
\begin{cases}
\min \sum\limits_{j=1}^n c_jx_j \\
\sum\limits_{j=1}^n a_{ij}x_j \geq 1 \qquad \forall i=1,\dots,m \\
x_j\in\{0,1\} \qquad \forall j=1,\dots,n
\end{cases}
$$

## Problema di partizione

Il [[Problemi di selezione di sottoinsiemi|problema di partizione]] consiste nel determinare una sottofamiglia di costo minimo tale che ogni elemento di $I$ appartenga esattamente a un sottoinsieme selezionato.

$$
\begin{cases}
\min \sum\limits_{j=1}^n c_jx_j \\
\sum\limits_{j=1}^n a_{ij}x_j = 1 \qquad \forall i=1,\dots,m \\
x_j\in\{0,1\} \qquad \forall j=1,\dots,n
\end{cases}
$$

## Problema di riempimento

Il [[Problemi di selezione di sottoinsiemi|problema di riempimento]] consiste nel determinare una sottofamiglia di valore massimo tale che ogni elemento di $I$ appartenga ad al più un sottoinsieme selezionato.

$$
\begin{cases}
\max \sum\limits_{j=1}^n c_jx_j \\
\sum\limits_{j=1}^n a_{ij}x_j \leq 1 \qquad \forall i=1,\dots,m \\
x_j\in\{0,1\} \qquad \forall j=1,\dots,n
\end{cases}
$$

Questi problemi sono casi tipici di [[Programmazione lineare Intera|programmazione lineare intera]] con variabili binarie.
