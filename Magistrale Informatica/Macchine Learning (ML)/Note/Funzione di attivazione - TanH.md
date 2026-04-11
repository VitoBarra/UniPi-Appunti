---
tags:
  - IIA
  - ML
Course: "[[Machine Learning (ML)]]"
Area: "[[Concetti generali del Machine Learning]]"
topic: "[[Intelligenza Artificiale (IA)|Reti neurali]]"
SubTopic: 
---

# Funzione di attivazione - TanH
---
La [[Funzioni di attivazione|funzione di attivazione]] __TanH__ o tangente iperbolica è definita come: $$tanh(x)=\frac{e^{x}-e^{-x}}{e^{x}+e^{-x}}$$
e la sua immagine (il suo output) è nel range  $[-1,1]$.
![[IMG - Funzione di attivazione - TanH.png]]

Questa è collegata alla [[Funzione di attivazione - Sigmoide|funzione sigmoidale]] tramite la seguente relazione :$$tanh\left(\cfrac{\alpha x}{2}\right)= 2\sigma(x,\alpha)-1$$