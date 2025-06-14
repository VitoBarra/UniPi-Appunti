---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Allineamento di sequenze - Algoritmo Smith-Waterman
---
L’**algoritmo di Smith–Waterman** è un [[Algoritmi|algoritmo]] di [[Programmazione Dinamica|programmazione dinamica]] per il calcolo dell’**[[Allineamento di sequenze|allineamento locale]]** tra [[Allineamento di sequenze pairwise|due sequenze]]. A differenza dell’allineamento globale, esso non richiede che l’intera lunghezza delle sequenze venga allineata, ma ricerca la migliore corrispondenza tra **sottosequenze contigue**.

Siano $X = x_1 \dots x_n$ e $Y = y_1 \dots y_m$ due [[Stringhe|sequenze]]. L’algoritmo costruisce una [[Matrici|matrice]] $H \in \mathbb{R}^{(n+1)\times(m+1)}$, in cui $H(i,j)$ rappresenta il **miglior punteggio di un allineamento locale che termina esattamente** nelle posizioni $x_i$ e $y_j$. Ogni valore della matrice è quindi interpretabile come il punteggio massimo di una sottosequenza allineata che ha come estremi quelle posizioni. La matrice viene inizializzata imponendo:$$
H(0,j)=0,\quad H(i,0)=0
$$in modo da consentire l’inizio di un nuovo allineamento in qualsiasi punto delle sequenze, senza penalità iniziali. La [[Ricorsione|relazione di ricorrenza]] è definita come:
$$
H(i,j)=\max
\begin{cases}
H(i-1,j-1)+s(x_i,y_j) \\
H(i-1,j)+g \\
H(i,j-1)+g \\
0
\end{cases}
$$
dove $s(x_i,y_j)$ è il punteggio di sostituzione e $g$ la penalità di gap. L’introduzione esplicita del valore $0$ consente di interrompere un allineamento quando il punteggio cumulativo diventa negativo, evitando che contributi sfavorevoli influenzino l’allineamento locale ottimale.

Il riempimento della matrice avviene in modo **bottom-up**. A differenza dell’[[Allineamento di sequenza con Needleman-Wunsch Algorithm|allineamento globale]], il punteggio ottimale non si trova necessariamente in una posizione prefissata, ma corrisponde al **massimo valore presente nella matrice** $H$.

La ricostruzione dell’allineamento finale avviene tramite una procedura di **traceback** che parte dalla cella con valore massimo e procede a ritroso seguendo le scelte che hanno generato tale valore. La procedura termina quando viene raggiunta una cella con valore $0$, identificando così l’estensione esatta delle sottosequenze coinvolte nell’allineamento locale.

l algoritmo è sempre ottimale a [[complessita|complessita]] del algoritmo è $O(nm)$

Nel [[Allineamento di sequenze pairwise per sequenze biologiche|contesto biologico]], l’algoritmo di Smith–Waterman utilizza matrici di sostituzione come **BLOSUM62** e modelli di penalità dei gap analoghi a quelli dell’allineamento globale, ma fornisce un confronto mirato all’individuazione di **regioni localizzate di elevata similarità**, indipendentemente dal resto delle sequenze. 

Ad esempio, fissando $g=8$, l’applicazione dell’algoritmo produce il seguente risultato:
![[IMG - Allineamento di sequenza con Smith-Waterman Algorithm.png]]
che identifica due allineamenti locali distinti, rappresentabili come:
$$
\begin{array}{c|c}
\begin{array}{cccc}
H & G & W & A \\
H & S & W & G
\end{array}
&
\begin{array}{ccc}
H & G & W \\
H & S & W
\end{array}
\end{array}
$$
In questo caso, ciascun blocco corrisponde a una sottosequenza contigua con punteggio elevato, mentre la separazione evidenzia l’assenza di un vincolo di continuità globale tra le regioni allineate.
