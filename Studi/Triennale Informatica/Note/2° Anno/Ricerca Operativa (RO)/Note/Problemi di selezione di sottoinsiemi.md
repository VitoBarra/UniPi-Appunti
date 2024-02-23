---
Subject: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic:
---

# Problemi di selezione di sottoinsiemi
---

### Definizione

Dati un [[Insiemi Matematici|insieme]] $I = \{1, \dots , m\}$ ed una famiglia $S_1, \dots, S_n \subset I$ ,
ogni sottoinsieme $S_j$  ha un costo (o valore) $c_j$, per ogni $j = 1, \dots , n.$

### Problema di copertura

determinare una sottofamiglia $\mathcal{F}$ di sottoinsiemi di costo minimo tale che ogni elemento di $I$ appartenga ad almeno un sottoinsieme di $\mathcal{F}$

### Problema di partizione

determinare una sottofamiglia $\mathcal{F}$ di sottoinsiemi di **costo minimo** tale che ogni elemento di $I$ appartenga esattamente ad un sottoinsieme di $\mathcal{F}$

### Problema di riempimento

determinare una sottofamiglia $\mathcal{F}$ di sottoinsiemi di valore massimo tale che ogni elemento di $I$ appartenga ad al più un sottoinsieme di $\mathcal{F}$.

### Esempi

sia $I = \{1, 2, 3, 4, 5, 6\}$

- $S1 = \{1, 3\}$,  $S2 = \{2, 4\}$, $S3 = \{2, 5, 6\}$, $S4 = \{5, 6\}$ , $S5 = \{3, 4\}$


$F1 = \{S1, S2, S3\}$  è una copertura ma non è una partizione

 $F2 = \{S1, S2, S4\}$ è una partizione

$F3 = \{S3, S5\}$  è un riempimento ma non `e una partizione

## Modelli

definiamo la matrice $a_{ij} =\begin{cases}1 \ \ \ \ if \ \ i \in S_j \\0 \ \ \ \ altrimenti\end{cases}$

ad ogni sottofamiglia $\mathcal{F}$ associamo una variabile $x$, dove $x_j =\begin{cases}1 \ \ \ \ if \ \ S_j  \in \mathcal{F} \\0 \ \ \ \ altrimenti\end{cases}$

 Copertura

$$
\begin{cases}
\min
\sum\limits_{j=1}^n c_jx_j \\

\sum\limits_{j=1}^n a_{ij}x_j \geq 1 \ \ \ \  \forall i \\

x_j \in \{ 0,1\} \ \ \ \forall j
\end{cases}
$$

 Partizione

$$
\begin{cases}
\min
\sum\limits_{j=1}^n c_jx_j \\

\sum\limits_{j=1}^n a_{ij}x_j = 1 \ \ \ \  \forall i \\

x_j \in \{ 0,1\} \ \ \ \forall j
\end{cases}
$$

 Riempimento

$$
\begin{cases}
\min
\sum\limits_{j=1}^n c_jx_j \\

\sum\limits_{j=1}^n a_{ij}x_j \leq 1 \ \ \ \  \forall i \\

x_j \in \{ 0,1\} \ \ \ \forall j
\end{cases}
$$
