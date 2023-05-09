---
type: nota
course: Cloud Computing
topic: 
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# Platform As A Service(Paas)
---
## Cos è il PaaS
la infrastruttura e la piattaforma sono gestite direttamente al cloud mentre al utente resta da gestire solo l applicazione e di dati  
![[IMG_0538.jpeg]]
- Il provider da HW e SW per lo svilluppo 
- l utente gestisce solo l applicazione e i dati 
	- _Vantaggi_:
		- Nessuna infrastruttura da gestire
		- la manutenzione è fatta dal privider
		- scaling e load balancing facilitato
		- piu facile adozione delle nuove offerte di tecnologia 
	- _Rischi_: 
		- Service availability:
			-  se il provider cade la nostra applicazione non funziona 
		- vendor lock-in
		- cambiamenti interni al PaaS che non possiamo gestire 
- Per-use-payment 


## Mercato PaaS
![[IMG_0539.jpeg]]
![[IMG_0540.jpeg]]

### Che vantaggi danno i PaaS
forniscono una piattammo per lo sviluppo dove tutti è gia pronto e gestito delegando molte delle parti che dovremmo gestisci noi come sviluppatori al cloud.



## Heroku 
Heroku  è una piattaforma cloud basato sulla gestione di [[Container e Docker|container]] con integrazione di servizi e un potente ambiente di sviluppo. per fare il deployment e gestire app moderne.


#### Dynos
I Dynos di Heroku sono dei containers Linux che sono utilizzati per gestire l applicazione del utente.

- Sono virtualizati e isolati e sono progettati per esegueire comandi specifici definito dal utente. 
	- quindi l utente oltre a fornire l applicazione deve fornire i _comandi_ per avviarla 
	- l App che gira su un _Dynos_ possono essere facilmente scalate con piu instanze basandosi sulla richiesta di risorse


#### Buildtime
al tempo di costruzione Heroku ha bisogno di
- source code
- la lista delle dipendenze
- un _Procfile_
	- ovvero un file di testo dove sarà contenuto il comando per avviare l applicazione 

tutti i procedimenti sono automatiche. basta dare i dati in input e sarà Heroku a gestire il building 
- Riceve il codice
- fetcha i Buildpack, i [[Macchina Astratta|language runtime support]] e code dependencies
- produce una Slug. ovvero un pacchetto con codice e dependency che sarà messo in un Dyno per far girare l app

![[IMG_0541.jpeg]]


#### Runtime
dopo aver prodotto lo Slug creare uno o piu Dyno, uno per istanza del applicazione e gestisce l’ esecuzione di essi
![[IMG_0542.jpeg]]
- l appplicazione receive la richiesta
- questa è consegnata al web dyno
- la richieta viene messa in coda
- un worker lavorerà su quella richiesta. nel caso i dati persisteranno su un database

#### Dyno Type

![[IMG_0543.jpeg]]
1. i Dyno standard supportano la _scalabilità_. ma questa va richiesta manualmente
2. i Dyno Performance supportano l _auto scaling_.
##### Pricing
![[IMG_0544.jpeg]]
non c è piu free tier

#### Add-Ons
piu di 150 servizi di terze parti che gli sviluppatori possono aggiungere direttamente su heroku. alcuni esempi sono
- Data storage
- logging
- monitoring 

gli add-on sono sono strumenti potenti per aggiungere funzonalita velocemente al applicazione ma tramite questi si aggiunge un potenziale _vendor lock-in_ siccome aggiungerne uno rendere piu _difficile_ trasferirsi su un altro PaaS. che potrebbe non avere quel add-on.

