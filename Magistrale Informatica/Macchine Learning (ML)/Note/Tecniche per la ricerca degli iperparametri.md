---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Tecniche per la ricerca degli iperparametri
---
Per fare ricerca dei [[Validation e Test di una modello di ML|migliori iperparametri (model selection)]] si utilizzano delle ricerche strutturate alcuni tra le piu comuni sono:

La __grid search__ è una ricerca esaustiva su tutte le possibili combinazioni dei valori che i vari iperparametri di un modello possono assumere.
I trial sono indipendenti uno dall'altro e si può parallelizzare. 
Il numero di trials aumenta con il numero di iperparametri e dei valori che questi possono assumere.

Si può effettuare una __nested grid search__, ossia utilizzare più livelli di __grid search__. All'inizio si ricerca su intervalli più ampi per poi diminuirli.

La __random search__ riduce i costi computazionali rispetto alla __grid search__ siccome non fa la ricerca esaustiva come la precedente e permette di esplorare anche i valori intermedi tenendo fissi quelli meno influenti.

![[grid search.png]]
A sinistra rappresentazione della __grid search__ e a destra della __random search__.



- [hyper band](https://medium.com/@fmnobar/hyperparameter-optimization-with-hyperband-30x-faster-than-bayesian-optimization-d6f01e7e6d0f)
- [baiesan search](https://en.wikipedia.org/wiki/Bayesian_optimization)



