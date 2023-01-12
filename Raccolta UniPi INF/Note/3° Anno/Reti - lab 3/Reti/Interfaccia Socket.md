---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3 MOC]]

# Interfaccia Socket
---
## Terminologia
- _API_: application programming interface
	- è un insieme di regole che un programmatore deve rispettare per utilizzare delle risorse


## API Socket
è un API che funge da interfaccia tra gli strati di applicazione e quelli di trasporto.

![[Pasted image 20230102184824.png]]
è probabilmente l interfaccia più importante del web siccome le applicazioni comunicano tra di loro leggendo e scrivendo direttamente da questa interfaccia utilizzandola come connessione logica tra gli host, astraendo cosi dal invio e la ricezione di cui si occuperà gli altri livelli dello strato [[Modello TCP-IP|TCP/IP]] nel [[Sistemi Operativi|Sistema operativo]]

![[Pasted image 20230102185215.png]]


### Identificare un processo 
un processo per essere inedificato ha bisogno di due parti
1. l indirizzo IP del host: 32 bit
2. il numero di porta 16 bit
![[Pasted image 20230102185707.png]]
due numeri sono necessari siccome cosi si possono indirizzare più processi sulla stessa macchina host cha ha lo stesso indirizzo IP ma potrebbe esporre servizi diversi su porte diverse.