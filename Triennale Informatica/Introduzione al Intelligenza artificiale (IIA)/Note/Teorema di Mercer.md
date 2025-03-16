---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Teorema di Mercer
---
Il **teorema di Mercer** è un risultato fondamentale nell'analisi funzionale e nella teoria delle equazioni integrali. È spesso utilizzato nel contesto delle macchine a vettori di supporto (SVM) e del metodo del kernel in apprendimento automatico. Il teorema fornisce una rappresentazione in serie per funzioni kernel definite positive su domini compatti.

## Enunciato del teorema

Sia $K(x, y)$ un **kernel continuo, simmetrico e definito positivo** su un dominio compatto $D \subset \mathbb{R}^n$, ovvero:

1. **Simmetria**:

   $$
   K(x, y) = K(y, x), \quad \forall x, y \in D.
   $$

2. **Definitività positiva**:

   $$
   \sum_{i=1}^{m} \sum_{j=1}^{m} c_i c_j K(x_i, x_j) \geq 0, \quad \forall m \in \mathbb{N}, \forall c_i \in \mathbb{R}, \forall x_i \in D.
   $$

Allora esiste una successione di **autovalori positivi** $\lambda_k$ e una famiglia ortonormale di **autofunzioni** $\varphi_k(x)$ tali che $K(x, y)$ ammette la seguente decomposizione in serie:

$$
K(x, y) = \sum_{k=1}^{\infty} \lambda_k \varphi_k(x) \varphi_k(y), \quad \forall x, y \in D.
$$

## Interpretazione e applicazioni

- **Base ortonormale di funzioni**: Il teorema garantisce che il kernel può essere rappresentato come una combinazione infinita di funzioni ortonormali pesate dai corrispondenti autovalori.
- **Riduzione dimensionale**: Questa decomposizione è alla base dell'Analisi delle Componenti Principali Kernel (KPCA), che generalizza la PCA ai dati non linearmente separabili.
- **Metodi del Kernel**: In apprendimento automatico, il teorema di Mercer assicura che una funzione kernel può essere scritta come un prodotto scalare in uno spazio di Hilbert di dimensione infinita, permettendo di lavorare implicitamente in spazi di alta dimensionalità senza doverli esplicitamente costruire (Trucco del Kernel).

## Esempio: Kernel Gaussiano

Un esempio classico di kernel che soddisfa le ipotesi del teorema di Mercer è il **kernel gaussiano o RBF**:

$$
K(x, y) = \exp\left(-\frac{\|x - y\|^2}{2\sigma^2}\right).
$$

Per questo kernel, il teorema di Mercer garantisce l'esistenza di una decomposizione in serie con autofunzioni e autovalori appropriati, il che lo rende particolarmente utile nei metodi di apprendimento automatico.

## Conclusioni

Il teorema di Mercer è un risultato chiave che connette le funzioni kernel con le serie di autovalori e autofunzioni, fornendo una solida base matematica per le tecniche di machine learning basate sui kernel. Questo permette di sfruttare proprietà di spazi di Hilbert di dimensione infinita senza doverli esplicitamente rappresentare, rendendo efficienti algoritmi come le SVM e la KPCA.
