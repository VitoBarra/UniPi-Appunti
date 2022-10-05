Processo software: insieme di azioni per sviluppare un un prodotto software 

Suddividere  in sotto attività


Standard processo software ISO 12207


**modello ci ciclo di vita 

Vari modelli di ciclo di vita 


- Build and fix (non modello)
	- da non fare 
- Modello in cascata 
	- modello a cascata di Royce prima indire delle fare e dei criteri per quella fase. Le fasi vanno fatti in successione e document driven ( odiato). Niente cicli di revisione e niente feedback 
-modello in cascata con parti al solito livello comunque vanno fatto in ordine ma sono rappresentate collegate. Con cose che collegato allo stesso livello come sviluppo di test che si possono già ricavare prima di sviluppare il codice. Da questo modello nasce il concetto di test driven develop 

- rapid prototyping (modello evolutivo )
	- fare un prototipo con le specifiche iniziali e poi reiterare ripartendo dalla fase di specifica essenzialmente feedback 
- modello incrementale 
	- faccio le cose in parti e vado sempre ad aggiungere si passa da produrre le parti importante e il resto delle feature si aggiungono man mano ( richiede un architettura iniziale fatta e finita )
-modello ad aspirale 
-  Unified process 
	- si reiterando più volte tutte le fasi dedicando tempo diverso a ognuna di essi 
**agile manifesto
- Comunicazione con i stakeholder soprattutto il cliente (committente e user )
- Semplificare la documentazione 
- Feedback sul sistema 

Extreme programming 
	- Lavoro flessibile 
	- Rilasciare versioni ogni 2-4 settimana
	 idee Fiche programmazione a coppie 
	 No lavoro straordinario 
	 Code refactoring 
	 Daily stand up meeting 

Scrum 
-  Scrum significa mischia del rugby 
- Product back log list 
- Design di alto livello del sistema 
- Insieme di sprint di 2 settimane un mese 
- Dagli stand up meating 

**ruoli 

Product owner : 
	- definisce le specifiche 
	- Accetta o rigetta il lavoro di uno sprint 
 team member :
	 -  Cross working 
	 - Organizzati indipendenti 
	 - Ognuno risolve una cosa alla volta 
- scrum master: 
	- supporto al team 
	- Non ha Autorità sul team 


	- ***Scrub: back log 
		- cose 
	- ***Scrum: Kansan 
		- le tre colonne per organizzare il progetto 
		- Non iniziare troppe cose contemporaneamente 
			- Ridurre i task switch 
		burn down chart 

**fasi sprint 
- Planning ( circa 8 ore )
- Daily meating 
- Review (4 ore incremento consegnato )
- Retrospettiva 




2022-09-23:


# Analisi dei requisiti

## Studio di fattibilità :
- ### analisi dei requisiti: 
	Questa fase si occupa di a _definire_ e _documentare_ COSA deve essere realizzato 
	- il _Dominio_ del sistema da realizare
		- il campo di applicazione del prodotto 
		- PRima di incontrare il ciliente conoscere un po’ la materia
			- Tecniche di definizione del dominio: _Glosrio_: [[Esempi Glossari | Esemepi ]]
				- Collezione di Termini
				- Modello statico: 
				- Modello dinamico: modello testuale per descrivere i passi o Con [[UML]]
				- 
					
	- i _requisiti_ utente 
		- Una condizione o capacita necesaria ad un potente per compiere qualcosa 
			- Usare i termini Definiti 
	- i _requisiti_ funzionali:
		- Descrive come il sistema deve reagire a certi Input 
	- i _requisiti NON_ funzionale 
		- Qualità:
			- Efficenza  | Affidabilità | Usabilita | Safety |  Interfaccia | Security | Robustezza 
		- caratteristiche di sviiluppo:
			- Metodologia , standard , Linguaggio
		- Requisiti di ineperobabilita:
			- 
		- Requisito fisico
			- mezzo di trasmissione, limiti sul Hardware, 
	- Opzionali:
		- Manuale utente
		- Casi di test

	I requisiti Sono separati perche devono essere realizzati in tempi diversi. Ad esempio Dividerei quando definisco come deve funzionare l interfaccia e in fase di progettazione rispetto i vincoli dei requisiti non funzionali 


	


	Fasi della definizione dl metodo naturale 
	1. Acquisizione : parlando con il cliente, e con gli utenti , iterando  prototipi 
		1. User Stories: 
	2. Elaborazione: [[Struttura Del documento dei requisiti| strutturare un documento di requisiti]] 
	3. [[Convalida del Documenti di requisiti| Convalida]]: rielaborazione dei requisiti elimindo le  [[ ambiguità nei documenti di requisito |ambiguità]], 
	4. Negoziazione: analisi costi e tempi di Produzione.  Definito con [[Tecniche per definire La priorità di un documento di requisiti|Priorità]] 
		1. Attributi: 
			1. Stato: aprovateo
			2. Priorita: priorità di tipo MoScow
			3. Asd
			4. Ad
			5. Ad
			6. Ad
	5. Gestione: 
		1. Tracciabillita: 

	
	

- Analisi di mercato:
	- Confronto mercato attuale e futuro 
	- Costo dell produzione, redditività 
- Analisi tecnica:
	- Verificare di avere le competenze tecniche 


2022-10-03:
Gli UML servono a rappresentare i [[ingengeria del softwere requisiti|Requisiti Funzionali]] 

gli attori Principali deve essere necessariamente solo uno mentre i secondarmi possono essere illimitati

In UML ci sono gli attore che interagiscono con le funzioni e c è una nazione di super attore ovvero con una freccia si più indicare la relazione di classi 



### narrativa dei casi d uso 
Spiega con parole le funzionalità dei singoli casi d usi 

È fatto da 
- nome
- ID
- Breve Descrizione
- Attore primario
- Attore secondari
- Precondizione
- Sequenza degli eventi principali: sequenza di passi per arrivare alla post condizione  
- Post condizione:
- Sequenza alternativa degli eventi: casi in cui ci sono errori, o ci sono delle interruzioni dei generici problemi nel raggiungere la post condizione. Magari gli eventi meno probabili  
- 

[[Triple di Hoare]]

Le erediriata nel UML esiste si può applicare sia a attori che a componenti. Deve rispettare il [[principio di sostituzione di Liskov]]

Esistono anche le dipendenze ovvero il caso il caso d uso uno ha bisogno di usare un altra cosa d uso


Un caso d uso incluso non necessariamente ha un attore principale 

Si puo fare estensione di un caso d uso significa al volere si possono ottenere sia la post condizione della classe che stende che quella che si sta usando 

Nei passi vanno scritti le interazioni tra l attore e il sistema oltre ai passi che deve fare effettivamente il sistema 

Il sistema che si sta implementando non è un attore 

Ci sono attori esterni la semantica e che non va implementato nel sistema esempio un DB




2022-10-05:

Diagramma delle classi e diagrammi oggetti

Ma quindi nella palle è storiato il piscio?

Voglio il grafo dello storage 

