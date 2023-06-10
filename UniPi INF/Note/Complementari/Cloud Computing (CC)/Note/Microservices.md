---
type: nota
course: Cloud Computing
topic: 
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# Microservices
---
Vantaggio di usare I micro servizi 


1. _Lead time_ ridotto per nuovo feature 
	- Lead TIme: tempo che intercorre tra il pensiero di una nuova feature e il prim utilizzo  del utente 
		- Accelera rebuild e redeployment
		- riduce il chord across functional silos
			- ovvero riduce il tempo in cui i dipartimenti di settore e tecnologie hanno bisogno di parlare(database e sviluppo)
2. necessita di _scalare_ eficaciamente
	- ovvero la qualita del servizio deve essere piu o meno comparabile a prescindere dal numero di utenti connessi al servizio 


### Modelli monolitici
l architettura senza i  micro servizi si basa su una singola applicazione _Monolita_ che contiene tutto il codice Server-side. questo fa ciò che ci si aspetta da un server
- Rispondere alle richieste _HTTP_
- eseguire la logica del server
- Query al database. 
- invia _HTMl view_ al client
![[IMG_0554.jpeg]]
ma questo ha dei Contro
- cambiare piccole parti dell applicazione richiedere il _rebuilding_ e il _redeploying_ del intero monolita
- fare _Rescaling_ richiedere fi farlo per tutto l applicazione monolitica e non solo sulle parti su cui sarebbe necessario 
	
>[!note] Scaling
>solitamente  lo _scaling_ si fa con piu instanze per l applicazione da scalare. farlo con un monolita e molto inficerete siccome si deve fare per tutto il programma invece di scalare solo la parte che fa da collo di bottiglia. 

## Caratteristiche dei micro servizi 
#### 1.  Service-orintation Programming
le applicazioni vengono sviluppate come un set di servizi _stateless_ 
- ogni servizio girava in un suo [[Astrazione dei Processi|processo]], oggi in un suo [[Container e Docker|container]] 
- la comunicazione tra servizi è _leggera_ 
	- [[Livello Applicativo - HTTP|HTTP]] request-response con API dirisorese
	- code asincrone  come tra [[Producer-Consumer|Produttore-consumatore]] 
		- piu lente rispetto ad HTTP ma rendere piu facile _scalare_ siccome si puo registrare _n_ produttori con _m_ consumatori
	- _Poliglotta_
		- i servizzi sono indipendenti e possono essere scritti in qualsiasi linguaggio. si puo scegliere il piu _adatto_
#### 2. organizza i servizzi intorno a alle capacita del busines
- la struttura del software spesso gira in torno a come è organizzata l azienda e un altro paradigma dello svilluppo a _microservizi_ e passare da un modello comparti  ad uno a _team_ cosi che ogni servizio sia indipendente e self-contained
- ![[IMG_0555.jpeg]]
- un altro problema del monolita è la presenta di _Chord_. ovvero dipartimenti che hanno bisogno di comunicare e quindi dipendenza 
- ![[IMG_0556.jpeg]]
- ogni _Chord_ represents un delay

##### Convertire un sistema monolite in microservizi
tenendo presente i concetti di [[Principi di progettazione e qualità di un progetto#Coesione|Coesione e Disaccoppiamento]] un modo per dividere il sistema e decomporre le varie parti in sevizi nel giusto numero 
- Troppi servizi $\rightarrow$ _bassa Coesione_ $\rightarrow$ overhead di comunicazione
- Troppo pochi servizzi $\rightarrow$ _alto accoppiamento_ $\rightarrow$ meno indipendenza per update e deployment
- 
  
consigli:
- bisogna bilanciare la divisone tra il numero di servizzi e l efficenza del sistema
- un principio da tenere a mente è il _common closure principle_
	- ovvero, metto insieme la parti del sistema che devo aggiornare insieme. se tocco uno tocco anche l altro  


#### 3. Decentralizza data management 
- ogni servizio gestisce i primo dati, il proprio [[Basi di dati|Database]] 
- questo puo portare ad errori ma su utilizza il concetto di _Eventual consistency_
##### CAP Theorem
in presenza di _Partizione_ sul Network non si puo avere sia _Availability_ e _Consistency_

le conseguenza di questo teorema e che in casi di dati duplicati dobbiamo creare dei sistemi in grado di tollerare un certo grado di inconsistenza di dati tra le varie partizioni, questo  per poter permettere una _Availability_ soddisfacente e poi prima o poi garantire la consistenza (_Eventual consistency_)

Due tipi di inconsistenze devono essere gestire
- _Dependent data inconsistency_
	- azioni o fallimenti di un sistema possono rendere inconsistenti i dati di un altro sistma
- _Replica Inconsistency_
	- piu repliche dello stesso servizio possono essere in esecuzione concordemente e ognuna di essi aggiorna la sua copia del database. 
		- prima o poi questi database dovranno essere “Consistenti” tra di loro

##### Esempio Netflix
Algoritmo per Eventual consistency
per replicare un dato aggiornato in n nodi 
1. scrivi il dato replicato dopo puoi. e se non va lo si sistema dopo
2. se la maggioranza relativa i $(\frac{n}{2}+1)$ riesce si va avanti e chi non ci è riuscito aggiornerà il dato successivamente. 












#### 4. servizi indipendentemente Deployabili 
- avere un organizations a servizzi ci permette di poter spegnere ed aggiornare solo la parte che dobbiamo aggiornare senza dover interrompere l attivita di tutti gli altri servizzi 
- in piu se uno si ferma si puo riavviare velocemente senza interrompere tutti gli altri 
- ![[IMG_0557.jpeg]]
	- il servizio giallo e quello che viene interroto (volontariamente o involontariamente)
#### 5. Servizi orizzontalmente Scalabili 
- La scalabilità orizzontale significa che posiamo _moltiplicare_ (Spawning) un servizio indipendentemente da gli altri. e con le adeguate tecniche di comunicazione come ad esempio una cosa asincrona tutto funziona normalmente senza che gli altri servizzi sappiano di questa modifica
![[IMG_0558.jpeg]]

##### Horizontal scaling vs Vertical Scaling 
![[IMG_0559.jpeg]]
#### 6. Servizi resistenti Ai fallimenti
tutti i sistemi prima o poi incontreranno un _fallimento_ .
possono esserci anche casi piu gravi come i fallimenti in cascata. nei casi cui dei servizi dipendono dalla risposta di altri. 

alcuni modi per risolvere questo problema sono isolare gli errori utilizzando dei serve [[Design pattern - Proxy|Proxy]] 
![[IMG_0560.jpeg]]
questi proxy vengono chiamati _circuit breaker_ e permette di isolare i fallimenti. pero questo ha un costo mettendo un indirizzino si allungano i tempi di attesa.

###### Chaos monkey
Chorus monkey è un sistema che chiude randomicamente dei [[Container e Docker|container]]. questo puo essere utile per testare la resilienza a gli errori 
![[IMG_0561.jpeg]]


### Figura DevOps
Gestisce sia lo sviluppo del applicazione che la gestione del suo RunTime. segue tutto il ciclo di vita di un servizio 



## Conclusion 
![[IMG_0562.jpeg]]
![[IMG_0563.jpeg]]