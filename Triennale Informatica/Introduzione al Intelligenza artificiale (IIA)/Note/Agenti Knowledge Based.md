---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---
# Agenti Knowledge Based
---
una **[[Agenti Razionali|agente]] basato sulla conoscenza** mantiene una **_[[Sistemi di inferenza logica|knowledge base]]_** o **_KB_**: un insieme di __enunciati__ (**sentence**) espressi con un dato **[[Linguaggi formali|linguaggio]]**, Ogni enunciato è un asserzione su modo in cui è situato l'agente e possono essere dati per assunti ed essere vere a prescinde, e questi sono detti **Assiomi** oppure derivato da altre conoscenze, quindi inferiti.


l'**agente** interagisce con la **KB** mediante una interfaccia funzionale tell-ask
- **_TELL_**: per aggiungere nuovi enunciati da **KB**
- **_ASK_**: per interrogare la knowledge, ottenere conoscenze pregresse

mentre le interfacce tra i sensori, gli attuatori sono incapsulate in tre funzioni principali: 
- **MAKE-PERCEPT-SENTENCE**: genera un enunciato relativa al percetto rilevato in un dato istante;
- **MAKE-ACTION-QUERY**: formula un enunciato interrogativa sull'azione da intraprendere; 
- **MAKE-ACTION-SENTENCE**: costruisce un enunciato dichiarativa sull'azione effettivamente eseguita.
  
l'agente in astratto si comporta seguendo questo algoritmo:
```pseudo
\begin{algorithm}
\caption{KB-AGENT}
\begin{algorithmic}
\Function{KB-AGENT}{percept}
\State persistent: $KB$, a knowledge base
\State persistent: $t$, a counter, initially 0, indicating time

\State \call{TELL}{$KB$, \call{MAKE-PERCEPT-SENTENCE}{percept, $t$}}
\State $action \gets$ \call{ASK}{$KB$, \call{MAKE-ACTION-QUERY}{$t$}}
\State \call{TELL}{$KB$, \call{MAKE-ACTION-SENTENCE}{action, $t$}}
\State $t \gets t + 1$
\Return $action$
\EndFunction
\end{algorithmic}
\end{algorithm}
```

Il **comportamento** dell'agente si può descrivere al livello della conoscenza (**knowledge level**), dove è sufficiente specificare le informazioni di cui dispone e gli obiettivi.

La costruzione di un agente basato sulla conoscenza può seguire un 
- **approccio dichiarativo**: dove l'agente viene progressivamente istruito attraverso TELL, trasmettendogli le informazioni necessarie per operare nell'ambiente.
- **approccio procedurale**: in cui i comportamenti desiderati sono codificati direttamente nel programma.
In letteratura, si riconosce oggi che un agente efficace combina elementi sia **dichiarativi** sia **procedurali**, con la possibilità di trasformare conoscenze dichiarative in codice procedurale più efficiente.

Inoltre, un agente può essere dotato di meccanismi di apprendimento che gli permettono di generare autonomamente conoscenze generali a partire da una serie di _percetti_, evolvendo così verso una maggiore autonomia operativa


### Grounding della base di conoscenza
la **base di conoscenza** rappresentata internamente è solo una collezione di simboli e non hanno necessariamente un collegamento con la realtà, quindi sta al designer fare in modo che ogni simbolo rispecchi un qualche elementi delle realtà, questo è detto  **grounding**. 
La coerenza tra le frasi memorizzate nella **base di conoscenza** e il mondo reale dipende dall'affidabilità delle **percezioni sensoriali**. I sensori dell'agente acquisiscono dati dall'ambiente, convertendoli in enunciati che, una volta inserite nella, sono considerate vere rispetto al mondo reale.
![[IMG - rappresentazione sentence e mondo reale.png]]









