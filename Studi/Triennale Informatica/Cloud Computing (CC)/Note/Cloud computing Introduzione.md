---
Subject: Cloud Computing
topic: nota
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# Cloud computing Introduzione
---


domande di solito chieste ai colloqui 
- Container
- MicroServizi: programmazione orientata ai microservizi
- Sviluppo servelless: 
- PaaS: Platform and Service
- AWS: amazon service


Virtualizzazione del hardware come software. 



Problemi di Portabilità: risolto dai container 

business model 

Data center


Prequisiti: 
Sistemi Operativi e computer networks


### Economia basata sui servizzi:
concetto di economia rilevante per capire il cloud computing 

l economia si è spostato da un economia di. “beni” in una a “servizi” 
beni: possiedi il bene è tuo responsabilità. esempio: _biciletta_
servizio: non possiede il bene ma compri un servizi, questo puo soddisfare lo stesso bisogno che soddisferebbe un bene : esempio _Cilopi_



la scelta di un servizio si basa su _contratto del servizio_ che definiscono i costi e le modalità di utilizzo del servizio. cosa è garantito 

sui i contatti si basano la risoluzione dei problemi 



### Cos è il cloud computing
Risorse di computazione o memorizzazione a cui si accede tramite servizi 

##### Definizione formale NIST
il cloud computing è un _modello_, per consentire un accesso tramite la [[Reti|Rete]], onnipresente, conveniente, e su richiesta ad un insieme condiviso di risorese computazionali configurabili (es: rete,servers, storage, applicazioni e servizi) con _pochissima_ gestione da parte del provider.
- Modello: Hardware, Software

#### Idee chiave
- una Servizi su richiesta effecenti di infrastrutture virtuale auto-gestite
- fornisce a molti clienti delle risorse virtualizate scalabili dinamicamente
	- ovvero possono cambiare in poco tempo le risorse effettive dedicate ad un dato cliente
- disaccoppiamento del servizio e della tecnologia impiegata per realizzarlo 
   
#### Economia per l aziende che lo usano 
- Eliminazione del costo iniziale da parte degli utenti del _cloud computing_
	- Costa meno avviare il servizio che comprare tutto l hardware e software per metterlo su
- Pay-For-user
	- anche se questo puo essere piu costato di un costo fisso questo è ripagato da una maggiore _elasticita_ e dal _trasferimento del rischio_
		- _elasticita_: se ci sono richieste improvise con il cloud si puo velocemente risponderne senza si dovrebbe aspettare i tempi tecnici della aumento delle risorse disponibili, più questo diventa un investimento che potrebbe essere sprecato se non si ripresenta quella domanda spesso
		- _trasferimento del rischio_: Se ci sono dei problemi la “colpa” (in accordo al SLA) è del gestore del cloud non del tecnico (es: si rompere un disco)

### Contratti
i contratti servono per definire la qualita del servizio e gli accordi se questi non dovessero essere garantiti 

_Qualità del servizio_:  

_Service Level Agreement_: 
scritte da 3 enti
- l espetto di informatica
- l esperto del prodotto 
- un esperto di norme  
![[IMG_0510.jpeg]]

sono le definizioni di cosa ci è garantito e di ciò che otterremo se non vengono mantenute quelle garanzie. 
- Importante leggere attentamente le definizioni di cosa si riferiscono i SLA


Esempio GOOGLE

sono fatti per far sentire bene il cliente, ovvero sono scritte in modo che sembri che le conseguenze della venuta meno delle ragazzine siano probabili e convenienti ma in realtà sono scritte per essere molto poco _[[Definizione di Probabilita|probabili]]_   

## Stabilire il  numero di risorse necessarie

_Overprovisioning_: si allocano più risorse di quelle effettivamente necessarie. solitamente si crea questa situazione quando si stima la _richiesta_ di risorse del sistema al picco delle domande degli utente  e si allocano le risorse per quella domanda, questo porta a sprechi se la stima è corretta e peggio ancora se si è fatta una sovrastima 
- Risorse possono essere di qualsiasi tipi: hardware, di rete e cosi via 
un allocazione eccessiva di risorse ci porta a _sprechi di capitarle_
![[IMG_0511.jpeg]]

_Underprovisioning_: Si allocano meno risorse di quelle effettivamente necessarie ciò porta a non sprecarle ma a delle conseguenze più _difficili da misurare_ 
- l Underprovisioning porta a _rifiutare_ gli utenti in eccesso e questo porta non solo ad utenti che non fruttano ma questi potrebbero anche _non tornare mai_
![[IMG_0512.jpeg]]


### Service Models
esempio di cosa significa la scala da qualcosa che gestisci e possiedi e ciò che otteniamo con un servizio 
![[IMG_0513.jpeg]]
sigle di modelli che virtualizzano cose 
1. _[[Infrastructure As A Service(Iaas)|Infrastructure As A Service]]_(_Iaas_) : 
	- provvede a dare un infrastruttura virtualizate come, server, storage e networking.  
	- _Il provider_ gestisce solo l infrastruttura 
	- _l utente_ tutto ciò che riguarda a gli altri aspetti del Deployment (OS,APP)
	- esempi di servizi: EC2, S3
2. _[[Platform As A Service(Paas)|Platform As A Service]]_ (_Paas_):
	- provvedere a fare un intera piattaforma virtualizate ([[Sistemi Operativi|OS]], Virtual machine, SDKs) 
	- _il provider_ e gestisce l infrastruttura + OS + Il software di abilitazione (?)
	-  _l Utente_ si occupa di installare e gestire l app 
	- esempi: Heroku, Azure, GAE
3. _[[Software As A Service(Saas)|Software As A Service]]_ (_Saas_):
	- Provvede a dare software su richiesta accessibile tramite [[Application Programming Interface (API)|APIs]] 
	- _il provider_: gestisce infrastruttura +OS+app
	- _L utente_: non gestisce nulla
	- esempi: Salesforce.com


### Deployment Models
![[IMG_0514.jpeg]]
1. _Private_: 
	- Controllo totale sui dati. sensato per un discorso della sicurezza dei dati
	- Scarsa calabilità
2. _Public_:
	- scalabilita totale
	- Scarsa controllo dei dati
3. _Ibrido_: la giusta via di mezzo 
	- controllo su la parte interessante dei dati
	- Scalabiltia sulle parti del applicazione che la necessitano 
	 

#### Problematiche del cloud computing
1. _Data Confidentiality_
	- Dove i dati vengono conservati?
	- L’integrità e la privacy dei dati sarà garantita
	- Potremmo sapere se ce stato un problema  
2. _Business continuity/service Availability_
	- Può succedere che il cloud vada giù
	- Può essere un singolo punto di fallimento
3. _Vendor lock-in_
	- Strategia per mantenere dentro gli utenti sul proprio servizio
		- Solitamente scritti nel contratto 
	- sono le problematiche che non permettono ad gli utenti di un servizio di cambiare provider. (es: formato dei dati, costo di ritoccare il codice ) 