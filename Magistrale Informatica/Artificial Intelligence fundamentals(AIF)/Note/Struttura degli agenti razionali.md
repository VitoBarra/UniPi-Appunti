---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course 2: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - AIF
  - IIA
Area: 
topic: 
SubTopic: 
---

# Struttura degli agenti razionali

Gli [[agenti razionali|agenti razionali]] possono essere di varie tipologie ed i vari modi si occupano di implementare in modo diverso il **[[Agenti Razionali|programma agente]]**

lo scheletro generale usato per i tipi di agenti mostrati è il seguente :
```pseudo
\begin{algorithm}
\caption{Skeleton-agente}
\begin{algorithmic}
\STATE \textbf{persistent:} memory, the agent’s memory of the world
\STATE memory $\leftarrow$ \textsc{UpdateMemory}(memory, percept)
\STATE action $\leftarrow$ \textsc{Choose-Best-Action}(memory)
\STATE memory $\leftarrow$ \textsc{UpdateMemory}(memory, action)
\RETURN action
\end{algorithmic}
\end{algorithm}

```

  
### Agenti Table driven
un **agente** **Table driven** è un [[Agenti Razionali|agente]] che utilizza una **tabella** in cui è associato ad ogni **storia di percezioni** una **specifica azione**.
```pseudo
\begin{algorithm}
\caption{TABLE-DRIVEN-AGENT(percept)}
\begin{algorithmic}
\State \textbf{persistent:} percepts, a sequence, initially empty
table, a table of actions, indexed by percept sequences, initially fully specified
\State append percept to the end of percepts
\State action $\leftarrow$ LOOKUP(percepts, table)
\Return action
\end{algorithmic}
\end{algorithm}
```
Questo tipo di agente fa sempre esattamente quello che si vuole ma non è realizzabile in quanto il numero di righe che andrebbero compilate sarebbe esorbitante, ad esempio per gli scacchi è $10^{150}$ piu del numero di atomi($10^{80}$).


##### Agenti reattivi semplici
gli **agenti reattivi semplici** sono [[Agenti Razionali|agenti]] che selezionano le **azioni** basandosi esclusivamente sul percepito corrente, senza tenere conto della **storia dei percetti**.
Questo ha il vantaggio di essere molto piu piccolo rispetto al approccio tabellare grazie al fatto che non c è bisogno di decidere in base al intera storia di percezioni.
```pseudo
\begin{algorithm}
\caption{AGENTE-REATTIVO-SEMPLICE}
\begin{algorithmic}
\State \textbf{persistent:} regole, un insieme di regole condizione-azione (if-then)
\State stato $\leftarrow$ \textsc{Interpreta-Input}(percezione)
\State regola $\leftarrow$ \textsc{Regola-Corrispondente}(stato, regole)
\State azione $\leftarrow$ regola.Azione
\Return azione
\end{algorithmic}
\end{algorithm}
```

![[IMG - aggente reattivi semplici.png]]
questo tipo di agente è limitato in [[Definizione di Problemi-Ambienti|ambienti parzialmente osservabili]]. In tali contesti, la percezione attuale può non contenere informazioni sufficienti per una scelta razionale Una strategia per mitigare tali limiti è l’introduzione della randomizzazione nelle decisioni. In assenza di informazioni sufficienti, un agente può scegliere casualmente tra più azioni, questo aiuta ad evitare comportamenti ciclici. Questo pero si puo anche ottenere con agenti piu sofisticati e solitamente questi sono migliori.  

##### Agenti riflessivo basati su modello (con stato)
Un **Agente basati su modello** è un [[Agenti Razionali|agente]] che mantiene uno **_stato interno_** del [[Definizione di Problemi-Ambienti|ambiente]] ciò permette in [[Definizione di Problemi-Ambienti|ambiente parzialmente osservabili]] di mantenere una conoscenza delle porzioni del ambiente che l agente non puo percepire *ora*.

Lo **_stato interno_** è costruito e aggiornato a partire dalla **storia delle percezioni**. L'aggiornamento continuo di tale stato richiede che l'agente incorpori due forme di conoscenza fondamentali: un **modello di transizione** e un **modello dei sensori**.


Il **modello di transizione** descrive il modo in cui lo stato del mondo evolve nel tempo. Questo modello tiene conto sia delle azioni dell'agente, che modificano lo stato in modo diretto, sia dei cambiamenti autonomi del ambiente, indipendenti dall'agente. Formalmente, questo modello può essere rappresentato come una [[Funzioni|funzione]] di transizione dello stato:$$

T(s, a) \rightarrow s'

$$dove $s$ è lo stato corrente, $a$ è l’azione eseguita dall’agente e $s'$ è lo stato risultante. In ambienti stocastici, tale modello assume la forma [[Definizione di Probabilita|probabilistica]]:$$

