---
Course: "[[Computational Mathematics for Learning and Data Analisys (CMLDA)]]"
tags:
  - CMLDA
Area: 
topic: 
SubTopic:
---
# Problemi di ottimizzazione convessi
---

$$
\begin{cases} 
 f(\mathbf{x}) \\
 g_i(\mathbf{x}) \leq 0, \quad i = 1, \dots, m \\
h_i(\mathbf{x}) = 0, \quad i = 1, \dots, p, 
\end{cases}
$$

$$\mathbf{x} \in \mathbb{R}^{n}$$
è il vettore delle variabili di ottimizzazione;

L'obiettivo della funzione è:$f: \mathcal{D} \subseteq \mathbb{R}^{n} \to \mathbb{R}$
ed è una funzione convessa;

Le funzioni di vincolo di disuguaglianza sono: $g_{i}: \mathbb{R}^{n} \to \mathbb{R}, \quad i=1,\ldots ,m$
e sono funzioni convesse;
Le funzioni di vincolo di uguaglianza sono: $h_{i}: \mathbb{R}^{n} \to \mathbb{R}, \quad i=1,\ldots ,p$
e sono trasformazioni affini, ovvero della forma: $h_{i}(\mathbf{x}) = \mathbf{a_{i}} \cdot \mathbf{x} - b_{i}$
dove $\mathbf{a_{i}}$ è un vettore e $b_{i}$ è uno scalare.
