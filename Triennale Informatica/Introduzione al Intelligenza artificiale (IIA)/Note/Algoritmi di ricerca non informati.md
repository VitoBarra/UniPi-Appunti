---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---

# Algoritmi di ricerca
---
Gli **algoritmi di ricerca** sono [[algoritmi|algoritmi]] per risolvere [[Problemi di ricerca|Problemi di ricerca]]. Questi algoritmi operano esplorando sistematicamente lo spazio degli stati, generando un [[Alberi|albero di ricerca]] sul [[grafi|grafo]] dello **spazio degli stati** dove ogni nodo corrisponde a uno **stato del problema** e gli archi rappresentano le **azioni** che portano a stati successivi. 

La **ricerca** inizia dallo **stato iniziale** (radice dell'albero) e procede **espandendo** i nodi, ovvero **generando** i rispettivi nodi figli attraverso l'applicazione delle azioni disponibili.
importanti sono i concetti di  
- **frontiera**: è una lista nodi non ancora **espansi**. ovvero le foglie del **albero di ricerca**  La strategia con cui si selezionano i nodi dalla frontiera determina le **proprietà dell'algoritmo**, influenzando sia la completezza che l'efficienza.
- i nodi **raggiunti** sono tutti i nodi che sono stati generati, sia quelli espansi che quelli non ancora espansi .

la **frontiera** separa lo spazio degli stati in due regioni ben distinte quella **interna** degli stati esplorati e quella **esterna** degli stati non ancora **raggiunti**
![[IMG - frontiera che divider stati esplorati e non raggiunti.png]]

Nell'ambito degli algoritmi di ricerca, l **[[alberi|albero]] di ricerca** è fondamentale per tracciare l'esplorazione degli stati, ciascun nodo $n$ è strutturato come un oggetto con quattro componenti chiave:  
- **$n.STATE$**: rappresenta lo stato associato al nodo corrente.  
- **$n.PARENT$**: riferisce al nodo genitore che ha generato il nodo corrente, permettendo la ricostruzione del cammino.  
- **$n.ACTION$**: l'azione applicata allo stato del genitore per ottenere lo stato corrente.  
- **$n.PATH\text{-}COST$**: il costo totale del percorso dallo stato iniziale al nodo corrente, spesso indicato come $g(n)$.  

La **frontiera**, ovvero l'insieme dei nodi da esplorare, è gestita tramite una **[[Coda (FIFO)|coda]]**. Le operazioni principali supportate sono:  
- **$IS\text{-}EMPTY(frontier)$**: verifica se la frontiera è vuota.  
- **$POP(frontier)$**: rimuove e restituisce il nodo in testa alla coda.  
- **$TOP(frontier)$**: restituisce il nodo in testa senza rimuoverlo.  
- **$ADD(node, frontier)$**: inserisce un nodo nella posizione appropriata, in base al tipo di coda. 
La tipologia di coda scelta definisce la strategia di ricerca. 
  
Gli stati già raggiunti sono memorizzati in una [[Hash Table|hash table]], dove ogni chiave è uno stato e il valore corrispondente è il nodo associato. Questa struttura ottimizza il controllo dei duplicati e la gestione dei cammini alternativi. 


uno dei problemi della ricerca su alberi sono i **repeated states** e i **redundant paths** rappresenta una sfida significativa per l'efficienza computazionale.
- Un ***repeated state*** si verifica quando uno stato viene raggiunto più volte attraverso percorsi diversi. Questo fenomeno può trasformare un albero di ricerca finito in una struttura infinita se non gestito adeguatamente.
- I ***redundant paths***, invece, sono percorsi alternativi che conducono allo stesso stato ma con costi maggiori.![[IMG - algoritmi di ricerca cammini ridontandi.png]]
Tre approcci principali emergono per mitigare questi problemi:  
1. **Memorizzazione degli stati raggiunti**: Utilizzato negli algoritmi di **graph search**, mantiene una tabella degli stati visitati per eliminare percorsi ridondanti. Questo metodo è ottimale quando la memoria disponibile può contenere l'intera tabella.
2. **Ignorare gli stati ripetuti**: In problemi dove i percorsi ridondanti sono impossibili o rari, un **tree-like search** può essere preferibile per risparmiare memoria, accettando una potenziale riduzione di performance.  
3. **Compromesso ciclico**: Verifica la presenza di cicli esaminando la catena di padri di un nodo senza memorizzazione aggiuntiva. Alcune implementazioni limitano la profondità di questa verifica.  


### Valutazione dei algoritmi di ricerca
La **valutazione degli algoritmi di ricerca** si basa su quattro criteri fondamentali:  

- **Completezza**:  Un algoritmo è completo se è __potenzialmente__ in grado di raggiungere tutti i nodi dello **spazio degli stati**  
	- **spazi finiti**: garantisce di trovare una soluzione quando esiste o segnalare correttamente l'assenza di soluzioni.
	- **spazi infiniti**: serve una ricerca sistematica che se esiste prima o poi trova una soluzione o non termina mai.
- **Ottimalità**:  Garantisce che la soluzione trovata abbia il **costo minimo** tra tutte quelle possibili.  
- **[[Complessita|Complessità in tempo]]**: il numero Numero di stati/azioni valutati per trovare una soluzione.  
- **[[Complessita|Complessità in spazio]]**:  Memoria necessaria per memorizzare i nodi durante la ricerca. e *Dipende dalla* Strategia di esplorazione.  


l albero di esplorazione è solitamente tenuto implicito e non esplicitamente come struttura dati, quindi per misurare la complessità di tempo in questi tipi di algoritmi si solitamente usa 3 fattori
- $d$: profondità della soluzione ottimale (n° di azioni necessarie).  
- $b$: **branching factor** (n° medio di successori per nodo).  
- $m$: numero massimo di azione in ogni path 
- $\varepsilon$ : in piccolo valore sitivo che setta il costo minimo che un arco deve avere.



alcuni algoritmi sono:
1. [[Ricerca in ampiezza (BF)]]
2. [[Ricerca in profondita (DF)]] 
3. [[Ricerca in profondita limitata (DLS)]] 
4. [[Ricerca con approfondimento iterativo (IDS)]] 
5. [[Ricerca di costo uniforme o Dijkstra algorithm (UC)]]
6. [[Ricerca Bidirezionale]]

Un confronto tra questi algoritmi tenendo in considerazione solo la ricerca su strutture ad albero e senza controllo dei path ridondanti si ha:

| Criterio  | BF       | UC                                        | DF       | DL       | ID       | Bidir        |
| --------- | -------- | ----------------------------------------- | -------- | -------- | -------- | ------------ |
| Complete? | si       | si(^)                                     | no       | si(+)    | si       | si(ˆx)       |
| Ottimale? | si(\*)   | si(^)                                     | no       | no       | si(\*)   | si(ˆx)       |
| Tempo     | $O(b^d)$ | $O(b^{1+\lfloor C^*/\varepsilon\rfloor})$ | $O(b^m)$ | $O(b^l)$ | $O(b^d)$ | $O(b^{d/2})$ |
| Spazio    | $O(b^d)$ | $O(b^{\lfloor1+C^*/\varepsilon \rfloor})$ | $O(b^m)$ | $O(b^l)$ | $O(b^d)$ | $O(b^{d/2})$ |

**Note:**  
- (\*) se gli operatori/archi hanno tutti lo stesso costo  
- (^) per costi degli archi $\geq  \varepsilon > 0$  
- (+) per problemi per cui si conosce un limite alla profondità della soluzione (se $\ell > d$)  
- (ˆx) usando UC (o BF)
