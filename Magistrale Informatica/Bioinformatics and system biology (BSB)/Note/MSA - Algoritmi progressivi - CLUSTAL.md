---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# MSA - Algoritmi progressivi - CLUSTAL
---
**CLUSTAL** è una famiglia di algoritmi per l’**[[Allineamento di sequenze multiple (MSA)|allineamento di sequenze multiple (MSA)]]** basata su un **approccio progressivo**, progettata per costruire un allineamento globale di più sequenze a partire da [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche|confronti pairwise]]. L’idea centrale è che sequenze più simili possano essere allineate in modo affidabile nelle fasi iniziali, utilizzando tali allineamenti come base per incorporare progressivamente le sequenze più distanti.

Il funzionamento di CLUSTAL è strutturato in **tre fasi concettualmente distinte**, che definiscono l’intero flusso dell’algoritmo.

Nella **prima fase**, CLUSTAL calcola una **matrice di similarità pairwise** tra tutte le coppie di sequenze. Ogni elemento della matrice rappresenta una stima della distanza o similarità tra due sequenze, ottenuta mediante un [[Allineamento di sequenze pairwise|allineamento pairwise]] globale o locale, a seconda della variante e delle impostazioni. I punteggi di allineamento vengono successivamente convertiti in distanze, producendo una matrice simmetrica che sintetizza le relazioni tra tutte le sequenze considerate.

nella **seconda fase** viene costruito un **albero guida** (*guide tree*) a partire da questa matrice di distanze, che rappresenta una struttura gerarchica delle relazioni tra le sequenze. L’albero funge da **ordinamento computazionale** che stabilisce l’ordine con cui le sequenze devono essere allineate. Le sequenze più simili vengono accorpate per prime, mentre quelle più distanti vengono integrate in fasi successive.  
![[IMG - CLUSTAL matrice di similarita e albero guida.png]]

Nella **terza fase**, CLUSTAL costruisce l’**allineamento progressivo** seguendo la topologia dell’albero guida. Inizialmente vengono allineate coppie di sequenze, producendo allineamenti pairwise. Ogni allineamento ottenuto viene quindi **trattato come un profilo**, ossia come una rappresentazione compatta di più sequenze allineate. Nei passi successivi, l’algoritmo combina progressivamente sequenze singole e allineamenti parziali già costruiti, eseguendo **allineamenti sequenza–profilo** o **profilo–profilo**. In questo contesto, un profilo rappresenta ciascuna colonna dell’allineamento tramite informazioni aggregate, come la distribuzione dei simboli e la presenza di gap. Le decisioni prese durante questa fase sono **irreversibili**, poiché l’approccio progressivo non prevede una fase di riallineamento globale. Errori introdotti nelle prime fasi tendono quindi a propagarsi nelle fasi successive.


Dal punto di vista della **funzione obiettivo**, CLUSTAL utilizza implicitamente una formulazione riconducibile alla **[[Funzioni obiettivo - sum of pairs (SP)|sum-of-pairs]]**, valutata tramite [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche|schemi di punteggio biologicamente informati]]. Le corrispondenze tra simboli sono valutate mediante **matrici di sostituzione** per le sequenze proteiche e tramite punteggi di match/mismatch per le sequenze nucleotidiche. I **gap** sono penalizzati secondo modelli che tengono conto sia dell’apertura sia dell’estensione, e la penalità può variare in funzione della posizione, ad esempio riducendosi in regioni già densamente allineate.

Una caratteristica importante di CLUSTAL è che la qualità dell’MSA dipende fortemente dalla **qualità dell’albero guida**. Errori nella stima delle distanze pairwise o nella costruzione dell’albero si propagano alle fasi successive e non possono essere corretti, poiché l’algoritmo non prevede un meccanismo di riallineamento globale. Questo rende CLUSTAL veloce ed efficiente, ma potenzialmente sensibile alle scelte iniziali.


Nel tempo sono state sviluppate diverse **varianti di CLUSTAL**, che condividono la struttura generale dell’algoritmo ma introducono miglioramenti.

**CLUSTALW** introduce un sistema di **pesi per le sequenze**, progettato per ridurre l’influenza eccessiva di gruppi di sequenze molto simili all’interno dell’allineamento. In assenza di pesatura, sequenze fortemente ridondanti tenderebbero a dominare la funzione obiettivo, biasando il risultato finale. L’assegnazione dei pesi avviene in base alla struttura dell’albero guida e riflette il grado di divergenza tra le sequenze.

Oltre alla pesatura, CLUSTALW utilizza **penalità di gap dipendenti dal contesto**. In particolare, la penalità per l’introduzione o l’estensione di un gap può variare in funzione della conservazione locale delle colonne già allineate e della posizione nell’allineamento. Questo consente di favorire l’inserimento di gap in regioni variabili e di scoraggiarlo in regioni altamente conservate, migliorando la coerenza biologica dell’allineamento finale.



**CLUSTAL Omega** rappresenta una riformulazione più recente e altamente scalabile dell’approccio CLUSTAL, sviluppata per affrontare il problema dell’allineamento di insiemi molto grandi di sequenze. Pur mantenendo la logica dell’allineamento progressivo, CLUSTAL Omega utilizza metodi più efficienti per la stima delle distanze iniziali e per la costruzione dell’albero guida, basati su rappresentazioni vettoriali compatte delle sequenze.

In CLUSTAL Omega, l’albero guida viene costruito in modo approssimato ma estremamente rapido, riducendo il costo computazionale delle fasi iniziali. Questo rende possibile l’allineamento di **decine o centinaia di migliaia di sequenze**, con un uso controllato della memoria. In questo contesto, l’obiettivo principale non è l’ottimalità locale dell’allineamento, ma la **robustezza**, la **coerenza globale** e la **scalabilità** dell’approccio su grandi collezioni di dati.



