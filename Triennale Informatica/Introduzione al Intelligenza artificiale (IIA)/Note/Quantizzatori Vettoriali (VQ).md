---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Quantizzatori Vettoriali (VQ)
---
la __quantizzazione vettoriale__ è una tecnica per codificare una [[Manifolds|manifold]] di dati  $V \subset \mathbb{R}^n$ con [[Insiemi Matematici|insieme]] di [[vettori|vettori]]  $w = (w_1, \dots w_K)$ com $w_i \in \mathbb{R}^n$ detti __vettori di riferimento__

Un vettore dato $x \in V$ viene descritto con no dei __vettori di riferimento__ $w^*(x)$ tale che questo minimizzi l'errore di distorsione:$$w_{*}(x)=\min_{w_i} d(x,w_i)$$questo divide il manifold $V$ in sotto regioni che possono essere descritte come $$V_i = \left\{ x \in V \ |\  \; \|x - w_i\| \leq \|x - w_j\| \; \forall j \right\}
$$ ovvero le regioni sono fatte in modo che contengono tutti i punti che sono più vicini al punto $x_i$ secondo una data metrica, rispetto a tutti gli altri, queste regioni sono dette [[poliedri di Voronoi]]. ![[Pasted image 20250213191825.png]]
dove i segmenti sono i punti equidistanti tra i punti che definiscono le regioni adiacenti. 
