---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: Machine Learning
topic: Reti Neurali
SubTopic:
---
# Funzione di attivazione - Sigmoidale
---
La __[[Funzioni di attivazione|funzione di attivazione]] sigmoidale ( o logistica)__ è un caso particolare di una [[Curve Logistiche|curva logistica]] ed è definita come $$\sigma(x,\alpha)=\cfrac{1}{1+e^{-\alpha x}}=\cfrac{e^{\alpha x}}{1+e^{\alpha x}}$$e la sua immagine (il suo output) è nel range $[0,1]$
![[Pasted image 20241227063802.png]]

Al variare di $\alpha$ si ha che 
- $\alpha \to 0$ si ha una retta funzione lineare
- $\alpha \to \infty$ si ha sempre di più una [[Linear Threshold Unit (LTU)|linear threshold unit]] (LTU)