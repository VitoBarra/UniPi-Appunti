---
Course: "[[Machine Learning (ML)]]"
Course 2: "[[Human Language Technology (HLT)]]"
tags:
  - IA
  - ML
  - HLT
Area: 
topic: 
SubTopic:
---
# Cross Entropy
---
La **Cross Entropy** è una funzione di **loss** che penalizza di più gli **errori commessi con troppa sicurezza** e viene utilizzata nei compiti di [[Algoritmi di learning supervisionato|classificazione]].

La Cross Entropy binaria è definita come :
$$CE=-\frac{1}n \sum_{i=1}^n[y_i \cdot \log(p_i)+(1-y_i)\cdot \log(1-p_i)]$$
dove:
- $y_i$ è l'etichetta reale
- $p_i$ è la probabilità predetta dal modello ed assume valori tra 0 e 1

Se $y_i=1$ allora solo la prima pare della sommatoria è diversa da 0. Se la previsione è vicina a 1 la loss è bassa altrimenti sarà alta.

Se $y_i=0$ si utilizza invece il secondo termine 

La cross entropy loss può essere riscritta come:
$$L_{CE}(\hat{y},y)=-[y\log \sigma(W\cdot X+b)+(1-y)\log(1-\sigma(W\cdot X+b))]$$

La derivata della CE è definita da:
$$\frac{\partial L_{CE}(\hat{y},y)}{\partial w_i}=[\sigma(W\cdot X+b)-y]x_i$$
