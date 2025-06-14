---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---
# Definizione di Problemi-Ambienti
---
Definire un problema per un [[Agenti Razionali|agente]] significa caratterizzare ’ambiente operativo in cui esso si trova ad agire. Per definire precisamente un problema si utilizza il modello **modello PEAS**, che descrive:
- _P_ (**Performance measure**): il criterio secondo cui si valuta il comportamento dell’agente.
- _E_ (**Environment**): tutto ciò che circonda l’agente e con cui interagisce.
- _A_ (**Actuators**): i mezzi tramite cui l’agente può agire sull’ambiente.
- _S_ (**Sensors**): gli strumenti di percezione dell’ambiente.
alcuni esempi di problemi specificati che seguono questo modello sono: ![[IMG - Tabella con esempi di problemi-ambienti.png]]
Ogni ambiente ($E$) può essere descritto da delle **proprietà** che influenzano le strategie di progettazione dell’agente.
1. **Osservabilità**:
	- **_completamente osservabile_** se, in ogni istante, l’agente può accedere a tutte le informazioni rilevanti per scegliere un’azione ottimale. 
	- **_parzialmente osservabile_**, i sensori non sono in grado di rilevare completamente lo stato dell’ambiente, L’agente deve quindi mantenere una rappresentazione interna dello stato.
	- **non osservabile**(o **sensorless**): l'agente non ha sensori e deve costringere lo stato obiettivo
2. **Singolo/Multiagente**:
	- **_Singolo agente_**, solo un agente è rilevante per il raggiungimento dell’obiettivo. Tuttavia, 
	- **_Multi agente_**: c è piu di un agente nel ambiente e come un agente deve agire dipende dal tipo di interazione che hanno gli agenti 
		- In ambienti **[[Teoria dei giochi - Giochi Non-Cooperativi|competitivi]]**, le azioni di un agente influenzano negativamente le prestazioni degli altri ($\text{maximizing}_{A} \Rightarrow \text{minimizing}_{B}$).
		- In ambienti **[[Teoria dei giochi - Giochi cooperativi|cooperativi]]**, più agenti condividono lo stesso obiettivo, e la comunicazione diventa razionale.
3. **Predicibilità**:
	- **_deterministico_** se il risultato di ogni azione è completamente prevedibile dato lo stato corrente.
	- **_non deterministico_**: se le azioni possono portare a più esiti e non si puo sapere a priori quale sarà l'esito.
	- **_Stocastico_**: se le azioni possono portare a più esiti ma questi sono governati da una certa [[Distribuzione di probabilita|distribuzione di probabilità]] nota o scopribile.
4. **Episodico/Sequenziale**:
	- **_Episodici_**: le decisioni si suddividono in episodi distinti e indipendenti: ogni percezione è seguita da un’unica azione, e l’episodio successivo non dipende da quello precedente.
	- **_Sequenziali_**: ogni azione può influenzare gli stati futuri. Di conseguenza, l’agente deve pianificare in funzione delle conseguenze a lungo termine.
5. **Statico/Dinamico**:
	- **_Statico_**:  se lo stato non cambia ameno che l agente non faccia qualche azione.
	- **_dinamico_**: lo stato dell’ambiente può cambiare mentre l’agente è in fase decisionale. In questi casi, anche il tempo gioca un ruolo: un ritardo può equivalere a un’azione nulla.
	- **_Semi-dinamico_**: in cui lo stato resta invariato ma la performance dell’agente degrada nel tempo.
6. **Discreto/Continuo**:
	- **_discreto/continuo_** si applica a vari aspetti: lo stato dell’ambiente, il tempo, le percezioni e le azioni. Gli ambienti discreti presentano un numero finito di stati e azioni, mentre quelli continui implicano spazi infiniti e variabili continue.
7. **Noto/Ignoto**:
	- **_Noto_**: se l’agente (o il suo progettista) conosce le regole che determinano le transizioni di stato e gli esiti delle azioni. In caso contrario
	- **_Ignoto_**: l agente non sa le regole delle transizioni deve apprendere come funziona attraverso l’interazione.