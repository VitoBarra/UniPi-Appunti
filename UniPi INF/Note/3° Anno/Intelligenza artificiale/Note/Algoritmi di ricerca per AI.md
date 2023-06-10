---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Algoritmi di ricerca per AI
---
questi sono utilizzati dai [[Agenti risolutori di problemi]] sotto le seguenti  assunzioni sul [[Definizione di problemi per AI - Ambienti|Ambiente]] , questo è
            _Statico_ | _Osservabile_ | _Discreto_ | _Deterministico_

### Algoritmi di ricerca
- Gli _algoritmi di ricerca_ prendono in input un problema e restituiscono un __cammino soluzione__. questa fase si chiama _ricerca_, i.e. un cammino che porta dallo stato iniziale a uno stato _goal_ 
- Misura delle prestazioni 
	- Trova una soluzione? Quanto costa trovarla? Quanto efficiente è la soluzione? 
	- Costo totale = costo della ricerca + costo del cammino soluzione
		- Possiamo valutare gli algoritmi sul costo della ricerca e ottimizzare il costo del cammino


Definito il problema si passa alla ricerca della soluzione. per farlo si utilizza una [[Albero struttura dati|Albero]] _di ricerca_ sovrapposto allo _spazio degli stati_. non è pero detto che un nodo sia uno stato diverso, si possono rincontrare stati già incontrati durante l esplorazione del albero.

Un _nodo_ $n$ è una struttura dati con quattro componenti: 
- Uno stato: $n.stato$ 
- Il nodo padre: $n.padre$
- L’azione effettuata per generarlo: $n.azione$ 
- Il costo del _cammino dal nodo iniziale al nodo_ $n$: n.costo-cammino indicata come $g(n)$ (=padre.costo-cammino+costo-passo ultimo)

 _Frontiera_: lista dei nodi in attesa di essere espansi (le foglie dell’albero di ricerca).  
- La frontiera è implementata come da una collezione stati
	- Diverse implementazioni di coda portano a _stratagie_ diverse. queste possono essere determinanti e possono cambiare la [[Complessita]] del algoritmo di ricerca  


#### Criteri di valutazione delle strategie di ricerca
- _Completezza_: se la soluzione esiste viene trovata 
- _Ottimalità_ (ammissibilità): trova la soluzione migliore, con costo minore (per il «costo del cammino soluzione») 
- _[[Complessita]] in tempo_: tempo richiesto per trovare la soluzione (costo di ricerca)
- _[[Complessita]] in spazio_: memoria richiesta (costo di ricerca)



## Complicanze  e note
![[Pasted image 20230212032701.png]]
![[Pasted image 20230212032712.png]]



### Algoritmi ricerche non informate:
1. [[Ricerca in ampiezza BF-AI]]
2. [[Ricerca in profondita DF-AI]] 
3. [[Ricerca in profondità limitata DL-AI]] 
4. [[Ricerca con approfondimento iterativo ID-AI]] 
5. [[Ricerca di costo uniforme UC-AI]]
6. [[Ricerca Bidirezionale bi-AI]]
7. ![[Pasted image 20230212032210.png]]
[[Algoritmi di ricerca informati per AI]] con euristiche:

