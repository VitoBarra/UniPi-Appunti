---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# UML - Diagramma di macchina a stati
---
Diagramma [[UML]] per rappresentare lo stato del sistema 


un diagramma a macchine a stati rapresenta il comportamento dinamici delle instanze di un classificatore ( es.oggetti istanza di una classe)

questa è composta dai nodi stati e da archi che rappresentano una transazione di fatto è un [[Grafo]]

#### Componenti
1. _Stato_: 
	- Questo è composto da valori 
	- ha un nome unici
	- puo essere composto da piu satti

### Sintassi
1. _Stato_: Rapresentato da rettangolo arrotondadi
2.  _Nodo finale_: cerchio bordato
3. _Nodo Iniziale_: cerchio 
	 ![[6FE5C134-EA22-4377-AE8D-FB54284DCC8D.jpeg]]
4. _Transazioni_: freccia che esce da uno stato e punta un altro 
- ![[539BC5E7-3B74-457F-8B69-57B4BA9B8AE2.jpeg]]
- tutte le parti sono opzionali ma l evento dovrebbe esserci sempre tranne nel caso delle transizioni di _completamento_
	- ##### Semantica
		- Definisce la risposta dell oggetto all occorrenza di un _evento_
			- un evento occorre istantaneamente
			- eventi per cui non esiste transizione dallo stato corrente vengonoignorati
			- se ci sono più transazioni per lo stesso eventi se ne sceglie uno in modo non deterministico
			- un evento viene aggiunto al diagramma solo se ha degli effetti.
			- ##### Tipi di evento
				- operazioni o segnale _op(a:T)_
					- la transizione è abilitata quan do l oggetto riceve una chiamata di metodo o un segnale con parametro a di tipo T (potrebbero non esserci parametri) 
				- Evento di variazione _quando(exp)_ o _When(exp)_
					- la transizione è abilitata appena l espressione diventa vera
					- l espressione può indicare un tempo assoluto o una condizione su variabili
				- Evento  Temporale _Dopo(time)_ o _after(time)_:
					- la transizione è abilitata dopo che l oggetto p stato fermo “time ” in quello stato 
		- viene presa solo se la _condizione_ è vera
		- comporta l esecuzione delle _azioni_ specificate
5.  _Entry,exit,Transazioni e attivita interne_:  operazioni che da eseguire in concomitanza con l astratta uscita o il restare in uno stato
	1. ![[FDCD959C-CBB2-460A-861F-36F16B4B3631.jpeg]]
	 - _Entry_: azione da fare all entrata nello stato
	 - _Exit_: azione da fare al uscita dallo stato
	 - _Transizioni interne_: azioni in risposte a degli eventi che non fanno uscire dallo stato 
	 - _do_: attivita interna in esecuzione durante la permanenza nello stato

### Stati compositi 
 Si possono nominare delle macchine a stato e usarle come stati stessi 
 ![[F9D7FE63-269A-4268-B4A1-142B2853062D.jpeg]]

possono essere sequenziali o paralleli 
![[4F2A172E-20EA-4435-A8DD-D23AA4D4B1BB.jpeg]]

in quello sequenziale si aspetta la normale uscita mentre in quello parallelo la transizione di completamento si comporta come una Join quindi ogni azione paralllela deve prima terminare  e poi si uscirà dallo stato.

### Sotto macchine
Si possono define delle macchine in modo poterne nominare e riutilizzarle n piu contesti.
si fa inserendo nella macchina un quadrato nominato 
![[9FDFA06B-C120-4B9C-A916-79B3325AB2C5.jpeg]]
nella macchina si possono definire gli entri e gli exit point questo permettono la comunicazione con le macchine esterne 
1. _Entry Point_ Indicate con un cerchio
2. _Exit Point_: Cerchio con croce


### Decisini 
si possono scegliere piu stati utilizzando dei preudo stati di decisone 
![[EBF21BF3-60E9-4B10-A1D8-B3AFA9F92A2F.jpeg]]
##### decisone
Come per il [[UML - Diagramma di attività|Diagramma di attivita]] la disguzione tra le disgunzione (l OR) deve essere _true_ ed è ammesso non determinismo 
![[531B7E84-CA4A-403B-BD7C-272336C070A0.jpeg]]
##### Giunzione 
uno pseudo stato in cui entra un numero di transizione e ne esce un altro 
![[F0ED69D7-CAA6-487C-9F55-1E7CDCE69ACC.jpeg]]
le condizioni sono valutato in modo statico 
![[96941907-735F-4BB1-8D22-A2CAB3C8FC29.jpeg]]
![[CA4575CF-2EA0-44CE-8C26-2092BBA75EA0.jpeg]]
in questo caso non c è bisogno che almeno una condizione sia vera  se è questo il caso non ci si muove di stato 
![[2CF4EF7D-078F-47DF-BA99-A6DD098BF9C9.jpeg]]
##### HIstory
![[3B07591E-928C-4280-8C15-A8A0B2AF7CD2.jpeg]]
![[EDC1B92C-E8AA-4071-AE10-54C4B634B0D8.jpeg]]