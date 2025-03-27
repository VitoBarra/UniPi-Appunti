---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: "[[Recurrent Neural Network (RNN)]]"
SubTopic: 
---

# RNN - Transformer
---

## Alternative alle RNN: Transformer e Attention Mechanism

Le RNN presentano limitazioni nel parallelismo e nell'apprendimento di lunghe dipendenze. Per risolvere questi problemi, i **Transformer** sono stati introdotti nel 2017 con l'architettura **"Attention is All You Need"**.

L'idea chiave dei Transformer è il **meccanismo di attenzione**, che calcola una rappresentazione ponderata di tutti gli stati precedenti:

$$
\text{Attention}(Q, K, V) = \text{softmax} \left( \frac{Q K^T}{\sqrt{d_k}} \right) V
$$

dove:
- $Q$ è la matrice delle query,
- $K$ è la matrice delle chiavi,
- $V$ è la matrice dei valori,
- $d_k$ è la dimensione delle chiavi.


![[Pasted image 20250207235010.png]]


![[Pasted image 20250207235826.png]]