---
Course: Cloud Computing
topic: nota
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# REST API e OpenAPI
---
## Rapresentational State Trasfer (REST)
originariamente è stato introdotto con uno _stile architetturale_, sviluppato come un modello astratto della architettura WEB per guidare il Redesign e la definizione i [[Livello Applicativo - HTTP|HTTP]] e URIs.

l idea di base risiede nel 
- Ogni azione risulta nella transizione al prossimo stato del applicazione, con il trasferimento di una rappresentazione di quello stato al utente
- ![[IMG_0549.jpeg]]
1. _Risorse identificate tramite [[WWW - Word Wide Web#Uniform resource Identifier (URI)|URIs]]_
	- _Servizi_ esposti come insieme di risorse indentificate da URIs
2.  _interfaccia uniforme_
	- I clients invocano  [[Livello Applicativo - HTTP#Request Method|metodi HTTP]] per creare/leggere/aggiornare/calcolare risorse
		- _POST_ e _PUT_: per creare e fare l update dello stato delle risorse
		- _DELETE_: per cancellare una risorsa
		- _GET_: per recuperare lo stato corrente di una risorsa
3. _Messaggi Self-Descrittive_
	- le richieste contengono abbastanza informazioni sul messaggio per rendere possibile processarlo
	- la richiesta è _disaccoppiata_ dalla sua rappresentazione. in questo modo il contenuto puo essere acceduto in piu formati.
4. _le Interazioni cons tanto son fatte con Hyperlinks_
	- tutte le interazioni con le risorse sono _senza stato_
	- i server non contengono stato del cliente, i dati della sessione sono mantenuti sul client
	- le interazioni con stato si basano sul concetto di _trasferimento esplicito_ di risorse



## OpenAPI
l iniziativa OpenAPI punta a creare una descrizione  Di REST API standardizzata e neutrale rispetto ai venditori. 
- un semplice linguaggio di descrizione per specificare HTTP API e endpoint, come questi sono usati e la struttura dei dati che entrano ed escono
![[IMG_0550.jpeg]]

![[IMG_0551.jpeg]]

![[IMG_0553.jpeg]]