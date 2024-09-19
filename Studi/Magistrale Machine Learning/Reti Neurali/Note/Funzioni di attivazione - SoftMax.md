---
Subject: "[[Intelligenza Artificiale (IA)]]"
tags:
  - IA
  - ML
Area: "[[Machine Learning (ML)]]"
topic: 
SubTopic:
---
# Funzioni di attivazione - SoftMax
---
**sia** $\boldsymbol{z}\in \mathbb{R}^n$ un vettore $n$ dimensione  
**allora**  *SoftMax* è una funzione $$SoftMax(\boldsymbol{z}) =\frac {e^{z_{i}}}{\sum _{j=1}^{K}e^{z_{j}}}$$
questa funzione mappa i valori del vettore in un range $[0,1]$ tale che valta 
$${\displaystyle SoftMax :\mathbb {R} ^{n}\to \left\{z\in \mathbb {R}^{n}{\Big |}z_{i}>0,\ \sum _{i=1}^{K}z_{i}=1\right\}}$$
ovver la somma di tutti gli elementi della mappa sommano ad 1 
questa viene usta nelle [[Reti Neurali (NN)|reti neurali]]  come [[Funzioni di attivazione|funzine di attivazione]] dei  [[neuroni artificioali|neuroni artficiali]] del ultimo layer  nel caso il problema che sista affrontando è un problema di classifazione  con piu di 2 classi 


 