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

![[B7F3705E-FED4-414D-A72C-CC21DE26B4A0.jpeg]]

## Meccanica 
![[611F1621-2D7D-4188-B0ED-D40192B3EAA4.jpeg]]
![[4E7CB73B-88B4-4E4E-BD26-C494FC363A92.jpeg]]


![[8B226EB0-4ACF-4A7C-AE86-7E3FDF251757.jpeg]]
## Sintassi del controllo
![[115B18E8-FA31-4519-B21E-98F6552EFC8B.jpeg]]
- la guarda  delle scelta è indicata tra \[\]

### Meccanica del controllo

![[7727E08D-1079-44EB-95EE-38D5F6A8B6BD.jpeg]]

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
![[D2005FF7-FB24-470D-BF6D-D873935B22D4.jpeg]]

## nodo fine flusso
![[7E8F0A98-50EB-48E3-83EF-7B9CCDECB26D.jpeg]]

fa terminare l flusso di esecuzione consumando il token ma non termina tutta l attività


## Segnali ed eventi 
![[9AA38C4D-00C8-42D4-8E11-C27A8FB1FCCE.jpeg]]
![[5FCAEC2C-E6C3-49AA-AB98-0A9C3774E864.jpeg]]

#### Quando usare eventi e quanto azione
1. _Azioni_ : quando è effettuata dal classificatore/ insieme dei classificatore che sta descrivendo il comportamento
2. _Eventi_ : quando si comunica con una entità esterna

## Sotto Attività

![[1A5880A5-9FE8-44BF-A281-E9854B54395C.jpeg]]
![[63823130-7450-4874-974D-DDF206162D0E.jpeg]]