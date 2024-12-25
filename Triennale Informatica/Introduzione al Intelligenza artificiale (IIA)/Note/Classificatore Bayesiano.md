---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Classificatore Bayesiano
---
Un __classificatore bayessiano__ utilizza la [[probabilita condizionata|probabilita condizionata]] per decidere quale classe assegnare ad un dato input mai visto. Formalmente si ha che

__Sia__
- __$\mathcal{P}(x, y)$__ la [[Distribuzione di probabilita|densità di probabilita]] delle coppie input output 
- $\{C_1, C_2, C_3, \dots, C_k\}$ le classi possibili
 __Allora__ un __classificatore bayessiano__ da in output la classe tale che $$\arg\max_v \mathcal{P}(v \mid \mathbf{x}) \ \ \ v \in  \{C_1, C_2, C_3, \dots, C_k\} $$
Questo classificatore è ottimale è  non c è modi di fare meglio sulla distribuzione di dati $\mathcal{P}(x, y)$
il __Bayes rate__ è Il tasso di errore di questo classificatore e rappresenta il tasso di __errore minimo__ che può essere raggiunto dato la distribuzione dei dati. ovvero è il miglior risultato possibile teorico che possiamo ottenere nel classificare i dati di quella distribuzione.