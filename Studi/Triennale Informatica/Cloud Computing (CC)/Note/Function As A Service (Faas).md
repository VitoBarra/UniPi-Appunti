---
Course: Cloud Computing
topic: nota
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# Function As A Service (Faas)
---
è un esempio di serverless siccome non ha bisogno neanche del hardware e neanche di una macchina virtuale


una semplificazione rispetto al [[Infrastructure As A Service(Iaas)|iaas]] siccome non ha bisogno di una macchina virtuale ma l idea principale e che si può avviare del codice senza dover gestire la macchina virtuale. quindi
- _avvio il codice_ senza un server di management quindi con _zero aministrazione_
- carichi il codice e ci presenta il sistema Faas a _scalarlo_
- si puo impostare un programmazione ad _eventi_. 
	- nel caso di _[[#AWS Lambda|lambda]]_ il servizio di amazon si possono triggerare funzioni allo scatenarsi di certe eventi negli altri servizi AWS
- paghi solo _il tempo computazionale_ che usi  
	- Sensibile ad [[Attacchi Denai of Service (DOS)|attacchi dos]]. questi possono incidere sul costo, siccome si cerca di soddisfare a tante richieste e questo aumenta il _tempo di computazione_
-  


## AWS Lambda

#### Pricing
![[IMG_0522.jpeg]]

### Mercato del FaaS
![[IMG_0523.jpeg]]
dai dati non si puo estrapolare se nasceranno player che domineranno il mercato 


### Scelta di un servizio FaaS
tra le tante alternative di servizio fasi ci sono 
![[IMG_0524.jpeg]]
sono divise in due categorie e vengono con vantaggi e svantaggi.

per la scelta di un servizio FaaS bisogno tenere in conti due tipi di visione sui motivi 
### Visione Di business

- _Licensing_
	- tutte le piattaforme open-source usano una licenza permissiva 
	- tutte le piattaforme properitarie usano una licenza proprietaria con eccezionale di microsoft che rilascia dei componenti come open-source
![[IMG_0525.jpeg]]
- _Installation_
	- tra le piattaforme commerciali solo Azure ha delle parti installabili
	- le piattaforme installabili supportano piu host 
![[IMG_0526.jpeg]]
- _Source code_
	- tutte le alternative open-source sono hostate su GitHub e la maggior parte di loro sono implementate in go
	- Azure è l unica piattaforma commerciale che è parzialmente open-source 
![[IMG_0527.jpeg]]
- _Interface_
	- tutte le piattaforme hanno una CLIs, mentre le API e la GUI non lo sono sempre
	- le piattaforme open-source ha interfacce molto varie
![[IMG_0528.jpeg]]
- _Community_
	- le piattaforme open-source hanno un numero di stelle e issue su github grande il che ci fa pensare ad un vasto utilizzo
	- le domande su stack overflow su i sistemi commerciali sono nettamente superiori il che denotano un _adattamento superiore_, il che è un grande vantaggio per la risoluzione di problemi
![[IMG_0529.jpeg]]
- _Documentation_
	- tutte le piattaforme forniscono documentazione sul deployment e sul uso della piattaforma
	- non tutte su sviluppo e architettura 
![[IMG_0530.jpeg]]

### Visione Tecnica
- _Development_: i linguaggi supportati
	- JAva, Node.js e Python sono quelli piu supportati, in piu è supportato docker
	- plugin per IDEs sono solitamente offerti solo da piattaforme commerciali
![[IMG_0531.jpeg]]
- _Version management_
	- la maggior parte dei sistemi Open-source provvedono ad un controllo versione *I*mplicito mentre rispetto ad uno *D*edicato
		- _implicito_: utilizza versione come parte della funzione o nomi del applicazione o namespace 
		-  _Dedicato_: il classico versionamento alla git
![[IMG_0533.jpeg]]
- _Event sources_
	- tutte le piattaforme supportano l invocazione di funzione _sincrone_ e basse su [[Livello Applicativo - HTTP|HTTP]]. mentre le chiamata _Asincrone_ sono supportate da poche piattaforme
	- molte delle piattaforme open-source non supportano gli eventi di _data storage_
	- schedulatori e steam processing sono supportate dalla maggior parte delle piattaforme 
	- la maggior parte della piattaforme supportano aventi _custom_
- _Function orchestration_
	- molte delle piattaforme FaaS permettono di fare orchestrazione ovvero di decidere il _work flow_ delle funzioni. definendo ordine 
![[IMG_0532.jpeg]]
- _Testing and debugging_
	- la maggior parte delle piattaforme supportano funzioni di [[Testing|testing]] e debug
	- piattaforme commerciali offrono sistemi piu sofisticati. mentre quelle open-source si basano principalmente su _test calls_ e _log-based debugging_
- _Observability_
	- le piattaforme offrono servizi per monitorare lo stato le funzioni e fare login quelle commerciali hanno solitamente tool proprietari mentre gli open-source utilizzano tool di terze parti  
![[IMG_0536.jpeg]]
- _Application delivery_
	- la maggior parte delle piattaforme usano un aproccio dichiarativo
	- piattaforme commerciali supportano nativa mente CI/CD ovvero _continuos integration_ e _Continuos Delivery_ mentre le open-source solitamente non lo fanno
![[IMG_0537.jpeg]]
- _Code reuse_:
	- Solo le funzioni AWS lambda e MS Azure  sono accompagnate da un mercato di funzioni 
- _Access management_:
	- Le piattaforme _commerciali_ supportano nativamente l atentificazione e il controllo delle risorse.
	- le Piattoforme _open-source_ tipicamente si basano su funzionalita dell host environment per garantire l autenticazione e li controllo delle risorse




### Lock-In
il vendor _lock in_ in FaaS non si basa su i [[Cloud computing Introduzione#Contratti|contratti]] che essendo _Pay-for-use_ è difficile da fare. si basa sul costo di conversione da un sistema Faas al altro. siccome la struttura delle funzioni spesso dipende dagli _eventi_ lanciati dalla piattaforma e quindi potrebbero non essere supportati in modo uguale da tutte le piattaforme 