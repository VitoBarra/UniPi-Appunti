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
La **marginalizzazione** o **summing out** permette di ottenere la [[Distribuzione di probabilita|distribuzione di probabilita]] di una variabile, o di un sottoinsieme di variabili, a partire dalla **[[Full Joint Distribution (FJD)|full joint distribution]]**. L'idea intuitiva e che si sommano via tutte le variabili che non interessano, cioè tutte le loro possibili configurazioni.

Formalmente, sia:
- $Y=X_i$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] di cui si vuole conoscere la [[Distribuzione di probabilita|distribuzione di probabilita]]
- $Z=\{X_1,\dots,X_{i-1},X_{i+1},\dots,X_n\}$ l'insieme di tutte le altre variabili aleatorie
**allora** la marginalizzazione è definita come: $$\mathcal{P}(Y)=\sum_z \mathcal{P}(Y,Z=z)$$ dove la sommatoria $\sum_z$ e estesa a tutte le combinazioni dei valori del set di variabili $Z$. In altre parole, per ottenere la distribuzione di $Y$ dalla [[Full Joint Distribution (FJD)|distribuzione congiunta]], si somma su tutto ciò che non si vuole mantenere esplicito. 

La figura rappresenta il passaggio da $p(X,Y)$ alle marginali $p(Y)$ e $p(X)$ mediante somma sulle variabili non osservate, e alla condizionata $p(X\mid Y=1)$ fissando $Y=1$ e rinormalizzando la distribuzione residua.
![[IMG - FJD - Marginalizzazione visualizazoine con binning.png]]
[[Probabilita condizionata|regola del prodotto]]  alla definizione di **marginalizzazione**$$\mathcal{P}(Y)=\sum_z \mathcal{P}(Y\mid Z=z)\mathcal{P}(Z=z)$$Questa formula mostra che la marginalizzazione puo essere vista anche come una **media pesata** delle distribuzioni [[Probabilita condizionata|condizionate]] di $Y$, pesate secondo quanto sono probabili i diversi valori di $Z$.



Nel caso di variabili continue, la definizione è equivalente ma la somma viene sostituita da un integrale: $$p(y)=\int p(y,z)\,dz$$![[IMG - FJD - Marginalizzazione in caso continuo.png]]

