---
Course: "[[Ingegneria Del Software (IS)]]"
topic: nota
tags:
  - IS
---
# UML - Diagramma di attività
---
Un diagramma [[Unified modeling Language (UML)]] per modellare il flusso di lavoro
- può essere un compiuto un algoritmo  o un processo o un attività.

Questo tipo di Diagramma è utile per rappresentare:
- Processi aziendali (analisi)
- flusso di [[UML - Diagramma dei casi d uso | casi d uso]] (analisi)
- funzionamento delle operazioni di una classe (progettazione)


>[!info] 
>derivate da i [[Flow Chart]] e dalle [[Reti di petri]]

## Sintassi 

![[IMG - UML - Diagramma di attività 1.jpeg]]

## Meccanica 
![[IMG - UML - Diagramma di attività 2.jpeg]]
![[IMG - UML - Diagramma di attività 3.jpeg]]


![[IMG - UML - Diagramma di attività 4.jpeg]]
## Sintassi del controllo
![[IMG - UML - Diagramma di attività 5.jpeg]]
- la guarda  delle scelta è indicata tra \[\]

### Meccanica del controllo

![[IMG - UML - Diagramma di attività 6.jpeg]]

- Le guardie devono comparire tutte le possibilità (il token non può bloccarsi )
- meglio se le operazioni sono mutualmente esclusive ma non è necessario, in caso non lo siano comportamento non deterministico 
- dato un nudo decisione non è obbligatorio un nodo fusione corrispondente
	- potrebbe esserci un nodo di fine flusso 

### Fork Join
- Token game:
	-  _fork_ moltiplica i token
		- dato un token in ingresso ne produce uno per ogni faccia uscente
	-  _Join_ consuma i token
		- si attende un token per ogni freccia entrante
		- si consumano tutti e ne esce solo uno
	- non è necessaria una join per ogni fork

## Fine attivita

se un token raggiunge un nodo di fine attività l intera attività e terminata 
![[IMG - UML - Diagramma di attività 7.jpeg]]

## nodo fine flusso
![[IMG - UML - Diagramma di attività 8.jpeg]]

fa terminare l flusso di esecuzione consumando il token ma non termina tutta l attività


## Segnali ed eventi 
![[IMG - UML - Diagramma di attività 9.jpeg]]
![[IMG - UML - Diagramma di attività 10.jpeg]]

#### Quando usare eventi e quanto azione
1. _Azioni_ : quando è effettuata dal classificatore/ insieme dei classificatore che sta descrivendo il comportamento
2. _Eventi_ : quando si comunica con una entità esterna

## Sotto Attività

![[IMG - UML - Diagramma di attività 11.jpeg]]
![[IMG - UML - Diagramma di attività 12.jpeg]]