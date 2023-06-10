---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# FFS Fixed Tree
---

## Index Structure

nel file system FFS l index structure è chiamata multi-level index questa è un albero fisso ed asimmetrico.  l albero è radicato negli Inode ovvero nelle entry del Inode array  che è mantenuto in un punto conosciuto del disco e viene accesso tramite il file number preso dalla [[Directories dati nominati|directory]] che contiene il file. ogni entry rappresenta un file e contiene i suoi metadati e i puntatori del albero

![[Untitled 44.png]]

tipicamente i puntatori sono 15 di cui 12 sono diretti 1 indiretto 1 doppio indiretto e 1 triplo indiretto dove.

- puntatori diretti: puntato direttamente ai blocchi dei dati.
- indiretti: puntano ad un blocco intermedio che contiene puntatori diretti
- doppi indiretti: puntano ad un blocco intermedio che contiene puntatori indiretti
- tripli indiretti: puntano ad un blocco intermedio che contiene puntatori doppi indiretti

cosi facendo se ogni blocco intermedio può contenere $2^{8}$ puntatori allora i blocchi indirizzabili sono $12+2^{8}+(2^{8})^{2}+(2^{8})^{3} = 2^{49}+3$

questa struttura permette alcuni vantaggi

- un implementazione semplice perché la struttura
- una ottimo random access siccome leggere un blocco a caso non casta troppo di più  o di meno di leggere il primo o l ultimo
- è flessibile grazie al fatto che è asimmetrico, grazie a questo i file piccoli possono essere salvati dai puntatori diretti e quindi non pagare l overhead dei puntatori indiretti che invece viene pagata dai i file più grandi

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 20.png]]


## Tracciamento dello spazio libero

si implementa con una bitmap e ogni bit indica se un blocco è libero o usato, la bitmap è salvata in una posizione nota quando si crea il volume FFS

## Euristiche di località

per assicurarsi buone performance utilizza due euristiche

### Block group placement e spazio riservato

si basa sul fatto che file nella stessi [[Directories dati nominati|directory]] vengono accese insieme.

- divide il disco in più gruppi. ogni gruppo avrà la sua porzione Inodes array  e della bitmap che si riferiscono ai blocchi di quel gruppo.
- directory e fine in quella directory vengono messi nello stesso gruppo ma le sotto directory invece vengono messe in un gruppo diverso per evitare di accumulare velocemente blocchi in un unico gruppo

![[Untitled 2 7 1.png]]

- per piazzare nuovi blocchi in un gruppo segue l eristica first fit ovvero partendo dal inizio del blocco scrive il primo blocco libero che incontra facendo cosi i file piccoli tenderanno a occupare i buchi mentre in caso di file grossi inizialmente si perde un po' di località ma andando avanti nella scrittura ci si ritroverà con strisce continue di blocchi

![[Untitled 3 5 1.png]]

- queste euristiche funzionano grazie al assunzione di molto spazio libero non è sempre il caso ma per garantire la possibilità di avere sempre buone performance il file system riserva una parte del disco (es 10%) per continuare a fare le sue operazioni.

## Svantaggi

non supporta bene i file sparsi ovvero qui file in cui i dati non sono scritti consecutivamente neanche a livello logico

![[Untitled 4 2 1.png]]

questo file starebbe indicizzando un 1GB di dati ma ne sta consumando solo 16kb, leggere questo file dal inizio alla fine causa il file system l allocazione dei blocchi intermedi portando l uso effettivo a 1Gb con molti blocchi tutti a 0
