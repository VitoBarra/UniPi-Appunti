---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Database Management System
---
#### Database Management System (Definizione)
Un _database Management System_ è un sistema (software) centralizzato o distribuito che consente di 
- Definire gli schemi dei _Database_
- Scegliere le [[Strutture Dati|strutture dati]] per la [[DBMS - Macchina Fisica|memorizzazione e l accesso ai dati]]
- Visualizzare e modificare i dati, tramite utenti o programmi applicativi
e che sia in grado di gestire collezioni di dati che siano:
- Grandi 
- Persistenti (con un periodo di vita indipendente dalle singole esecuzioni dei programmi che le utilizzano) 
- Condivise (utilizzate da applicazioni diverse)
un DBMS deve fornire le seguenti funzionalità
- Strumenti per l’amministratore della base di dati 
	- Un linguaggio per la definizione e la modifica degli [[Introduzione ai Data Base|schemi logico]], interno ed esterno.  (solitamente la parte [[SQL - Data Declaration Lenguage|DDL]] in [[Linguaggio per Database - SQL]])
	- Strumenti per il controllo e messa a punto del funzionamento del sistema. 
	- Strumenti per stabilire i diritti di accesso ai dati ([[SQL - Controllo degli accessi|Controllo accessi]])
	- per ripristinare la base di dati in caso di malfunzionamenti. ([[DBMS - Gestione affidabilita e concorrenza|Affidabilita]]) 
- Strumenti per lo sviluppo delle applicazioni 
	- Produzione di rapporti, grafici, fogli elettronici 
	- Sviluppo di menu, form, componenti grafici


e' deve garantire delle proprietà sulla [[Introduzione ai Data Base|base di dati]]
- __Integrità__: mantenimento delle proprietà specificate in modo dichiarativo nello schema (vincoli d’integrità) 
- __Sicurezza__: protezione dei dati da usi non autorizzati 
- __Affidabilità__: protezione dei dati da malfunzionamenti hardware o software (fallimenti di transazione, di sistema e disastri) e da interferenze indesiderate dovute all’accesso concorrente ai dati da parte di più utenti.




#### Architettura 
Un architettura semplificata è qualcosa del tipo
![[IMG_1028.jpeg]]
ma questa e' solo una semplificazione l [[Architettura di un DBMS|architettura di un DBMS]] e' piu complessa


SVANTAGGI DEI DBMS:
- Prima di caricare i dati è necessario definire uno schema 
- Possono gestire solo dati strutturati e omogenei 
- Possono essere costosi e complessi da installare e mantenere in esercizi 
- Sono ottimizzati per le applicazioni OLTP, non per quelle OLAP