---
Course: "[[Machine Learning (ML)]]"
tags:
  - ML
  - NotFinisced
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic: 
---
# Teorema di convergenza del percetrone
---
il [[Percettrone|precetrone]] converge sempre ad una solutzione assumendo che lo spazio sia [[Linearmente Separabili|linearmente separabile]] 

in questo contesto linearmente separabile significa che 
__dato__ un training set TR di punti $(\mathbf{x}_i,d_i)$ con $d_i =+1$  o $-1$ e con $i=1\dots l$ dove $l$ è il numero di dati nel dataset.
__se__ esiste un vettore $\mathbf{w}^*$ tale che $$d_i(\mathbf{w^*x_i}) \geq \alpha \ \ \ \ \ a=\min_i d_i(\mathbf{w^*x_i})>0$$

