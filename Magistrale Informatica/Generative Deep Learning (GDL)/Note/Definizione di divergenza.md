---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Definizione di divergenza
---
La **Divergenza** è un operatore differenziale che misura il flusso netto uscente di un [[Campo vettoriale]] da un punto dello spazio. Essa quantifica quanto il campo si comporti localmente come una **sorgente** o come un **pozzo**.

Dato un [[Campo vettoriale|campo vettoriale]] $\mathbf{F} = (F_1, F_2, \dots, F_n)$ definito in $\mathbb{R}^n$, la divergenza è definita come la somma delle derivate parziali delle componenti del campo rispetto alle rispettive coordinate spaziali.$$\nabla \cdot \mathbf{F} = \sum_{i=1}^{n} \frac{\partial F_i}{\partial x_i}$$
Nel caso tridimensionale, per un campo $\mathbf{F} = (F_x, F_y, F_z)$ la divergenza assume la forma$$\nabla \cdot \mathbf{F} =
\frac{\partial F_x}{\partial x} +
\frac{\partial F_y}{\partial y} +
\frac{\partial F_z}{\partial z}$$Se $\nabla \cdot \mathbf{F} > 0$ il punto si comporta come una **sorgente locale**, mentre se $\nabla \cdot \mathbf{F} < 0$ rappresenta un **pozzo**.

![[IMG - divergenza.png]]
La divergenza compare nel [[Teorema della divergenza]] (o teorema di Gauss), che collega il flusso di un campo vettoriale attraverso una superficie chiusa con l’integrale della divergenza nel volume racchiuso.