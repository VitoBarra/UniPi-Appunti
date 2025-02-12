---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Reservoir Computing - Echo State Machine
---
Un'alternativa interessante alle RNN classiche è il modello **Echo State Network (ESN)**, che sfrutta un **reservoir di neuroni con pesi fissi** e allena solo lo strato di output. Questo approccio riduce significativamente il costo computazionale dell'addestramento.

L'aggiornamento dello stato interno segue la dinamica:

$$
x(t) = \tanh(W_{\text{in}} l(t) + W x(t-1))
$$

dove $ W_{\text{in}} $ è la matrice dei pesi dell'input e $ W $ è la matrice dei pesi del reservoir.

L'output è calcolato tramite una semplice combinazione lineare:

$$
y(t) = W_{\text{out}} x(t)
$$

L'addestramento si riduce alla stima dei pesi $ W_{\text{out}} $, tipicamente con **regressione ridge**.

![[Pasted image 20250208003444.png]]


![[Pasted image 20250208003541.png]]