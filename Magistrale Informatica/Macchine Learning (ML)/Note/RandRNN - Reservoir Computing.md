---
Course: "[[Machine Learning (ML)]]"
Area: "[[Recurrent Neural Network (RNN)]]"
topic: "[[Intelligenza Artificiale (IA)|Reti neurali]]"
SubTopic: 
tags:
  - IA
  - ML
---
# RandRNN - Reservoir Computing
---
Cose che devo sapere
- [[Reti Neurali (NN)|Reti neurali]]: 
- __[[Recurrent Neural Network (RNN)|Reti neurali riccorrenti]]__ (RNN) : i neuroni mantengono memoria delle informazioni passate, li rende utili per situazioni in cui si usano dati sequenziali 
- Vanishing Gradiente:  da capire
- Struttura reservoir: 
	- Riserva di neuroni collegati in modo ricorrente
	- Proiezione randomizati del input 
- 




una problematica del resorvoir computing e' l inabilita a lavorare con diversi time scale, cosa che migliora usando  leaking integrator echo state macchine (LI-ESM), ovvero si ha un modo per regolare il timescale e si usano neuroni con diversi time scale nello stesso reservoir