---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Introduzione ai Data Base
---

#### Definizione di Base si dati
Una _base di dati_ è un insieme _organizzato di dati_ utilizzati per il supporto allo svolgimento di attività di un ente.

Una _base di dati_ relazionale (_DB_) è definito da 
1. I _metadati_ ovvero lo schema della _base di dati_, è una _raccolta di definizioni_ che descrivono
	- La struttura dei dati
	- Le restrizioni sui valori ammissibili dei dati ([[Modellazione della conoscenza|vincoli d'integrità]])
	- Le [[Relazioni tra insiemi|relazioni]] esistenti fra gli [[Insiemi Matematici|insiemi]] (Le tabelle).
	- Avvolte possono essere include delle _operazioni_
2. I _dati_ che sono rappresentazioni di certi fatti conformi alle definizioni dello _schema_, con le seguenti caratteristiche:
   - Sono _organizzati_ in [[Insiemi Matematici|insiemi]] _strutturati e omogenei_
   - Sono _molti_, in assoluto e rispetto ai _metadati_, non possono essere gestiti tutti contemporaneamente in [[Architettura Von-Neumann|memoria temporanea(principale)]].
   - Sono _permanenti_, cioè, una volta creati, continuano ad esistere finché non sono esplicitamente rimossi.
   - Sono _accessibili_ mediante _[[DBMS - Gestione affidabilita e concorrenza|transazioni]]_, unità di lavoro atomiche che non possono avere effetti parziali.
   - Sono _protetti_ sia dall'[[SQL - Controllo degli accessi|accesso]] di utenti non autorizzati, sia da corruzione dovuta a malfunzionamenti hardware e software.
   - Sono utilizzabili _contemporaneamente_ da utenti diversi.

>[!example]-
> Un esempio di database qualcosa del tipo
> ![[IMG_1023.jpeg]]

Per garantire le proprietà di un _database_ definite sopra si utilizza un _[[Database Managment System (DBMS)|Database management System]]_ (_DBMS_) 



ai fini del utilizzo e' utile dividere il database  in tre livelli
![[Pasted image 20240114180811.png]]
dove
- __Vista logica__: descrive come deve apparire la struttura della base di dati ad una certa applicazione (Schema esterno o vista).
- __Livello logico__: descrive la struttura degli insiemi di dati e delle relazioni fra loro, secondo un certo modello dei dati, senza nessun riferimento alla loro organizzazione fisica nella memoria permanente (Schema logico).
- __Livello fisico__: descrive come vanno organizzati fisicamente i dati nelle memorie permanenti e quali strutture dati ausiliarie prevedere per facilitarne l’uso (Schema fisico o interno).

Questo approccio a 3 livelli permette di garantire delle proprietà importanti
- __Indipendenza logica__: i programmi applicativi non devono essere modificati in seguito a modifiche dello schema logico.
- __Indipendenza fisica__: i programmi applicativi non devono essere modificati in seguito a modifiche dell’organizzazione fisica dei dati.




