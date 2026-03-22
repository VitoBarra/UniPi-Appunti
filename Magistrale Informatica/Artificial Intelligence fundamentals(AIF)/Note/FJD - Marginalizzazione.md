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
La **marginalizzazione** o **summing out** permette di ottenere la [[Distribuzione di probabilita|distribuzione di probabilita]] di una variabile, o di un sottoinsieme di variabili, a partire dalla **[[Full Joint Distribution (FJD)|full joint distribution]]**. L'idea intuitiva e che si sommano via tutte le variabili che non interessano, cioe tutte le loro possibili configurazioni.

Formalmente, sia:
- $Y=X_i$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] di cui si vuole conoscere la [[Distribuzione di probabilita|distribuzione di probabilita]]
- $Z=\{X_1,\dots,X_{i-1},X_{i+1},\dots,X_n\}$ l'insieme di tutte le altre variabili aleatorie

allora la marginalizzazione e $$\mathcal{P}(Y)=\sum_z \mathcal{P}(Y,Z=z)$$ dove la sommatoria $\sum_z$ e estesa a tutte le combinazioni dei valori del set di variabili $Z$.

In altre parole, per ottenere la distribuzione di $Y$ dalla [[Full Joint Distribution (FJD)|distribuzione congiunta]], si somma su tutto cio che non si vuole mantenere esplicito.

Piu in generale, se si ha una distribuzione congiunta su piu variabili, per esempio $\mathcal{P}(X,Y,Z)$, allora si possono ottenere anche delle **sotto-marginali**: $$\mathcal{P}(X,Y)=\sum_z \mathcal{P}(X,Y,Z=z)$$ quindi si marginalizza sempre rispetto alle variabili che non interessano.

Nel caso di variabili continue, la somma viene sostituita da un integrale: $$p(y)=\int p(y,z)\,dz$$

Una forma equivalente particolarmente utile si ottiene combinando marginalizzazione e [[Probabilita condizionata|regola del prodotto]]. Per ogni valore $z$ di $Z$ si ha $$\mathcal{P}(Y,Z=z)=\mathcal{P}(Y\mid Z=z)\mathcal{P}(Z=z)$$ e quindi $$\mathcal{P}(Y)=\sum_z \mathcal{P}(Y\mid Z=z)\mathcal{P}(Z=z)$$Questa formula mostra che la marginalizzazione puo essere vista anche come una **media pesata** delle distribuzioni [[Probabilita condizionata|condizionate]] di $Y$, pesate secondo quanto sono probabili i diversi valori di $Z$.
