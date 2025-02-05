---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Ensemble Learning
---
l __Ensemble Learning__ migliora le prestazioni combinando più [[Algoritmi di Machine Learning|modelli]] 
![[Pasted image 20250203185316.png]]
per fare ciò sono due strategie principali

###  Bagging
 - Addestra $K$ classificatori su sottoinsiemi bootstrap del dataset.
 - Riduce la varianza mediando $h(x)$.

### Boosting
 - Dà più peso alle istanze mal classificate.
 - Riduce il bias migliorando le prestazioni di classificatori deboli.