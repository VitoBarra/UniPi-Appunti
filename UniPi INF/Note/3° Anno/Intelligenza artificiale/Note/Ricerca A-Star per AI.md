---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Ricerca A* per AI
---
L A diverso da A* è un [[Algoritmi di ricerca informati per AI|Algoritmo di ricerca Informato]] di tipo Best-Frist  funziona come la [[Ricerca di costo uniforme UC-AI|UC]] ma utilizza nella [[Coda di Priorita|Coda di priorita]] la funzione $$f(n) = g(n)+h(n)$$
dove
- $g(n)$ è il costo del cammino dal nodo di partenza al nodo $n$
- $h(n)$ è il la funzione di valutazione euristica



## Completezza di A
- _Strategia completa_ se $g(n) \geq d(n) \cdot \epsilon$  dove $\epsilon >0$ costo minimo di un arco
	- Questo evita situazioni di crescita infinitesimale 
	- ![[B0F514AF-3C33-4EF1-B79C-E769A852BD4E.jpeg]]
	- ##### Dimostrazione 
	- Sia $n’$ un nodo nella _frontiera_  che è sul cammino che porta al nodo goal
	- $n’$ prima o poi verrà espanso siccome non possono esiste  infiniti nodi con $f(x) \leq f(n’)$
	- questo deriva dalla condizione imposta per la completezza
		- Non può esiste un percorso infinito con archi a crescita infinitesimale
	- iterando prima o poi si arriva al goal 


### Stima ideale
la funzione di valutazione ideale è definita come:
$$f^*(n)=g^*(n)+h^*(n)$$
dove 
- $g^*(n)$ costo del cammino minimo da radica a $n$
- $h^*(n)$ costo del cammino minimo da $n$ a goal
- $f^*(n)$ costo del cammino minimo da nodo radice a nodo goal, passando $n$

in casi non ideali abbiamo:
- $g(n) \geq g^*(n)$ 
- $h(n)$ è una stima di $h^*(n)$ 
	- quindi si può sia sovrastimare che sottostimare
	 
## Ammissibilità di un euristica
un euristica ammissibile è una sottostima di $h^*$	 $$\forall n.h(n) \leq h^*(n)$$
per essere anche una buona euristica il nodo goal deve avere distanza 0


### Algoritmo A*
l gli algoritmi $A^*$ sono algoritmi di tipo $A$ con una funzione d _euristica ammissibile

>[!note]
>[[Ricerca in ampiezza BF-AI|BF]] e [[Ricerca di costo uniforme UC-AI|UC]] sono ottimali siccome equivale a fare un $A^*$ con $h(n)=0$


### Ottimalità di A*
_Strategia ottima_ caso ad _albero_
_Strategia ottima_ caso a _grafo_ sotto condizione forti come la _Consistenza_ (o detta _monotonicità_)

#### Consistenza di un euristica
Un euristica consistente è un euristica per cui valgono le seguenti proprietà
- $\forall n.h(n) \leq c(n,a,n’) + h(n’)$
	- Dove $n’$ è un successore di $n$
	- $c(n,a,n’)$ è il costo per passare dal nodo $n$ al nodo $n’$ tramite l azione $a$
	- questa formula viene direttamente dal [[Diseguaglianza triangolare|diseguaglianza triangolare]]
-  da cui possiamo dire $f(n) \leq f(n’)$ 
	- $f$ non decresce mai da qui il termine [[Funzione Monotona|Monotona]]
	
	
#### Teorema di ottimalità di A*
1. $f$ è [[Funzione Monotona|Monotona]]
	- ##### Dimostrazione 
		- $$\begin{equation}
			\begin{split}
			&h(n) \leq c(n,a,n’) + h(n’)&= \\
			&g(n)+h(n) \leq c(n,a,n’)+g(n) + h(n’) &=\\
			&g(n)+h(n) \leq g(n’)+h(n’) &= \\
			&f(n) \leq f(n’)
			\end{split}
			\end{equation}$$
2. Ogni volta che A* seleziona un nodo per l’espansione, il cammino ottimo a tale nodo è stato trovato 
	- se così non fosse,  ci sarebbe un altro nodo nella frontiera sul cammino ottimo  per arrivare ad $n$, con $f(m)$ minore (da _monotonicita_)  ma ciò non è possibile perché tale nodo sarebbe già stato espanso (**si espande prima un nodo con f minore**)
3.  Quando seleziona nodo goal è cammino ottimo $[h=0, f=C*]$


### Vantaggi di A*
- $A*$ espande tutti i nodi con $f(n) <C^*$    
- $A*$ espande  alcuni nodi con $f(n) =C^*$ 
- $A*$ non espande alcun nodo con $f(n) > C^*$ 

Quindi alcuni nodi (e suoi sottoalberi) non verranno considerati per l’ espansione (ma restiamo ottimali):
	_pruning_ (h opportuna, più alta possibile tra le ammissibili, fa tagliare molto )


Commenti : 
- con $f(n) > C^*$ Più $f$ è aderente a stima ottimale, più taglio!  
- Cercheremo quindi una h il più alta possibile tra le ammissibili
-  Se molto bassa molti (sino a tutti i) nodi restano minore di $C*$ 
	- Il espando tutti 
- pruning sottoalberi è il punto focale: non li abbiamo già in memoria e evitiamo di generarli  ( decisivo per i problemi di AI a spazio stati esponenziali )


> [!nota]
>   alcuni algoritmi possono essere considerati come casi speciali di A dove:
>  - [[Ricerca di costo uniforme UC-AI|UC]] : con $f(n)= g(n)$ e quindi  $h(n) = 0$, diventa [[Ricerca in ampiezza BF-AI|BF]] se costi tutti uguali
>  - [[Ricerca Greedy best-frist AI|Greedy best-frist]]: con $f(n)= h(n)$ e quindi  $g(n) = 0$
>  - [[Ricerca in profondita DF-AI|DF]]:





