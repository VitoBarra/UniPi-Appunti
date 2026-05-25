---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Incremental architectures
---

# NN4G+
**NN4G+** e una variante incrementale delle reti neurali per grafi in cui l'architettura viene costruita progressivamente invece di essere fissata a priori e addestrata end-to-end. L'obiettivo e ridurre il costo di ricerca architetturale mantenendo una buona capacita di adattamento al problema.

Il criterio costruttivo si basa su una **doppia espansione sinergica**. Da un lato si aggiungono unita all'interno di un livello finche la metrica di validazione continua a migliorare; dall'altro si aggiungono nuovi livelli finche ulteriori espansioni producono ancora un guadagno. Operativamente, la crescita dell'architettura e guidata dall'errore di validazione invece che da una scelta statica del numero di layer e unita.

In questa impostazione l'apprendimento non richiede necessariamente backpropagation end-to-end su tutta la profondita. Ogni blocco nuovo viene addestrato nel contesto della struttura gia costruita, e questo riduce il costo di ottimizzazione rispetto a modelli profondi completamente ricalibrati a ogni iterazione.

NN4G+ e quindi interessante quando il problema principale non e solo la qualita della rappresentazione, ma anche il tempo di progettazione dell'architettura. Il prezzo da pagare e che la procedura greedy puo fissare precocemente scelte subottimali, soprattutto se la metrica di validazione locale non riflette bene il comportamento globale del modello.

Proprieta chiave:
- costruisce l'architettura in modo incrementale e greedily guided
- usa la validazione per decidere espansione in ampiezza e profondita
- riduce il costo della selezione architetturale
- puo sacrificare ottimalita globale per velocita di costruzione




#### NN4G+ e l'Espansione Sinergica Doppia 

[[Contextual Neural Networks for Graphs Plus (NN4G+)]] e costruito in modo incrementale, con un'espansione sinergica doppia.

- Alleniamo un'unità alla volta: nessun backprop end-to-end attraverso i livelli.
- Un livello viene espanso in modo greedy fino a quando l'accuratezza di validazione non migliora più.
- Nuovi livelli vengono aggiunti fino a quando l'accuratezza di validazione non migliora più.


![[IMG- NN4G+ automatic architecture.png]]


NN4G+ costruisce un'architettura neurale in **minuti** invece che in **ore**, rispetto ai modelli addestrati end-to-end.  
![[IMG - NN4G+ arctecture graph.png]]

- In un confronto equo con la selezione esplicita dell'architettura, **NN4G+ accelera di oltre 10×** senza penalizzare l'accuratezza.  
  ![[IMG- NN4G+ training and selection time.png]]



alcune problematiche sono:
- **Over-smoothing**: con l’aumento della profondità, grazie al meccanismo del message passing le rappresentazioni ad alto livello tendono a diventare simili ovvero i diventano indistinguibili
	- ![[IMG-NN4G+ over smothing.png]]
- __Over-squashing__: I campi ricettivi aumentano **esponenzialmente** con la profondità, mentre la dimensione dell'embedding del nodo rimane fissa 
	- Decrescita esponenziale della sensibilità delle rappresentazioni dei nodi rispetto alle feature in ingresso.  
	- Questo effetto è quantificato attraverso il **Jacobiano**, in funzione del numero di layer $h_v^{(L)}$
	- ![[IMG - NN4G+ over squashing.png]]

 
 un altro broblema è la difficolta di classificazone di grafi __eterofili__ siccome il __message passing__ introduce un Bias verso grafi omogenei, con difficoltà nell'adattarsi a strutture eterofile.  
 __HomoPhilic graph__ : I nodi nello stesso vicinato appartengono prevalentemente alla stessa classe.  
__EteroPhilic graph__: I nodi della stessa classe tendono a essere più distanti tra loro.  
   
![[IMG - HomoPhilic EteroPhilic graphs.png]]
