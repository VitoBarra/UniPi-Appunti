---
Subject: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Descrizione dei requisiti con Linguaggio naturale
---

## Fasi della definizione dl metodo naturale 
la descrizione  dei [[Analisi dei requisiti|Requisiti]] con linguaggio naturale è divisa in più fasi: 
1. _Acquisizione_ : 
	-  facendo interviste con il cliente e con gli utenti 
		- strutturate 
		- non strutturate
	- eventualmente iterando prototipi 
	- Casi d uso 
		- Il caso d’uso è un modo in cui un utente può usare il prodotto 
		- Si prospetta al committente insieme al risultato atteso  e si aspettano i commenti 
		- I casi d’uso  devono includere non solo la sequenza di eventi corretta ma anche comportamenti inattesi: eccezioni 
	- [[User stories|User Staries]] 
		- spesso fatte su foglio di carta fisici 
			- Difficilmente scalabili
		- informali

1. _Elaborazione_: [[Struttura Del documento dei requisiti| strutturare un documento di requisiti]] 
2. [[Analisi dei Requisiti  In linguaggio Naturale - Convalida - Tecniche|Convalida]]: rielaborazione dei requisiti eliminando le  [[ Analisi dei Requisiti  In linguaggio Naturale - Convalida - Errori |ambiguità]]  in particolare non ci devono esser i seguenti difetti:
	1. Omissioni (incompletezze)
		 - Mancata presenza di un requisito (incompletezza)
	 2. Inconsistenze 
		 - Contraddizione fra i vari requisiti o dei requisiti rispetto all’ambiente operativo 
	 3. Ambiguità
		 - Requisiti con significati 
	 4. Sinonimi  e omonimi 
		 - multipli Termini diversi con il medesimo significato e termini uguali con differenti significati 
	 5. Presenza di dettagli tecnici
	 6. Ridondanza 
		 - Può esserci ridondanza, ma solo tra sezioni diverse.
3. _Negoziazione_: in questa fase si assegnano le priorità ai requisiti in base a 
	- Esigenze del committente
	- Analisi costi, tempi di produzione
	- queste priorità vengono poi utilizzate per decidere se cancellare o posticipare le funzionalità 
	le priorità vengono categorizzate con il metodo MoSCow
	![[B1099487-AFE9-4B59-92CF-D646D1662409.jpeg]]

5. _Gestione_: 
	1. Assegnare ad ogni requisiti un identificate unico
		- Numero sequenziale  (1,2,3,4....) 
		- Numero basato sulla struttura del documento (2.4.7) 
		- Coppia <CATEGORIA, NUMERO>
	2. Attributi:
		- Stato 
			- Proposto, approvato, rifiutato, incorporato 
		- Priorità 
		- Importanza, tipo MoSCoW 
		- Sforzo in gg/persona
		- Rischio 
			- Valutazione della fattibilità tecnica
		- Stabilità 
		- Versione destinazione Ingegneria del Software 
			- Per lo sviluppo incrementale
	3.  Tracciabilità:
		- La tracciabilità è la capacità di descrivere e seguire la vita di un requisito del processo di sviluppo
		- Mappa tra requisiti 
		- componenti del sistema
		- codice
		- test
		- Strumenti CASE per la gestione dei requisiti 


- Analisi di mercato:
	- Confronto mercato attuale e futuro 
	- Costo del produzione, redditività 
- Analisi tecnica:
	- Verificare di avere le competenze tecniche 


