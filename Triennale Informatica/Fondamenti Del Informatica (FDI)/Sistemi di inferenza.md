---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - FDI
  - AIF
  - IA
Area: 
topic: nota
SubTopic: 
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
---
# Sistemi di inferenza
---
Nel contesto della [[Logica|logica]] un **sistema di inferenza** o **di deduzione** è una classe di [[Algoritmi|algoritmi]] per generare **nuova conoscenza** da un **insieme di conoscenze** (**knowledge base**) indicato con $KB$. Per fare ciò si combinano le conoscenze pregresse con delle regole solitamente definite tramite [[Linguaggi formali|Linguaggi formali]].

indicando con $i$  un generico **sistema di inferenza** allora si denota il fatto che l'**enunciato** $\alpha$ è **derivabile** (**deducibile**) da $KB$ con $$KB \vdash_i \alpha$$ letto $\alpha$ è derivabile da $KB$ tramite $i$

Un **sistema di inferenza** ha due proprietà fondamentali:
**_Correttezza_** (**soundness**): tutti gli enunciati $\alpha$ derivabili sono **conseguenza logica** di $KB$ ovvero le regole **preservano la verità**. vale quindi che $KB \vdash_i \alpha\implies KB \models_i \alpha$

**_Completezza_** (**Completness**): tutto ciò che è [[Logica#Deduzione (o conseguenza logica)|conseguenza logica]] è ottenibile tramite in **sistema inferenziale** ovvero vale  che  $KB \models \alpha \implies KB \vdash_i \alpha$




#### Model cheeking
Una procedura esemplificativa di inferenza è il model checking, che si basa sull'enumerazione di tutti i modelli possibili. Attraverso questa tecnica si verifica che, in ciascun modello in cui le frasi della $KB$ risultano vere, lo sia anche la proposizione $\alpha$, confermando così che $M(KB) \subseteq M(\alpha)$.


#### Teorema di refutazione 
$$KB \models \alpha \iff (KB \land \lnot \alpha) \text{ è insodisfacibbile}$$  
 questo ci dice quindi che la conseguenza logica si può riportare ad un problema [[Problemi della Sodisfacibilita (SAT)|SAT]]




