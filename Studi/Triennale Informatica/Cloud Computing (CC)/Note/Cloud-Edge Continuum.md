---
Subject: Cloud Computing
topic: nota
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# Cloud-Edge Continuum
---
uno dei strumenti piu aggiornati per quanto riguarda il cloud.
 


si parla di _Internet of Things(IoT) + cloud_. ovvero 


#### Strutture classiche
_IoT + Edge_:ovvero infrastrutture dove c era bisogno di costruire vicino a la sensoristica anche il piccolo data center per l elaborazione dei dati
_IoT + cloud_: stessa struttura dove L IoT ha la se ma l elaborazione viene fatta in cloud 
![[IMG_0580.jpeg]]



## Cloud-Edge continuom 
Cerca di prendere il meglio dei due mondi di _IoT+Edge_ e _IoT+Cloud_  cercando di spostare il calcolo verso l IoT cosi da avere
- piu computing power
- piu connettivita
- meno latenza 
![[IMG_0581.jpeg]]
![[IMG_0582.jpeg]]

##### Problematiche dei Edge-Cloud continuom 
![[IMG_0583.jpeg]]


il fatto che l infrastruttura sia molti dinamica puo essere molto problematico per via della difficoltai gestione 


### Problema della distribuzione
utilizzare questa tecnologia porta a delle problematiche di scelta del nodo da utilizzare  su dove piazzare l applicazione e i dati che voglio far girare.
i parametri sono 
- Il costo di utulizzo
- la qualità del servizio che puo essere garantita
- il consumo di risorse
- e la sicurezza del nodo 
![[IMG_0585.jpeg]]
per questo piazzamento ci d sono diversi approccio da considerare 
![[IMG_0586.jpeg]]

- _MILP_: si fomalizza il problema come un problema di [[Programmazione lineare]] e si risolve con l [[Algoritmo del Simplesso|Algoritmo del Simplesso]].
	-  Trova l _ottimo_ ma puo richiedere molto tempo
	- difficolta di esprimere informazioni non numeriche. come la possibilità di escludere certi nodi
- _[[Machine Learning|MAchine learning]]_: si puo utilizzare l intelligenza artificiale 
	- si puo imparare una strategia ma molti difficile per via della variabilità dei dati in casi di reti grandi
	- manca di Explainability la soluzione è difficile da capire e spiegare
- _Dichiarativo_:Servizio S puo essere piazzata al nodo N se
	- facile da leggere
	- piu veloce di MILP
	- facile esprimere informazioni non numeriche
	- spiegabile

L approccio dichiaravativo funziona come una lista di requisiti e poi si lascia al _inference engine_ la ricerca della soluzione che soddisfa tutto i vincoli.



Si utilizzano la [[Definizione di Probabilita|probabilita]] per modellare _la dinamicita del infrastruttura_    
![[IMG_0587.jpeg]]
il problema della _Trust_ non è [[Funzione Monotona|Monotona]]

### Monitoring e Sostituzione
controllando i fari servizzi potrebbe risuccedere che i servizzi debbano essere rispostati

per fare rifare il ripiazzamento si utilizza il _cotinuo risoning_ ovvero dopo il piazzamento si controlla solo il [[Microservices|servizio]] che da problemi e si rimpiazza solo quello 
![[IMG_0588.jpeg]]