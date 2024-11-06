---
Course: "[[Machine Learning (ML)]]"
Area: "[[Reti Neurali Ricorrenti (RNN)]]"
topic: "[[Intelligenza Artificiale (IA)|Reti neurali]]"
SubTopic: 
tags:
  - IA
  - ML
---
# Reti Neurali Ricorrenti - Reservoir Computing
---


Cose che devo sapere
- [[Reti Neurali (NN)|Reti neurali]]: 
- __[[Reti Neurali Ricorrenti (RNN)|Reti neurali riccorrenti]]__ (RNN) : i neuroni mantengono memoria delle informazioni passate, li rende utili per situazioni in cui si usano dati sequenziali 
- Vanishing Gradiente:  da capire
- Struttura reservoir: 
	- Riserva di neuroni collegati in modo ricorrente
	- Proiezione randomizati del input 
- 


Regole per scegliere un buon reservoir operando sul [[Raggio spettrale|raggio spettrale]]  $\rho(\boldsymbol{W})$  dei pesi abbiamo che 
- $\rho$ vicino ad 1 per task che richiedono molta memoria
- $\rho$ non troppo vicino se il task richiede poca memoria



NRMSE:
$$E(\boldsymbol{y},\boldsymbol{y}_{target})=\sqrt{\frac{ \langle\|y(n)-\boldsymbol{y}_{target}(n)\|^{2}\rangle }{ \langle\|y_{target}(n)-\langle\boldsymbol{y}_{target}(n)\rangle\|^{2}\rangle}}$$
dove $\|\cdot\|$ e' la [[Norme Matriciali e Norme Vettoriali#Norma vettoriale|norma euclidea]]



una problematica del resorvoir computing e' l inabilita a lavorare con diversi time scale, cosa che migliora usando  leaking integrator echo state macchine (LI-ESM), ovvero si ha un modo per regolare il timescale e si usano neuroni con diversi time scale nello stesso reservoir