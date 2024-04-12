---
Subject: Interazione uomo macchina
topic: nota
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# Le azioni degli utenti
---
i 7 stati delle azioni fatte dal utente è un modello semplificato per modellizzare come l utente interagirà con il sistema che stiamo costruendo.
queste azioni sono raggruppate in due _Gulf_
![[Pasted image 20230608150646.png]]
- _Gulf of execution_: dove gli utenti cercano di capire cosa fare (_FeedForward_)
- _Gulf of Evaluation_: dove gli utenti cercano di capire cosa è successo (_FeedBack_)

il ruolo del design è quello di aiutare l utente a passare per questi due _gulf_ senza problemi. Questo tramite i [[Principi di progettazione del interazione|principi del design]] nello specifico si usano per
-  _Gulf of execution_: signifiers, constraints, mappings, e conceptual model.
- _Gulf of Evaluation_: Feedback and conceptual model


la prima azione è la _specifica del goal_ e i due _gulf_ sono divisi in ulteriori 3 azioni ciascuno
![[Pasted image 20230608150510.png]]
1. Goal (form the goal)
2. Plan (the action)
3. Specify (an action sequence)
4. Perform (the action sequence)
5. Perceive (the state of the world)
6. Interpret (the perception)
7. Compare (the outcome with the goal)

questo è un modello _molto semplificato_, gli obiettivi possono cambiare durante l azione e non sempre tutte le fasi vengono attraversate. ad esempio l utente esperto non necessariamente passera per tutte le fasi mentre è più probabile che uno novizio lo faccia.
infatti questo modello è usato come _linee guide_ per la [[Principi di progettazione del interazione|progettazione del interazione]].

queste domande ci guidano facendoci fare una domanda per ogni ogni passo
![[Pasted image 20230608155823.png]]


### Opportunistic Actions
le azioni opportunistiche sono azioni che non seguono una _pianificazione o un obiettivo preciso_, sono azioni a basto costo mentale e posso essere facilmente sfruttate per indurre l utente a fare certe azioni. 
- ad esempio le adv su internet sfruttano questo tipo di azioni.
in generale sono fugaci e chi li sfrutta deve essere veloce a rendere l utente "pagante" non deve quindi distrarlo con altro.
es di elementi distraenti. chiedere la registrazione al sito, immettere dati  


### Pensiero conscio e inconscio
in generale le azioni e i pensieri delle persone si basano su due diverse modalità _consce_ e _subconscie_ 

nella modalità _subconscia_ si lavora per pattern matching. è veloce ed efficiente dal punto di vista energetico, questa si base sulle esperienze passate. queste azioni sono automatiche 
la modalità _conscia_ lavora invece con il ragionamento attivo è lenta e costosa. queste azioni sono controllate attivamente
![[Pasted image 20230608165251.png]]

### Memoria dichiarativa e Procedurale
Ci sono due tipi di memoria, tutte le azioni richiedono un qualche tipo di memoria ma questa puo essere di diverso tipo.
- _Memoria dichiarativa_: lavora per le associazioni e serve a recuperare informazioni fattuali
* _Memoria Procedurale_: lavora per passi e serve a recuperare la sequenza di passi da fare per ottenere un effetto
solitamente la _Memoria Procedurale_ è molto più facile da allenare e quindi per far provare meno frustrazioni possibile al utente si cerca di lavorare sfruttando la _memoria procedurale_ 



### Divisione delle azioni per livelli
le varie fasi delle azioni sono divise per livelli 
ogni livello si distingue per il grado di automatismo nel cervello e per difficolta nel cambiamento
![[Pasted image 20230608180043.png]]
1. _Livello viscerale_: è il livello più _inconscio_ e più automatico ciò che le persone non devono pensare di fare ma semplicemente fanno. questo livello guida tutto ciò che è immediato
	- es.  percepire informazioni visive e giudizi immediati (bello, attrattivo, brutto, respingente)
2.  _livello comportamentale (Behavioral)_: è un livello intermedio dove risiedono tutte la abilita apprese che preformiamo senza pensarci attivamente, si è consci di ciò che si sta facendo ma non dei dettagli di come lo si stia facendo
	- es. muovere il mouse, andare in bicicletta, parlare
3. _livello riflessivo (reflective)_: è il livello più conscio, dove siamo completamente a conoscenza di cosa stiamo facendo e come lo stiamo facendo. E' a questo livello che avvengono tutti i pensieri attivi e perciò è uno livello _lento_ dove si sviluppa una comprensione precisa di ciò che sta succedendo e ci permette di valutare la situazione e prendere decisioni. Da questo livello vengono anche stati emozionali come il _senso di colpa_ e _orgoglio_ per le proprie azioni, questo siccome è in questo livello che si fa l associazione di causa effetto tra quello che facciamo e ciò che otteniamo. 
	- Per il designer questo livello è il più importante siccome è da dove vengono le emozioni e do dove si impianta la memoria a lungo termine date da quelle stesse emozioni. Spesso sono più importanti queste memorie che la realtà stessa dal punto di vista del utilizzo di un prodotto

