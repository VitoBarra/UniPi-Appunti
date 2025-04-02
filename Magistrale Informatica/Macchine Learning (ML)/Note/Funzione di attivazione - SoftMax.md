---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Funzione di attivazione - SoftMax
---
**Sia** $\boldsymbol{z}\in \mathbb{R}^n$ un [[Vettori|vettore]] $n$ dimensione  
**allora**  __SoftMax__ è una [[Funzioni|funzione]] definita come:$$SoftMax(\boldsymbol{z},j)=\frac {e^{z_{j}}}{\sum _{k=1}^{K}e^{z_{k}}}$$
questa funzione mappa i valori del vettore in un range $[0,1]$ tale che valga 
$${\displaystyle SoftMax :\mathbb {R} ^{n}\to \left\{z\in \mathbb {R}^{n}{\Big |}z_{i}>0,\ \sum _{i=1}^{K}z_{i}=1\right\}}$$
ovvero la somma di tutti gli elementi della mappa sommano ad 1 
questa viene usta nelle [[Reti Neurali (NN)|reti neurali]]  come [[Funzioni di attivazione|funzione di attivazione]] dei __neuroni__ del layer di output nel caso il problema che si sta affrontando è un [[Algoritmi di Machine Learning|problema di classificazione]] con più di 2 classi, Funziona bene con la funzione di loss [[Cross Entropy|Cross Entropy]]




 