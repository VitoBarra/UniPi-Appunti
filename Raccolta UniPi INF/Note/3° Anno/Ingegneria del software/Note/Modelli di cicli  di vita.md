---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Modelli di cicli  di vita
---
I modelli di cicli di vita servo ad affrontare lo sviluppo di un softwere. affrontare questo problema permette una migliore gestione  dei tempi e dei costi. 
- Organizzazione delle attivita
	- Ordinamento delle attività 
	- Criteri per terminare e passare alla successiva

>[!note]
>buona parte dei costi dello sviluppo softwere deriva dal costo di mantenimento 

>[!warning]
>applicare discussione sui costi

Ogni modello presentato è una nuova iterazione e ogni o di essi affronta il problema in modo diverso 

## Build and fix (non modello)
non è un modello che struttura il progetto ma consiste nel scrivere un programma e aggiustarlo finche non soffiava il committente.
![[3E729A92-318F-4994-A27F-10FA41F66727.jpeg]]

non struttura il lavora e ciò va bene per progetti molto piccoli, per progetti molto piu grandi è un modo pessimo di proseguire lo sviluppo siccome è difficile mantenere un programma senza un adeguata progettazione.

# Modelli Sequenziali
## Modello a cascata (waterfall)
modello detto in cascata ogni parte dello sviluppo deve essere completata prima di passare alla successiva. ogni fase deve produrre un documento che deve essere approvato.
![[276D86AD-ACB8-47FB-BBCF-583B7B715AED.jpeg]]
#### svantaggi: 
- nessuna revisione con il cliente: il che porta a dover reiterare tutto il processo in caso di discrepanze tra il prodotto voluto e quello construito, uno scenario tutto tranne che raro.
- Troppa produzione di documenti non si può passare alla fase successi se prima il documento non viene approvato il che porta ad una produzione molto lenta.
#### COsa ha Introdotto
- La definizione e divisione della fase dello sviluppo software.
>[!nota]
>Il modello Proposto originariamente da Royce includeva i feedback loop per ovviare ai problemi di revisione 
![[AC8A4D7D-11D5-41EE-9ABF-43D1ADB50B81.jpeg]]



## Modello a V (modello di validazione o verifica)
 Le frecce blu rappresentano il tempo, quelle tratteggiate le dipendenze causali
![[8927BA1B-FBDB-4414-9703-115F1C05B456.jpeg]]
questo modello piega la meta inferiore del modello a cascata.
il lato destro verifica e controlla sempre il lato sinistro ed evidenzia come si possono gia definire i test che devono validare il codice in fase di analisi. questi infatti vengono integrati nelle fasi di sviluppo software.




# Modelli Iterativi

## Rapid Prototyping (noto come modello evolutivo)
in questo modello si producono prototipi che si presentano al committende in modo che questo posta dare feedback sul prodotto.
![[EDEACE08-00A7-48ED-9D05-CF2DA9C0A699.jpeg]]
- molto utile quando i requisiti non sono chiari. 
## Modello Incrementale
in questo modello si definiscono inizialmente i requisiti e poi si implementano solo delle parti e via via si aggiungono nuove funzionalità.
![[F1D97FB9-9E4E-4C10-9F08-2DA8506C9240.jpeg]]
particolarmente utile in caso di specifiche stabili e in caso c è bisogno di ritardare alcune feature in attesa di fattori esterni (es. aggiornamenti framework, hardware sperimentale)
- Progettato male può diventare un build and fix
## Modello a spirale
![[FAE5D97D-418B-4BA2-B4FA-15A84F56C914.jpeg]]
ogni iterazione è organizzata in 4 fasi: 
- Definizione degli obiettivi
- analisi dei rischi 
- Sviluppo e validazione
- Pianificazione del nuovo ciclo 
![[FED1C295-28E3-4C52-BAD6-D5E58ACE43FB.jpeg]]
![[3A7370EA-57BF-4F98-A108-9A435A6B9B6B.jpeg]]

## Unified Process 
è un modello guidato dai casi d uso e dall analisi dei rischi.
raccolta dei requisiti e passi successivi guardati dallo studio degli use case
![[1ACC61C7-AD60-4104-B552-577EA496F968.jpeg]]

si sviluppa l architettura generale in modo incrementale. lasciano i dettagli alle fasi successive.




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
