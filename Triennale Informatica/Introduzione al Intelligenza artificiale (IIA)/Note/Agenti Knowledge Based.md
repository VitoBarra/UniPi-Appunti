---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IA
  - AIF
---
# Agenti Knowledge Based
---
una **[[Agenti Razionali|agente]] basato sulla conoscenza** mantiene una _[[Sistemi di inferenza|knowledge base]]_ ** o **_KB_**: un insieme di __enunciati__ (**sentence**) espressi con un dato **[[Linguaggi formali|linguaggio]]**, Ogni enunciato è un asserzione su modo in cui è situato l'agente e possono essere dati per assunti ed essere vere a prescinde, e questi sono detti **Assiomi** oppure derivato da altre conoscenze, quindi inferiti.


l'**agente** interagisce con la **KB** mediante una interfaccia funzionale tell-ask
- **_TELL_**: per aggiungere nuovi enunciati da **KB**
- **_ASK_**: per interrogare la knowledge, ottenere conoscenze pregresse
- **_REACT_**: per eliminare enunciati ???
  
  
  
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


### Formalismi per la rappresentazione della conoscenza
una formalismo per la rappresentazione della conoscenza ha tre componenti:
1. _sintassi_: un linguaggio composto d un vocabolario e regole per la formazione delle frasi (_enunciati_)
2. _semantica_: stabilisce una corrispondenza tra gli enunciati e i fatti del mondo; se una agente ha un enunciato $\alpha$ nella sua KB crede che il fatto corrispondente sia vero nel mondo
3.  _[[Logica|meccanismo inferenziale]]_: codificato tramite delle regole che ci consente di inferire nuovi fatti dai fatti presenti nella KB
 
il problema _fondamentale_ in R.C. è trovare il giusto compromesso tra:
- _Espressivita_ del linguaggio di rapresentazione
- _Complessita_ del meccanismo inferenziale
queste due caratteristiche sono in contrasto tra loro siccome un linguaggio piu _espressivo_ rende meno efficente il meccanismo inferenziale 





L'interazione tra la conoscenza rappresentata internamente e la realtà esterna è regolata dal concetto di grounding. La coerenza tra le frasi memorizzate nella base di conoscenza e il mondo reale dipende dall'affidabilità delle percezioni sensoriali. I sensori dell'agente acquisiscono dati dall'ambiente, convertendoli in proposizioni che, una volta inserite nella $KB$, sono considerate vere rispetto al mondo reale. Tuttavia, una parte consistente delle affermazioni deriva da processi di apprendimento, che possono essere imperfetti o soggetti a errori. Nonostante ciò, adottando procedure di apprendimento adeguate, è possibile mantenere un elevato grado di affidabilità e coerenza tra la conoscenza interna e la realtà osservabile, rafforzando la capacità deduttiva del sistema e la sua efficienza nel rappresentare il mondo attraverso un linguaggio rigoroso e strutturato.

![[IMG - rappresentazione sentence e mondo reale.png]]








L'agente basato sulla conoscenza opera ricevendo un percetto (percept) in ingresso e restituendo un'azione come uscita. La struttura interna prevede che la KB contenga, fin dall'inizio, un insieme di conoscenze di base, dette conoscenze pregresse o background knowledge. A ogni ciclo operativo, l'agente svolge tre funzioni: comunica alla KB ciò che ha percepito attraverso TELL; interroga la KB per determinare l'azione opportuna tramite ASK; infine, informa la KB sull'azione selezionata, sempre tramite TELL, e la esegue.

Le interfacce tra i sensori, gli attuatori e il nucleo logico dell'agente sono incapsulate in tre funzioni principali: **MAKE-PERCEPT-SENTENCE**, che genera una sentenza relativa al percetto rilevato in un dato istante; **MAKE-ACTION-QUERY**, che formula una sentenza interrogativa sull'azione da intraprendere; e **MAKE-ACTION-SENTENCE**, che costruisce una sentenza dichiarativa sull'azione effettivamente eseguita.

Il funzionamento dell'agente si può descrivere al livello della conoscenza (knowledge level), dove è sufficiente specificare le informazioni di cui dispone e gli obiettivi perseguiti per dedurre il comportamento. Si sottolinea che tale analisi è indipendente dal livello implementativo (implementation level), ovvero dalla modalità concreta con cui le conoscenze sono codificate o i processi inferenziali sono realizzati, siano essi basati su strutture dati come liste collegate, mappe di pixel o reti neurali.

La costruzione di un agente basato sulla conoscenza può seguire un approccio dichiarativo, dove l'agente viene progressivamente istruito attraverso TELL, trasmettendogli le informazioni necessarie per operare nell'ambiente. Tale approccio si contrappone a quello procedurale, in cui i comportamenti desiderati sono codificati direttamente nel programma. In letteratura, si riconosce oggi che un agente efficace combina elementi sia dichiarativi sia procedurali, con la possibilità di trasformare conoscenze dichiarative in codice procedurale più efficiente.

Inoltre, un agente può essere dotato di meccanismi di apprendimento che gli permettono di generare autonomamente conoscenze generali a partire da una serie di percetti, evolvendo così verso una maggiore autonomia operativa.
