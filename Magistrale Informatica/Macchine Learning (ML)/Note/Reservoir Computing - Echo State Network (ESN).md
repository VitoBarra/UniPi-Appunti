---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Reservoir Computing - Echo State Machine (ESN)
---
il modello **Echo State Network (ESN)** è un modello del [[RandRNN - Reservoir Computing|Reservoir Computing]] quindi è una [[Recurrent Neural Network (RNN)|RNN]] ma [[Random Neural Network (RandNN)|RandNN]].
una __ESN__ che sfrutta un __reservoir di neuroni con pesi fissi__ e allena solo lo strato di output. Questo approccio riduce significativamente il costo computazionale dell'addestramento.

L'aggiornamento dello stato interno segue la dinamica:$$
x(t) = \tanh(W_{\text{in}} l(t) + W x(t-1))
$$dove $W_{\text{in}}$ è la matrice dei pesi dell'input e $W$ è la matrice dei pesi del reservoir.

L'output è calcolato tramite una semplice combinazione lineare:$$
y(t) = W_{\text{out}} x(t)
$$L'addestramento si riduce alla stima dei pesi $W_{\text{out}}$, tipicamente con **regressione ridge**.

![[Pasted image 20250208003444.png]]




Regole per scegliere un buon reservoir operando sul [[Raggio spettrale|raggio spettrale]]  $\rho(\boldsymbol{W})$  dei pesi abbiamo che 
- $\rho$ vicino ad 1 per task che richiedono molta memoria
- $\rho$ non troppo vicino se il task richiede poca memoria

NRMSE:
$$E(\boldsymbol{y},\boldsymbol{y}_{target})=\sqrt{\frac{ \langle\|y(n)-\boldsymbol{y}_{target}(n)\|^{2}\rangle }{ \langle\|y_{target}(n)-\langle\boldsymbol{y}_{target}(n)\rangle\|^{2}\rangle}}$$
dove $\|\cdot\|$ e' la [[Norme Matriciali e Norme Vettoriali#Norma vettoriale|norma euclidea]]


![[Pasted image 20250208003541.png]]