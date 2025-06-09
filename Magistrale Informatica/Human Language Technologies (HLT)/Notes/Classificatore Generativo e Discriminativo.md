---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Classificatore Generativo e Discriminativo
---

Un classificatore generativo, come il [[Naive Bayes Classifier]], cerca di modellare come si presentano i dati all’interno di ciascuna classe. 
In altre parole, tenta di ricostruire la distribuzione delle caratteristiche osservate sapendo a quale classe appartiene l’osservazione. 
Questo tipo di modello lavora stimando separatamente la probabilità dei dati dati la classe $P(x|y)$ e la probabilità della classe stessa $P(y)$, per poi combinare queste informazioni usando la regola di Bayes.

Al contrario, un classificatore discriminativo, come la [[regressione logistica]], si concentra esclusivamente sul confine tra le classi, ovvero su come **distinguere** un’etichetta da un’altra in base alle caratteristiche dell’input. 
In termini probabilistici, stima direttamente $P(y|x)$, senza preoccuparsi di come vengono generati i dati. La probabilità si dice essere calcolata a *posteriori*.
Questo approccio consente spesso una maggiore flessibilità e migliori prestazioni quando l'obiettivo è la classificazione pura. 
$$\hat{c}=argmax _{c \in  C} P(c \mid d)$$

Questa distinzione tra generativo e discriminativo è fondamentale per comprendere non solo il funzionamento interno dei modelli, ma anche i loro punti di forza in base al contesto applicativo.