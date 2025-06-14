---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Allineamento di sequenze - Algoritmo Needleman-Wunsch
---
L’**algoritmo di Needleman–Wunsch** è un [[Algoritmi|algoritmo]] di [[Programmazione Dinamica|programmazione dinamica]] per il calcolo dell’**[[Allineamento di sequenze|allineamento globale]]** tra [[Allineamento di sequenze pairwise|due sequenze]]. Esso assume che l’intera lunghezza di entrambe le sequenze sia rilevante per il confronto e ricerca l’allineamento ottimale considerando tutte le posizioni.

Siano $X = x_1 \dots x_n$ e $Y = y_1 \dots y_m$ due [[Stringhe|sequenze]]. L’algoritmo costruisce una [[Matrici|matrice]] $F \in \mathbb{R}^{(n+1)\times(m+1)}$, in cui $F(i,j)$ rappresenta il **miglior punteggio ottenibile** allineando i prefissi $x_1\dots x_i$ e $y_1\dots y_j$. Ogni valore della matrice sintetizza quindi l’esito ottimale di tutte le possibili scelte di allineamento fino a quelle posizioni. La matrice viene inizializzata imponendo penalità cumulative per i gap iniziali:$$
F(0,0)=0,\quad F(i,0)=i\cdot g,\quad F(0,j)=j\cdot g
$$dove $g$ è la penalità associata all’inserimento di un gap. Questa inizializzazione riflette l’ipotesi che l’allineamento globale debba includere l’intera lunghezza delle sequenze, anche a costo di introdurre gap. La [[Ricorsione|relazione di ricorrenza]] che definisce l’algoritmo è:$$
F(i,j)=\max
\begin{cases}
F(i-1,j-1)+s(x_i,y_j) \\
F(i-1,j)+g \\
F(i,j-1)+g
\end{cases}
$$dove $s(x_i,y_j)$ è il punteggio di sostituzione tra i simboli $x_i$ e $y_j$, determinato dalla funzione obiettivo adottata. Ogni cella confronta quindi tre possibilità: allineare due simboli, introdurre un gap in $Y$ oppure introdurre un gap in $X$.

Il riempimento della matrice avviene in modo **bottom-up**, garantendo che ogni valore venga calcolato una sola volta. Il valore numerico in ciascuna cella rappresenta il punteggio ottimale cumulativo fino a quella posizione. Il punteggio dell’allineamento globale ottimale è contenuto nella cella $F(n,m)$.

La ricostruzione dell’allineamento finale avviene tramite una procedura di **traceback**, che parte dalla cella $F(n,m)$ e risale la matrice seguendo, a ogni passo, la scelta che ha contribuito al valore ottimale corrente. Un movimento diagonale corrisponde all’allineamento di due simboli, mentre un movimento verticale o orizzontale introduce un gap in una delle due sequenze. La procedura termina nella cella $F(0,0)$, producendo due sequenze allineate della stessa lunghezza.

l algoritmo è sempre ottimale a [[complessita|complessita]] del algoritmo è $O(nm)$

Nel [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche|contesto biologico]], l’algoritmo di Needleman–Wunsch utilizza una funzione di sostituzione $s(a,b)$ derivata da una matrice di sostituzione, come **BLOSUM62**, e una penalità di gap fissata. Ad esempio, fissando $g=8$, un possibile allineamento globale è il seguente:
![[IMG - Allineamento di sequenza con Needleman-Wunsch Algorithm.png]]
che allinea le sequenze come:
$$
\begin{array}{}
- & H & G & W & A & G \\
P & H & S & W & - & G
\end{array}
$$
