---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# SQL  - Procedure e trigger
---
Un __trigger__ sono una funzionalità di [[Linguaggio per Database - SQL]] che permette di definire azioni da compiere in risposta a certi eventi nel [[Introduzione ai Data Base|DataBase]]
 Possono essere utilizzati:
  - per migliorare l’integrità referenziale dichiarativa 
  - per imporre regole complesse legate all’attività del database 
  - per effettuare revisioni sulle modifiche dei dati.
  - trattare vincoli non esprimibili nello schema

L’esecuzione dei trigger è trasparente all’utente. 

I trigger vengono _eseguiti automaticamente_ dal database quando specifici tipi di comandi (Eventi) di manipolazione dei dati vengono eseguiti su specifiche tabelle. 
I comandi su cui si puo scrivere un trigger 
del [[SQL - Data Declaration Lenguage|DML]] sono
- INSERT
- UPDATE
- DELETE
mentre [[SQL - Data Manipulation Lenguage|DDL]] 
- Create View ecc

Anche gli aggiornamenti di specifiche colonne possono essere utilizzati come trigger di eventi.


I trigger possono essere eseguiti a piu livelli
- __Livello di riga__: si esegue l azione del trigger per ogni riga con cui ha avuto a che fare la [[DBMS - Gestione affidabilita e concorrenza|transazione]]
	- si usa per l operazioni di audit (controllo correttezza) dei dati e per mantenere sincronizzati i __dati distribuiti__.
	- Va specificato __FOR EACH ROW__ dopo il __CRETE TRIGGER__
- __Livello di istruzione__: viene eseguita una sola volta per ogni istruzione
	- si usa per imporre misure aggiuntive di sicurezza sui tipi di transazione che possono essere eseguiti su una tabella.
	- e' la modalità predefinita


i tipi di trigger
- BEFORE e AFTER: i trigger possono essere eseguiti prima o dopo l’utilizzo dei comandi insert, update e delete; all’interno del trigger è possibile fare riferimento ai vecchi e nuovi valori coinvolti nella transazione. 

![[Pasted image 20240113013805.png]]

i Trigger possono essere
- __Attivo__: quando, in corrispondenza di certi eventi, modifica lo stato della base di dati.
- __Passivo__ se serve a provocare il fallimento della transazione corrente sotto certe condizioni.



un particolare tipo di trigger INSTEAD OF:
questo serve a specificare che cosa fare al posto di di eseguire le azioni che hanno attivato il trigger. 
- possono essere definiti su viste (relazionali od oggetto). 
- devono essere a livello di riga

