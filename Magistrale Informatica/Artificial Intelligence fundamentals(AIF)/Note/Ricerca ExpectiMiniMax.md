---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ambienti stocastici
---
la **Ricerca ExpectiMiniMax** è un algoritmo di ricerca estensione del algoritmo di [[Ricerca MiniMax|Ricerca MiniMax]] che gli permette di fare ricerca in **[[Definizione di Problemi-Ambienti|ambienti stocastici]]** come ad esempio in **giochi stocastici**. Questo significa che l'algoritmi deve gestire un **elemento di imprevedibilità**, come ad esempio puo essere il lancio di dadi.


L'**albero di gioco** è esteso con l'inclusione di nodi di probabilità, detti ***chance nodes***. I rami che partono da tali nodi indicano i possibili risultati del evento [[Definizione di Probabilita|probabilistico]],

Per prendere decisioni corrette in **presenza di incertezza**, si definisce il valore ***expectiminimax*** generalizzazione del con probabilità **[[Ricerca MiniMax|minimax]]**, il quale calcola il valore atteso di una posizione, mediando sugli esiti probabilistici:

$$
\text{EXPECTIMINIMAX}(s) = 
\begin{cases}
\text{UTILITY}(s, \text{MAX}) & \text{se } \text{IS-TERMINAL}(s) \\
\max_a \text{EXPECTIMINIMAX}(\text{RESULT}(s, a)) & \text{se } \text{TO-MOVE}(s) = \text{MAX} \\
\min_a \text{EXPECTIMINIMAX}(\text{RESULT}(s, a)) & \text{se } \text{TO-MOVE}(s) = \text{MIN} \\
\sum_r P(r) \cdot \text{EXPECTIMINIMAX}(\text{RESULT}(s, r)) & \text{se } \text{TO-MOVE}(s) = \text{CHANCE}
\end{cases}
$$

Qui $r$ rappresenta un esito casuale (ad esempio un lancio di dadi) e $\text{RESULT}(s, r)$ rappresenta lo stato $s$ aggiornato con tale risultato. 


Nel contesto della potatura anticipata dell'albero di ricerca, come già visto con l’algoritmo [[Ricerca alpha-beta pruning|alfa–beta]] nei giochi deterministici, l’intuizione si complica. In presenza di nodi di probabilità, l’utilità media di un nodo chance potrebbe sembrare non calcolabile senza esaminare tutti i figli. Tuttavia, se si conoscono i limiti dell’intervallo dei valori di utilità è possibile stabilire un limite superiore o inferiore al valore atteso anche prima di aver visitato tutti i rami. Questo rende possibile la potatura anche in presenza di eventi casuali.


 la [[Complessita|complessità computazionale]] di **expectiminimax** è $O(b^m n^m)$, dove $n$ è il numero di esiti casuali distinti e $m$ è la profondità massima della ricerca, per mitigare la crescita esponenziale dello spazio di ricerca nei nodi chance, si può ricorrere al ***[[Ricerca alpha-beta pruning|forward pruning]]***, che consiste nel campionare un sottoinsieme degli esiti casuali, oppure si può optare per tecniche di *[[Ricerca albero Monte Carlo (MCST)|Monte Carlo tree search]]*, che eseguono **playout** casuali incorporando i tiri di dadi, senza bisogno di un'esplicita funzione di valutazione.
 
![[IMG - alberi Ambienti stocastici.png]]

La scelta di **funzioni di valutazione** nei giochi con incertezza richiede particolare attenzione, infatti cambiare i valori come in figura porta a scelte diverse 
![[IMG - alberi stocastici trasformare la funzione di valutazione.png]]
 la **funzione di valutazione** deve essere una **trasformazione lineare positiva** della [[Definizione di Probabilita|probabilità]] di vincita o dell’utilità attesa. Questo vincolo garantisce che il processo decisionale rifletta accuratamente le probabilità implicite nei diversi scenari.