P(s' \mid s, a)

$$
Il **modello dei sensori**, invece, definisce la relazione tra lo stato del mondo e i percetti che l’agente riceve e permette all'agente di inferire informazioni sullo **stato del mondo** a partire dai dati **sensoriali**.
```pseudo
\begin{algorithm}
\caption{MODEL-BASED-REFLEX-AGENT}
\begin{algorithmic}
\State \textbf{persistent:}
\State $\hspace{1.5em}$ state, the agent’s current conception of the world state
\State $\hspace{1.5em}$ transition\_model, how the next state depends on current state and action
\State $\hspace{1.5em}$ sensor\_model, how the current world state is reflected in percepts
\State $\hspace{1.5em}$ rules, a set of condition–action rules
\State $\hspace{1.5em}$ action, the most recent action, initially none
\State
\State state $\leftarrow$ \textsc{Update-State}(state, action, percept, transition\_model, sensor\_model)
\State rule $\leftarrow$ \textsc{Rule-Match}(state, rules)
\State action $\leftarrow$ rule.ACTION
\return action
\end{algorithmic}
\end{algorithm}
```

![[IMG - agenti basati su modello.png]]

  

##### Agenti basati sul obbiettivo
Un **Agente basati sul obbiettivo** è un [[Agenti Razionali|agente]] che oltre ad avere un **modello** hanno anche un obiettivo che li guida nelle scelte delle azioni da fare.

La **selezione** delle azioni può risultare immediata nel caso in cui il soddisfacimento del **goal** segua direttamente da una singola azione, ma generalmente non è questo il caso è scegliere un azione richiede la valutazione di sequenze di azioni, e questo puo essere risolto tramite [[Problem-Solving Agent|agenti risolutori di problemi]] o [[Planning Agent|aggenti pianificatori]]

![[IMG - agenti con obiettivi.png]]
Il processo decisionale negli **agenti goal-based** si distingue in modo sostanziale dalle regole condizione–azione tipiche degli agenti riflessivi. Mentre questi ultimi associano direttamente un percetto ad un’azione senza una rappresentazione esplicita del perché, gli agenti goal-based valutano prospetticamente l’impatto delle azioni. Le domande che guidano la scelta sono del tipo: “Cosa succederà se eseguo questa azione?” e “Questa conseguenza contribuirà al raggiungimento del mio obiettivo?”. La conoscenza utilizzata per il ragionamento è rappresentata in maniera esplicita e modificabile, rendendo il comportamento dell’agente più flessibile.

  

##### Agenti basati su funzione di utilità
Un **Agente basato su funzione di utilità** è un [[Agenti Razionali|agente]] un agente intelligente non può affidarsi unicamente a obiettivi per generare comportamenti di alta qualità in ambienti complessi, infatti possono esserci degli obiettivi secondari che se presi in considerazione rendono il comportamento piu razionale.

Per ottenere ciò si utilizza un __*funzione di utilità*__ (**utility function**) che è una funzione che da un peso ed un valore a tutti i sotto obiettivi che vogliamo rispettare.

l'agente sceglie azioni massimizzando il valore di **utilità atteso**

Un agente basato sull’utilità possiede una maggiore flessibilità rispetto a un agente puramente **basato su obiettivi**. ad esempio, in presenza di obiettivi in conflitto (ad esempio, rapidità e sicurezza nella guida), la funzione di utilità consente di modellare i compromessi appropriati. Oppure, quando nessun obiettivo può essere raggiunto con certezza, l’utilità permette di valutare le probabilità di successo in relazione all’importanza dei singoli obiettivi.
![[IMG - agenti con valutazione di utilita.png]]
Inoltre, non tutti gli agenti basati sull’utilità possiedono un modello esplicito del mondo. Alcuni e sono detti **model-free agents**.

##### Agenti che apprendono
Un **agente** intelligente può essere progettato in molteplici modi, ma una delle prospettive più significative consiste nel concepirlo come un agente apprendista, ovvero capace di migliorare le proprie prestazioni nel tempo.

Un agente che apprende può essere costruito a partire da qualsiasi tipo di agente ed è particolarmente utile in ambienti **[[Definizione di problemi-Ambienti|inizialmente sconosciuti]]**. La struttura concettuale di un tale agente comprende quattro componenti fondamentali: **elemento di apprendimento**, **elemento di prestazione**, **critico** e **generatore di problemi**

L'**elemento di prestazione** è responsabile della selezione delle azioni e corrisponde all'agente nella sua forma tradizionale, trattando le percezioni e traducendole in decisioni. L'elemento di apprendimento, invece, ha il compito di migliorare nel tempo il comportamento dell'agente, basandosi sul feedback fornito dal **critico**.

Il **critico** fornisce una valutazione basata su uno standard di prestazione esterno, fisso e immutabile, necessario per evitare che l'agente adatti il proprio criterio di successo in modo autoreferenziale. Questo standard può assumere la forma di ricompensa o penalità ed serve a fare in modo che l agente "scopra" cosa è positivo è cosa è negativo.

il **generatore di problemi** ha la funzione di proporre esperienze nuove e informative, anche se subottimali nel breve periodo. Ciò è essenziale per l’esplorazione: senza questa componente, l’agente si limiterebbe ad agire secondo la conoscenza attuale, precludendosi la possibilità di migliorare.
![[IMG - architettura agente che aprende.png]]