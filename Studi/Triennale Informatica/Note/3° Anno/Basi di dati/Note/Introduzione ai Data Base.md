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

Una _base di dati_ (_DB_) è definito da 
1. I _metadati_ ovvero lo schema della _base di dati_, è una _raccolta di definizioni_ che descrivono
	-  la struttura dei dati
	-  le restrizioni sui valori ammissibili dei dati (vincoli d'integrità)
	- Le [[Relazioni tra insiemi|relazioni]] esistenti fra gli [[Insiemi Matematici|insiemi]] (Le tabelle).
	- Avvolte possono essere include delle _operazioni_
2. I _dati_ sono rappresentazioni di certi fatti conformi alle definizioni dello _schema_, con le seguenti caratteristiche:
   - Sono _organizzati_ in [[Insiemi Matematici|insiemi]] _strutturati e omogenei_
   - Sono _molti_, in assoluto e rispetto ai _metadati_, non possono essere gestiti tutti contemporaneamente in [[RAM|memoria temporanea]].
   - Sono _permanenti_, cioè, una volta creati, continuano ad esistere finché non sono esplicitamente rimossi.
   - Sono _accessibili_ mediante _[[DBMS - Transazioni|transazioni]]_, unità di lavoro atomiche che non possono avere effetti parziali.
   - Sono _protetti_ sia dall'accesso di utenti non autorizzati, sia da corruzione dovuta a malfunzionamenti hardware e software.
   - Sono utilizzabili _contemporaneamente_ da utenti diversi.

>[!example]-
> Un esempio di database qualcosa del tipo
> ![[IMG_1023.jpeg]]

Per garantire le proprietà di un _database_ definite sopra si utilizza un _[[Database Managment System (DBMS)|Database management System]]_ (_DBMS_) 






