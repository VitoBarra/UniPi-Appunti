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



come le [[Contextual Neural Networks for Graphs (NN4G)]], in cui il contesto viene esteso strato dopo strato senza risolvere una ricorrenza globale. Operativamente, il primo layer usa il vicinato immediato, i successivi allargano il raggio informativo, e la profondita sostituisce l'iterazione al punto fisso. ![[IMG - Contextual Neural Networks for Graphs (NN4G).png|743]]

A feedforwardapproachto processgraphs

Handle loops throughlayering

Usescontextfrom frozenearlierlayerscompute the state on the nodeatcurrentlayer

Layerwisetraining


Le **Contextual Neural Networks for Graphs (NN4G)** sono modelli feed-forward per grafi che sostituiscono la ricerca di un punto fisso globale con una costruzione progressiva del contesto attraverso la profondita della rete. L'idea e che ogni layer espanda il raggio informativo del nodo senza richiedere una dinamica ricorrente fino a convergenza.

Si parte da una rappresentazione locale del nodo e si costruiscono layer successivi che incorporano l'informazione del vicinato. Dopo un layer il nodo vede il proprio intorno immediato, dopo due layer integra informazione a due hop, e cosi via. Operativamente, la profondita della rete determina il raggio entro cui il contesto puo influenzare la rappresentazione del nodo.

NN4G puo essere letto come un precursore delle moderne [[Message Passing Neural Network (MPNN)|message passing neural networks]]. La differenza principale e che il modello nasce come architettura feed-forward contestuale, mentre nelle formulazioni moderne l'accento cade sull'astrazione di messaggio, aggregazione e update. In entrambi i casi, pero, il nodo non e rappresentato in isolamento: il suo embedding dipende progressivamente dalla struttura locale del grafo.

Il vantaggio di NN4G rispetto ai modelli ricorrenti contrattivi e la maggiore semplicita di addestramento. Il limite e che la dipendenza dal contesto resta vincolata alla profondita della rete, quindi informazione molto distante richiede molti layer e puo incontrare i problemi tipici della propagazione profonda su grafi.

Proprieta chiave:
- sostituiscono la ricorrenza globale con una costruzione feed-forward del contesto
- la profondita controlla il raggio informativo del nodo
- anticipano il paradigma moderno del message passing
- semplificano il training rispetto ai modelli contrattivi



