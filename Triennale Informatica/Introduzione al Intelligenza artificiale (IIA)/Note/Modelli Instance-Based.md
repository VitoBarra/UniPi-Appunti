---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Modelli Instance-Based
---
I __[[Modelli di dati|modello]] instance-based__ di [[Machine Learning (ML)|machine learning]] sono generati da un [[Algoritmi di Machine Learning|algoritmi di learning]] e sono una sottoclasse dei  __[[Modelli di machine learning NON parametrici|modelli NON parametrici]]__.  Questi modelli memorizzano tutte le istanze dei dati e calcolano le predizioni basandosi sulla __somiglianza__ tra l'istanza da predire e quelle presenti nel dataset.

Come i modelli __[[Modelli di machine learning NON parametrici|non parametrici]]__ i modelli __instance-base__ non sono un __ipotesi esplicita e analitica__, ma mentre i modelli __non parametrici__  possono generare una struttura per le predizioni, i modelli __instance-based__ si basano direttamente sul confrontare i dati da predire con sulle istanze dei dati già visti in training 

gli [[Algoritmi di Machine Learning|algoritmi di learning ]] che generano dei __modelli instance-based__ sono detti anche "__lazy__" siccome non c è costruzione di ipotesi durate il training ed è tutto rimandato alla fare si inferenza

__Vantaggi__:  
- __Flessibilità__: Grazie all'uso diretto dei dati, questi modelli sono particolarmente efficaci nel trattare relazioni complesse e non lineari.  
- __Adattabilità__: Aggiungere nuovi dati al sistema è semplice e non richiede la ricostruzione di un modello.  

__Svantaggi__:  
- __Requisiti di memoria elevati__: La necessità di conservare tutto il dataset può diventare proibitiva per dataset molto grandi.  
- __Scalabilità limitata__: Fare predizioni può risultare lento, poiché richiede il confronto con tutte le istanze memorizzate.  

Tra gli esempi più comuni di modelli instance-based troviamo:  
- __[[K-Nearest Neighbor (K-NN)|k-Nearest Neighbors]]__  
- __Kernel regression__  



