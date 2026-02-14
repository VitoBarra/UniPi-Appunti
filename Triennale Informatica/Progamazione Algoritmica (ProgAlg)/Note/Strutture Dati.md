---
Course: "[[Programmazione e Algoritmica (PEA)]]"
topic: "[[Strutture Dati]]"
tags:
  - PEA
---
# Strutture Dati
---
una struttura dati è un’organizzazione formale dei dati in memoria definita da vincoli strutturali, relazioni tra elementi e operazioni ammissibili, con l’obiettivo di rendere efficienti accesso, aggiornamento e gestione dell’informazione in funzione di specifiche esigenze computazionali. una struttura dati non è soltanto un contenitore di valori, ma un’astrazione che stabilisce come i dati sono disposti, collegati e manipolati attraverso un insieme di operazioni primitive che costituiscono la sua interfaccia logica.

la definizione di una struttura dati implica tre componenti: il dominio dei dati memorizzabili, la rappresentazione interna in memoria e l’insieme di operazioni consentite. la rappresentazione determina la disposizione fisica o logica degli elementi (contigua, collegata, gerarchica, indicizzata), mentre le operazioni definiscono l’interazione con la struttura (lettura, inserimento, cancellazione, aggiornamento, ricerca, iterazione). l’interfaccia astrae i dettagli implementativi e stabilisce un contratto tra utilizzatore e struttura.

le strutture dati possono essere classificate secondo diversi criteri. rispetto alla forma, si distinguono strutture lineari e non lineari: nelle strutture lineari gli elementi sono organizzati in sequenza con una relazione di precedenza (array, liste, pile, code), mentre nelle strutture non lineari le relazioni possono essere gerarchiche o reticolari (alberi, grafi). rispetto alla gestione della memoria, si distinguono strutture statiche, con dimensione fissata a priori, e dinamiche, che possono crescere o ridursi durante l’esecuzione. rispetto al livello di astrazione, si distinguono strutture concrete (array, liste collegate) e tipi di dato astratti, in cui l’attenzione è posta sulle operazioni e non sulla rappresentazione.

una struttura dati è progettata in funzione delle operazioni dominanti e dei vincoli di complessità temporale e spaziale. ogni operazione ha un costo computazionale che dipende dalla dimensione $n$ della struttura e dalla sua organizzazione interna; la progettazione consiste nel bilanciare tali costi. per esempio, una struttura ottimizzata per l’accesso diretto privilegia la contiguità in memoria, mentre una struttura ottimizzata per inserimenti e cancellazioni frequenti privilegia collegamenti dinamici tra nodi.

la nozione di accesso ai dati comprende modalità diverse: accesso diretto tramite indice, accesso sequenziale tramite iterazione, accesso basato su chiave mediante funzioni di ricerca o hashing. l’aggiunta e la rimozione possono avvenire in posizioni specifiche o secondo regole imposte dalla struttura stessa, come nelle pile (politica LIFO) o nelle code (politica FIFO). tali vincoli definiscono il comportamento semantico della struttura e ne determinano gli invarianti, cioè proprietà che devono rimanere vere dopo ogni operazione.

una struttura dati mantiene invarianti strutturali e relazionali: ordinamenti, proprietà di bilanciamento, relazioni padre-figlio, connettività tra nodi. le operazioni devono preservare tali invarianti per garantire correttezza e prevedibilità. l’implementazione concreta utilizza allocazione di memoria, puntatori o indici, e meccanismi di gestione dello spazio per rappresentare le relazioni tra elementi.

nel contesto della progettazione algoritmica, le strutture dati sono inseparabili dagli algoritmi che le utilizzano. la scelta della struttura dati determina l’efficienza globale di un sistema e influisce sulla complessità asintotica delle operazioni principali. l’astrazione di struttura dati consente di separare il livello logico da quello implementativo, favorendo modularità, riuso e analisi formale delle prestazioni.
