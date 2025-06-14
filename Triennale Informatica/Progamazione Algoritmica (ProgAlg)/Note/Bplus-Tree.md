---
Course: "[[Programmazione e Algoritmica (PEA)]]"
topic: "[[Strutture Dati]]"
tags:
  - PEA
---

# Struttura dati - Bplus-Tree
---
I **Bplus-Tree** sono una [[Strutture Dati|struttura dati]] basata sul [[B-Tree|B-tree]], caratterizzata dalla particolare organizzazione dei dati che risiedono esclusivamente nelle foglie. La differenza principale rispetto al [[B-Tree|B-tree]] risiede proprio in questa separazione tra nodi interni e foglie: i nodi interni contengono solamente chiavi utilizzate per la navigazione e l'indirizzamento, mentre le foglie contengono sia le chiavi sia i dati associati.

Ogni nodo interno del **Bplus-Tree** agisce come un indice per facilitare l'accesso ai dati nelle foglie. La struttura mantiene il bilanciamento grazie al rispetto delle proprietà dei [[B-Tree|B-tree]], garantendo una profondità uniforme per tutte le foglie. Questo implica che il tempo di accesso a qualsiasi dato sia costante in termini di numero di livelli da attraversare, contribuendo a prestazioni stabili anche con grandi moli di dati.

In un **Bplus-Tree** di ordine $m$, ogni nodo interno può contenere fino a $m - 1$ chiavi e $m$ figli. Le foglie, invece, possono contenere fino a $m - 1$ coppie chiave-dato. Formalmente:
- numero massimo di figli per nodo interno: $m$
- numero minimo di figli per nodo interno (eccetto la radice): $\lceil \frac{m}{2} \rceil$
- numero massimo di chiavi per foglia: $m - 1$
- numero minimo di chiavi per foglia: $\lceil \frac{m}{2} \rceil - 1$

Una caratteristica peculiare delle foglie è la loro connessione tramite puntatori che formano una lista collegata, permettendo scansioni sequenziali efficienti dei dati. Questo collegamento orizzontale delle foglie favorisce le operazioni di range query e la lettura ordinata dei dati.

L’inserimento in un **Bplus-Tree** segue la logica di inserire la nuova chiave nella foglia appropriata. Qualora la foglia superi il numero massimo di chiavi consentito, avviene una suddivisione (split) e la chiave mediana viene promossa al nodo genitore. Tale propagazione dello split può continuare ricorsivamente fino alla radice, dove potrebbe generare la creazione di una nuova radice e, conseguentemente, un incremento della profondità dell’albero.

Analogamente, la cancellazione richiede che, in seguito alla rimozione di una chiave, venga verificato il rispetto del numero minimo di chiavi. Se necessario, può avvenire una fusione (merge) o un prestito (redistribution) da nodi fratelli, con eventuale propagazione verso l’alto per mantenere le proprietà strutturali dell’albero.

I **Bplus-Tree** trovano vasta applicazione nei sistemi di gestione di basi di dati e nei file system, dove la loro capacità di gestire efficientemente grandi quantità di dati su memoria secondaria rappresenta un vantaggio significativo rispetto ad altre [[Strutture Dati|strutture dati]].
