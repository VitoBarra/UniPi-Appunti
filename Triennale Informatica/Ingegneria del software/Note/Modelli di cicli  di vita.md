---
Course: "[[Ingegneria Del Software (IS)]]"
topic: nota
tags: IS
---
# Modelli di cicli  di vita
---
I modelli di cicli di vita servo ad affrontare lo sviluppo di un software. affrontare questo problema permette una migliore gestione  dei tempi e dei costi. 
- Organizzazione delle attività
	- Ordinamento delle attività 
	- Criteri per terminare e passare alla successiva

>[!note]
>buona parte dei costi dello sviluppo softwere deriva dal costo di mantenimento 

>[!warning]
>ampliare discussione sui costi

Ogni modello presentato è una nuova iterazione e ogni o di essi affronta il problema in modo diverso 

## Build and fix (non modello)
non è un modello che struttura il progetto ma consiste nel scrivere un programma e aggiustarlo finche non è soddisfatto il committente.
![[IMG - Modelli di cicli di vita 1.jpeg]]

non struttura il lavora e ciò va bene per progetti molto piccoli, per progetti molto più grandi è un modo pessimo di proseguire lo sviluppo siccome è difficile mantenere un programma senza un adeguata progettazione.

# Modelli Sequenziali
## Modello a cascata (waterfall)
modello detto in cascata ogni parte dello sviluppo deve essere completata prima di passare alla successiva. ogni fase deve produrre un documento che deve essere approvato.
![[IMG - Modelli di cicli di vita 2.jpeg]]
#### svantaggi: 
- nessuna revisione con il cliente: il che porta a dover reiterare tutto il processo in caso di discrepanze tra il prodotto voluto e quello costruito, uno scenario tutto tranne che raro.
- Troppa produzione di documenti non si può passare alla fase successi se prima il documento non viene approvato il che porta ad una produzione molto lenta.
#### Cosa ha Introdotto
- La definizione e divisione della fase dello sviluppo software.
>[!nota]
>Il modello Proposto originariamente da Royce includeva i feedback loop per ovviare ai problemi di revisione 
![[IMG - Modelli di cicli di vita 3.jpeg]]



## Modello a V (modello di validazione o verifica)
Le frecce blu rappresentano il tempo, quelle tratteggiate le dipendenze causali
![[IMG - Modelli di cicli di vita 4.jpeg]]
questo modello piega la meta inferiore del modello a cascata.
il lato destro verifica e controlla sempre il lato sinistro ed evidenzia come si possono già definire i test che devono validare il codice in fase di analisi. questi infatti vengono integrati nelle fasi di sviluppo software.


# Modelli Iterativi

## Rapid Prototyping (noto come modello evolutivo)
in questo modello si producono prototipi che si presentano al committente in modo che questo posta dare feedback sul prodotto.
![[IMG - Modelli di cicli di vita 5.jpeg]]
- molto utile quando i requisiti non sono chiari. 
## Modello Incrementale
in questo modello si definiscono inizialmente i requisiti e poi si implementano solo delle parti e via via si aggiungono nuove funzionalità.
![[IMG - Modelli di cicli di vita 6.jpeg]]
particolarmente utile in caso di specifiche stabili e in caso c è bisogno di ritardare alcune _feature_ in attesa di fattori esterni (es. aggiornamenti framework, hardware sperimentale)
- Progettato male può diventare un Build and fix
## Modello a spirale
![[IMG - Modelli di cicli di vita 7.jpeg]]
ogni iterazione è organizzata in 4 fasi: 
- Definizione degli obiettivi
- Analisi dei rischi 
- Sviluppo e validazione
- Pianificazione del nuovo ciclo 
![[IMG - Modelli di cicli di vita 8.jpeg]]

- è un modello astratto
	- va specializzato per dire cosa fare in concreto in ogni iterazione e in ogni sua fase
	- applicabile ai cicli tradizionali
- Evidenzia gli aspetti gestionali
	- pianificazione dalle fasi 
	- _Centro sull’ analisi dei rischio_ (modello “risk driven”)
		- tipici rischi:
			- dominio poco noto, Linguaggi o strumenti nuovi, personale non addestrato 
		- Ispirato dal plan-do-check-act cycle
		- prevede maggior comunicazione azione e confronto con il committente

## Unified Process 
è un modello guidato dai casi d uso e dal analisi dei rischi.
raccolta dei requisiti e passi successivi guardati dallo studio degli use case
![[IMG - Modelli di cicli di vita 9.jpeg]]

si sviluppa l architettura generale in modo incrementale. lasciano i dettagli alle fasi successive.




## agile manifesto
- Comunicazione con i stakeholder soprattutto il cliente (committente e user )
- Semplificare la documentazione 
- Feedback sul sistema 

#### Extreme programming 
- Lavoro flessibile 
- Rilasciare versioni ogni 2-4 settimana
- Programmazione a coppie
- No lavoro straordinario
	- stanchezza incrementa la probabilità di introdurre bug
- Code refactoring
- Daily stand up meeting 

#### Scrum 
- Scrum significa mischia del rugby 
- Product back log list 
- Design di alto livello del sistema 
- Insieme di sprint di 2 settimane un mese 
- Dagli stand up meating 

**ruoli 
- Product owner : 
	- definisce le specifiche 
	- Accetta o rigetta il lavoro di uno sprint 
 - team member :
	 -  Cross working 
	 - Organizzati indipendenti 
	 - Ognuno risolve una cosa alla volta 
- scrum master: 
	- supporto al team 
	- Non ha Autorità sul team 


- ***Scrub: back log 
	- cose 
- ***Scrum: Kanban con WIP limit 
	- le tre colonne per organizzare il progetto
		- _request_: le attività non ancora iniziate 
		- _in progres_: le attività che correntemente sono in sviluppo
		- _Done_ : le attività completate
	- la colonna dei _in progress_ ha una limite di attività da fare contemporaneamente. questo permette di concentrarsi su pochi task e portarli a termine piuttosto che iniziarne tanti e finirne pochi. questo riduce anche i _task switching_ che consuma energia e tempo 
	- ![[IMG - Modelli di cicli di vita 10.jpeg]]


**fasi di uno Sprint  
- _Planning_ ( circa 8 ore )
	- Il producer owner gestisce l evento di pianificazione dello Sprint
	- con il team si definisce lo sprint backlog
- _Daily meating_ 
	- i membri del team si posizionano in semicerchio davanti alla kanban, gli Scrum master si posizionano  nella vicinanze. si risponde alle domande:
		- “cosa ho fatto ieri?”
		- “cosa faro oggi?”
		- “quali difficolta sito affrontando?”
- _Review_ (circa 4 ore ad ogni incremento consegnato )
	- il team in collaborazione con gli utenti ispeziona il software per ottenere un feedback. si discutono domande come:
		- “è questo i prodotto che vogliamo costruire?”
		- “Co penserebbero gli utenti finali del prodotto?”
		- “quel è il feedback degli utenti finali?”
		- “è ancora il prodotto che ci è stato richiesto?”
		- “Ci sono cambiamenti o nuove idee?”
- _Retrospettiva_:
	- dopo ogni sprint si organizza un evento per riflettere imparare e riadattarsi alla prossima fase di sprint.
	- ![[IMG - Modelli di cicli di vita 11.jpeg]]


![[IMG - Modelli di cicli di vita 12.jpeg]]