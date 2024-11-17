---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic: 
---
# Algoritmi di Machine Learning
---
Gli **algoritmi di learning** definiscono il campo del _[[Concetti generali del Machine Learning|machine learning]]. Questi algoritmi consentono a una macchina di estrarre conoscenza dai dati, ovvero di apprendere informazioni basandosi sui dati a cui hanno accesso.

L'apprendimento (o _learning_) viene definito come la ricerca di un'ipotesi $h$ nello spazio delle ipotesi $\mathcal{H}$. Lo **spazio delle ipotesi** $\mathcal{H}$ rappresenta tutte le possibili ipotesi che possono essere formulate utilizzando l'algoritmo scelto. $\mathcal{H}$ non coincide con l'insieme di tutte le possibili [[Funzioni|funzioni]] ma è limitato grazie a delle assunzioni. Questo si fa perché altrimenti $\mathcal{H}$ coinciderebbe con uno spazio infinito dove fare una ricerca è impraticabile siccome sarebbe anche essa infinita.  
Queste assunzioni prendono il nome di __[[Bias Induttivo|bias induttivo]]__, una caratteristica del algoritmo che guida la scelta dell'ipotesi. Esistono due tipi di __bias induttivo__:
- **Bias di linguaggio**: limita le funzioni che un algoritmo può esprimere, restringendo la forma delle ipotesi possibili.
- **Bias di ricerca**: guida il modo in cui l'algoritmo cerca l'ipotesi all'interno dello spazio $\mathcal{H}$.
la scelta di un __bias induttivo__ è importante anche per una altra ragione senza non si puo imparare nient'altro che una __tabella di verità__. Ovvero Senza un __bias induttivo__ non è esiste __capacità di generalizzare__
![[43BCF722-8E18-4052-B640-35712D4198B7.jpeg]]

gli [[Algoritmi di Machine Learning|algoritmi di learning]] possono essere divisi in varie categorie come 
1. [[Apprendimento supervisionato]]
2. [[Apprendimento NON supervisionato]]
3. [[Reinforcement Learning]]
dove indipendentemente dalla categoria i passi sono solitamente
1. __Fase di apprendimento__ (training o fitting):  ricerca di un ipotesi a partire dai dati conosciuti, insieme dei quali è chiamato __training set__.
2. __Fase si predizione__ (o stima): si utilizza l ipotesi generata dal modello per predire nuovi dati. 

si possono utilizzare i dati predetti per confrontarli con degli altri dati che si assumono corretti, solitamente detto [[Validazione e test di una modello di ML|test set]], e fare ciò ci da informazioni sul ipotesi predittiva e quindi sulle __capacita di generalizzare__. Questa è la capacita di ottenere buone prestazioni su dati non presenti nel training set.