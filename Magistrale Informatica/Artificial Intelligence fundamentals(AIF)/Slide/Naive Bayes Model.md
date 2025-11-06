---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Naive Bayes Model
---
Il **Naive Bayes Model** rappresenta una **struttura probabilistica** basata sul [[Formula di Bayes|teorema di bayes]] in cui una singola **causa influisce** direttamente su un **insieme di effetti**, i quali risultano tra loro **[[Indipendenza condizionata|condizionatamente indipendenti]]** se la **causa** è data. In tale configurazione, la [[Distribuzione di probabilita congiunta totale|distribuzione congiunta]] tra la **causa** e gli **effetti** può essere espressa nella forma:$$
P(Cause, Effect_1, \ldots, Effect_n) = P(Cause) \prod_i P(Effect_i \mid Cause)
$$Questo tipo di distribuzione viene definito **_naive_** poiché si basa sull’assunzione che le variabili effetto siano [[Indipendenza condizionata|condizionalemente indipendenti]], ipotesi che nella pratica è spesso falsa. Nonostante questo nella pratica funziona bene

per usare il modello si usa la regola di [[Inferenza con Full Joint distribution|inferenza per la full joint distribution]] per inferire la probabilità della **causa** a partire da un insieme di effetti osservati $E = e$, ovvero:$$
\mathbf{P}(Cause \mid e) = \alpha\mathbf{P}(Cause \mid e)=\alpha \sum_y P(Cause, e, y)
$$dove $\alpha$ è una costante di normalizzazione e $y$ rappresenta le variabili effetto non osservate. Sostituendo la **[[Distribuzione di probabilita congiunta totale|distribuzione congiunta]]** con il **modello di bayes**, si ottiene:$$
\begin{array}{}
\mathbf{P}(Cause \mid e)  &  = &\displaystyle  \alpha \sum_y \mathbf{P}(Cause,y) \left( \prod_j \mathbf{P}(e_j \mid Cause) \right) \\ \\
 & = &\displaystyle  \alpha \sum_y \mathbf{P}(Cause)\mathbf{P}(y \mid Cause) \left( \prod_j \mathbf{P}(e_j \mid Cause) \right) \\ 
 & = & \displaystyle \alpha  \mathbf{P}(Cause) \left( \prod_j \mathbf{P}(e_j \mid Cause) \right) \sum_y\mathbf{P}(y \mid Cause)

\end{array}
$$Poiché $\sum_y\mathbf{P}(y \mid Cause)=1$, la relazione si semplifica in:$$
P(Cause \mid e) = \alpha P(Cause) \prod_j P(e_j \mid Cause)
$$Questa formulazione mostra che, per ciascuna possibile causa, è sufficiente moltiplicare la probabilità a priori della causa per il prodotto delle probabilità condizionate degli effetti osservati dati la causa, per poi normalizzare il risultato.  
Il calcolo risultante è lineare rispetto al numero di effetti osservati e indipendente dal numero di effetti non osservati.
