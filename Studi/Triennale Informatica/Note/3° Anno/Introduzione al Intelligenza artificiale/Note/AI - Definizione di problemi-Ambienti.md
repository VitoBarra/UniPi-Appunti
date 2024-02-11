---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione al Intelligenza Artificiale (IIA)]]

# Definizione di problemi-Ambienti
---
Definire un problema per un agente significa caratterizzare l’ambiente in cui l’agente opera (ambiente operativo). 
Descrizione PEAS dei problemi 
- _P_ erformance 
- _E_ nvironment 
- _A_ ctuators 
- _S_ ensors

Esempi di ambienti 
![[Pasted image 20230211162609.png]]
Proprietà dell’ambiente-problema
##### Osservabilità
- Ambiente _completamente osservabile_ 
	- L’apparato percettivo è in grado di dare una conoscenza completa dell’ambiente o almeno tutto quello che serve a decidere l’azione 
	-  Non c’è bisogno di mantenere uno stato del mondo (esterno) 
- Ambiente _parzialmente osservabile_: 
	-  Sono presenti limiti o inaccuratezze dell’apparato sensoriale.
##### singolo/multiagente
-  Distinzione agente/non agente 
	-  Il mondo può anche cambiare per eventi, non necessariamente per azioni di agenti. 
-  Ambiente **multi-agente _competitivo_** (schacchi) 
	- Comportamento randomizzato (è razionale) 
-  Ambiente _multi-agente cooperativo_ (o benigno) 
	-  Stesso obiettivo 
	-  Comunicazione
##### Predicibilità
-  _Deterministico_ 
	- Se lo stato successivo è completamente determinato dallo stato corrente e dall’azione. Esempio: scacchi 
-  _Stocastico_ 
	- Esistono elementi di incertezza con associata probabilità. Esempi: guida, tiro in porta 
-  _Non deterministico_ 
	- Si tiene traccia di più stati possibili risultato dell’azione (ma non in base ad una probabilità)

##### Episodico/sequenziale
- _Episodico_ 
	-  L’esperienza dell’agente è divisa in episodi atomici indipendenti (es. partite diverse)
	-  In ambienti episodici non c’è bisogno di pianificare 
- _Sequenziale_ 
	-  Ogni decisione influenza le successive (es. scacchi in una partita)

##### Statico/dinamico
- _Statico_ 
	-  Il mondo non cambia mentre l’agente decide l’azione (es. Cruciverba) 
- _Dinamico_ 
	-  Cambia nel tempo, va osservata la contingenza 
		- Esempio: Taxi 
	-  Tardare equivale a non agire 
- _Semi-dinamico_ 
	-  L’ambiente non cambia ma la valutazione dell’agente sì 
		- Esempio: Scacchi con timer
		
##### Discreto/continuo
- Possono assumere valori _discreti o continui_
	-  lo stato: solo un numero finito di stati 
	-  il tempo 
	-  le percezioni 
	-  le azioni 
-  Combinatoria (nel discreto) versus infinito (nel continuo)
	- non è detto che combinatorio sia meglio di infinito

##### Noto/Ignoto
- Distinzione riferita allo stato di conoscenza dell’agente sulle leggi fisiche dell’ambiente 
- L’agente conosce l’ambiente oppure deve compiere azioni esplorative? 
- Noto diverso da osservabile (es. carte coperte, ma regole note) 
