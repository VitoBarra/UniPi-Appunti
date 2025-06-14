---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi filogenetica - metodi basati massima parsimonia
---
L’**Massima parsimonia per l [[Analisi Filogenetica|analisi filogenetica]]** è un approccio che costruisce **alberi filogenetici** scegliendo la topologia capace di spiegare i dati osservati attraverso il numero minimo di cambiamenti evolutivi complessivi. In questo metodo l’albero filogenetico viene interpretato come una rappresentazione in cui le mutazioni sono eventi discreti, e la soluzione migliore è quella che richiede il minor numero totale di trasformazioni lungo i rami. L’obiettivo è quello di minimizzare il numero di mutazioni necessarie affinché le sequenze osservate possano derivare da un insieme coerente di antenati intermedi.

Il processo operativo tipico parte dall’[[Allineamento di sequenze|allineamento di sequenze]] [[Allineamento di sequenze multiple (MSA)|multiplo]], da cui vengono selezionate le colonne informative, cioè quelle posizioni che contribuiscono effettivamente a discriminare tra diverse possibili topologie. La costruzione dell’albero consiste quindi nella ricerca della struttura che richiede il numero minimo di mutazioni, secondo un principio di economia evolutiva.

Formalmente, il problema può essere espresso come una minimizzazione del costo complessivo associato ai cambiamenti lungo i rami:$$\text{score}(T)=\sum \text{mutazioni richieste sui caratteri}$$La soluzione più semplice consisterebbe nell’enumerare tutti i possibili alberi e calcolarne il costo, ma questo approccio è computazionalmente proibitivo, poiché la ricerca è un problema [[Classi di complessita - NP-Hard]] ed è praticabile solo per insiemi molto piccoli di sequenze, solitamente il numero massimo è $10$.

Per affrontare la complessità, vengono impiegate strategie esatte come il metodo [[Branch and Bound|branch and bound]]. Questo algoritmo costruisce alberi in modo incrementale, combinando una crescita sistematica delle topologie con un meccanismo di eliminazione basato su un limite inferiore di parsimonia.

Il funzionamento può essere descritto come segue:
1. viene calcolato un best score iniziale, ad esempio tramite un albero ottenuto con un metodo euristico rapido  
2. la ricerca parte da un albero molto piccolo, tipicamente con $3$–$4$ taxa trovato velocemente in modo euristico
3. un nuovo taxon viene aggiunto in tutte le posizioni possibili, generando diversi alberi parziali (branch)  
4. per ogni albero parziale viene stimato un bound, cioè il numero minimo di mutazioni che l’albero è già costretto ad avere, indipendentemente dall’inserimento dei taxa rimanenti  
5. se vale la condizione:$$\text{bound} \geq \text{best score}$$il ramo viene eliminato (prune), perché non può portare a soluzioni migliori  
6. se invece il bound è inferiore, l’albero viene mantenuto ed espanso ulteriormente  
7. quando viene costruito un albero completo, se il suo punteggio è più basso, il best score viene aggiornato  
8. la procedura continua finché tutti i rami sono stati completati oppure eliminati  

Gli alberi che rimangono associati al punteggio minimo costituiscono l’insieme delle soluzioni più parsimoniose e si prende il migliore a fine del processo.
