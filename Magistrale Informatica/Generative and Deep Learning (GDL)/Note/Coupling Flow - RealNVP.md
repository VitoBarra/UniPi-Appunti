---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Flow-based models
SubTopic:
---
# RealNVP
---
Le **RealNVP** (**Real-valued Non-Volume Preserving**) estendono l'idea di [[Coupling Flow - NICE|NICE]] sostituendo il coupling additivo con il **coupling affine**.

La forma tipica del layer e:

$$y_A = x_A$$

$$y_B = x_B \odot \exp(s_{\theta}(x_A)) + t_{\theta}(x_A)$$

Rispetto a NICE, il layer non si limita piu a traslare una parte delle variabili, ma puo anche scalarla localmente. Questo rende la trasformazione molto piu espressiva.

## Perche si chiama non-volume preserving
In NICE il determinante del jacobiano vale sempre $1$, quindi il volume locale viene preservato. In RealNVP questo non vale piu, perché il termine di scala puo espandere o comprimere localmente lo spazio.

Il log-determinante resta comunque semplice:

$$\log |\det J| = \sum_j s_{\theta}(x_A)_j$$

Quindi il modello guadagna espressivita senza perdere la trattabilita della likelihood.

## Architettura
Dal punto di vista pratico, RealNVP usa in genere:
- molti coupling layer in sequenza
- masking o permutazioni alternati
- una struttura **multi-scale**

La struttura multi-scale separa progressivamente parte delle variabili latenti, mentre le altre continuano ad attraversare nuovi layer. Questo migliora efficienza ed espressivita.
![[IMG - RealNVP multi scale Coupling Flow.png]]
![[IMG - RealNVP Masking and Squeezing.png]]

## Ruolo nei normalizing flows
Le **RealNVP** sono importanti perché mostrano un compromesso molto efficace:
- trasformazioni invertibili
- jacobiano trattabile
- possibilita di cambiare localmente il volume

In questo senso rappresentano un passo naturale oltre NICE e una base diretta per architetture successive come [[Coupling Flow - GLOW]].
![[IMG - RealNVP results.png]]
