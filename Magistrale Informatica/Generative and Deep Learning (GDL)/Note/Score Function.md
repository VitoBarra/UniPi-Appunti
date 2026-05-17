---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Score-based models
SubTopic:
---
# Score Function
---
La **score function** di una [[Distribuzione di probabilita|distribuzione continua]] $p(x)$ è il gradiente della **log-densità** rispetto a $x$:$$s(x) = \frac{\partial \log p(x)}{\partial x} = \nabla_x \log p(x)$$
L'idea intuitiva è distinguere tra:
- $\log p(x)$: misura quanto un punto $x$ sia plausibile secondo la distribuzione
- $\nabla_x \log p(x)$: indica in quale direzione bisogna muoversi a partire da $x$ per aumentare più rapidamente la probabilità
Quindi lo **score** dice in che direzione spostare $x$ per raggiungere regioni a densità più alta. Se $x$ si trova in una zona poco probabile, il vettore score tende a puntare verso zone più probabili.

Equivalentemente, lo score definisce un [[Campo vettoriale|campo vettoriale]] nello spazio dei dati: a ogni punto $x$ associa una direzione di salita della densità.