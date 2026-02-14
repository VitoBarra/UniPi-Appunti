---
Course: "[[Teoria del informazione (TDI)]]"
tags:
  - TDI
Area:
topic:
SubTopic:
---

# Mutual Information (MI)
---
la **mutual information (MI)** quantifica quanta informazione la [[Variabili Aleatorie (Casuali)|variabile casuale]] $X$ fornisce sulla [[Variabili Aleatorie (Casuali)|variabile]] $Y$. Formalmente:$$I(X;Y)=\sum_{x,y}p(x,y)\log\frac{p(x,y)}{p(x)p(y)}$$dove:
- $p(x,y)$ è la [[Definizione di Probabilita|probabilità]] congiunta delle due variabili
- $p(x)$ e $p(y)$ sono le probabilità marginali

La **mutual information** può essere definita in modo equivalente tramite l’[[Entropia|entropia]] $H$, che misura l’incertezza associata a una [[Variabili Aleatorie (Casuali)|variabile casuale]]:$$I(X;Y)=H(X)+H(Y)-H(X,Y)$$oppure in forma condizionata:$$I(X;Y)=H(X)-H(X|Y)$$Questa formulazione mostra che la mutual information misura **quanto la conoscenza di $Y$ riduce l’incertezza su $X$**.

Proprietà principali della mutual information:
- $I(X;Y)\ge 0$
- $I(X;Y)=0$ se e solo se $X$ e $Y$ sono indipendenti ($p(x,y)=p(x)p(y)$)
- è **simmetrica**: $I(X;Y)=I(Y;X)$
- permette di rilevare **relazioni non lineari** tra variabili
Nella pratica la stima di $I(X;Y)$ richiede di stimare la distribuzione congiunta $p(x,y)$ a partire dai dati sperimentali
