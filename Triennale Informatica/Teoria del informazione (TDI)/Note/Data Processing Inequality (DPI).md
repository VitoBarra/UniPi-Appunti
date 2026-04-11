---
Course: "[[Teoria del informazione (TDI)]]"
tags:
  - TDI
Area:
topic:
SubTopic:
---

# Data Processing Inequality (DPI)
---
La [[Data Processing Inequality (DPI)|Data Processing Inequality (DPI)]] è una proprietà fondamentale della [[Mutual Information (MI)|mutual information]] che descrive come l'informazione non possa aumentare attraverso operazioni di elaborazione su variabili aleatorie.

Sia $X \to Y \to Z$ una [[Markov chains|catena di Markov]], cioè $Z$ dipende da $X$ solo tramite $Y$. In questa situazione vale la disuguaglianza:
$$I(X;Z) \le I(X;Y)$$

In forma simmetrica la proprietà può essere espressa come:
$$I(X;Z) \le \min\{I(X;Y), I(Y;Z)\}$$

Interpretazione informativa:
- ogni trasformazione o elaborazione dei dati può solo preservare o ridurre l'informazione
- nessun algoritmo può creare nuova informazione su $X$ a partire da $Y$
- l'informazione condivisa tra variabili diminuisce lungo una catena di elaborazioni

Struttura formale della catena:
- $X$ variabile sorgente
- $Y$ rappresentazione intermedia
- $Z$ risultato di un'ulteriore trasformazione
- condizione di Markov: $P(z|x,y)=P(z|y)$

Conseguenze teoriche:
- la mutual information è monotona non crescente lungo una [[Markov chains|catena di Markov]]
- qualsiasi funzione deterministica o stocastica applicata ai dati non aumenta la [[Mutual Information (MI)|mutual information]]