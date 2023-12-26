---
type: nota
course: Ricerca Operativa
topic: 
tags: RO Algoritmo
---

Prev: [[Ricerca Operativa (RO)]]

# Algoritmo di Kruskal
---


### *Teorema*

L’[[Algoritmi|algoritmo]] di Kruskal Trova un [[Albero di copertura|Albero di copertura]] di costo minimo [[Complessita]] in tempo polinomiale.

### Dimostrazione

Segue dalla [[Condizione di ottimalità sui cicli|condizione di ottimalità basata sui cicli]].

### *Algoritmo*

1. Ordina gli archi $a_1,\dots,a_m$ in ordine crescente di costo. $T = \emptyset ,k=1$. Associa ad ogni nodo $i$ un etichetta $d_i=i$
2. Se $|T| = n-1$ allora stop
3. Sia $a_k = (p,q)$ un il k-esimo arco nella lista degli archi del grafo.
Se $d_p \not= d_q$ (cioè $a_k$ non forma un ciclo con gli archi di $T$ ) allora
    1. [aggiorna l’albero] $T = T \cup \{ a_k\}$
    2. [aggiorna le etichette] per ogni nodo $i$  con $d_i = \max\{d_p,d_q\}$ poni $d_i = \min\{d_p,d_q\}$
4. $k=k+1$   e torna a passo 2


>[!info]
le etichette sui nodi individuano le componetti connesse di $T$, cioè due nodi appartengono alla stessa compenente conessa se e solo se hanno la stessa etichetta.





![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled.png]]


>[!info] #### OSSERVAZIONE
>Ad ogni iterazione dell’ algoritmo di Kruskal l’ insieme $T$ non è necessariamente un [[Albero struttura dati|albero]]