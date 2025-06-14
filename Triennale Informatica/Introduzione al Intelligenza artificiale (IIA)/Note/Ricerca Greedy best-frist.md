---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: "[[Algoritmi di ricerca informati]]"
tags:
  - IA
  - AIF
---

# Ricerca Greedy best-frist
---
il **Ricerca Greedy best-frist** è un [[Algoritmi di ricerca informati|Algoritmo di ricerca informata]] variante della [[Ricerca Best-first|ricerca best-rist]] 
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
- **completa**: se la soluzione non esiste prima o poi esplora tutto lo spazio
- **[[Complessita|Complessità spazio]]** (nodi in memoria): $O()$ 
- **[[Complessita|Complessità nel tempo]]** (nodi generati): $O(|V|)$  ma si puo abbassare a $O(bm)$ con una buona **euristca** in alcuni problemi


Spazi di **Non finit**:
- **NON ottimale**: può incontrare uno stato goal senza aver controllato altri percorsi magari migliori.
- **NON completa**: può restare incastrato in discese infinite anche senza la presenza di cicli.
- **[[Complessita|Complessità spazio]]**: $O(\infty)$
- **[[Complessita|Complessità nel tempo]]**: $O(\infty)$ 


