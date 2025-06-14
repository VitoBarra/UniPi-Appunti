---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - SATPlan
---
La [[Planning|pianificazione]] come [[Problemi della Sodisfacibilita (SAT)|soddisfacibilità]] booleana si fonda sull’idea di trasformare un problema espresso in linguaggio PDDL in una formula proposizionale, la cui soddisfacibilità corrisponde all’esistenza di un piano valido. Tale trasformazione procede attraverso una serie di passaggi formali che consentono di rendere espliciti i vincoli temporali e causali dell’ambiente.  

In primo luogo, le azioni vengono **proposizionalizzate**: ogni schema d’azione con variabili viene sostituito da istanze completamente determinate, ottenute tramite la sostituzione delle costanti disponibili. Ogni azione è inoltre indicizzata nel tempo, così che $A^t$ rappresenti l’esecuzione di un’azione $A$ al passo temporale $t$.  

Successivamente, si introducono gli **assiomi di esclusione delle azioni**, che garantiscono che due o più azioni incompatibili non possano verificarsi simultaneamente. Formalmente, per ogni coppia di azioni mutuamente esclusive, si impone una formula del tipo $\neg(A^t_i \wedge A^t_j)$, assicurando che in un dato istante temporale solo un insieme coerente di azioni possa essere eseguito.  

Si aggiungono poi gli **assiomi di precondizione**, esprimendo che l’esecuzione di un’azione implica la verità delle condizioni necessarie al suo compimento. La forma generale è $A^t \Rightarrow PRE(A)^t$, dove $PRE(A)^t$ rappresenta la congiunzione dei predicati che devono essere veri affinché l’azione sia eseguibile.  

Lo **stato iniziale** viene specificato enumerando i fluenti veri e falsi al tempo $t=0$. Ogni fluente $F$ appartenente allo stato iniziale è affermato come $F^0$, mentre per i fluenti non menzionati si assume $\neg F^0$.  

Il **goal** viene espresso come una formula proposizionale che sostituisce le variabili con tutte le possibili costanti del dominio. Se l’obiettivo contiene variabili, esso diviene una disgiunzione di istanze completamente determinate, riflettendo tutte le combinazioni ammissibili.  

Infine, vengono introdotti gli **assiomi di stato successivo**, che descrivono l’evoluzione dei fluenti nel tempo. Ogni fluente $F$ è definito da una formula del tipo:

$$
F^{t+1} \Leftrightarrow ActionCausesF \vee (F^t \wedge \neg ActionCausesNotF)
$$

dove $ActionCausesF$ rappresenta la disgiunzione di tutte le azioni che determinano $F$ come vero, mentre $ActionCausesNotF$ rappresenta la disgiunzione delle azioni che lo rendono falso.  

L’intera traduzione produce una formula proposizionale estesa, spesso molto più ampia del problema originale, ma gestibile grazie all’elevata efficienza dei moderni risolutori SAT, capaci di esplorare lo spazio delle possibilità in modo sistematico e ottimizzato.
