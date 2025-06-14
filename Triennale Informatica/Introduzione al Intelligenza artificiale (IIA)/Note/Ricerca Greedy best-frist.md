---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: "[[Algoritmi di ricerca informata]]"
tags:
  - IIA
  - AIF
---

# Ricerca Greedy best-frist
---
il **Ricerca Greedy best-frist** è un [[Algoritmi di ricerca informata|Algoritmo di ricerca informata]] variante della [[Ricerca Best-first|ricerca best-first]] 
in questo algoritmo si scegli sempre il nodo che, usando la stima data dl **euristica** $h(x)$ , risulta essere il piu vicino possibile allo stato **goal**, per fare ciò si pone la **funzione di valutazione** $f$  uguale alla funzione di **valutazione euristica**$$f(x)=h(x)$$ 
```pseudo
\begin{algorithm}
\caption{Greedy Best-frist Search}
\begin{algorithmic}
	\Function{GREEDY-BEST-FRIST}{problem}
	\Return \Call{BEST-FIRST-SEARCH}{problem, h}
	\EndFunction
\end{algorithmic}
\end{algorithm}
```



## Analisi della complessità
Sia 
- $b=$ fattore di ramificazione (*B*ranching), quindi il numero massimo di successori
- $d=$ profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)

 Spazi **finiti**:
- **NON ottimale**: puo dare una soluzione non ottimale
- **NON completa**: puo incastrarsi in cicli, gestibile con checking di ripetizione di stati 
- **[[Complessita|Complessità spazio]]** (nodi in memoria): $O(b^m)$ tiene tutti  i nodi in memoria
- **[[Complessita|Complessità nel tempo]]** (nodi generati): $O(b^m)$ ma si puo abbassare a $O(bm)$ con una buona **euristica** in alcuni problemi


Spazi di **infiniti**:
- **NON ottimale**: può incontrare uno stato goal senza aver controllato altri percorsi magari migliori.
- **NON completa**: può restare incastrato in discese infinite anche senza la presenza di cicli.
- **[[Complessita|Complessità spazio]]**: $O(b^m)$  puo non terminare
- **[[Complessita|Complessità nel tempo]]**: $O(b^m)$  puo non terminare


