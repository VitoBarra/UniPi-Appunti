---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Genoma
---
Il **genoma** e' l'insieme completo del materiale genetico di un organismo, cioe' la totalita' delle sequenze di [[DNA|DNA]] che contengono, organizzano e regolano l'informazione ereditaria. Negli organismi cellulari il genoma e' organizzato in cromosomi; in altri sistemi biologici, come virus o plasmidi, puo' essere contenuto in molecole genetiche piu' semplici.

Il genoma non coincide con un singolo [[Gene|gene]] e non corrisponde soltanto alle regioni che codificano proteine. Comprende anche regioni regolative, sequenze ripetute, regioni intergeniche, introni, elementi mobili, varianti e altre porzioni che contribuiscono alla struttura, alla regolazione e all'evoluzione del sistema biologico.

## Genoma e DNA

Il [[DNA|DNA]] e' la molecola fisica che immagazzina l'informazione genetica; il genoma e' il contenuto informativo complessivo organizzato in quella molecola. Questa distinzione e' utile per separare il livello chimico-molecolare dal livello informazionale e computazionale.

Un [[Gene|gene]] e' una regione del genoma associata alla produzione di un prodotto funzionale, come un [[RNA|RNA]] o una proteina. Il trascrittoma, invece, e' l'insieme dei trascritti effettivamente prodotti in una cellula, tessuto o condizione: rappresenta quindi solo la parte del genoma che viene espressa in un certo contesto.

## Come si ottiene

Dal punto di vista sperimentale, una sequenza genomica si ottiene tramite [[Tecnologie di sequenziamento|tecnologie di sequenziamento]]. Poiche' i sequenziatori producono frammenti brevi o lunghi chiamati read, il genoma non viene normalmente letto come una singola sequenza continua. Le read devono essere controllate, filtrate e poi:

- allineate a un genoma di riferimento, se esiste una sequenza gia' disponibile;
- assemblate, se si vuole ricostruire una sequenza genomica senza affidarsi completamente a un riferimento;
- confrontate con altre sequenze per identificare varianti, regioni conservate o differenze strutturali.

Il risultato puo' essere una **sequenza di riferimento**, cioe' una rappresentazione curata del genoma usata come coordinate comuni per analisi successive. Un genoma di riferimento non e' il genoma di ogni individuo, ma una rappresentazione utile per mappare read, annotare regioni e confrontare campioni.

## Uso nell'analisi bioinformatica

In bioinformatica il genoma e' usato come spazio di riferimento su cui collocare dati sperimentali. Le read di un esperimento possono essere mappate sul genoma per stabilire da quale regione provengono; le varianti possono essere descritte tramite coordinate genomiche; i segnali sperimentali possono essere confrontati con geni, promotori, esoni o regioni regolative.

Il genoma diventa quindi una struttura coordinata su cui integrare livelli informativi diversi: sequenza, varianti, espressione, regolazione, conservazione evolutiva e dati epigenomici. Per rendere interpretabile questa struttura servono le [[Annotazione genomica|annotazioni genomiche]], che associano significato biologico a regioni specifiche della sequenza.
