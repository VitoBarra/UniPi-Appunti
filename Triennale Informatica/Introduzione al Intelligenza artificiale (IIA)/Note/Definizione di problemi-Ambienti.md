---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IA
  - AIF
---
# Definizione di problemi-Ambienti
---
Definire un problema per un [[Agenti Razionali|agente]] significa caratterizzare ’ambiente operativo in cui esso si trova ad agire. La definizione accurata del problema e della progettazione di un agente passa attraverso il **modello PEAS**, che descrive:
- _P_ (**Performance measure**): il criterio secondo cui si valuta il comportamento dell’agente.
- _E_ (**Environment**): tutto ciò che circonda l’agente e con cui interagisce.
- _A_ (**Actuators**): i mezzi tramite cui l’agente può agire sull’ambiente.
- _S_ (**Sensors**): gli strumenti di percezione dell’ambiente.

alcuni esempi di problemi specificati che seguono questo modello sono: ![[IMG - Tabella con esempi di problemi-ambienti.png]]

Ogni ambiente-problema può essere descritto secondo alcune **proprietà fondamentali** che influenzano le strategie di progettazione dell’agente.

1. **Osservabilità**:
	- Un ambiente è detto **_completamente osservabile_** se, in ogni istante, l’agente può accedere a tutte le informazioni rilevanti per scegliere un’azione ottimale. In tali casi, l’agente non necessita di un modello interno dello stato del mondo.
	- Al contrario, in ambienti **_parzialmente osservabili_**, i sensori non sono in grado di rilevare completamente lo stato dell’ambiente, per limiti tecnici o perché alcune variabili sono intrinsecamente nascoste. L’agente deve quindi mantenere una rappresentazione interna dello stato.
2. **Singolo/Multiagente**:
	- In ambienti **_singolo-agente_**, solo un agente è rilevante per il raggiungimento dell’obiettivo. Tuttavia, molti ambienti reali sono **_multi-agente_**, cioè popolati da altri agenti con cui può essere necessario cooperare o competere.
	- In ambienti **competitivi**, le azioni di un agente influenzano negativamente le prestazioni degli altri ($\text{maximizing}_{A} \Rightarrow \text{minimizing}_{B}$).
	- In ambienti **cooperativi**, più agenti condividono lo stesso obiettivo, e la comunicazione diventa razionale.

3. **Predicibilità**:
	- Un ambiente è _deterministico_ se il risultato di ogni azione è completamente prevedibile dato lo stato corrente. Quando invece le azioni possono portare a più esiti, si parla di ambiente **_non deterministico_**.
	- Se le **[[Definizione di Probabilita|probabilità]]** associate agli esiti sono note, l’ambiente è detto _stocastico_. In questo caso, l’agente può adottare strategie basate su modelli probabilistici.$$
\text{P}(s_{t+1} | s_t, a_t) = \text{nota} \Rightarrow \text{ambiente stocastico}
$$
4. **Episodico/Sequenziale**:
	- In ambienti **_episodici_**, le decisioni si suddividono in episodi distinti e indipendenti: ogni percezione è seguita da un’unica azione, e l’episodio successivo non dipende da quello precedente.
	- Negli ambienti **_sequenziali_**, ogni azione può influenzare gli stati futuri. Di conseguenza, l’agente deve pianificare in funzione delle conseguenze a lungo termine.

5. **Statico/Dinamico**:
	- Un ambiente è **_statico_** se non cambia mentre l’agente sta deliberando. Questo semplifica notevolmente il processo decisionale.
	- In ambienti **_dinamici_**, lo stato dell’ambiente può cambiare mentre l’agente è in fase decisionale. In questi casi, anche il tempo gioca un ruolo: un ritardo può equivalere a un’azione nulla.
	- Tra i due estremi si colloca l’ambiente _semi-dinamico_, in cui lo stato resta invariato ma la performance dell’agente degrada nel tempo.

6. **Discreto/Continuo**:
	- La distinzione _discreto/continuo_ si applica a vari aspetti: lo stato dell’ambiente, il tempo, le percezioni e le azioni. Gli ambienti discreti presentano un numero finito di stati e azioni, mentre quelli continui implicano spazi infiniti e variabili continue.
	- Questa distinzione influisce sulla complessità computazionale: nei casi discreti si possono esplorare combinazioni, mentre nei continui è spesso necessario ricorrere ad approssimazioni.

7. **Noto/Ignoto**:
	- Infine, un ambiente è _noto_ se l’agente (o il suo progettista) conosce le regole che determinano le transizioni di stato e gli esiti delle azioni. In caso contrario, l’ambiente è _ignoto_ e l’agente deve apprendere come funziona attraverso l’interazione.
	- La conoscenza dell’ambiente è distinta dalla sua osservabilità: un ambiente può essere completamente osservabile ma ignoto (es. un videogioco nuovo con regole non note) o noto ma parzialmente osservabile (es. giochi di carte con regole note ma carte coperte).
