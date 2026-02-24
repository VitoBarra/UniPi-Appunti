---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# FJD - Marginalizzazione
---
la **marginalizzazione** o **summing out** permette di ottenere la [[Distribuzione di probabilita|distribuzione di probabilità]] di una singola variabile sommando le probabilità su tutte le possibili configurazioni delle altre variabili prese dalla **[[Full Joint Distribution (FJD)|full joint distribution]]**, questo è descritto formalmente come
**sia**
- $Y=X_i$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] di cui si vuole sapere la **[[Distribuzione di probabilita|distribuzione di probabilita]]**
- $Z={X_1,\dots,X_{i-1}X_{i+1},\dots, X_n}$  tutte le altre  variabili aleatorie
**allora** la marginalizazione segue come:$$
\mathcal{P}(Y) = \sum_{z} \mathcal{P}(Y, Z = z)
$$dove la sommatoria $\sum_z$ è estesa a tutte le combinazioni dei valori del set di variabili $Z$. Utilizzando la [[Probabilita condizionata|regola del prodotto]], si può riscrivere $P(Y, z) = P(Y \mid z)P(z)$, ottenendo la regola del **conditioning**:  $$
P(Y) = \sum_{z} \mathcal{P}(Y \mid z) \mathcal{P}(z)
$$