---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Nested k-fold cross validation (Double cross validation)
---

Viene fatto un ciclo di k-fold esterno dove si ottiene una parte per il test, che non si tocca ed una per il design.
Si hanno quindi k design set e su ognuno di questo viene effettuata un ulteriore k-fold per il training set e per il validation set.

Questo metodo fornisce numerosi modelli e numerose stime, utilizza i dati in modo efficiente ma è molto costoso dal punto di vista computazionale.

![[nested k-fold.png]]
