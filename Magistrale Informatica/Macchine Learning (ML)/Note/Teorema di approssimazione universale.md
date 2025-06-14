---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: 
topic: 
SubTopic:
---
# Teorema di approssimazione universale
---
__sia__
- $\mathbf{x} \in \mathbb{R}^n$ Un [[Vettori|vettore]] di input 
- Dato un errore $\varepsilon$
 __allora__ esiste una [[Funzioni|funzione]] $$h(\mathbf{x}) = f_k \left( \sum_j w_{kj} f_j \left( \sum_i w_{ji} x_i \right) \right)$$tale che l'approssimazione dell'errore $$|f(\mathbf{x}) - h(\mathbf{x})| < \varepsilon$$ sia valida per ogni  $\mathbf{x}$ nell'ipercubo.
![[Pasted image 20250101122118.png]]

Ovvero:    
- Una rete a singolo livello nascosto (con funzioni di attivazione logistiche) è in grado di generalizzare approssimazioni, ad esempio utilizzando serie di Fourier finite.
- Una rete MLP (Multilayer Perceptron) può approssimare qualsiasi mappatura input-output (arbitrariamente bene), a condizione che ci siano abbastanza unità nei livelli nascosti.

Questo è un __teorema di esistenza__ ma non da informazioni sul numero di unita necessarie ne tanto meno sul algoritmo di learning da usare.