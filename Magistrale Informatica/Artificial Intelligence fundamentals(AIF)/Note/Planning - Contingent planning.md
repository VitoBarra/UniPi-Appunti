---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---

# Planning - Contingent planning
---
Gli **agenti Contigent Planning** per [[Planning - Domini incerti|ambienti incerti]] operano in [[Definizione di Problemi-Ambienti| ambienti parzialmente osservabili o non deterministici]] segue la stessa linea della ricerca in [[Ricerca in ambienti parzialmente osservabili|ambienti parzialmente osservabilie]] nei quali l’esecuzione delle azioni può produrre esiti differenti e l’agente riceve solo informazioni parziali sullo stato effettivo del mondo. In tali contesti, la pianificazione deve tener conto delle possibili percezioni future, includendo scelte condizionali che permettano di adattare il comportamento in base alle osservazioni ricevute.  

Nel **contingent planning**, il piano non è più una sequenza lineare di azioni, ma una **struttura condizionale** che specifica, per ogni situazione percettiva possibile, quale azione eseguire successivamente. Ogni ramo del piano dipende da una condizione percettiva della forma *“se il percetto è vero, allora esegui questa azione”*. L’agente, durante l’esecuzione, osserva il mondo e seleziona il ramo del piano coerente con il percetto rilevato, garantendo così una risposta adeguata anche in presenza di incertezza.  

Il belief state viene aggiornato in due fasi distinte. Nella prima, si calcola lo stato di conoscenza risultante dall’applicazione dell’azione, come per il caso degli agenti sensorless:  
$$
\hat{b} = (b - DEL(a)) \cup ADD(a)
$$
dove $DEL(a)$ e $ADD(a)$ rappresentano rispettivamente gli effetti negativi e positivi dell’azione.  
Nella seconda fase, si integra l’informazione proveniente dalle percezioni. Se il percetto ricevuto $p$ è associato a un unico *percept schema* del tipo $\text{Percept}(p,\; PRECOND:c)$, le condizioni $c$ che permettono la percezione vengono aggiunte al belief state insieme al percetto stesso. Tuttavia, se un percetto può derivare da più schemi percettivi compatibili con il belief state $\hat{b}$, l’agente deve includere nel proprio stato di conoscenza la **disgiunzione** delle condizioni possibili, incrementando così la complessità della rappresentazione.  

L’interpretazione logica del belief state consente all’agente di valutare ogni condizione di ramificazione verificando se la formula corrispondente è logicamente implicata o contraddetta dallo stato corrente. In questo modo, l’agente evita di trovarsi in una situazione in cui la verità di una condizione sia indeterminata. Le variabili presenti nei rami condizionali sono considerate **quantificate esistenzialmente**, poiché il piano resta valido finché esiste una sostituzione coerente che soddisfi le condizioni di ogni ramo.  

L’aggiornamento dei belief states, combinato con la gestione delle percezioni, permette di estendere la ricerca nel dominio delle politiche condizionali, rappresentabili come una forma di [[Alberi di ricerca AND-OR|ricerca AND–OR]] sui belief states. Le azioni con effetti non deterministici, definite mediante disgiunzioni negli **EFFECT** degli schemi d’azione, vengono trattate nello stesso quadro formale, con opportune modifiche nella fase di aggiornamento ma senza alterare la struttura della ricerca.  

Le euristiche impiegate nel [[Planning - Agenti Sensorless|planning sensorless]] possono essere adattate anche al caso contingente, poiché entrambi i paradigmi condividono la necessità di stimare la distanza informativa dal goal e di gestire esplicitamente l’incertezza del belief state. In questo modo, il **contingent planning** consente la generazione di piani robusti che mantengono validità anche di fronte a percezioni parziali e risultati d’azione non deterministici, garantendo un comportamento coerente e razionale dell’agente in ambienti incerti.

