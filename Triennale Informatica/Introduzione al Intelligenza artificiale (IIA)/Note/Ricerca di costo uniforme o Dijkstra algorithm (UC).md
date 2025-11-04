---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Ricerca di costo uniforme o Dijkstra algorithm (UC)
---
la **Ricerca di costo uniforme** (**UC**) o **Dijkstra algorithm** è un [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] che  è una generalizzazione della [[Ricerca in ampiezza (BF)|BF]] dove non vale piu l'assunzione di costi degli **archi** uniformi tutti ad $1$. 
In questo caso non è la **profondità** che viene esplorata in modo **uniforme** come per la **BF** ma il **costo** dei [[Path|percorsi]] infatti ad ogni iterazione si **espande** il nodo di costo più basso presente nella **frontiera**, per fare ciò la frontiera è implementata usando una [[Coda di Priorita|Coda di priorita]].

l'[[Algoritmi|algoritmo]] è lo stesso nel [[Algoritmo di Dijkstra|Algoritmo di Dijkstra per cercare un albero di cammini minimi]] ma ci si ferma al primo nodo obiettivo che viene **espanso** e non si esplora quindi tutto il [[grafi|grafo]]  

è importante notare che il **goal** viene controllato solo durante l'**espansione** di quel nodo questo serve per garantire l **ottimalità**, infatti se cosi non fosse potrebbe capitare di espandere un nodo che è collegato a quello **goal** ma tramite un arco con costo alto e puo succedere che esista un altor path di costo inferiore.
questo accade ad esempio, partendo da **sibiu** e prendendo **bucarest** come goal:
![[IMG - Ricerca di costo uniforme o Dijkstra algorithm esempio bucarest.png]]

questo algoritmo può essere implementato come caso particolare del [[Ricerca Best-first|algoritmo best-first]] usando come funzione di assegnazione di costi $f$ il costo del percorso:
```pseudo
\begin{algorithm}
\caption{Uniform Cost Search}
\begin{algorithmic}
	\Function{UNIFORM-COST-SEARCH}{problem}
	\Return \Call{BEST-FIRST-SEARCH}{problem, PATH-COST}
	\EndFunction
\end{algorithmic}
\end{algorithm}
```
come nel caso del nel [[Algoritmo di Dijkstra|Algoritmo di Dijkstra standard]] non è garantito riuscire a trovare una soluzione se i costi di alcuni archi sono negativi. 

## Analisi
Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)
- $C^* =$ costo della soluzione ottima
- $\epsilon=$ costo minimo (per tutti i costi vale $c_{ij}\geq \epsilon$)

- _Strategia completa_ se costo $\epsilon >0$
- _Strategia ottimale_ se costo $\epsilon >0$
- _[[Complessita]] nel tempo_  $O(b^{1+\left\lfloor C^* /\epsilon\right\rfloor})$ 
	- $\left\lfloor C^* /\epsilon\right\rfloor$ numero di mosse ne caso peggiore
	- $+1$ per post controllo necessaria per l ottimalità
- _[[Complessita]] in spazio_ $O(b^{1+\left\lfloor C^* /\epsilon\right\rfloor})$ 

puo capitare che $O(b^{1+\left\lfloor C^* /\epsilon\right\rfloor}) \gg O(b^d)$ siccome l algoritmo può prendere [[cammini su grafi|cammini]] con costi sempre più piccoli e arrivare molto dopo alla soluzione reale
in piu se tutti i costi sono uguali l algoritmo si comporta come la [[Ricerca in ampiezza (BF)|BF]] ma con complessità diventa $O(b^{d+1})$ per spazio e tempo, questo avviene a causa **late goal test** 