---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi di sequenze
---
L’**analisi di sequenze** riguarda lo studio formale e computazionale di **sequenze simboliche**, intese come [[Stringhe|stringhe]] definite su un **[[Alfabeto|alfabeto finito]]**. La **struttura sequenziale** è l’unico elemento rilevante: l’ordine dei simboli determina le relazioni e i vincoli che caratterizzano il problema, rendendo applicabili strumenti formali sviluppati per lo studio delle stringhe.

L’analisi di sequenze non si identifica con una singola tecnica, ma comprende una **classe di problemi** accomunati dall’obiettivo di:
- **confrontare** sequenze, ossia valutare se e in che misura due stringhe siano correlate, simili o diverse, secondo criteri formali;
- **analizzare** sequenze, ossia individuare strutture, regolarità, sottosequenze o pattern rilevanti all’interno di una singola stringa o tra più stringhe;
- **interpretare** sequenze, ossia associare un significato computazionale o strutturale ai risultati del confronto o dell’analisi, sulla base di modelli formali predefiniti.

 A seconda del contesto, il confronto può richiedere una corrispondenza esatta tra simboli oppure ammettere discrepanze, consentendo trasformazioni o sostituzioni. La scelta del modello di confronto influisce direttamente sulla natura del problema e sulla complessità della sua risoluzione.

Dal punto di vista algoritmico, i problemi di analisi di sequenze dipendono tipicamente dalla lunghezza $n$ delle stringhe considerate. La valutazione della complessità temporale e spaziale degli algoritmi assume quindi un ruolo centrale, soprattutto quando l’analisi deve essere condotta su insiemi numerosi o su sequenze di grandi dimensioni.

Nel quadro generale degli algoritmi su stringhe, l’analisi di sequenze costituisce il livello concettuale di base da cui derivano approcci più specifici, come il [[Confronto tra sequenze]] e l’[[Allineamento di sequenze]], che ne rappresentano istanziazioni strutturate e specializzate.
