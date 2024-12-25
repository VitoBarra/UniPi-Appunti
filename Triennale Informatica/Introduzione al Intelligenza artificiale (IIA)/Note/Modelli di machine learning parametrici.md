---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Modelli di machine learning parametrici
---
i  __modelli parametrici__ di [[Machine Learning (ML)|macchine learning]] sono generati da un [[Algoritmi di Machine Learning|algoritmi di learning]]. Sono caratterizzati da un numero fisso di __parametri__ che vengono imparati durante la fase di training.

Questo approccio elimina la necessità di mantenere in memoria l'intero dataset durante l'inferenza questo siccome il modello è rappresentato da un ipotesi analitica esplicita. 
gli algoritmi che costruiscono questi tipi di modelli sono detti anche "__eager__".

__Vantaggi__:  
- __Efficienza__: L'uso di un numero limitato di parametri rende questi algoritmi generalmente più rapidi sia durante l'addestramento che nell'inferenza.  
- __Semplicità__: Il modello è spesso più semplice da interpretare e implementare rispetto ad altre metodologie.  

__Svantaggi__:  
- __Rigidità__: Non sempre riescono a catturare relazioni complesse o pattern non lineari nei dati.  
- __Possibile sottoparametrizzazione__: Se il modello è troppo semplice rispetto alla complessità dei dati, le prestazioni potrebbero risentirne.  

Tra gli esempi più comuni di algoritmi parametrici troviamo:  
- __[[Modelli lineari con LMS|Regressione lineare]]__  
- __Regressione logistica__  
- __Modelli lineari generalizzati__  