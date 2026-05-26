---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Feed-forward graph models
---

# Contextual Neural Networks for Graphs (NN4G)
Le **Contextual Neural Networks for Graphs (NN4G)** sono modelli feed-forward per grafi che sostituiscono la ricerca di un punto fisso globale con una costruzione progressiva del contesto attraverso la profondita della rete. L'idea e gestire i cicli non tramite una dinamica ricorrente fino a convergenza, ma tramite **layering**: ogni layer usa il contesto prodotto dai layer precedenti e lo estende di un hop. ![[IMG - Contextual Neural Networks for Graphs (NN4G).png]]
Nel primo layer ogni nodo viene trasformato soltanto a partire dal proprio input locale. Se $x_v$ e la rappresentazione iniziale del nodo $v$, il primo embedding e una trasformazione non lineare delle sole feature del nodo; operativamente, in questo stadio la rappresentazione non e ancora relazionale, perche il nodo non guarda gli embedding correnti degli altri nodi.

Dal secondo layer in poi il contesto entra nel calcolo. La rappresentazione del nodo al layer corrente viene costruita usando gli embedding gia calcolati nei layer precedenti per i nodi del vicinato. Formalmente, se $h_v^{(l)}$ e lo stato del nodo $v$ al layer $l$ e $N(v)$ il suo vicinato, si definisce un aggiornamento feed-forward che usa contesto congelato dei layer precedenti, non interazioni ricorrenti all'interno dello stesso layer. Operativamente, dopo un layer il nodo vede il proprio intorno immediato, dopo due layer integra informazione a due hop, e cosi via; la profondita controlla quindi il raggio informativo del modello.

Le **Contextual Neural Networks for Graphs (NN4G)** risolvono i loop attraverso la profondita, non attraverso il punto fisso. Questa e la differenza fondamentale rispetto alle [[Graph Neural Networks (GNN)|Graph Neural Networks]]: nei modelli contrattivi la dinamica deve convergere, mentre qui il flusso e puramente feed-forward e il contesto arriva solo da layer precedenti gia calcolati. Il vantaggio e un addestramento molto piu semplice, spesso organizzato anche in forma **layerwise**, senza la necessita di mantenere la contrattivita dopo ogni aggiornamento dei pesi.

NN4G puo essere letto come un precursore delle moderne architetture basate sul **[[Deep Graph Networks (DGN)|message passing]]**. In entrambi i casi il nodo viene rappresentato nel proprio contesto; la differenza e che NN4G esplicita il contesto come informazione proveniente da layer precedenti congelati, mentre il message passing moderno astrarrà il processo in termini di messaggi, aggregazione e update.

Il limite principale e l'**inductive bias** legato alla profondita fissata. Se il modello viene calibrato su grafi relativamente piccoli, la sua profondita puo bastare a coprire una parte rilevante della struttura; ma applicato a grafi molto piu grandi, lo stesso numero di layer osserva solo un intorno locale ridotto. Operativamente, NN4G e piu veloce e semplice dei modelli ricorrenti contrattivi, ma generalizza meno naturalmente fuori distribuzione rispetto alla dimensione del grafo.


#### NN4G+ e l'Espansione Sinergica Doppia 
**NN4G+** e una variante incrementale delle reti neurali per grafi in cui l'architettura viene costruita progressivamente invece di essere fissata a priori e addestrata end-to-end. L'obiettivo e ridurre il costo di ricerca architetturale mantenendo una buona capacita di adattamento al problema.

Il criterio costruttivo si basa su una **doppia espansione sinergica**. Da un lato sihh aggiungono unita all'interno di un livello finche la metrica di validazione continua a migliorare; dall'altro si aggiungono nuovi livelli finche ulteriori espansioni producono ancora un guadagno. Operativamente, la crescita dell'architettura e guidata dall'errore di validazione invece che da una scelta statica del numero di layer e unita.

In questa impostazione l'apprendimento non richiede necessariamente backpropagation end-to-end su tutta la profondita. Ogni blocco nuovo viene addestrato nel contesto della struttura gia costruita, e questo riduce il costo di ottimizzazione rispetto a modelli profondi completamente ricalibrati a ogni iterazione.

NN4G+ e quindi interessante quando il problema principale non e solo la qualita della rappresentazione, ma anche il tempo di progettazione dell'architettura. Il prezzo da pagare e che la procedura greedy puo fissare precocemente scelte subottimali, soprattutto se la metrica di validazione locale non riflette bene il comportamento globale del modello.

 costruito in modo incrementale, con un'espansione sinergica doppia.

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
