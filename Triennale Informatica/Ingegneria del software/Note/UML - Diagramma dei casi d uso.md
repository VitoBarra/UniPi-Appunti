---
Course: "[[Ingegneria Del Software (IS)]]"
topic: nota
tags:
  - IS
---

# UML - Diagramma dei casi d uso
---
Un diagramma di [[Unified modeling Language (UML)]] 

Descrive i [[Analisi dei requisiti| Requisiti Funzionali]], descrive quindi le funzionalità che il sistema deve fornire al esterno.  i campiti che un utente può fare con l aiuto del sistema.


## Componenti Statici
1. _Attore_:  un’entità sterna al sistema, che in interagisce direttamente con esso in un determinato ruolo
	- autore
	- altro sistema
	- tempo (attore speciale)
2. _Caso d uso_:
	- Una funzionalità o un servizio offerto dal sistema a uno o più attori 
	- formalmente: un compito che un attore può svolgere con l’aiuto del sistema 
	- espressa come un insieme di SCENARI
3. _Scenario_:
	- Una sequenza di interazioni (scambi di messaggi)  tra sistema attori


## Costruzione
1. individuare il confine del sistema
2. individuare attori
3. individuare i casi d uso
4. individuare le relazioni attore-caso d uso 
5. specificare il caso d uso con una descrizione testuale(narrativa)

## Regole di costruzione  

![[IMG - UML - Diagramma dei casi d uso 1.jpeg]]
### Generalizzazioni
![[IMG - UML - Diagramma dei casi d uso 2.jpeg]]
![[IMG - UML - Diagramma dei casi d uso 3.jpeg]]
#### errori di generalizzazione 
![[IMG - UML - Diagramma dei casi d uso 4.jpeg]]
![[IMG - UML - Diagramma dei casi d uso 5.jpeg]]

## Dipendenze tra casi di uso
le dipendenze sono segnate con una freccia tratteggiata e va letta dalla dove parte verso la punta quindi: “caso d uso di partenza” dipende ”caso d uso di arrivo”. 

per differenziare le varie dipendenze si scrive lo stereotipo  tra le doppie  parentesi angolate \<stereotipo\>

### Inclusione
![[IMG - UML - Diagramma dei casi d uso 6.jpeg]]
i casi inclusi indicano una dipendenza e viene interpretata come
- il primo caso _necessariamente_ esegue il secondo
i casi inclusi possono essere in stanziati da un attore o essere utilizzati solo da altri casi d uso. è un buon sistema per fattorizzare le operazioni ripetute 

### Estensione
![[IMG - UML - Diagramma dei casi d uso 7.jpeg]]
nel caso in  cui il secondo caso d uso _necessariamente_ esegue  anche il primo ma _non necessariamente viceversa_. 

Extension Point 
![[IMG - UML - Diagramma dei casi d uso 8.jpeg]]

## Componenti dinamici
1. _narrazione associate al caso d uso_: Documento che descrive il modello dinamico 
	- gli senari rilevanti di un caso d uso
	- dal punto di vista degli attori
	- Caratteristica: 
		- Inizio, fine, passi intermedi
		- Condizioni eccezionali
		- precondizioni, Postcondizioni
	![[IMG - UML - Diagramma dei casi d uso 9.jpeg]]
la relazioni di per-condizione e post condizione sono identiche a quelle descritte dalle [[Triple di Hoare]] a meno del esecuzione dei casi eccezionali


- Sintassi della sequenza principale:
	<numero>. <soggetto><azione><complementi>


