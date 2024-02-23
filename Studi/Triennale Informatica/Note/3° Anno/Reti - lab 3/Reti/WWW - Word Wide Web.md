---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# WWW - Word Wide Web
---

è la rete di dimensione globale ed è ha queste caratteristiche: 
- un collezioni di informazioni nella quale le risorse sono distribuite e collegate l una al altra
- Qualsiasi server web nel mondo può aggiungere risorse
- è Basato su [[Livello Applicativo - HTTP|HTTP]]
- fa largo uso di _Hyperlink_  ovvero risorse che hanno riferimenti ad altre risorse (testuali o media)


## Uniform resource Identifier (URI)
una URI è una forma generale per identificare una risorsa presente sulla rete
- _Uniform_: uniformità delle sintassi del identificatore anche se i meccanismi per accedere alla risorse possono variare
- _Resource_: qualsiasi cosa abbia un identità 
	- Documento, servizio, immagine, collezione di risorse
- _Identifier_: informazioni che permettono di distinguer un oggetto da altri oggetti entro un ambito definito di identificazione

## Uniform resource Locator (URL)
sotto insieme di URI che identifica le risorse attraverso il loro meccanismo di accesso
![[Pasted image 20230102190924.png]]
#### sintassi 
	<schema>://<user>:<password>@<host>:<port>/<path>?<query>
- _user_ e _password_ opzionali e generalmente deprecato
- _Scheme_: protocollo di accesso alla risorsa
- _host_: nome di dominio di un host o indirizzo IP
- _Port_: numero si porta del server di solito si usano quelle di default
- _Path_: contiene dati per l host e schema e identifica la risorsa nel contesto di quello schema e host può consistere in una sequenza di segmenti sperata di / ad esempio nel file system del serve ma non solo il path specifica la Request-URI
#### HTTP URL
- _query_: stringa di informazioni che deve essere interpretata dal server

le URL possono essere di 2 tipi
1. _URL assoluta_ : identifica una risorsa indipendentemente dal contesto in cui è usata
2. _URL relativa_ :informazioni per identificare una risorsa in relazione ad un’altra URL (è priva dello schema e della authority)
	![[Pasted image 20230102192305.png]]
queste
- NON viaggiano sulla rete 
- Sono interpretate dal browser in relazione al documento di partenza

## Uniform resource name (URN)
Sottoinsieme di URI che deve o rimanere globalmente unici e persistente anche quando la risorsa cessa di esistere e diventa non disponibile es. 
- urn:oasis:names:specification:docbook:dtd:xml:4.1.2: 
- urn:doi:10.1109/LCN.1988.10239
