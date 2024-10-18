---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - IA
Area: "[[Machine Learning]]"
topic: 
SubTopic:
---
# Algoritmi di Apprendimento automatico
---
gli __algoritmi di learning__ sono degli algoritmi che permetto ad una macchina di estrarre dei dati della conoscenza, ovvero riescono ad imparare qualcosa basandosi sui dati a cui l algoritmo ha accesso. 

- _Learning_  [[AI - Algoritmi di ricerca informati|ricerca con euristiche]] nello spazio delle ipotesi $H$ della _migliore Ipotesi_ 
	- si cerca la migliore approssimazione per la funzione _sconosciuta_ 
	- Tipicamente impostata come la ricerca con il _minimo errore_
	- la _Miglir ipotesi_   si misura con l _Errore di generalizazione_ che misura quanto accurato il modello predice su dati _nuovi_  
- TIpicamente $H$ non coincide con l insieme di tutte le possibili funzioni, e la ricerca non puo essere esaustiva (sarebbe infinita): sono necessarie della assunzioni per ridurre lo spazio di ricerca, ti utlizza il _[[ML - Bias Induttivo|bias induttivo]]_
- ![[43BCF722-8E18-4052-B640-35712D4198B7.jpeg]]


gli [[Algoritmi di Apprendimento automatico|algoritmi di learning]] possono essere divisi in varie categorie come 
1. [[Apprendimento supervisionato]]
2. [[Apprendimento NON supervisionato]]
3. [[Reinforcement Learning]]



### Generalizzazione 
la generalizzazione è il concetto principale del machine learning e si riferisce alla capacita di predire con basso errore i nuovi dati rispetto a quelli del _training set_
- __Fase di aprendimento__ (training o fitting):  costruzione del modello dai dati conosciuti
- _fase si predizione_ (o stima): si danno nuovi dati al modello, si compara il risultato del modello con il risultato target 
questo ci da informazioni sul ipotesi predittiva e quindi sulle _capacita di generalizzare_

la performance del ML è definita come = _accuratezza predittiva_
