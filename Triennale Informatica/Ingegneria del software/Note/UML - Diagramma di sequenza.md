---
Course: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# UML - Diagramma di sequenza
---

Un diagramma di [[Unified modeling Language (UML)]] per descrivere il comportamento dinamico dello scambio dei messaggi e dati tra oggetti 

#### Componenti
- un rettangolo che indica ruolo e/o tipo del oggetto ( uno dei due obbligatori, entrambi solo se utile)

- Linea verticale chiamata idea di vita del oggetto
	- linea _tratteggiata_ quando l oggetto è inattivo
	- _continua e spessa_ quando l oggetto è attivo
![[IMG - UML - Diagramma di sequenza 1.jpeg]]
##  Messaggi
- Rappresentano invocazione di operazione o segnali 
	- Possono essere:
		- sincroni (1)
		- di return  (1.1)(Opzionale)
		- Asincroni(2)
		- Asincroni con esplicito consumo di tempo (3) 
		- ![[IMG - UML - Diagramma di sequenza 2.jpeg]]
		- attributo = notoMessaggi(arg1,arg2,…): valore di ritorno
		- i partecipanti possono essere aggiunti e rimossi dinamicamente 
		- ![[IMG - UML - Diagramma di sequenza 3.jpeg]]
			- questo aggiunge una dipendenza di creazione 
	### Vincoli di tempo e durata
	- ![[IMG - UML - Diagramma di sequenza 4.jpeg]]
	### Chiamata di metodo 
	- ![[IMG - UML - Diagramma di sequenza 5.jpeg]]
	### Frame condizionali 
	- ![[IMG - UML - Diagramma di sequenza 6.jpeg]]
	- senza guarda = \[true\]
	- piu guarde vere scelta non deterministica
	- tutte guardie false: frame saltato
	### Frame Iterativo 
	- ![[IMG - UML - Diagramma di sequenza 7.jpeg]]
		- Loop(n,m): 
			- n: Numero minimo di iterazioni
			- m: numero massimo di interazioni
		- _While_: Loop(0,\*)\[guardia\] o Loop \[guardia\] 
		- _Do-While_: Loop(1,\*) \[guardia\]
		- _for_: loop(n,n) o loop(n) senza guardia
	### Frame Opzionale 
	- ![[IMG - UML - Diagramma di sequenza 8.jpeg]]
		- le interazioni contenute nel frame si eseguono solo se la condizione è vera modella l _if then_ quindi senza else
	### Frame Parallelo 
	- ![[IMG - UML - Diagramma di sequenza 9.jpeg]]
	- Semantica a interleaving
	- nel esempio le richieste possono arrivare in un ordine qualsiasi 
	### Inclusione di una interazione 
	- ![[IMG - UML - Diagramma di sequenza 10.jpeg]]
	- si puo includere un interazione definita altrove
	- indicata con ref
	 ### VIncoli di durata
	- ![[IMG - UML - Diagramma di sequenza 11.jpeg]]
		- Indicata con {vincolo}
	### Gate
	- ![[IMG - UML - Diagramma di sequenza 12.jpeg]]
	- è un punto sul bordo del diagramma a cui è collegato un messaggi in ingresso o in uscita
		- utile quando si riferiscono altri diagrammi.
				

