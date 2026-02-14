---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - inferenza - GENIE3
---
**GENIE3 (GEne Network Inference with Ensemble of trees)** è un metodo di **machine learning** per l’[[GRN - inferenza|inferenza]] delle [[Gene Regulatory Networks (GRN)|GRN]] che formula il problema della ricostruzione della rete come una serie di problemi di **regressione supervisionata**.

L’idea centrale è stimare l’espressione di ciascun gene target a partire dall’espressione degli altri geni, interpretando i possibili regolatori come **variabili predittive**.

Dato un insieme di $n$ geni e una **expression matrix**

$$X\in\mathbb{R}^{m\times n}$$

dove:
- $m$ è il numero di esperimenti
- $n$ è il numero di geni
- $x_{ij}$ rappresenta l’espressione del gene $j$ nell’esperimento $i$

l’algoritmo considera ogni gene $g$ come **target gene** e costruisce un modello predittivo:

$$y_g = f(X_{-g})$$

dove:
- $y_g$ è il vettore delle espressioni del gene $g$
- $X_{-g}$ rappresenta l’espressione di tutti gli altri geni

Il modello $f$ viene appreso tramite **Random Forest** o altri ensemble di **decision trees**.

In una Random Forest:
- ogni albero apprende una funzione che predice l’espressione del gene target
- ad ogni nodo dell’albero viene selezionata una variabile predittiva che massimizza la riduzione dell’errore

Durante l’addestramento è possibile stimare l’**importanza delle variabili**, che misura quanto ciascun gene contribuisce alla predizione del gene target.

Se $X_r$ rappresenta l’espressione del gene regolatore candidato $r$, il peso dell’interazione regolatoria viene definito come

$$w_{r,g}\propto importance(X_r \Rightarrow y_g)$$

Questo valore riflette quanto la variabile $X_r$ è rilevante nel predire l’espressione del gene $g$.

Ripetendo il processo per tutti i geni target si ottiene una matrice di pesi

$$W=(w_{ij})$$

dove $w_{ij}$ rappresenta l’importanza del gene $i$ nella predizione del gene $j$.

La matrice $W$ definisce una rete regolatoria pesata in cui:
- i nodi rappresentano geni
- gli archi $i\rightarrow j$ indicano una possibile regolazione
- il peso dell’arco rappresenta la forza dell’influenza stimata

Per ottenere la rete finale è possibile applicare una soglia sui pesi oppure selezionare gli archi con importanza più elevata.

Se è noto l’insieme dei **transcription factors**, l’algoritmo può essere limitato ai soli regolatori candidati

$$TF \rightarrow G$$

riducendo il numero di variabili predittive e migliorando la qualità dell’inferenza.

GENIE3 è stato uno dei metodi con le migliori prestazioni nelle competizioni **DREAM challenge** dedicate all’inferenza delle reti regolatorie geniche, grazie alla capacità degli ensemble di alberi di catturare relazioni non lineari tra geni.