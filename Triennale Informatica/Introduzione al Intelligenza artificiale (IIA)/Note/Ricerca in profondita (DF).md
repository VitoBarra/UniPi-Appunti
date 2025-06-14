---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca in profondità (DF)
---
la **Ricerca in profondità** o **depth-first** (**DF**) è un [[Algoritmi di ricerca|Algoritmo di ricerca]] che utilizza una **frontiera** implementata con una  [[Coda (FIFO)|coda LIFO]], ogni volta che arriva in un nodo in cui non sono generati nuovi nodi fa da un taglio su i rami completamente esplorati diminuendo il consumo di memoria.
![[IMG - Ricerca in profondita.png]]

questo algoritmo puo essere implementato come caso particolare del [[Ricerca Best-first|algoritmo best-first]] usando come funzione di assegnazione di costi $f$ il negativo della profondita:
```pseudo
\begin{algorithm}
\caption{Uniform Cost Search}
\begin{algorithmic}
	\Function{UNIFORM-COST-SEARCH}{problem}
	\Return \Call{BEST-FIRST-SEARCH}{problem, - DEPTH}
	\EndFunction
\end{algorithmic}
\end{algorithm}
```
ma spesso è implementato **evitando di mantenere un tabella per i nodi raggiunti** e quando un nodo non ha piu un successore si usa la relazione padre per tornare in dietro fino al prossimo nodo piu profondo non esplorato, Questa implementazione permette di mantenere in memoria solo la **frontiera** 

In generale ritorna il primo stato **goal** trovato

### Analisi della complessità
Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)


in spazzi degli stati ad [[Alberi|albero]] e Finiti:
- **_NON ottimale_**: Può incontrare  uno stato goal senza aver controllato altri percorsi magari migliori
- **Completa**: se non c è soluzione esplorerà tutto lo spazio
- **_[[Complessita|Complessità spazio]]_** (nodi in memoria): $O(bm)$ _Cammino dalla radice al nodo_ + _fratelli inesplorati_ 
- **_[[Complessita|Complessità nel tempo]]_** (nodi generati) $O(b^m)$ che potrebbe essere maggiore $O(b^d)$  

in spazzi __grafi aciclici__ e Finiti:
- **_NON ottimale_**: Può incontrare  uno stato goal senza aver controllato altri percorsi magari migliori
- __Completa__: se non c è soluzione prima o poi esplora tutto lo spazio eventualmente **espandendo** piu volte su uno stesso nodo. 
  
in spazzi __grafi ciclici__ e Finiti:
- **_NON ottimale_**: Può incontrare  uno stato goal senza aver controllato altri percorsi magari migliori
- __NON Completa__: puo rimanere incastrato in cicli infiniti, eventualmente risolvibile con **[[Algoritmi di riconoscimento cicli|cycle detection]]** ma aumenta il costo di memoria
  
in spazzi __di qualsiasi tipo__ e infiniti:
- **_NON ottimale_**: Può incontrare  uno stato goal senza aver controllato altri percorsi magari migliori
- **NON Completa**: puo restare incastrato in discese infinite, anche senza presenza di cicli



