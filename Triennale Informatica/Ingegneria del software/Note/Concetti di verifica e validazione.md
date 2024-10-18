---
Course: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Concetti di verifica e validazione
---

Il problema di verifica e validazione è un problema [[Calcolabilità|indecidibile]] una tecnica concreta è la tecnica del [[Testing|Testing]]


## Terminologia 
- V&V: Verifica e validazione del software 
- _Malfunzionamento_: il sistema software a tempo di esecuzione non si comporta secondo le specifiche 
	- Ha quindi una natura dinamica e lo si nota solo a run time
	- questo è causato da almeno un difetto
- _Difetto_: è un difetto nel codice e appartiene alla natura statica del programma 
	-  la correzione di questi defetti è detta debug o bugFixing
	- se un difetto porta ad un _malfunzionamento_  solo ogni tanto allora questo viene detto difetto latente
- _Errore_: è la causa di un difetto
	- Incomprensione umana nel tentativi di comprendere o risolvere un problema o nel uso di strumenti 
##### Difficolta della V&V software
- requisiti di qualità diversa
- Se sempre in evoluzione
- distribuzione irregolare dei quesiti
- non linearità :
	- se un procedura ordina correttamente 256 elementi non è detto che lo faccia anche con meno o più elementi
- Dipendenti dal linguaggio: 
	- Deadlock o race condition over il software distribuito
	- Problemi dovuto al polimorfismo o al binding dinamico nel software object-oriented

### Progettazione della fase di verifica
-  scegliere e programmare la giusta combinazione di tecniche 
	- per raggiungere il livello richiesti di qualità 
	- entro i limiti di costo
- Progettare una soluzione specifica che si adatta
	- Al problema 
	- ai requisiti
	- al ambiente di sviluppo
Le soluzioni sono quindi fatte ad hoc non ci si po' basare su ricette già fatte. 

#### Guida 
### 1. Quando iniziare verifica e convalida? 
- _Dallo studio di fattibilità_
	- Tenendo conto quindi dei costi e della qualità richiesta
	- _le attività sono_
		- analisi del rischio
		- definizione delle misure necessarie per valutare e controllare la qualità in ogni stadio di sviluppo
		- valutazione dell'impatto di nuove funzionalità e nuovi requisiti di qualità
		- valutazione economica  delle attività di controllo della qualità: costi e tempi di sviluppo
	- _Dopo il rilascio_
		- analisi delle modifiche ed estensione
		- generazione di nuove suite di test per le funzionalità aggiuntive
		- test di non regressione
		- rilevamento e analisi dei guasti
## 2. quando sono complete? 
- Il [[Testing]] è solo una parte della V&V
- V&V iniziano non appena decidiamo di creare un prodotto software
- V&V durano per tutto il tempo in cui il software è in uno e servono anche per far fronte alle evoluzioni e agli adattamenti alle nuove condizioni
## 3. quali tecniche applicare?
- Nessuna tecnica basta da sola
- _principi di combinazione_ 
	- efficacia per diverse classi di difetti
	- Applicabilità in diverse fasi del processo di sviluppo
	- Differenza di scopi
	- Compromessi in termini di costo e affidabilità
## 4. Come possiamo valutare se un prodotto è pronto per essere rilasciato?
- Da una buona definizione delle misure
- a seconda della misura scelta si possono avere risultato molto diversi quindi la scelta della misura dipende dal obbiettivo
- _Alfa test_: 
	- test eseguiti dagli sviluppatori o dagli utenti in ambiente controllato, osservarti dall organizzazione dello sviluppo
- _Beta test_:
	- Test eseguiti da utenti reali nel loro ambiente, eseguendo attività reali senza interferenze o monitoraggio ravvicinato
## 5.Come possiamo controllare la qualità delle release successive?
_Attivita dopo la consegna_
- Test e analisi del codice nuovo e modificato
- esecuzione dei testi di sistema
- memorizzazione di tutti i bug trovati
- test di regressione
- Distinzione tra “major” e “minor” revision
## 6. Come può essere migliorato il processo di sviluppo? 
- SI incontrano gli stessi difetti progetto dopo progetto
	- Indentificare e simulare i punti deboli nel processo di sviluppo
	- identificare e rimuovere i punti deboli del test 
	-  del analisi che consentono loro di non essere individuati 


#### Verifica vs Convalida
la _Convalida_ : Controlla che il sistema che sta venendo costruito è utile al utente
la _Verifica_: controlla che si stia costruendo un sistema che rispecchia i requisiti 

![[831B5298-7721-42D4-879E-88C2659E94C2.jpeg]]
![[7A4056BE-AE10-4EE9-97BD-3AE0F11230EC.jpeg]]








