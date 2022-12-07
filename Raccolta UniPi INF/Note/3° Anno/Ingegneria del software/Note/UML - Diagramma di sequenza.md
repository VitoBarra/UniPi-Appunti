---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# UML - Diagramma di sequenza
---

Un diagramma di [[UML]] per descrivere il comportamento dinamico dello scambio dei messaggi e dati tra oggetti 

#### Componenti
- un rettangolo che indica ruolo e/o tipo dell oggetto ( uno dei due obbligatori, entrambi solo se utile)

- Linea verticale chiamata idea di vita del oggetto
	- linea _tratteggiata_ quando l oggetto è inattivo
	- _continua e spessa_ quando l oggetto è attivo
![[3087AFF8-A47D-4CAC-83D6-54DAC83581EA.jpeg]]
##  Messaggi
- Rappresentano invocazione di operazione o segnali 
	- Possono essere:
		- sincroni (1)
		- di return  (1.1)(Opzionale)
		- Asincroni(2)
		- Asincroni con esplicito consumo di tempo (3) 
		- ![[C62C6E52-587F-4C38-9CE5-9F42CD565ED2.jpeg]]
		- attributo = notoMessaggi(arg1,arg2,…): valore di ritorno
		- i partecipanti possono essere aggiunti e rimossi dinamicamente 
		- ![[472B674C-EA0A-42D7-BF61-3722B7256BEE.jpeg]]
			- questo aggiunge una dipendenza di creazione 
	### Vincoli di tempo e durata
	- ![[2FB6F6F5-AE37-4723-A533-4AC32B92E4F5.jpeg]]
	### Chiamata di metodo 
	- ![[75A08C20-5829-4A7A-A88E-E51A2324061B.jpeg]]
	### Frame condizionali 
	- ![[1CBFA1AD-C720-4C95-BA63-7E7A3D028525.jpeg]]
	- senza guarda = \[true\]
	- piu guarde vere scelta non deterministica
	- tutte guardie false: frame saltato
	### Frame Iterativo 
	- ![[FB9E1D47-B0D4-42F0-8E7E-D5714DB224D4.jpeg]]
		- Loop(n,m): 
			- n: Numero minimo di iterazioni
			- m: numero massimo di interazioni
		- _While_: Loop(0,\*)\[guardia\] o Loop \[guardia\] 
		- _Do-While_: Loop(1,\*) \[guardia\]
		- _for_: loop(n,n) o loop(n) senza guardia
	### Frame Opzionale 
	- ![[F767FDB6-AAC4-4250-A39E-0E45AA4F6E4F.jpeg]]
		- le interazioni contenute nel frame si eseguono solo se la condizione è vera modella l _if then_ quindi senza else
	### Frame Parallelo 
	- ![[91EAED03-0F3D-439F-B17D-410B787D175A.jpeg]]
	- Semantica a interleaving
	- nel esempio le richieste possono arrivare in un ordine qualsiasi 
	### Inclusione di una interazione 
	- ![[B21144EC-DF1A-461C-A5E2-E19BE1947607.jpeg]]
	- si puo includere un interazione definita altrove
	- indicata con ref
	 ### VIncoli di durata
	- ![[660EFD4C-58F5-4527-92E4-68E1BAD22214.jpeg]]
		- Indicata con {vincolo}
	### Gate
	- ![[F672A666-2846-4E18-AE72-F02E57DE9B16.jpeg]]
	- è un punto sul bordo del diagramma a cui è collegato un messaggi in ingresso o in uscita
		- utile quando si riferiscono altri diagrammi.
				

