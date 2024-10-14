---
Subject: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Problema del oracolo
---

Il problema del oracolo si riferisce al problema del [[Testing]] di avere già disposizione i valori di output. non sempre questi sono facili da conoscere.

- Si possono ricavare da
	- specifiche formali
	- specifiche eseguibili
- inversione delle funzioni
	- quando l inversa è più facile
	- a volte disponibili fra le funzionalità
	- limitazioni per difetti di approssimazione
	- partire del output e trovare l input
- Versione Precedente dello stesso codice.
	- disponibili (per funzionalità non modificate)
	- utile per la prova di non regressione
- versioni multiple
	- programmi preesistenti 
	- programmi ad hoc
	- semplificare gli algoritmi
		- inefficienti ma corretti
- Semplificazione dei dati d ingresso
	- provare le funzionalità su dati semplici
	- risultati noti o calcolabili con altri mezzi
	- ipotesi di comportamento costante
- semplificazione dei risultati
	- Accontentarsi di risultati plausibili
	- tramite vincoli fra ingressi e uscite
	- tramite invarianti sulle uscite

![[36AE7455-3080-4C0F-8A18-D4271994F274.jpeg]]


