---
Course: "[[Ingegneria Del Software (IS)]]"
topic: nota
tags: IS
---

# Analisi dei requisiti
---
i Requisiti di un sistema sistema sono le funzionalità che il sistema deve prevedere 


## Studio di fattibilità
fase preliminare per stabilire l opportunità o meno di realizzare il software 
 Si basa su:
 - Una descrizione sommaria del sistema sw e delle necessità utente Un’analisi di mercato: 
	 - Confronto tra il mercato attuale e quello futuro Costo della produzione, redditività dell’investimento 
 - Un’analisi tecnica per capire se è realizzabile 
	 - Strumenti per la realizzazione (software, librerie, ...)
	 - Soluzioni algoritmiche e architetturali 
	 - Hardware 
	 - Ingegneria del Software Processo ( prototipazione, progetti esplorativi, ricerca..)

### Analisi dei requisiti
Questa fase si occupa di a _definire_ e _documentare_ COSA deve essere realizzato 
- il _Dominio_ del sistema da realizzare 
	- in generale è il campo di applicazione del prodotto 
Definizione del Dominio parti:
 - _Glossario_: una collezione di definizioni di termini del dominio. 
	- generalmente costruito prima di parlare con il cliente e poi ampliato dopo aver comunicato con gli stakeholder.
- *Modello statico*:  modello [[Unified modeling Language (UML)]] 
- *Modello dinamico*: modello testuale per descrivere i passi o modello dinamico [[Unified modeling Language (UML)]] a stati finiti
>[!note]
>Il dominio esiste a prescindere dal sistema software  che opera o controlla quel dominio. 
>- entità, relazioni processi e comportamenti.
		 
- i _requisiti_ utente: 
	- Una condizione o capacita necessaria ad un utente per risolvere un problema
	- Una condizione (capacità) che deve essere soddisfatta (posseduta) da un sistema per soddisfare un contratto
	- Si possono definire tramite [[User stories|User Stories]]
>[!tip] Ovvero
>Una proprietà che deve essere garantita dal sistema per soddisfare una necessità (Bisogno) di un utente 
- i _requisiti_ funzionali:
	- Azioni che il sistema deve compiere
	- Descrive come il sistema deve reagire a certi Input
	- Come si comporta in situazioni particolari 
- i _requisiti NON_ funzionale 
	- Qualità:
		- Efficienza  | Affidabilità | Usabilità | Safety |  Interfaccia | Security | Robustezza 
	- caratteristiche di sviluppo:
		- Metodologia , standard , Linguaggio
	- Requisiti di interoperabilità: 
	- Requisito fisico
		- mezzo di trasmissione, limiti sul Hardware, 
	- Opzionali:
		- Manuale utente
		- Casi di test
> [!Info] perche avere due categorie di requisiti 
> questi due requisiti sono separati siccome vengono utilizzati in tempi diversi. infatti prima si definiscono i requisiti non funzionali e poi quelli funzionali in modo che si rispettino i vincoli di quelli non funzionali 

Per la descrizione dei requisiti ci sono due metodi principali
- Basa su  [[Descrizione dei requisiti con Linguaggio naturale |linguaggio naturale]]
- basata su linguaggi grafici ad esempio  [[Unified modeling Language (UML)]]
Le due non sono mutualmente esclusive.


>[!info]  Utilità di un documento di requisiti dal punto di vista contrattuale
>- Il documento dei requisiti normalmente precede la stipula del contratto, e ne è parte integrante
>- Se alla stipula del contratto non è possibile avere un documento definitivo, è opportuno prevedere di rinegoziare il contratto.
>- In caso di gara il documento dei requisiti può essere prodotto dal committente come parte di capitolato tecnico.
>