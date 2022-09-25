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

L’algoritmo di Kruskal Trova un Albero di copertura di costo minimo in tempo polinomiale e.

### dimostrazione

Segue dalla [condizione di ottimalità basata sui cicli](obsidian://open?vault=UniPi-Appunti&file=Raccolta%20UniPi%20INF%2FNote%2F2%C2%B0%20Anno%2FRicerca%20Operativa%20(RO)%2FGrafi%2FProblema%20del%20albero%20di%20copertura%20costo%20minimo%2FCondizione%20di%20ottimalit%C3%A0%20sui%20cicli%20(albero%20di%20copertura%20di%20costo%20minimo)).

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





![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled.png]]


>[!info] #### OSSERVAZIONE
>Ad ogni iterazione dell’ algoritmo di Kruskal l’ insieme $T$ non è necessariamente un [[Albero struttura dati|albero]]