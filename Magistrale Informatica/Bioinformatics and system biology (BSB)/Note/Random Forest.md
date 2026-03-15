---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: 
topic: 
SubTopic:
---
# Random Forest
---
[[Random Forest|Random Forest]] è un algoritmo di [[Ensemble Learning|ensemble learning]] che combina molti [[Alberi di decisione|decision tree]] per ottenere un modello predittivo più stabile e con minore varianza rispetto a un singolo albero. L’idea è costruire diversi modelli debolmente correlati e aggregarne le predizioni.

Dato un dataset $D=\{(x_i,y_i)\}_{i=1}^{N}$ con $x_i\in\mathbb{R}^d$ vettore delle feature e $y_i$ variabile target, una [[Random Forest|Random Forest]] costruisce un insieme di $T$ alberi $\{h_t(x)\}_{t=1}^{T}$.

Costruzione della foresta:
- per ogni albero viene generato un dataset tramite [[Bagging (bootsrap aggregating)|bootstrap sampling]] estraendo $N$ campioni con reinserimento dal dataset originale
- ad ogni nodo dell’albero viene selezionato casualmente un sottoinsieme di feature
- lo split viene scelto tra queste feature massimizzando la riduzione dell’impurità

La casualizzazione avviene quindi su due livelli:
- campionamento dei dati
- campionamento delle feature

Questa strategia riduce la correlazione tra i [[Alberi di decisione|decision tree]] e rende efficace l’aggregazione delle predizioni.

Predizione del modello.

Caso di [[Classificazione|classificazione]]:
- ogni albero produce una classe $\hat y_t$
- la predizione finale è il voto di maggioranza  
$\hat y=\text{mode}\{h_t(x)\}_{t=1}^{T}$

Caso di [[Regressione|regressione]]:
- ogni albero produce una predizione $\hat y_t$
- la predizione finale è la media delle predizioni  
$\hat y=\frac{1}{T}\sum_{t=1}^{T} h_t(x)$

Criteri di split nei [[Decision Tree|decision tree]]:
- classificazione: [[Indice di Gini|indice di Gini]] oppure [[Entropia (teoria dell'informazione)|entropia]]
- regressione: riduzione della varianza o [[Mean Squared Error|MSE]]

Valutazione interna del modello.

Durante il [[Bootstrap sampling|bootstrap sampling]] circa $1/3$ dei campioni non viene utilizzato per costruire un albero. Questi campioni costituiscono il **[[Out-of-bag error|out-of-bag error]] set** e permettono di stimare l’errore di generalizzazione senza separare un dataset di validazione.

Importanza delle variabili.

Le [[Random Forest|Random Forest]] permettono di stimare l’importanza delle feature tramite la riduzione media dell’impurità prodotta dagli split associati ad una variabile:
$$importance(X_j)=\sum_{t=1}^{T}\sum_{n\in splits(X_j)} \Delta impurity(n)$$

dove $\Delta impurity(n)$ rappresenta la riduzione della misura di impurità nel nodo $n$.

Proprietà principali:
- riduzione della varianza rispetto a un singolo [[Alberi di decisione|decision tree]]
- buona capacità di modellare relazioni non lineari
- robustezza al rumore e all’overfitting
- addestramento facilmente parallelizzabile

Costo computazionale approssimato dell’addestramento:
$$O(T \times N\log N \times m)$$

dove:
- $T$ numero di alberi
- $N$ numero di campioni
- $m$ numero di feature considerate ad ogni split
